---
layout: post
title: Create a private podcast feed
published: True
date: 2015-09-01 22:11
categories: []
tags: []
---

I've gotten into the habit of listening to spoken podcasts at a reasonably high speed using *Smart Speed* in [Overcast](https://overcast.fm/). I've a few directories of sound files I'd like to listen to in Overcast, but that Overcast can't directly import from an existing RSS feed, e.g.:

<!--more-->

* Some of these are available by RSS, but are from a subscription-only site who's security doesn't play nicely with Overcast's feed crawler. 
* Some are ripped from CD's. 
* Some are podcasts I grabbed some time ago, but which have now disappeared from the internet because their host sites only keep the most recent few episodes available.  

I needed a way to create a private RSS feed available only to myself, or at least not publicly available out to the whole wide world.

Listening to [episode 10 of Cortex](http://www.relay.fm/cortex/10) I heard several suggestions.  The best & simplest of which involves a simple Ruby script to process a directory in Dropbox:

<script src="https://gist.github.com/lukf/44cbd90dfa86c6cd3131.js" class="gist"></script>

