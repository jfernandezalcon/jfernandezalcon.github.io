---
layout: post
title:  "Clear Sans Font Family"
date:   2016-12-02 16:00
categories: gentoo
author: Blackmagic
---

I found very nice font that I like. It is called Clear Sans Thin, and they are part of the Clear Sans family created by Intel.

You can download them from here: https://01.org/clear-SANS

The package comes with the fonts in multiple formats (eot, svg, ttf, woff). 

To install it in Gentoo simply:

```bash
emerge -av clearsans
```

To install it manually:

```bash
wget https://01.org/sites/default/files/downloads/clear-sans/clearsans-1.00.zip
unzip clearsans-1.00.zip
sudo cp EOT/* /usr/share/fonts/eot
sudo cp SVG/* /usr/share/fonts/svg
sudo cp TTF/* /usr/share/fonts/truetype
sudo cp WOFF/* /usr/share/fonts/woff
```
