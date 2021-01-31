---
categories:
- emacs
- configuration
comments: true
date: 2013-12-18T00:00:00Z
title: Another Year of Emacs
---

So, the year is almost over.

For the past year, I've been using Emacs as my only editor. Not just for code, but for other things as well -- including the post you're writing right now. Last year at Christmas, I started from scratch with my Emacs configuration. I wanted to start over, re-writing it to use some of the stuff I had learned the year before that, and to try out a few new things.

<!--more-->

I've got some goals for what I'd like to accomplish with Emacs in the coming year, and I'll get to those in a moment. First though, I'd like to share some of the stuff I've learned about Emacs in the past year.

* I found out how to use [TRAMP][1] and [sudo][2] together to remotely edit files as root. The syntax is pretty simple: {{< highlight bash >}}
    /ssh:user@remotehost|sudo:root@remotehost
    {{< / highlight >}}

    There are two things to remember: use the pipe in-between the ssh and sudo portions, and when you do the sudo part, make sure you do 'root@remotehost' and not 'root@localhost' -- if you use localhost, TRAMP will try to open files on _your_ machine, not the remote one.

    This has been a huge timesaver for me, because I've recently become the DevOps team lead at work. That means lots of configuring remote machines. It's really nice to be able to edit a server configuration file locally ( with all my modes and key-bindings ), instead of sshing into a machine, ensuring it has Emacs installed, and then editing it remotely. TRAMP was already a life-saver, now it's just pure awesome.

* I discovered [EMMS][3], which lets me play and control my music via Emacs. A bit harder to add new songs compared to Grooveshark, but the convenience of being able to pause the music when someone needs to talk to me ( compared to switching to the [workspace][4] and finding the Grooveshark tab ) is pretty nice.

* I discovered multi-term, which lets me use [zsh][5] ( and all the [oh-my-zsh][6] goodies ) inside Emacs. I'm not entirely sold on this one though, partially because when you have three monitors, it's pretty handy to have multiple terminals visible at once, and full screened. However, on something with only one screen ( laptops, possibly tablets ), I can see it being pretty handy. I could just cave in and learn eshell, but I'm a pretty big fan of zsh ( _especially_ oh-my-zsh ), so I don't think that will be happening any time soon.

* I discovered that the PHP modes for Emacs have come quite a ways. Earlier this year, I switched jobs and went from Ruby back to PHP. The last time that I had been working in PHP, there were a few modes for Emacs, but they weren't as cool/awesome/slick as the modes available for Ruby ( or even C++ ). However, there are a few modes ( php-mode+, php-repl, php-boris ) that make developing in PHP fun again. Also, I've been picking up a few tricks so that I can do things like run unit tests and whatnot from inside Emacs, which has made my life considerably easier.

* I re-discovered IRC this year, thanks to the Jenkins notification plugin. I'm using Circe, but I may look around to see if there are other IRC modes that are easier to user or configure.

* I found tumblesocks and twittering-mode, which let me access ( and post to! ) tumblr and twitter from inside Emacs. I've only recently discovered them though, so I've still got a bit of learning to do.

I'm sure that there are tons of other things that I've learned or discovered about Emacs in the past year, and I know I've barely scratched the surface of what I can get Emacs to do for me.

## What's Next?

Here are a few of the things that I'd like to accomplish with Emacs in the next year:

* Start using it as my main method of communication. I'd like to start using as not only my email client, but also as my chat client. There are a few things to figure out here: I've got three email accounts that I need to stay up-to-date on ( personal, and two work accounts ), and I'd like to be notified in the modeline when I get a new email. Getting Emacs set up to do Hangouts ( at least, the chat part ) is pretty easy, but Skype is how I communicate with people at work. There are a few projects out there that look like they might provide Skype integration to Emacs, but I haven't tested any of them yet. The modeline notifications also extends to IRC, as well.

* Really get projects set up and integrated into Emacs. At work we've usually got a few projects on the go at any one time, each with their own GitHub repo and code structure. I'd like to get Emacs set up so that I can easily open up a project, and have a few key-bindings that work regardless of folder structure. Things like running unit tests, running tools installed via composer, that sort of thing. Now that I've also got a bit of a bigger monitor ( at work and at home ), I may also take another shot at setting up [ECB][7]. I found that on smaller monitors, ECB took up too much space if you wanted it to be useful.

* Along with getting unit tests running regardless of project, I'd also like to set up red-green notifications in the modeline. I found an awesome mode for Ruby a few years ago that would show a red or green dot in the modeline based on the status of the unit tests ( and it would update whenever you saved either a unit test or a file that was unit tested ). It was pretty awesome, and I like the fact that it didn't pop up a compile buffer whenever I wanted to run unit tests.

* Dive into buffer settings, so that I can learn how to set it up so that some buffers don't spawn at half-size. For example, when I run my Circe setup function, it starts spawning new buffers, one for the server and then one for every channel I've configured to auto-join. I end up with my frame split into four buffers, when I would really prefer those to either open in the background, or in another frame entirely.

* Start memorizing all the various keyboard bindings I've set up. I really need to create a list of all the keyboard bindings for a) modes that I use, and b) ones that I've created. Then I need to turn that into a nice poster that I can put up beside my desk at home, and my desk at work. There are a few things like code folding and whatnot that I'd really like to become muscle memory, because they can make reading and editing code so much easier.

* Make my set up a lot leaner. Right now Emacs loads in all the modes and whatnot when I start up Emacs. What I'd really like is for it to only load up the modes ( and custom configurations related to that mode ) if I open a particular file type. For example, it should only load up php+-mode and all the other related modes and configurations if I load in a file that ends in ".php". Same thing for Ruby, Perl, Erlang, Lisp, etc.

* Learn how to use Dired better. I don't use it very often, and I find that with ido-mode I can find files pretty easily. However, it'd be nice to be able to perform things like moving files around without having to quickly switch to a terminal.

* Learn more about multiple-cursors, keyboard macros, and things like that. I've seen some pretty awesome stuff on the [Emacs Rocks][8] YouTube channel, and I'd like to learn more about that.

* Dive into using shell commands on a buffer, and other tricks on how to transform a bunch of text at once.

* Figure out how to have some stuff ( like account passwords ) encrypted, but accessible to Emacs. That way I can store them in GitHub along with the rest of my Emacs config, and not have to worry about people getting into my stuff.

* Really figure out how to use Emacs as a diff client, to handle those pesky merge conflicts in Git. Also dive more into Magit, and see what it's capable of, especially in regards to some of the Magit->GitHub integration stuff I've seen on Elpa.

* I'd like to figure out a way to monitor logs, or a service like Logstash or Logentries. That way I can get notified, in Emacs, if something is going oddly. Another nice thing would be figuring out how to access other DevOps tools from within Emacs -- stuff like Munin, Nagios, NewRelic, and other assorted services.

## Thoughts?

What do you think? Are there any Emacs tricks or plugins I should really know about? What makes your life easier as a developer ( or even as a sysadmin/ops ) when using Emacs? Let me know!


[1]: http://www.gnu.org/software/tramp/
[2]: http://en.wikipedia.org/wiki/Sudo
[3]: http://www.gnu.org/software/emms/
[4]: http://www.youtube.com/watch?v=bVRJsVuCU1g
[5]: http://www.zsh.org/
[6]: https://github.com/robbyrussell/oh-my-zsh
[7]: http://ecb.sourceforge.net/
[8]: http://www.youtube.com/user/emacsrocks
