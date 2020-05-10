---
layout: post
title:  "Using a DisplayLink device on Gentoo"
date:   2017-12-02 16:00
categories: gentoo
author: Blackmagic
---

1. Download he official ubuntu package from 

http://www.displaylink.com/downloads/ubuntu.php

```bash
./displaylink-driver-1.4.210.run --target .
tar -xzvf evdi-1.4.210-src.tar.gz 
make
sudo cp evdi.ko /lib/modules/4.14.1-gentoo-blackmagic/kernel/drivers/gpu/drm/evdi/evdi.ko
depmod -a
cp -r x64-ubuntu-1604/* /opt/displaylink/
```


It is outdated, but some of the files can be used.

[DisplayLink Overlay](https://github.com/gentoo-mirror/mrueg/blob/master/x11-drivers/displaylink-driver)

Run D3100.sh