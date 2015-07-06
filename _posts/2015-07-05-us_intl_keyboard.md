---
layout: post
title:  "US International keyboard on KDE"
date:   2015-07-05 13:23:25
categories: kde keyboard
---

The *us_intl* keyboard is US qwerty keyboard map that also provides accent marks
and special symbols. It is ideal for people who need to type in different languages
and for programmers who need to write in their own language and code (have you ever
  tried to program using an AZERTY keyboard?)

**The problem:** You can not select *us_intl* as a layout at the KDE system settings.

**The solution:** Edit *~/.kde/share/config/kxkbrc*. There set *LayoutList* to *us(intl)*.
If you want to have more than one keyboard layout, just add the extra layouts separated by
commas.

Here is a *kxkbrc* example:

```
[Layout]
DisplayNames=,,
LayoutList=us(intl),il,us
LayoutLoopCount=-1
Model=pc101
ResetOldOptions=false
ShowFlag=true
ShowLabel=false
ShowLayoutIndicator=true
ShowSingle=true
SwitchMode=Global
Use=true
```
