---
layout: post
title:  "Upgrading from Plasma 4 to Plasma 5 on Gentoo"
date:   2015-05-29 23:10:51
categories: gentoo plasma 5
author: Blackmagic
---

Last night I upgraded KDE SC 4 to the Plasma 5 desktop on Gentoo. The instructions at [Gentoo Wiki] are very detailed and easy to follow.

The first thing I did was to remove my installation of KDE SC 4. Plasma 4 and 5 can not coexist, to my knowledge at least, and I thought it would be a safe move. In order to do this is recommended to have another desktop/WM installed, so that you can work from it while you unmerge KDE. There is a [KDE removal page] at the Gentoo Wiki.

Then I followed the plasma upgrade instructions at the [Gentoo Wiki].

While uninstalling KDE I also removed kdm. kdm is deprecated in plasma 5 and has been substituted by SDDM. Installing SDDM is quite simple:

```bash
emerge --unmerge kdm
emerge -av sddm
```

Then you need to edit /etc/conf.d/xdm and modified so that it contains the following line:

```
DISPLAYMANAGER="sddm"
```

Then you should be ready to start using plasma 5.

[Gentoo Wiki]: https://wiki.gentoo.org/wiki/KDE/Plasma_5_upgrade
[KDE removal page]: https://wiki.gentoo.org/wiki/KDE/Removal