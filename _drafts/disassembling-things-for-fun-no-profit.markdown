---
layout: post
title: "Disassembling Things For Fun ( No Profit )"
date: 2014-01-10 00:08
comments: true
categories: [electronics, hacking, parts]
---

When I got my Arduino Uno, it made me realize that I've got a ton of stuff laying around that could supply me with parts. For the longest time I've had a bin of old cell phones, mp3 players, and some other random things that I was thinking of just tossing or taking to a pawn shop. When I got the Arduino though, I realized that it's a great source for quite a few things:

* surface mount components ( mostly resistors )
* LEDs
* LCD screens ( of varying sizes )
* SIM card holders
* audio jacks
* buttons of all shapes and sizes and functionality
* motors! ( especially important if I want to build a 3d printer! )
* and a few other bits

Some of the things I've taken apart: a few old cell phones, an old mp3 player that apparently never worked, a DVD drive, a printer ( rescued that one from the electronics bin at work ), and two old video cameras. The last four are what I'm most excited about right now. Sure, the cell phones have some cool parts in them, but the project at the top of my list right now is a 3d printer, so the printer and the cameras seemed to have quite a few awesome parts.

I got lucky with the printer too -- it was a combination printer/scanner that apparently didn't work. I've got at least one awesome motor + gear belt out of it, so it's a win for me!

Let's take a look at some of the awesome stuff I found.

<!-- more -->

First up, the lenses and image sensors from the video cameras!

[{% img flickr-link http://farm8.staticflickr.com/7338/11866578136_2ae6751bdc.jpg 250 250 "Lens Assembly Bottom" "Lens Assembly Bottom" %}][1]
[{% img flickr-link http://farm8.staticflickr.com/7330/11865729775_0b12546132.jpg 250 250 "Lens Assembly Side" "Lens Assembly Side" %}][2]
[{% img flickr-link http://farm6.staticflickr.com/5475/11865993803_9db7bf6ee7.jpg 250 250 "Image Sensor" "Image Sensor" %}][3]

I'm not even sure I want to take the motors off of these. Who knows, maybe having some auto-focus lenses for another project may come in handy? The image sensor I think could be used for something pretty cool.

These two parts came from the printer:

[{% img flickr-link http://farm6.staticflickr.com/5511/11865707095_c98bc50147.jpg 500 500 "What?" "What?" %}][4]

I have no idea what the two circles are for. The glass tube is a halogen light bulb, and sat inside a metal tube. This light bulb would heat up the tube enough to cause the toner to bond with the paper as it passed by ( at least, that's my understanding of how those kinds of printers work ). I think the two black round things were attached to the same roller that the halogen light bulb was in, but I don't quite remember -- my fault for not documenting the disassembly process better. Anyways. I'd like to figure out what those are, because they may come in handy.

[{% img flickr-link http://farm6.staticflickr.com/5537/11865716415_9fddef2841.jpg 500 500 "Stepper!" "Stepper!" %}][5]

This is one of the parts I'm happiest to get from the printer -- the stepper motor of the built-in scanner part. It comes with a belt and a wheel for the opposite end. I'm not sure if the motor is powerful enough to give me lots of speed, but I think it might be enough to drive one of the axis of my 3d printer! Woo!

[{% img flickr-link http://farm4.staticflickr.com/3744/11865709155_cd645a3358.jpg 500 500 "Scanner Head" "Scanner Head" %}][6]

This is the actual scanner part of the scanner. I'm thinking I could use this to make a hand-held whiteboard scanner, which could come in handy at work. Or at home. I think this part might be one of the trickiest to work with -- I'm a bit worried that the amount of data coming from it will require slightly more power than your regular off-the-shelf ATmega can provide. I could be wrong though, there might be one that can handle it. It'll just take some research and experimentation to find out!

[{% img flickr-link http://farm4.staticflickr.com/3667/11866147704_4f793dd78a.jpg 500 500 "Electromagnet" "Electromagnet" %}][7]

I got two of these from the printer. I'm fairly certain they're little electromagnets that produce a magnetic field when you pass a current through them. This one is upside down in the picture, that spring you see is supposed to keep the piece of metal pulled down. Once I get one working, I'll post a video so it's more clear.

[{% img flickr-link http://farm4.staticflickr.com/3724/11865710505_80e5b75665.jpg 500 500 "Stepper Motor!" "Stepper Motor!" %}][8]

Another stepper motor! I think this came from one of the video cameras. What I really like about this one is that it comes with a pin out!

I've saved the best for last:

[{% img flickr-link http://farm8.staticflickr.com/7348/11866581366_36445caa0e.jpg 500 500 "Cathode Ray Tube" "Cathode Ray Tube" %}][9]

It's a tiny little [cathode ray tube][10]! This was the thing that produced the image for the older video camera when you looked into the eyepiece. Basically, it's the same thing that used to produce images for TV screens, just really tiny. One of the first things that came to mind is using it to make either an oscilloscope or the viewer for a microscope. Not sure. Probably requires quite a few amps though.

There might also be some fun stuff I could do with just the electron gun part, but I think I'm going to try and keep it intact for now. Plus, I don't really want to try to create a vacuum powered explosion in my apartment.

You can see a few more photos of stuff I scavenged on [the set on Flickr][11]. I also recieved my order from [Adafruit][12] in the mail last night, so this weekend I'm going to try and put those things together -- photographing and taping the whole process, so you guys can see how well ( or how bad ) I do.

On a pretty unrelated side-note -- I think after using both Adafruit and [SparkFun][13], I'm a much bigger fan of SparkFun. Their site is just easier to use -- it's faster ( ESPECIALLY when adding something to a wish-list ), has more functionality, and I feel that it's just better designed. I haven't had to dive into the world of DigiKey or Mouser to find stuff yet, so I'm thankful for that.

[1]: http://www.flickr.com/photos/rebelcan/11866578136/in/set-72157639604009836
[2]: http://www.flickr.com/photos/rebelcan/11866125534/in/set-72157639604009836
[3]: http://www.flickr.com/photos/rebelcan/11865993803/in/set-72157639604009836
[4]: http://flic.kr/p/j5wRjP
[5]: http://flic.kr/p/j5wU6v
[6]: http://flic.kr/p/j5wRWk
[7]: http://flic.kr/p/j5z7iw
[8]: http://flic.kr/p/j5wSkB
[9]: http://flic.kr/p/j5Bkds
[10]: http://en.wikipedia.org/wiki/Cathode_ray_tube
[11]: http://www.flickr.com/photos/rebelcan/sets/72157639604009836/
[12]: http://adafruit.com
[13]: http://sparkfun.com
