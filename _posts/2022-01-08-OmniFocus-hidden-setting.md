---
layout: post
title: "OmniFocus Hidden Setting to Open a New Window from URL Links"
date: 2022-01-08
---


TIL that there's an OmniFocus hidden setting so that URL links to OmniFocus that open perspectives, projects, etc are opened in a new window. The default behavior had been to change the frontmost window, which is often the window I'm working in. 

<!--more-->

To trigger this setting, open the following URL:

[omnifocus:///change-preference?ShouldOpenLinksInNewWindows=true](omnifocus:///change-preference?ShouldOpenLinksInNewWindows=true)

Obviously can reverse it with:

[omnifocus:///change-preference?ShouldOpenLinksInNewWindows=false](omnifocus:///change-preference?ShouldOpenLinksInNewWindows=false)

This is one of those nice little sanding off a small rough edge that's been slightly annoying. 

Credit to this [forum post](https://discourse.omnigroup.com/t/open-in-new-view-tab/43143) for revealing this to me.