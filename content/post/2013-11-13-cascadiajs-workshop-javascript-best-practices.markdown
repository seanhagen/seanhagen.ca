---
categories:
- javascript
- learning
- conference
- cascadiajs
comments: true
date: 2013-11-13T00:00:00Z
title: 'CascadiaJS Workshop: JavaScript Best Practices'
url: /2013/11/13/cascadiajs-workshop-javascript-best-practices/
---

So, this is going to be a bit of a stream-of-consciousness. I'm going to be taking notes on the interesting stuff from this talk, because I'm sure there are going to be things that I don't already know about that I'll want to refer to later.

<!--more-->

**8:17am**

I'm currently sitting in one of the lecture halls in the downtown campus of SFU. There are about 12 people sitting in the room already, and we've run into one problem already: power. These lecutre halls were not built with the tech savy in mind. We've got a few extension cords that have multiple sockets on the end, but I don't think they'll cut it if any more people show up.

I'm not blaming the CascadiaJS people here. They probably didn't get a chance to scope out the room until today, which would explain the rush to get a few actual power bars into the room.

I just hope that the actual conference won't have the same issues.

I will say this though: the croisants that they're providing as part of the breakfast spread are much better than the ones we get at work.

-----------------------

**8:42am**

The presentation starts! Getting an intro, starting off with a joke. The presenter [Dan Heberden][1] is using Vim to do his presentation, which is kind of awesome. It also seems to be a bit of a trend at these talks.

----------------------

**9:13**

The presenter just advised people to take a day or two to learn RegExps. I foresee a lot of people having problems in the future.

----------------------

**9:33am**

Dan mentions something called 'evil.js', which sounds awesome. We're also 730 lines through his apparently 5646 line presentation. No wonder this is a full day thing.

----------------------

**10:00am**

Time for a quick break! So far, we've just been covering some JavaScript basics, mostly gotchas around some of the basic types; things like falsy values, hoisting, and other things that can trip you up when you start programming in JavaScript.

----------------------

**10:15am**

JavaScript function pass by copy of reference: something I didn't know! Basically, when you pass an object to a function, the function gets a copy of the reference to the object.

So you can do something like this;

        var obj1 = { foo: 'bar' };
        function doStuff(obj){
          obj = null;
        }
        doStuff(obj1);
        console.log( obj1 ); // will output { foo: 'bar'}

Which is actually pretty awesome.

Weirdness about object notation:

        var obj = {};
        function test(){ return 123; }

        obj[test()] = 200;

        obj === { '123': 200 }

        obj[test] = 300;

        obj === { '123': 200, 'function test(){ return 123; }': 300 }

New stuff in JavaScript: [Map][5] & [WeakMap][6]. Both pretty awesome, although WeakMap seems a bit more powerful ( despite the name 'weak' ).

----------------------

**11:08am**

Something I never knew before: using "new Array(4,5,6)" will create an array like so: "[4,5,6]". But using it like this: "new Array(4)" will create an array like so: "[,,,]".


----------------------

**11:31am**

Getting in-depth with some funky JavaScript object namespacing using functions. I already knew some of this stuff, but it's always nice to have someone explain stuff to you. I tend to pick up on a lot of stuff on my own, but at events like this I tend to pick up the 20% I didn't know about or didn't understand before. Also learning a bit about the .call() and .bind() stuff that's built into JavaScript, which are also pretty awesome. There are some libraries out there that provide a somewhat nicer interface to some of these things, but understanding how they work in pure JS is always a good idea.

----------------------

**11:34am**

Talking about the 'arguments' reserved keyword for use inside functions. Not something I think I'll end up using a ton, but it can be amazingly useful in certain situations.

- note for later ( include souce )
Update addNumbers(ln:~1733) to do recursion so that users can use it like so:
        addNumbers([1,2,3],[4,5,6]);

----------------------

**11:39am**

Using Function.caller to figure out who called a function. Not sure why you'd want to use this ( changing the way a method works depending on who calls it seems like a bad idea ), but still -- kinda awesome you can do this.

----------------------

**12:10pm**

Lunch break! [CascadiaJS][2] ( and/or [Bocoup][3] ) provided lunch, which is pretty awesome, so shout out to those folks. This is probably a good point to send some thanks to everyone who is helping to put together this whole [Vancouver DevWeek][4], because it's nice to be able to go to a conference like this in my hometown.

----------------------

**12:41pm**

Lunch was good. That is all.

----------------------

**12:44pm**

Back to the presentation! I'm hoping that we start diving into some of the more fun things that you can do with JavaScript.

First thing we're diving into: [Immediately Invoked Function Expressions][7] (IIFE), which are a pretty neat part of JavaScript. I've used these in a few places before, as they're pretty powerful.

Say you've got a function like so:

    function foo(a){
      var x="foo";
      console.log("foo: ", foo, " a:", a);
    }

    foo(1); // "foo: foo a: 1"

