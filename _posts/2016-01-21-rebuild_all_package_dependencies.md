---
layout: post
title:  "Rebuilding all package dependencies of a gentoo package"
date:   2016-01-21 11:41
categories: gentoo
author: Blackmagic
---

Sometimes, you need to rebuild all package dependecies of a package for it to build and/or work correctly. In my case the problem was that upgrading kdelibs was failing at linking because I have moved from gcc-4.9 to gcc-5.3 and the dependencies were using the old ABI (Application Binary Interface).

With *equery* we can find out the list of dependencies that the package at stake has.
```bash
equery depends <package>
```

We could now rebuild those packages one by one, and lso we could compile them by hand on a piece of paper. Or, if you are lazy, you can type a string like this one that would to everything for you.

```bash
emerge -a --oneshot `equery depends <package-name>|awk '{print " ="$1}'`
```

After that, the problematic package should build fine, or at least you should be able to proceed to the next problem.

```bash
emerge -av <package-name>
```
