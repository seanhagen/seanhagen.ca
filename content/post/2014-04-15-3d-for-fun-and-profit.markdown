---
categories:
- javascript
- programming
- 3d
- threejs
comments: true
date: 2014-04-15T00:00:00Z
title: 3D For Fun And Profit
---

The project that I've been working on at ThoughtShop is almost ready to show off. There have been a few interesting snags that I've run into while getting the project all set up on the hardware that's going to end up in the showroom.

The main issue is the way the screens are set up. The project is running on 3 screens ( one of which is a touch scren ), which are all connected to a Mac Mini. The screens are all going to be mounted vertically, with the touch screen on the bottom. The touch screen is going to be showing some interactive stuff, and the top two screens are going to be showing a 3d model.

There are a few things about this project that I think are pretty cool.

<!--more-->

## Websockets!

The first is [websockets][1], courtesy of [SocketIO][2]. The project is actually composed of three parts: a [NodeJS][3] backend, and two browsers that communicate via websockets. When a user touches certain parts of the interface, that browser sends events to NodeJS, which send those commands on to the other browser.

I'm a little in love with the SocketIO library. It has made working with websockets super easy, both in the browser and inside NodeJS.

## WebGL

The other thing that I think is really cool about this project is that there's a 3D portion. I've been using the [ThreeJS][4] library for this portion. It's been pretty awesome. It does a great job of abstracting away the nitty-gritty of the WebGL stuff.

## Solving Problems

I did run into one interesting problem on this project. Because the Mac Mini only has two monitor ports ( a mini Display Port and a HDMI port ), we had to use a [Matrox DualHead2Go][5]. This lets us connect two monitors to the mini Display Port on the Mini. Unfortunately, the only way to have those monitors show up is as one long monitor. This screws with the way that the browser opens up when it's told to go fullscreen -- it expands across both the screens.

This causes the model to split horizontally across the two screens -- which is a problem, as the screens are stacked vertically.

So, I looked into a few solutions. The first one I tried out was rendering the scene using two cameras, and splitting up the rendering area using ThreeJS's setViewport. Unfortunately, this caused a slight issue: the two cameras view's don't line up. Because they're perspective cameras, the top of one camera won't match up with the bottom of another.

Thankfully, there was another solution.

The cameras that ThreeJS offers has a [setViewoffset][6] method, which allows developers to take the view from a single camera and split it up so that it can be rendered in multiple parts. The code ended up being pretty simple. Take a look:

{{< highlight coffeescript >}}
    screen_width = window.innerWidth/2
    screen_height = window.innerHeight*2

    renderer.setViewport 0, 0, screen_width, screen_height
    renderer.clear()

    fraction = 1/@NUM_SCREENS
    num = @NUM_SCREENS

    viewport_height = window.innerHeight
    viewport_width = window.innerWidth * fraction
    viewport_y = 0

    offset_height = screen_height * fraction
    offset_width = screen_width
    offset_x = 0

    range = (num for num in [1..@NUM_SCREENS])

    _.each range, (index) =>
      i = index - 1

      offset_y = (i * offset_height)
      @camera.setViewOffset screen_width, screen_height, offset_x, offset_y, offset_width, offset_height
      @camera.updateProjectionMatrix()

      viewport_x = (i * viewport_width)
      renderer.setViewport viewport_x,viewport_y,viewport_width, viewport_height
      renderer.render @scene.scene, @camera.camera
{{< / highlight >}}

This saved my bacon. Hopefully it will help someone else.

[1]:http://en.wikipedia.org/wiki/WebSocket
[2]:http://socket.io/
[3]:http://nodejs.org/
[4]:http://threejs.org/
[5]:http://www.matrox.com/graphics/en/products/legacy/gxm/dh2go/displayport/
[6]:http://threejs.org/docs/#Reference/Cameras/PerspectiveCamera
