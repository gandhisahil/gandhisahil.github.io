---
layout: post
title: Block AdBlock from blocking your social icons
date: 2014-09-27 16:00:00
categories: hacks web
published: true
---

#TL;DR
To avoid adblock from hiding your social icons, change class/icon names to anything other than standard ones used.

>Have you made a website and wondered why your social icons, or your social buttons don't show up? 

Well the culprit is AdBlock. Not only does AdBlock block ads, but also social icons, social buttons, and social share buttons. 

For the more technical audience, adblock simple adds the `visibility: hidden` to the DOM element it thinks is an advertisement or a social button/icon/widget. Here are a few examples:

##SumoMe social widget with and without AdBlock

![SumoMe with AdBlock](http://cl.ly/image/0N230834280a/Image%202014-09-27%20at%204.01.46%20pm.png)
![SumoMe without AdBlock](http://cl.ly/image/2K2R3q2u2O0Z/Image%202014-09-27%20at%204.11.05%20pm.png)


##Blog with social share buttons and widgets

![With AdBlock](http://cl.ly/image/3J2G2X3r1I3O/Unknown.png)
![Without AdBlock](http://cl.ly/image/0f2A440y3V0L/Screenshot.png)


It identifies social icons by its class name. With the popularity of standard icon libraries like, FontAwesome, almost everyone uses it. AdBlock hides elements that match social icon names like `fa-facebook` or `fa-twitter`. Similarly it hides the standard class names of social sign-in buttons. So in order to avoid this, all you need is change the class/icon name of the icon that adblock hides, to anything else and you're good to go. 