This is how you'd turn that into an IIFE:

    (function(a){
      var x = "foo";
      console.log("foo: ", foo, " a: ", a);
    }(4))

    //immediately outputs "foo: foo a: 4"

This is more useful when you want to be able to handle private variables in JavaScript.

    function makeCounter(){
      var i=0;
      return function(){
        return ++i;
      }
    }

    var counter = makeCounter();
    counter(); // 1
    counter(); // 2

    var counterTwo = makeCounter();
    counterTwo(); // 1, because 'i' is private to the closure
    counterTwo(); // 2

Pretty awesome, no?

If you want a property ( not exactly the right name, but just go with me ) public, you can do something like this:

    function makeCounter(){
      var counter = function(){
        return ++counter.i
      }
      counter.i = 0;
      return counter
    }

Now, when 'makeCounter' behaves in the same manner, but you can now do something like this:

    var counter = makeCounter();
    counter(); // 1
    counter(); // 2
    console.log( "count: ", counter.i ); // outputs "count: 2"

IIFEs can be super useful when you want to set a handler on a bunch of elements at once by looping through the elements.

    var elems = document.getElementsByTagName("a");

    for ( var i=0; i< elems.length; i++ ){
      (function(lockedInValue){
        elems[i].addEventListener("click", function(e){
          e.preventDefault();
          console.log("I am link #", lockedInValue);
        })
      }(i));
    }

----------------------

**1:06pm**

The Module Pattern! Wooo! Objects and constructors! More wooo!

----------------------

**1:23pm**

Never thought about the fact that JavaScript's prototype system can help reduce memory usage. Using an object and adding functions to it means that every copy of the object will have a copy of the function. If you're doing something like a game or particle effect demo, that's thousands of copies of the function. If you do the object prototype method, then there's only one copy of the function in memory, saving you memory ( and probably CPU somehow -- I don't know, don't look at me ).

----------------------

**1:30pm**

Awesome way to make sure that a function object always returns an object, and doesn't just let you call it as a function:

    function Person(first, last){
      if ( !(this instanceof Person) ){
        return new Person(first, last);
      }
      this.first = first;
      this.last = last;
    }

Holy hell yes.

Of course, this doesn't work so well when you want to use that function as the prototype for another function object.

----------------------

**1:52pm**

Constructor madness. Setting up JavaScript prototype inheritance is weird and messy, but pretty powerful.

----------------------

**1:55pm**

Talking about how to get around inheriting from a object that has static properties. My solution? Don't use static properties.

----------------------

**2:24pm**

Object.defineProperty is pretty awesome. I can see using this kind of syntax to create a public JS API that just gets included on a page, but allows me to do things like slowly deprecate methods and/or properties.

----------------------

**2:30pm**

Hell yeah functions are first-class citizens in JavaScript. One of my favourite things about JS, to be honest.

Side note: what if you had a bunch of functions that just returned functions, and ended up with something like this:

    someFunction('what')('happens')('now')('huh')('?');

I have a feeling that would lead to murder.

----------------------

**2:35pm**

The _void_ operator! Completely useless.

----------------------

**2:48pm**

Glad to see I'm not the only person who occasionally mistypes 'console' as 'conosle'.

----------------------

**2:58pm**

Lots of confusion over the way JS returns value from && and || operations. I kind of get the confusion, but at the same time the way JS lets you do things like this:

    var x = someTruthyThing && someOtherTruthyThing;
    x === someOtherTruthyThing; // true!

Seems pretty natural to me. I'm not sure why that is.

----------------------

**3:29pm**

Something that can never be repeated enough: **ALWAYS USE SEMICOLONS**. Otherwise, the JS interpreter might make some weird decisions for you.

----------------------

**3:39pm**

At last, the best reason for using try-catch-finally, instead of just try-catch:

If your catch code needs to re-throw an error, or it accidentally throws its' own error, then the code in finally will still run.

For example:

    try {
      codeThatThrowsError();
    } catch (e) {
      errorHandlerThatMayThrowError(e);
    } finally {
      thisAlwaysHappens();
    }

Pretty awesome!

----------------------

**3:52pm**

Just going over some neat little tips and tricks for JS stuff. I'll gather some of the good ones together for a post later, but he's going through them pretty quickly right now, making it hard to add them to these notes.

----------------------

**3:58pm**

And that's it for the day! Pretty awesome talk, many thanks to [Dan][1], [Bocoup][3], and [CascadiaJS][2] for putting on this awesome lesson!

[1]: https://twitter.com/danheberden "Dan Heberden's Twitter"
[2]: http://2013.cascadiajs.com
[3]: http://bocoup.com/
[4]: http://vancouver.devweek.org/
[5]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map
[6]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap
[7]: http://benalman.com/news/2010/11/immediately-invoked-function-expression/
