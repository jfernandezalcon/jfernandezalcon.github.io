---
layout: post
title:  "Removing i386 architechture from debian"
date:   2016-01-16 15:21
categories: debian
author: Blackmagic
---

I decided I was going to start using skype in a docker container, so I don't need any of the i386 packages anymore.

Going back to a pure 64bit OS is quite simple:

```bash
apt-get purge ".*:i386"
dpkg --remove-architecture i386
```

The *purge* command is similar to *remove*, but it also deletes any configuration file.
