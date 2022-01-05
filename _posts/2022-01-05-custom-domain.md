---
layout: post
title:  "Connect my Custom Domain"
date:   2022-01-05 Wednesday
categories: behindscenes 
---
Until today my most recent blog install on heroku was visible at *https://hroe.me*. To move that domain over to point at this new GitHub Pages hosted version:

<!--more-->

On the domain registrar, which for me is [hover](https://hover.com):

* Remove any A records with Host "*" as GitHub makes clear that's a security risk that someone else could then set up a GitHub Pages site using a subdomain of my domain. 

* Remove any other A records with Host "@" and insert four new A records, each with Host "@" pointing at IP addresses 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153.

* Insert a new CNAME record with Host "www" and Target Name "hroe.me".

On GitHub go to the project page and select the *Settings* tab at the top and then the *Pages* settings page on the lower left, then:

* Enter "hroe.me" to *Custom Domain* and click *Save*

* Wait for the DNS Check to complete

* Check that the site is appearing correctly at my custom domain. (Likely only on the *http* version and not yet on the *https* version as of yet.)

* Select the *Enforce HTTPS* checkbox. (May have to wait a while and come back and do this later.)

* Work through the [Verify your Domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages) instructions on GitHub to increase security against a domain takeover. 

Wow, that was a lot easier than what I remember having to do to make the custom domain work correctly over on Heroku back in 2015 or so.