---
layout: post
title:  "KDE Frameworks Live on Gentoo"
date:   2015-06-01 14:14:32
categories: gentoo plasma 5
---

It was getting boring and everything seemed to be working, so I decided to test the live version and live on the edge. So far no problems.

{% highlight bash%}
emerge -av @kde-frameworks-live @kde-plasma-live
{% endhighlight %}

Live packages -the ones marked with the 9999 version- download the latest revision and builds it. Because of that, when you use the the live packages there is no way for the emerge to find out if there is new version of the package. If you want to upgrade, you will have to rebuild all the packages 9999-version packages. You can easily do that by executing the same command you used to install the live packages.

{% highlight bash%}
emerge -av @kde-frameworks-live @kde-plasma-live
{% endhighlight %}
