---
layout: post
title:  "Hey Siri, Restore My Blog"
date:   2021-12-31 12:25:00 -0300
categories: jekyll behindscenes 
---
I've been on-again-mostly-off-again with writing blog posts. It's always been entirely for myself, mostly to record information somewhere that I will find it again when I need it. This is the latest version of that, having been in an off-again mode for five years or so. With some of the things I want to work on and think about in the coming year I'd like to try on-again.

<!--more-->

In terms of behind-the-scenes I want something simple and markdown based. And, ultimately I want to migrate my earlier posts from two earlier blogs here to consolidate into a single place. (Originally I used SquareSpace and blogged at [henrysmac](henrysmac.org). Later I had a markdown based blog hosted on heroku, but the system that was running on was deprecated also and I need to find a new solution.) Based on some notes I wrote to myself 5+ years ago and some quick googling, I'm going to try a [Github](https://github.com) based [jekyll](https://jekyllrb.com) blog.

The following is how I made things work on a 2021 14" MacBook Pro M1 Max running MacOS 12.1 Monterey.

## Toward getting a local Jekyll install working:

- Xcode command line tools were already installed
- [homebrew](https://brew.sh) was already installed
- User [tower](https://www.git-tower.com/) to clone my [henryroe.github.io](https://github.com/henryroe/henryroe.github.io) to locally at `~/sites/henryroe.github.io`

## To install [Jekyll](https://jekyllrb.com) in the following I am working through [these instructions](https://jekyllrb.com/docs/installation/macos/):

`ruby -v` returned `ruby 2.6.8p205`, so the built-in ruby should have been new enough (>=2.5), but I ran into problems using it. So, will install ruby 3 with homebrew instead.

Run the following in a terminal (*note that we are creating a local to the project `zshrc` file that we will source each time we want to work here. This is to avoid stepping on the system ruby installation.*)

    cd ~/sites/henryroe.github.io
    echo 'export SDKROOT=$(xcrun --show-sdk-path)' > zshrc
    source zshrc
    brew install ruby
    echo 'export PATH="/opt/homebrew/opt/ruby/bin:/opt/homebrew/lib/ruby/gems/3.0.0/bin:$HOME/.gem/ruby/3.0.0/bin $PATH"' >> zshrc
    echo 'export LDFLAGS="-L/opt/homebrew/opt/ruby/lib"' >> zshrc
    echo 'export CPPFLAGS="-I/opt/homebrew/opt/ruby/include"' >> zshrc
    source zshrc

Add and commit the `zshrc` file to GitHub:

    gem install --user-install bundler
    gem install --user-install jekyll

Now to set up the initial jekyll site in order to preview it locally. (following along [here](https://docs.github.com/en/enterprise-server@3.1/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)) The following assumes opening a new terminal window, though you don't have to:

    cd ~/sites/henryroe.github.io
    source zshrc
    jekyll new --skip-bundle --force .
    
Open `Gemfile` that jekyll created and:

- Add "#" to the beginning of the line that starts with gem "jekyll" to comment out this line.
- Replace line `# gem "github-pages"` with `gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins`, replacing `GITHUB-PAGES-VERSION` with version shown [here](https://pages.github.com/versions/), which was 219 at time of writing.

then:

    bundle install
    bundle add webrick
    bundle install

Now launch and check the site locally (can be in terminal window):

    cd ~/sites/henryroe.github.io
    source zshrc
    bundle exec jekyll serve

Now, can open [http://127.0.0.1:4000/](http://127.0.0.1:4000/
) in a local browser window! And, once have committed back into GitHub, can view the same on GitHub at [https://henryroe.github.io](https://henryroe.github.io).

## Install a theme

I decided I wanted my new blog to look a lot like my most recent heroku-based blog, which was based on the "BlackDoc" Jekyll theme. Here are my notes:

Looking online the basic version of [blackdoc](https://jekyllthemes.io/theme/blackdoc) in its [github form](https://github.com/karloespiritu/BlackDoc) doesn't work with github pages. There is a forked version that itself has forks for [github pages](https://github.com/Robert-Zacchigna/BlackDoc) and [running locally](https://github.com/Robert-Zacchigna/BlackDoc/tree/BlackDoc-Local). (Found from [these notes](https://github.com/karloespiritu/BlackDoc/issues/9).)

I pulled down copies of both of those forked versions and hacked them together into a single version that works both locally for testing and on github pages for deployment. The key being to insert a bunch of `if` statements like:

	{% if jekyll.environment == "development" %}
	  <meta name="msapplication-config" content="/assets/favicons/browserconfig.xml">
	{% else %}
	  <meta name="msapplication-config" content="{{ "/assets/favicons/browserconfig.xml" | prepend: site.baseurl }}">
	{% endif %}

I then migrated over a bunch of the style edits I'd made to the old Heroku-served blog. The end result is what you see here. (And can see the source files of [here](https://github.com/henryroe/henryroe.github.io).)

And, being Markdown based, it was incredibly easy to migrate over the posts from my earlier heroku-based version of this blog. 
