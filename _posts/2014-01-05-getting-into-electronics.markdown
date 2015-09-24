---
layout: post
title: "Getting Into Electronics"
date: 2014-01-05 15:19
comments: true
categories: [arduino,hacking,electronics]
---

I got something pretty awesome for Christmas this year:

![Arduino Box](/images/arduino.jpg)

<!-- more -->

I've been wanting to get one for a while now. I've got a ton of project ideas that I've been thinking about for a while that would require the use of one ( or more Arduinos ), and now I can start hacking away at some of them. What are the project ideas? Well, I'm so glad you asked, because I'm going to tell you.

The first one I'm going to tackle is a stop-light style display that will check in on the status of a few [Jenkins][1] builds at work so that I can get a quick overview of how the various jobs are doing. It's not going to be useful for super long though. Right now there are only two projects really using Jenkins, and each has three jobs. That's probably going to expand to more jobs per project pretty soon, and there are going to be a few more projects starting up soon as well. I've got a pretty good idea of how to hook it all up. I'm going to be using a few 8-bit shift registers hooked up in series to drive all the LEDs that will make up the traffic light style displays, as well as an Arduino Uno to do all the heavy lifting.

I'm also hoping to start finding parts to put together a 3d printer. I think having a 3d printer would really help out, and not just with projects. Sure, it'd be super helpful to have something I could use to make custom enclosures for the various projects I want to make. But it'd also be super useful to have around the house to make things to help out -- like making custom bits when the GF and I want to make our own hallway closets, or stuff like that. Hell, the ladyfriend even said she'd like one around to make custom Christmas orniments. I'm going to do my best to build it from scratch, and buying the absolute minimum number of parts. It's not just to keep the cost down ( although that is a pretty big factor ), it's also to see if I'm able to do it -- which is really the reason I take on most projects. I've got my eye on a few parts sitting in an electronics recycle bin at work that I'm going to try and disassemble for parts and bits next week; there's a printer or two I could probably get some pretty decent parts from sitting in there.

I'd also like to try out hacking some NFC/RFID stuff. I've got two ideas that require one or the other. The first is a keyless door lock. I'd like something that I could use on the entrance to my place so that I can reduce the number of keys I have to carry around. I'd still carry a back up with me ( of course ), but it could sit in my bag instead of on my keychain. Another idea I had was to make a automatic window opener for my sister and her cat. She's complained about her cat getting really annoying when he wants in and out of her place. Unfortunately, she lives in a basement suite of an older building, so she can't put in a cat door ( plus that'd make her place even colder ). So I figured that making a little device that will unlatch the window and open it when the cat wants to go outside/come in, and close and re-latch the window when he's gone might be pretty helpful for her.

One other thing that I'd like to get into is amateur radio. It's something I've always been a bit interested in, and I think it'd be a fun hobby. Plus, the prospect of talking to folks from the other side of the globe with a radio I built myself? Pretty awesome idea. I think I'll probably try to study on my own and take the exam, and take a course if I don't do so hot on the exam. This is a hobby where I'd definitely have to build my own equipment, because even the cheapest amateur radio setups are about $500. No thanks. Not only do I not really want to spend that much on a single piece of gear, I think my GF would kill me if I did. Plus, I feel like building my own kit is almost a rite of passage or something. Something that proves I've got the chops to be part of the hacking club.

Those are only a few of the hardware projects I've got in mind. I've got quite a few others sitting around on paper or in various files on my computer. I'll be documenting them all as best as possible when I start working on each one. The code and any other files for each project will be fully open source, so I'll be creating a GitHub repo for each one when I start working on them. I'll also be keeping a project log on here for each project to document all the fun, success, mistakes, and plain old fails that I create on my way to a finished project.

Any other ideas on stuff I could create with an Arduino or two?

[1]: http://jenkins-ci.org/
