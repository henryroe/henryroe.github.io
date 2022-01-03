---
layout: post
title: iMessage yourself
published: True
date: 2015-08-12 13:32
categories: []
tags: []
---

There are instances where I find it useful to iMessage myself.  For
example, when a long code is done running.  Or, when something has gone
wrong with a piece of equipment.

<!--more-->

For something simple like when a code is done running on my laptop, I'll
iMessage myself from my own account.  In the case of alerting me about
equipment, particularly where others have access to the server, I'll set
up a separate iCloud account for that server.

In either case, the key elements are that my contact information in the
sending iCloud account's Contacts with my cell phone number.

Pretending that my cell phone number is *+1 (928) 123-4567*, the following
command line works:

{% highlight bash %}

osascript -e 'tell application "Messages" to send "Hey, your code crashed again. Better check on it." to buddy "19281234567" of (1st service whose service type = iMessage)'

{% endhighlight %}

Pulled apart in to an AppleScript:

{% highlight applescript %}

tell application "Messages"
	send "Hey, your code crashed again. Better check on it." to ¬
	     buddy "19281234567" of ¬
	     (1st service whose service type = iMessage)
end tell

{% endhighlight %}

Or, finally as some simple python with no need for fancy applescript libraries:

{% highlight python %}

import subprocess

msg = "Hey, your code crashed again. Better check on it."

cmd = 'tell application "Messages" to send "'
cmd += msg
cmd += '" to buddy "19281234567" of '
cmd += '(1st service whose service type = iMessage)'
subprocess.call(['osascript', '-e', cmd])

{% endhighlight %}
