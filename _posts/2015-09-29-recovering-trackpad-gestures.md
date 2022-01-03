---
layout: post
title: Recovering Trackpad Gestures
published: True
date: 2015-09-29 11:13
categories: []
tags: []
---

Occasionally more complicated trackpad gestures stops working.  (I am currently on OS X Yosemite, but think I've been using this tip since at least Mavericks and maybe Mountain Lion.)  Typically two fingered tap for right click continues to work, but gestures like four fingered swipe between spaces stop working.  [A little googling revealed a quick easy way to recover:](http://apple.stackexchange.com/questions/151907/how-to-bring-back-multi-touch-gestures-after-it-crashes-without-reboot)

    killall Dock

