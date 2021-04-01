---
title: "Programming Terrors Never End"
slug: programming-terrors-never-end
date: 2021-02-12T22:24:28-08:00
comments: true
categories: blogging
excerpt: null
header:
    feature: neon-cropped
    creditlink: https://www.flickr.com/photos/rebelcan/2309011771
---

I wanted to talk a bit about this tweet I saw the other day. The images are from
an article called ["Researcher hacks over 35 tech firms in novel supply chain attack"](https://www.bleepingcomputer.com/news/security/researcher-hacks-over-35-tech-firms-in-novel-supply-chain-attack/).

{{< tweet 1359478493386592267 >}}

I haven't really heard much about supply chain attacks before this, so lets
start with a quick intro.

## Supply Chain Attacks!

You could just go read [the Wikipedia
article](https://en.wikipedia.org/wiki/Supply_chain_attack), but I'll try
summarize.

When software is built, it is usually built with a bunch of
dependencies. Instead of writing everything from the ground-up every time,
developers use shared libraries. 

Say you're writing a website that needs to parse some input. Maybe you're
validating postal codes. Or phone numbers. Maybe you just need to check [if a
number is odd](https://www.npmjs.com/package/is-odd). But rather than writing
that code yourself, you go looking for a package. Someone else must have run
into this problem before, right? And if they were nice, they took their code,
bundled it up and put it where other folks can grab it to include in their
projects.

You could write and maintain your own library of stuff, of course.

But what if you don't know how to turn the math behind [the AES
algorithm](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) into
code? Or you don't know how to convert a PNG image to a JPEG, or a WAV to an
MP3, or one of the other thousands of file conversions you might have to care
about.

Or maybe you need to interface with the API for some company so you can send
mail, find the coordinates for an address, use an AI to tag an image, or one of
the hundreds of thousands of APIs out there that can be super useful.

For all of these things and more, there are packages out there to make your job
easier. Or maybe you just don't have the time! Maybe you need a captcha on your
website _right now_ and you don't have the time to implement one yourself. Plus,
using packages maintained by other people means that you aren't the only person
using it, which means you get stuff like:

* bug fixes!
* new features!
* optimizations!

Without having to do anything! Which is pretty awesome.

## Cool. So, Supply Chain Attacks?

![mr bean waiting](/images/mrbeanwaiting.gif)

So in order to use those packages you need two things ( well, three ):

* a place for information about those packages to live
* a way to define what packages you want to use in your code[^1]
* a tool that can use the file that defines what packages to go and grab those
  packages for you and put them where your code can use them
  
Pretty much every language these days has something that fulfills these
roles. NodeJS has NPM. Ruby has Gems. PHP has Composer. Python has PyPi. C# has
Nuget. Java has.... Maven? Go has modules[^2].

Anyways.

For this supply chain attack the researcher discovered, there's one more piece
we need:

Private repos.

Companies like being able to use packages for code they write themselves, but
maybe that code isn't something they want to (or are ready to) open source. Maybe it
contains too much secret sauce, or it's just not ready for the public to use, or
it's just so specialized there's no point in making it public.

So pretty much all of the packages managers have some way to say "hey, this
module is private and can be found at X". Or maybe you use a proxy that contains
the private packages, and will go reach out to the public service when it
doesn't have the package ( and might cache it if it's nice ).

But that's where the problem ( and the attack ) comes in.

The part of the code that would check if a package existed would either:

* default to the public repo first

**OR**

* default to the highest version, regardless of public or private

So this means that if I wrote some code that relied on the `secret-api-module`
private package and someone then created a `secret-api-module` _public_ package,
then when my package manager went to grab packages it'd grab the unsafe public
version instead of the private version.

You might think that grabbing packages doesn't happen very often -- maybe only
when I first install a package to use, right?

Nope.

See, a lot of companies use build servers that take care of building code[^3] so
that they can get notified if a new feature breaks old tests, or as part of the
deployment process. And to save space ( especially if a company has lots of
projects on the go ) these build servers don't keep old builds OR old package
downloads around. Every time a build happens they download all the dependencies
fresh. At the very least, part of deploying new code to production happens on a
build machine so that you know that the code in production isn't tainted with
weird libraries or stuff from a developers machine.

## Yikes

![don't like that](/images/nopedontlike.gif)

Yeah, it's not great. And that's where the name "supply chain" comes from --
because you're not attacking the code in production via some bug, you're
literally attacking the supply chain that takes place before the code even goes
to production.

What's new about this variation is that previously attackers would have to
create packages based on misspellings ( "goggle-map-api" instead of
"google-map-api", for example ) or giving bad info directly to a
developer[^4]. Now all that's required is guessing what names a company might
use for private packages.

## This Is Why Programming Sucks

Yup.

And this is what I actually wanted to write a post on. Being a programmer kind
of sucks some days.

It means eventually coming to terms with the fact that you could
write code to the best of your ability, using all the best practices like
tests and feature flags and whatever else -- and still have your code taken
hostage. 

You kind of just have to live with the fact that your code sits on a mountain of
other peoples code. For example, thinking about some stuff I've got running in
production right now, all of this stuff has to be secure and reasonably bug
free:

* the packages used directly by the code 
* any of the tools used during the build or deploy process 
* any of the [Docker][1] images or their dependencies
* any OS packages installed during the docker image build package
* the OS of the docker image 
* the [Kubernetes][2] software 
* the OS & packages on the [GCP Compute Engine nodes][3] Kubernetes runs on 
* the various layers between those nodes and the public internet ( the Google
  Cloud stack )
* everything between Google Cloud and a users phone
* everything on a user's phone

And that's the **simple** list. And there are probably at _least_ a handful of
unknown ( or known and simply unpatched ) vulnerabilities in that stack of things
that could be used to take control of my stuff running in production and make it
dance a merry jig.

![sad dance](/images/saddance.gif)

And yeah, sure, you could write everything yourself and maybe just depend on the
standard library. But even then you can get screwed; there are many, many, many
stories of some critical part of the standard library being hilariously broken (
or just broken under specific circumstances ). 

Or if you're like me, you're too lazy or not smart enough to write everything
you need yourself. So you have to rely on packages, and just hope that
everything is secure _enough_ so that if someone pokes at your code in
production it looks too hard to be worth it.

And honestly, that's probably the best you can hope for. There's plenty of
unpatched old Wordpress installs just _waiting_ to become part of a botnet,
so unless you're Google or Netflix[^5] then you're probably not worth the effort
of actually doing an in-depth attack.

Most companies aren't multi-billion dollar companies that are worth the time and
effort of sophisticated[^6] attacks. When you hear about some small-to-medium
business being hacked, the actual cause is probably one of the following:

* someone used a bad password
* someone plugged in a USB key that had malware on it 
* someone got [phished](https://en.wikipedia.org/wiki/Phishing)
* some code with an unknown or unpatched vulnerability was exploited
* someone was incredibly stupid and [left a laptop with critical information
  where it could get taken with very little effort](https://www.cbc.ca/news/canada/north/nwt-stolen-laptop-summary-1.5059552)

Basically, either low-effort hacks that can be easily automated and then thrown out
into a botnet that will just run the attack against every computer connected to
the internet -- or social engineering.

And our job as programmers is to just try our best, apply patches to security
holes in a timely manner, and pray we're not sitting on a mountain of unknown
vulnerabilities ( or that we've got really understanding bosses ).


[1]: https://www.docker.com/
[2]: https://kubernetes.io/
[3]: https://cloud.google.com/

[^1]: Hopefully you also get to define what version you want too
[^2]: Which (I think) side-step the supply chain attack we're talking about here.
[^3]: Maybe just when a PR happens, or maybe on every commit, or maybe just every hour -- point is that pulling packages can happen any time.
[^4]: Basically telling someone on a forum or in a chat that "this package will totally solve your issues"
[^5]: Or [CD Project
    Red](https://www.bleepingcomputer.com/news/security/cd-projekts-stolen-source-code-allegedly-sold-by-ransomware-gang/)
[^6]: And [not so sophisticated](https://www.csoonline.com/article/2124681/what-is-social-engineering.html)
