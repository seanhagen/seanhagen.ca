---
categories:
- javascript
- learning
- conference
- cascadiajs
comments: true
date: 2013-11-15T00:00:00Z
title: CascadiaJS Day Two
url: /2013/11/15/cascadiajs-day-two/
---

Last day of the conference! I'm a little beat from yesterday. We had the [Hacking Olympics][1], and while my team didn't place it was still a ton of fun. Time to start this thing!

<!--more-->

----------------------

**9:02am**

Getting everything started. First talk is from [Charles Bihis][2], and his talk is "JavaScript Puzzlers: Puzzles to Make You Think". This sounds interesting.

So what is a "puzzler"? It's a simple programming puzzle that demonstrates or exploits weird behaviorus and quirky edge-cases that are part of the language specification.

Side note: it seems about a little less than half of the attendees work mostly on the back-end, which is kind of awesome.

First puzzler is interesting. Code below:

        (function(){
            var values = [7,4,'13', Infinity, -9];
            for ( var i =0; i< values.length; i++){
                if (isOdd(values[i])){
                    alert(values[i]);
                }
            }
        });

        function isOdd(num){
            return num % 2 == 1;
        }


What should that output?

{% spoiler "It will alert 7 & 13. This is because (-9 % 2) returns -1" %}

Side note: that spoiler is powered by a [plugin I built today in a few minutes for Octopress][15]!

I'm not going to keep typing out these examples, so I'll try to find a link to the slides to post. I definitely recommend taking a look, because so far they're pretty awesome.

----------------------

**9:42am**

The next talk is apparently called "EMCAScript Regrets", by [David Bruant][3], which should be interesting.

Regrets are parts of a technology (HTML,CSS,JS,DOM,etc) that we wish could be removed, but have to stay for various reasons.

Ideally, specs would come first. In reality, specs are usually written last -- _after_ there are tons of implementations sitting out on the web.

Overall, a great talk.

----------------------

**10:06am**

Next talk is about "Bringing Crypto To The Masses", by [Matthew Bergman][4].

So far an interesting talk. A bit bombastic, but fun.

Most important part of this talk:

Cryptography is about keeping information secret **till it's no longer of use to adversaries**.

A pretty good talk, but he seemed a little obsessed with his hat ( and how objectively awesome it was ).

----------------------

**11:26am**

Missed some of the next talk because I took a while grabbing something to drink from the corner store, but it was about hardware hacking and using JavaScript to control things like the Arduino.

The talk was "Where does the JavaScript run, anyway?", by [CJ Silveio][5].

Some pretty awesome stuff in this talk, about how to use [Johnny Five][7] to use JS to control an Arduino or other similar devices.

----------------------

**11:30am**

The next talk is "So you want to build a robot?", by [Raquel Velez][6].

Talking about what exactly a robot is, the different types of robot ( remote controlled, semi-autonomus, autonomous ).

This talk is really fun, she's got lots of energy and the talk is pretty great.

Side note: I'm stuck behind a tall guy who sat down during the last talk, so now it's a bit hard to see.

She brought along a tiny robot (BatBot!) that can find it's way out of a paper bag, and the code was written in JavaScript. It was pretty awesome.

----------------------

**12:01pm**

LUNCH!!!

----------------------

**12:39pm**

