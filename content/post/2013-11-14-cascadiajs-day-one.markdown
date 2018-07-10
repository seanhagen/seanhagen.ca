---
categories:
- javascript
- learning
- conference
- cascadiajs
comments: true
date: 2013-11-14T00:00:00Z
title: CascadiaJS Day One
url: /2013/11/14/cascadiajs-day-one/
---

Another live blog! This time, it's Day One of [CascadiaJS][1]!

<!--more-->

----------------------

**9:07am**

I've arrived at the venue, got my pass, and grabbed some breakfast. They had a nice spread of fruits, muffins, juices, and coffee. The venue is already pretty packed, but I'm able to grab a decent seat near the back of the room. The set-up is a bit different than I was expecting. I saw a tweet from the Rackspace guys saying that they were setting up their booth -- so I was expecting a few booths, showing off different stuff. It turns out that Rackspace is the only company with a booth set up. I don't really care that much, it just means there's less chance for awesome free swag. Oh well.

----------------------

**9:24am**

The Wifi password is put up, everyone attempts to connect, WiFi promptly dies.

----------------------

**9:30am**

The conference kicks off! By show of hands, most of the people are attending CascadiaJS for the first time. The logo from last year was kinda cool, but definitely kind of "programmer design".

Apparently, CascadiaJS is supposed to be an "intimate, single-track conference".

Also, definitely thinking I should get a MacBook. My lap is starting to get kinda hot thanks to my laptop not being so good with the whole "dispersing heat" thing.

----------------------

**9:41am**

The keynote! The MC starts off with some good jokes.

The keynote speaker is [Glen Lougheed][2], talking about the awesomenes that is JavaScript and the future ahead of us a JS devs.

Skype apparently now accounts for 30% of the call volume made -- in the _world_.

----------------------

**10:08am**

The keynote was awesome, but unfortunately the power doesn't seem to be working. I'm going to have to turn off my laptop before it dies ( the battery in my laptop suuuuuucks ).

----------------------

**11:14am**

The power bar I'm hooked into is working again, so back to this! There were two great presentations to start off. The first one was from [Chris Dickinson][3], and he was talking about parsers in JavaScript. He had a couple of really cool tools that let you use a CSS style syntax for grepping through code to find things. He showed off a tool that lets you write a pretty simple linter to check your code for standards violations. I'm thinking that could be pretty useful at work.

The second presenter was a [Zach Bruggeman][4] 16-year old. He talked about how JS is a great language for getting teenagers ( and even younger kids ) interested in programming. A good point he made is that JS has a really quick "zero to hello world" factor, and a pretty small "hello world to whoa" factor too. To start working with JS all you need is a text editor and browser, both of which come with just about every computer on the planet. Going from "hello world" to "whoa" ( something that shows off how awesome a language can be) is pretty short too, as there are tons of awesome demos out there on how to do WebGL, audio, even game programming using JS.

Now I'm just waiting for the next round of presentations. I think there's a single presentation, and then we lunch.

\* looks at schedule \*

That's correct!

Apparently today's lunch is being provided by [Sauce Labs][5], so kudos to them.

----------------------

**11:30am**

Next up, a talk about web components and web audio, being presented by [Soledad Penadés][6].

New emoticon: \*\o/\*.

Talking about getting proper audio in the browser, with Adobe's Make Noise initiative. We got things like the <audio> tag ( and associated hacks ), Firefox's AudioData, and Chrome's Web Audio. Web Audio ended up winning, apparently because it was modular, compared to AudioData being "just a buffer".

Chrome's Web Audio got chosen by W3C to be the official web audio API.

Web components == custom DOM elements, which is pretty awesome. They can have custom behaviour, custom appearance, and a few other things. They can be pretty powerful.

Soledad shows off the web component that she created that lets you build a synthezier using HTML tags, which is amazing.

I really need to find the code for this and send it to a few friends that would flip out.

Another awesome things about web components: you can style them with CSS!

