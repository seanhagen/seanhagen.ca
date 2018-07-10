---
categories:
- octopress
- plugin
- programming
comments: true
date: 2013-11-15T00:00:00Z
title: I Made An Octopress Plugin!
url: /2013/11/15/i-made-an-octopress-plugin/
---

So I ran into a problem with my new love, [Octopress][1]. I'm pseudo-live-blogging the [CascadiaJS][2], and for one of the talks I wanted to show off a puzzle, along with the answer. To do this I'd need some sort of spoiler tag.

I did some searching, and I couldn't find a 'ready-to-go' plugin for Octopress. I found a few big sites that use [Markdown][3] ( the default way of storing text in Octopress before it's transformed to HTML ), and had modified it to allow users to put in spoiler tags. A good example is the [Stack Overflow][4] group of sites, which use an extension of blockquotes to do spoiler tags.

However, I wasn't able to find a plug in that I could just drop into my site, and have it just work.

So, being a programmer, I made my own!

<!--more-->

The code is [up on GitHub][5], and I was actually pretty surprised at how easy it was to make. These are the only two files I needed to create in order to have spoiler tags:

### Ruby Plugin
{{< highlight ruby >}}
module Jekyll
  class SpoilerTag < Liquid::Tag
    def initialize(tag_name, text, token)
      super
      @text = text.strip
    end

    def render(context)
      "<div class='octopress-spoiler-tag'>#{@text}</div>"
    end

    private

    def get_config(string)
      Jekyll.configuration({})[string]
    end
  end
end

Liquid::Template.register_tag('spoiler', Jekyll::SpoilerTag)
{{< / highlight >}}


### Stylesheet
{{< highlight scss >}}
.octopress-spoiler-tag {

   background: black;
   color: black;

   &:hover {
      background: white;
   }

}
{{< / highlight >}}

### End Result

And here's what it lets me do:

{% spoiler "Look at this saucy spoiler!" %}


### Possible Modifications

Here's a few things I'm thinking of changing so the spoiler tag becomes more useful:

1. Maybe turn it into a plugin that works similar to the [codeblock][6] plugin
2. Maybe make so that it also works as a plain markdown plugin for other systems, so that you can just do the following:
        \>! text in a block like this is a spoiler!
3. Have the plugin read from the configuration file so you can easily customize the colors if you don't want to mess with the stylesheet

That's about all I can think of right now. If you've got any ideas, [fork the repo][5] and send me some pull requests!

[1]: http://octopress.org/
[2]: http://2013.cascadiajs.com
[3]: http://daringfireball.net/projects/markdown/
[4]: http://meta.stackoverflow.com/questions/1191/add-markdown-support-for-hidden-until-you-click-text-aka-spoilers
[5]: https://github.com/seanhagen/octopress-spoiler-tag
[6]: http://octopress.org/docs/plugins/codeblock/
