---
title: "{{ .TranslationBaseName | replaceRE "^[0-9]{4}-[0-9]{2}-[0-9]{2}-" "" | replaceRE "-" " " | title }}"
slug: {{ .TranslationBaseName | replaceRE "^[0-9]{4}-[0-9]{2}-[0-9]{2}-" ""  }}
date: {{ .Date }}
comments: true
categories: blogging
excerpt: null
header:
    feature: neon-cropped
    creditlink: https://www.flickr.com/photos/rebelcan/2309011771
---