Check out this awesome project on [GitHub][7]

----------------------

**12:02am**

Apparently there's one last talk before lunch!

This talk is "Making WebRTC Awesome" by [Henrik Joreteg][8].

I'll admit, I've never heard of WebRTC, apparently I need to do some more research.

At it's core, WebRTC, is a peer connection:

    new RTCPeerConnection()

It's low-latency peer-to-peer networking IN THE BROWSER. Which is pretty damn awesome. With WebRTC, you can build a **TELECOM** in JavaScript. Holy crap.

Henrik helped build a service called [Talky.io][9].

You can use WebRTC for video, audio, or both. Even screensharing.

Things people can ( or have! ) built with WebRTC
- surveillance systems
- baby monitors
- remote-controlled electron microscopes
- intercom systems
- always-on office portals
- distributed team collaboration
- peer-replicated broadcasting
- pirate radio

Data channels are aparently a bit half-baked, but are amazing ( apparently ).

- File transfers! [ShareFest.me][10]
- Web-based bit torrent! [Webtorrent][11]
- Peer-seeded CDN! [PeerCDN][12]
- Multi-player WebGL games! [Mozila Hack][13]

Makes a good point about the big web companies being the next generation of telecoms. Facebook, Google, Microsoft, Apple -- FB Messenger, Hangouts, Skype, and Facetime are competing with the telecoms of today.

Federation is the next step for these companies. Until you can use your Facebook account to chat with someone on Google Hangouts, these technologies won't _really_ take off as new standard of communication. Look into something like [OTalk][https://otalk.im].

A great talk, and has given me a bunch of ideas.

----------------------

**12:27am**

Lunchtime! Provided by La Taquira.

----------------------

**2:32pm**

All done lunch, time for some more presentation. Apparently some free swag -- a Twilio umbrella, actually pretty useful in Vancouver.

The first talk of the afternoon is "The Node.js Event Loop", by [Stephen Belanger][14]

I turn away for two seconds, miss the first three slides, apparently.

We're talking about the Nodejs event loop. Callbacks are _not_ magically async. Async doesn't equal fast, it means _efficient_. Batching operations is always a good idea. Break down your code into the smallest unit possible, and batch those units when possible.

This guy is talking about something I'd love to learn more about, but he's really not a great presenter. His slides aren't well made ( way too small of a font for code examples ), he goes through the slides much too quickly, and is basically just reading off the slides.

----------------------

**2:51pm**

Next talk is "Computer Science Through Streams", which already sounds pretty interesting. The speaker is [Tom Buchok][15].

Backpressure: the rate at which file I/O happens is always going to be faster than network I/O. It's basically the ability to quickly read ahead in a file to get the next chunk to send out, while still waiting for the current chunk to get sent over the network.

----------------------

**3:07pm**

My computer crashed ( no idea why ), but thankfully I didn't seem to lose much. Unfortunately, I seemed to lose a bunch of notes I had been taking on the side. Oh well. Back to blogging!

I'm finding that some of these talks are really great, showing off some great/awesome/cool/neat tech. Things that I'd like to play around with, or things that I've been thinking about learning. Or maybe the presenter is just really good at grabbing my attention and gets me to pay attention.

However, I'm finding that some of the talks are not so great. Some of them fail to grab my attention, or the slides aren't well put together, or the speaker just isn't exactly the right person to be doing a presentation.

Still having fun overall though.

----------------------

**3:19pm**

Taking a short break while the next presenter gets ready.

----------------------

**3:21pm**

Next talk is apparently about "Programming Really Big Computers", from the glance I got at the first slide while the next presenter sets up.

----------------------

**3:22pm**

I got the title right. It's a talk by [Neuman Vong][16], who works at Twitter, which is awesome. He's talking about using NodeJS with cluster programming, whether it's spreading computation over all the cores in a CPU, or across multiple compute nodes.

I love how he refers to accidentally waking up all the threads at once as "the thundering herd problem".

