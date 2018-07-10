---
categories:
- learning
- testing
- octopress
comments: true
date: 2013-11-12T00:00:00Z
published: false
title: Testing Out Tags
url: /2013/11/12/testing-out-tags/
---

##Seeing How Markdown & Liquid Work

This is the image tag:
{{< figure src="http://placekitten.com/890/280" >}}

Slow-carb tattooed deep v direct trade, disrupt biodiesel Neutra meggings vegan Tonx. Minim Portland Tumblr consectetur cupidatat 8-bit, kale chips distillery squid eu High Life forage irure. Labore XOXO High Life sapiente umami eu. Austin biodiesel sed, mollit viral PBR distillery semiotics chia raw denim polaroid. Intelligentsia Austin nesciunt, quis selfies small batch roof party food truck ad ex. Aute voluptate cillum Blue Bottle, organic id pickled Helvetica Tumblr dolor readymade Odd Future. Consectetur accusamus odio banjo placeat anim.

Ethical magna selfies assumenda selvage. Brooklyn kale chips narwhal, artisan 3 wolf moon fingerstache literally wayfarers. Church-key ea chambray stumptown accusamus, ad pork belly craft beer farm-to-table VHS chillwave 8-bit Austin reprehenderit. Kale chips dolor sriracha, bespoke drinking vinegar cardigan Etsy put a bird on it kogi vero seitan Tonx Williamsburg 8-bit ea. Cornhole Tonx blog Brooklyn semiotics reprehenderit. Bicycle rights 3 wolf moon ut, accusamus fixie PBR salvia Intelligentsia. 8-bit wolf artisan occaecat ugh assumenda, Terry Richardson mixtape dolor magna aliquip synth Wes Anderson gastropub.

<!--more-->

##And This Is A Video!
--------------------

{% video http://s3.imathis.com/video/zero-to-fancy-buttons.mp4 640 320 http://s3.imathis.com/video/zero-to-fancy-buttons.png %}

And here's a blockquote:
{% blockquote %}
Last night I lay in bed looking up at the stars in the sky and I thought to myself, where the heck is the ceiling.
{% endblockquote %}

Blockquote with author:
{% blockquote Douglas Adams, The Hichhikers Guide to the Galaxy %}
Flying is learning how to throw yourself at the ground and miss.
{% endblockquote %}

Blockquote with author and named link:
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

What about Markdown blockquotes?
> Well, this should work.
> It's Markdown, right?
> > Two levels, bitch!
> Hey hey!

##Lists!
* Unordered
* Lists
* Are
* Pretty
* Easy


1. Ordered
2. Lists
3. Are
4. Kinda
5. Boring

Intelligentsia Austin nesciunt, quis selfies small batch roof party food truck ad ex.

        hey hey hey
        things.

What about some <del>horrible</del> strike-through text?

What about _italizing_ or __bolding__ text?

##Pullquotes!
{% pullquote %}
Slow-carb tattooed deep v direct trade, disrupt biodiesel Neutra meggings vegan Tonx. Minim Portland Tumblr consectetur cupidatat 8-bit, kale chips distillery squid eu High Life forage irure. Labore XOXO High Life sapiente umami eu. {"Church-key ea chambray stumptown accusamus, ad pork belly craft beer farm-to-table VHS chillwave 8-bit Austin reprehenderit."}Austin biodiesel sed, mollit viral PBR distillery semiotics chia raw denim polaroid. Intelligentsia Austin nesciunt, quis selfies small batch roof party food truck ad ex. Aute voluptate cillum Blue Bottle, organic id pickled Helvetica Tumblr dolor readymade Odd Future. Consectetur accusamus odio banjo placeat anim.
{% endpullquote %}

##And Now, Some Code
{% codeblock %}
Awesome code snippet
{% endcodeblock %}

{% codeblock lang:coffeescript %}
class Youngagrarians.Models.Category extends Backbone.RelationalModel
  paramRoot: 'category'

  defaults:
    name: null

  relations: [
    type: 'HasMany'
    key: 'subcategory'
    relatedModel: 'Youngagrarians.Models.Subcategory'
    includeInJSON: [Backbone.Model.prototype.idAttribute, 'name']
    collectionType: 'Youngagrarians.Collections.SubcategoryCollection'
    reverseRelation:
      key: 'location'
      includeInJSON: '_id'
  ]

  isHidden: =>
    #warning: hack, attribute in model would be better
    return @get('name') == 'Web Resource' or @get('name') == 'Publication'

  getIcon: =>
    return '/~youngagr/map/assets/map-icons/' + @get('name').toLowerCase().replace(' ', '-') + ".png"

{% endcodeblock %}

##How About A Gist?

Take a look at this!

{% gist 7440480 %}
