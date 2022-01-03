---
layout: post
title: Simple Command Line FITS Tools - lessfits and grepfits
published: True
date: 2016-07-25 20:40
categories: []
tags: []
---

For years I've used a couple of hacked together bash scripts `lessfits` and `grepfits` for doing quick command line looks at the contents of FITS files. (FITS format is a file that most astronomical images/spectra/data. It's a bit antiquated at this point, but unlikely to go away any time soon.) 

`lessfits` is like the unix command `less` but for the header of a FITS file. e.g.:

    $ lessfits 2016-06-24_0138.fits.gz
    SIMPLE  =                    T / conforms to FITS standard                      
    BITPIX  =                   32 / array data type                                
    NAXIS   =                    3 / number of array dimensions                     
    NAXIS1  =                  320                                                  
    NAXIS2  =                  256                                                  
    NAXIS3  =                   21                                                  
    EXTEND  =                    T                                                  
    [....paging through the entire FITS header with all the usual navigation hotkeys of "less"]

`grepfits` outputs values of selected keywords from the headers of one or more FITS files. e.g.:

    $ grepfits EXPTIME,NEXP,RA,DEC 2016-06-24_013[6-9].fits.gz 
    filename                 EXPTIME NEXP RA          DEC        
    2016-06-24_0136.fits.gz: 1.0     21   22:23:21.47 +10:15:31.1
    2016-06-24_0137.fits.gz: 1.05    21   22:23:47.50 +10:15:31.3
    2016-06-24_0138.fits.gz: 1.1     21   22:24:13.53 +10:15:31.4
    2016-06-24_0139.fits.gz: 1.15    21   22:24:40.57 +10:15:31.5

Because I habitually `gzip --best` any FITS file I'm dealing with, both of these scripts work smoothly on either `*.fits` or `*.fits.gz` files. I recently spent a few minutes updating these scripts to work more reliably. Both are available as gists on github (see below). Note that they do not not require any type of fits library to be installed. Both scripts do use python, but with no additional library dependencies beyond *gzip* and *sys*, which are both included in every python install I've ever encountered. This is an intentional choice to make these scripts work as universally as possible.

<!--more-->

<script src="https://gist.github.com/henryroe/8ddaf96fec7cd4f92f1d59c791e511a4.js"></script>

<script src="https://gist.github.com/henryroe/90edcb066f33d8c922de06a12c233d80.js"></script>