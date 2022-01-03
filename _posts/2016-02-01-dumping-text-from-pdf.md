---
layout: post
title: Dumping Text from a PDF file on OSX Command line
published: True
date: 2016-02-01 17:31
categories: []
tags: []
---

If I've had to google search for a tip or tool more than a few times, then it's time to post something here.

Occasionally I need to dump the text from a PDF file, to search for a word or extract some bit of information. This does the trick nicely:

    mdimport -d2 filename.pdf
    
