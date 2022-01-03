---
layout: post
title: Graphing Python Dependencies with Snakefood
published: True
date: 2015-09-29 11:40
categories: []
tags: []
---

When I need to tease out complex dependencies in a python project, I use [snakefood](http://furius.ca/snakefood/).

<!--more-->

To install:

    brew install graphviz
    pip install snakefood
    
Read more documentation [here](http://furius.ca/snakefood/doc/snakefood-doc.html), but here's a quick example use:

    cd YOUR-PROJECT
    sfood . | sfood-graph | dot -Tps | pstopdf -i -o map.pdf
    open map.pdf

Which produces a `map.pdf` that looks like:

![Example snakefood graph](/assets/images/snakefood-map.png "Example snakefood dependency graph")

(In the PDF you can zoom in and read the labels and pan around the dependency links.)