Of course he goes and reminds me that I really want to learn Erlang -- and that reminds me I really want to learn Go, Lisp, Haskell, and a few other languages.

Towards the end of his presentation, he shows off some pretty neat stuff on how to create a master-slave messaging system. If you want to take a look, you can check out his slides [here][17].

----------------------

**3:57pm**

Break time!

----------------------

**4:20pm**

Special announcement!

Apparently there's a hacker olympics happening tonight! It's apparently nothing like your regular hackathon. It sounds like a ton of fun, I'm looking forward to it!

The next talk is by [Brad Bouse][18], about "Make Art Not Money". He co-authored a book with his wife that is an augmented reality book of poetry, which is pretty awesome.

Brad shows off some pretty neat demos using JS and WebRTC. I'll try and get links and post them here later.

He makes a good point in one of the slides: no mouse interaction! What do you do when you come from a world where everything relies on a single point of interaction? Moving to a world where you use something like the Leap Motion, Kinect, or other sensing hardward and instead of getting just a single point of interaction, but tons of points including things like scale, translation, and rotation could be brain wrinkling.

![Some image](http://www.quickmeme.com/img/1c/1cba060cd8b4e4b2151808a105afe916d8145d8084e6cf5e959aad3eca02e7d5.jpg)

Gestures are also a whole different ball game. So much to think about. I'm not sure my brain could handle trying to program something like that.

Some takeaways:
- performance is really important
- many atomic actions <= controlling memory leaks
- control event flow <= multiple libraries interacting can get confusing
- interface problem solving <= there's no click ( no mouse! )
- abstraction

If you want to check the slides, they're available [online][wholepixel.com/cascadia]!

----------------------

**5:01pm**

Next presentation! "High-performance WebGL Apps With LLJS And ASM.js", by [James Long][19].

...This actually sounds pretty awesome.

----------------------

**5:07pm**

This talk is way to interesting to take notes during it, I'm just going to link up the slides later.

----------------------

**5:36pm**

So awesome. Also the first presenter that I could tell they were using Emacs.

Next speaker is [Nathan Vander Wilt][20], talking about "Building web apps with [D3.js][21]". This one should be interesting, as we're using D3.js at work, so I'm hoping to learn a few cool things.

----------------------

**5:50pm**

Again, this talk is too interesting to take notes, so I'll post up a link to the slide later.

----------------------

**6:07pm**

Registration for Hacker Olympics! Dinner! Hoodies!

That's it for now, I may blog some more during the Hacker Olympics, but I'm not sure.


[1]: http://2013.cascadiajs.com/
[2]: https://twitter.com/glougheed
[3]: http://2013.cascadiajs.com/speakers/chris-dickinson
[4]: http://2013.cascadiajs.com/speakers/zach-bruggeman
[5]: https://saucelabs.com/
[6]: https://twitter.com/supersole
[7]: https://github.com/sole/audio-tags
[8]: https://twitter.com/HenrikJoreteg
[9]: http://talky.io
[10]: https://www.sharefest.me
[11]: https://github.com/feross/webtorrent
[12]: https://peercdn.com
[13]: hacks.mozilla.org/2013/03/webrtc-data-channels-for-great-multiplayer
[14]: http://2013.cascadiajs.com/speakers/stephen-belanger
[15]: http://2013.cascadiajs.com/speakers/tom-buchok
[16]: http://2013.cascadiajs.com/speakers/neuman-vong
[17]: https://docs.google.com/presentation/d/1v0YZeffzYGyIPz4_byDek3syFTafhYvlTyZOBH-okuw/pub?start=false&loop=false&delayms=3000#slide=id.p
[18]: http://2013.cascadiajs.com/speakers/brad-bouse
[19]: http://2013.cascadiajs.com/speakers/james-long
[20]: http://2013.cascadiajs.com/speakers/nathan-vander-wilt
[21]: http://d3js.org