Lunch was not as awesome as yesterday. Oh well. ( If you're wondering, it was Roaming Dragon ).

----------------------

**1:32pm**

Maybe it's because the chairs here suck, maybe it's because I'm not a social butterfly, but I really wish they'd start the conference back up. I'm not a fan of sitting here waiting, because seriously, my back is killing me.

----------------------

**1:57pm**

Getting ready for the next presentation. Saw the first slide for a second, had something about rum on it. Now I'm definitely curious.

----------------------

**1:59pm**

It's actually called "Six Bottles of RUM: Surprising stores of real world mobile performance", by [Peter McLachlan][8]. RUM actually stands for Real User Monitoring ( not the delicious beverage ).

> A 1 second delay in page response can result in a 7% reduction in conversions.

Which is important, even if you're not running an e-commerce site.

Mobile speeds don't impact performance very much. Latency is what's important, not so much bandwidth.

Some of the usual performance advice tidbits don't always apply. They might not apply to every site. Some are even anti-patterns.

RUM is about:
- collecting data on how a web page /application works in the real world by instrumenting points of interest
- key advantages:
 - way more scale than is possible in synthetic testing
 - more comprehensive (often surprising) results

Good point about header size: keeping the headers small lets the server handle the request with the first packet, instead of having to wait for multiple packets to arrive.

A good idea for serving static assets, is to serve them from a domain that never uses cookies, to avoid paying the cost if you have huge cookies.

Sharding domains ( hacking your domains so that the browsers can make more requersts ) is not exactly a good idea, because you may have to pay the cold start-up connection cost for each connection.

HTTP 2.0 is going to take sharding from a "you probably shouldn't do this" to a "definitely don't do this" with connection multiplexing.

With images, data-uri doesn't perform as well as just using sprite sheets, although this is something browser vendors are looking into as there isn't a clear reason why that is.

[Steve Souders][9] did an experiment on using CSS selectors in a few different tests. For desktop browsers, there's not much point in optimizing selectors in CSS. On mobile, it's much the same, although Firefox just blows the other mobile browsers away. So CSS optimizations are less about performance, and more about refactoring for readability.

That's not to say that there's nothing that you should optimize. A good example is don't use the '*' selector if you don't have to, especially when using GPU heavy rules.

Overall, this was a pretty good talk, pointing out some areas to watch out for when building sites or applications for mobile devices.

----------------------

**2:34pm**

[Dave Whinnery][10] from Twilio, talking about running JS on iOS7 -- specifically writing native iOS applications using JavaScript.

Not something I'm super interested in, but there's some cool info. If you want to check out the slides, they're [available online][13]

----------------------

**2:44pm**

He's writing a "short" iOS demo in ObjectiveC to show off how to write JS in iOS applications. ObjectiveC is **verbose**. It's not exactly simple.

----------------------

**2:54pm**

Showing of the [Apple iOS Sprite Kit][11], which is this really awesome library that lets you easily make games in JavaScript for iOS devices.

----------------------

**2:57pm**

Time for another break, time to go talk to the Rackspace dudes about some questions I have about the [Rackspace Dev Trial][12]

----------------------

**3:16pm**

Got some good info from the Rackspace guys ( thanks [Ken Perkins][14]! ). Apparently, if you're running a completely Open Source project, Rackspace will help you out by hosting the project for free! That's pretty damn awesome. So if you create a project that is open source, but requires a bunch of servers to demo it ( or host the service that people use ), Rackspace will help you get that all sorted out.

----------------------

**3:28pm**

The next speaker is getting ready, and it's [Joe Sepi][16], talking about "Front End Dependency Management". This is definitely one I'm interested in, because it's something we've been talking about at work and the best way to handle it.

<slide link>

Some of the benefits of solving dependency problems:
- performance
- stability
- reuse
- sanity!

One thing about requirejs: how do people handle a module that has a TON of dependencies?

Browserfy definitely cuts out a lot of the RequireJS/AMD boilerplate, which is pretty nice. The downside is that the Browserfy 'require' calls are synchronous, so they're blocking -- something to beware of if you call 'require' inside of a function. RequireJS does have a different way of writing the modules, using a sort of hybrid approach. The hybrid approach does make the loading of things in ( for say, a Backbone view ) a lot simpler.

----------------------

**3:54pm**

Next up is [Dave Foley][17], talking about "Event is the new Model". He's a "frustrated ex-programmer" ( ie, CTO at a tech start-up company ).

Starts off by making the crowd angry by saying that CoffeeScript is better than JavaScript. I agree with him there, though -- it is way better.

A new novel idea: storing events, not snapshots. This is in regard to models, the M in MVC. An event is immutable, it can't be changed or deleted.

This would be perfect for a lot of stuff that we're doing at [BBTV][18]. It would make it so much easier to do analytics on various things -- instead of having to look at a history log, you have an event log.

A good joke about MongoDB ( not caring if the data is there when you go back to it ).

Overall, a pretty awesome talk, with some stuff that could be applicable at work.

----------------------

**4:26pm**

"Stop Breaking The Web", by [Tom Dale][19], which sounds like it could be pretty awesome. This is one of the guys behind [EmberJS][20]... and he kind of looks like the mascot for EmberJS.

Talking about measles, and how back when telephones first started being "a thing" measels was responsible for the creation of phone numbers.

He makes the a good point that phone numbers and URLs are pretty closely related, they're both addresses for things ( either people or documents ).

Without URL's you can't do the following:
- sharing
- collaboration
- bookmarking
- forking
 - opening up a new tab to save the state of the application when there's something you need to handle, but can't do right away

> You're only a web developer if you're building an application that uses URLs

Pretty brain-wrinkling to think about.

I've got to take a closer look at EmberJS, it looks like it's gained a few awesome features since I last looked at it.

Some great ideas that I'm going to be bringing back to work.

----------------------

**4:57pm**

Looks like we've reached the final talk. Next up is the closing keynote by [Jenn Turner][21]!

----------------------

**5:02pm**

Keynote topic? "Farewell CascadiaJS".

To start off? Breakdance miming!

And then into a pretty interesting talk. No way to take notes. I'll link the video later.

She talks about imposter syndrome, which I totally get. I mean, I'm sitting at a conference full of really smart people, and there is part of me that's not really sure I belong here.

----------------------

**5:45pm**

So that's the end of the conference! There's an after-party, but I'm done. I need to go home and take a nap.

I'll do a post tomorrow on what I think about the conference, once I've had some time to digest everything.








[1]: http://thehackerolympics.com/
[2]: http://2013.cascadiajs.com/speakers/charles-bihis
[3]: http://2013.cascadiajs.com/speakers/david-bruant
[4]: http://2013.cascadiajs.com/speakers/matthew-bergman
[5]: http://2013.cascadiajs.com/speakers/cj-silverio
[6]: http://2013.cascadiajs.com/speakers/raquel-velez
[7]: https://github.com/rwaldron/johnny-five
[8]: http://2013.cascadiajs.com/speakers/peter-mclachlan
[9]: http://www.stevesouders.com/blog/2009/03/10/performance-impact-of-css-selectors/
[10]: http://2013.cascadiajs.com/speakers/kevin-whinnery
[11]: https://developer.apple.com/LIBRARY/IOS/documentation/GraphicsAnimation/Conceptual/SpriteKit_PG/Introduction/Introduction.html
[12]: http://developer.rackspace.com/devtrial/
[13]: http://www.slideshare.net/kwhinnery
[14]: https://twitter.com/kenperkins
[15]: https://github.com/seanhagen/octopress-spoiler-tag
[16]: http://2013.cascadiajs.com/speakers/joe-sepi
[17]: http://2013.cascadiajs.com/speakers/dave-foley
[18]: http://broadbandtvcorp.com/
[19]: http://2013.cascadiajs.com/speakers/tom-dale
[20]: http://emberjs.com/
[21]: http://2013.cascadiajs.com/speakers/jenn-turner
