---
layout: post
title:  "Downgrading Qt 5.6 to Qt 5.5 in gentoo"
date:   2016-05-03 19:15
categories: gentoo
author: Blackmagic
---

I rencently upgraded my gentoo installation and found out that some actions where not very responsive. For instance, the Alt-F2 combo that brings krunner would take a couple of seconds to display, and the same would happend when I would click on any on the icons in the plasma system tray.

The ''solution'' was to downgrade Qt from 5.6 to 5.5. Well, It is not really a solution, but you can have a working system. Now, how do you downgrade Qt?

1. I created the file /etc/portage/package.mask/qt56 with all the packages at dev-qt greater than 5.6 masked: 

~~~
>=dev-qt/assistant-5.6.0
>=dev-qt/designer-5.6.0
>=dev-qt/linguist-5.6.0
>=dev-qt/linguist-tools-5.6.0
>=dev-qt/pixeltool-5.6.0
>=dev-qt/qdbus-5.6.0
>=dev-qt/qtdbus-5.6.0
>=dev-qt/qdbusviewer-5.6.0
>=dev-qt/qdoc-5.6.0
>=dev-qt/qt-docs-5.6.0
>=dev-qt/qtbluetooth-5.6.0
>=dev-qt/qtconcurrent-5.6.0
>=dev-qt/qtcore-5.6.0
>=dev-qt/qtdbus-5.6.0
>=dev-qt/qtdeclarative-5.6.0
>=dev-qt/qtdiag-5.6.0
>=dev-qt/qtgraphicaleffects-5.6.0
>=dev-qt/qtgui-5.6.0
>=dev-qt/qthelp-5.6.0
>=dev-qt/qtimageformats-5.6.0
>=dev-qt/qtmultimedia-5.6.0
>=dev-qt/qtnetwork-5.6.0
>=dev-qt/qtopengl-5.6.0
>=dev-qt/qtpaths-5.6.0
>=dev-qt/qtpositioning-5.6.0
>=dev-qt/qtprintsupport-5.6.0
>=dev-qt/qtquick1-5.6.0
>=dev-qt/qtquickcontrols-5.6.0
>=dev-qt/qtscript-5.6.0
>=dev-qt/qtsensors-5.6.0
>=dev-qt/qtserialport-5.6.0
>=dev-qt/qtsql-5.6.0
>=dev-qt/qtsvg-5.6.0
>=dev-qt/qttest-5.6.0
>=dev-qt/qttranslations-5.6.0
>=dev-qt/qtwayland-5.6.0
>=dev-qt/qtwebchannel-5.6.0
>=dev-qt/qtwebkit-5.6.0
>=dev-qt/qtwebsockets-5.6.0
>=dev-qt/qtwidgets-5.6.0
>=dev-qt/qtwidget-5.6.0
>=dev-qt/qtx11extras-5.6.0
>=dev-qt/qtxml-5.6.0
>=dev-qt/qtxmlpatterns-5.6.0 
~~~

2. Log out of plasma to another desktop environment or to a virtual terminal. We are going to uninstall Qt and install it again so, some packages might break, leaving you with a non working desktop (until you finish the rebuild).

3. Remove all Qt 5.6 packages.

	```
	emerge --unmerge --ask $(qlist -ICS 'dev-qt/qt') 
	```


4. Then re-emerge Kde-frameworks, Plasma and the Apps (They will pull the required Qt packages).

	```
	emerge -av $(qlist -ICS kde-frameworks) $(qlist -ICS plasma) $(qlist -ICS kde-apps)
	```

5. Wait for a couple of hours.

6. Run revdep-rebuild to check that nothing is broken.

	```
	revdep-rebuild.sh -v -- --ask 
	```

7. Enjoy.