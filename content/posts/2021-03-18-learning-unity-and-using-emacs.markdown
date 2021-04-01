---
title: "Learning Unity and Using Emacs"
slug: learning-unity-and-using-emacs
date: 2021-03-18T00:34:18-07:00
draft: true
comments: true
categories: blogging
excerpt: null
header:
    feature: neon-cropped
    creditlink: https://www.flickr.com/photos/rebelcan/2309011771
---




steps to get lsp-mode working in emacs with C#, Omnisharp, and Unity:

- install dotnet, mono, msbuild via pacman
- let lsp install the omnisharp server
- for me this was `~/.emacs.d/.cache/lsp/omnisharp-roslyn/v1.37.7`
- edit the `run` script, change `bin_dir=${base_dir}/bin` to `bin_dir=/usr/bin`
- create `~/.omnisharp/omnisharp.json`, put ( at least ) this in it: 

{{< highlight json >}}
{
  "msbuild": {
    "enabled": true,
    "MSBuildSDKsPath": "/usr/share/dotnet/sdk",
    "FrameworkPathOverride": "/usr/lib/mono/4.5"
  }
}
{{< / highlight >}}

TADA!

It works!

![LSP working in Emacs with Unity](/images/emacs-unity-lsp-working.png)


