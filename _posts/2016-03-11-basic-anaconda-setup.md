---
layout: post
title: Basic Anaconda Python Setup
published: False
date: 2016-03-11 08:40
categories: []
tags: []
---

**This is old; I would not follow this today.** *Added 2022-01-03 Monday*

Consolidating some notes on how I do my basic setup for using the [anaconda python environment:](https://www.continuum.io/)

<!--more-->

1. Download & install anaconda python from [here.](https://www.continuum.io/downloads)  My personal preference is for the command line installer for Mac OS X.  This installs into `~/anaconda2`.
2. Add the following to your `.bash_profile` file so you can easily jump into/out-of the Anaconda environment:

    alias start-anaconda='export PATH="/Users/`whoami`/anaconda/bin:$PATH"'
    alias stop-anaconda='export PATH=$(echo "$PATH" | sed -e "s/\/Users\/`whoami`\/anaconda\/bin\://")'
