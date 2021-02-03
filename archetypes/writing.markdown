---
title: "{{ .TranslationBaseName | replaceRE "^[0-9]{4}-[0-9]{2}-[0-9]{2}-" "" | replaceRE "-" " " | title }}"
slug: {{ .TranslationBaseName | replaceRE "^[0-9]{4}-[0-9]{2}-[0-9]{2}-" ""  }}
date: {{ .Date }}
comments: true
categories: writing
---
