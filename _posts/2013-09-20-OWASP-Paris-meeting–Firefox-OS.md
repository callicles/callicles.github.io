---
layout: post
title:  "OWASP Paris meeting – Firefox OS"
date:   2013-09-30 18:00:00
categories: Meetups
---

This Monday I was at the OWASP meeting for the first time. It was hosted at the Mozilla France quarters 
in Paris, in Montmartre Street.

The upcoming OWASP election was mentioned but the main topic still was Firefox Os

The Firefox Os is completely Web technology based. What this means is that everything is made
from Javascript, HTML and CSS. It also raises a lot of security issues. “Would you trust a call app
entirely web based ?” asked Paul Theriault, our Mozilla speaker. Probably not.

The Os is mainly based on Firefox engine, without the UI part. The lowest level has just enough 
linux and android to run the adapted version of Firefox. Then everything is rendered as JS, CSS 
and HTML, from the menu icons to the phone interface. The philosophy behind that choice is that a 
smartphone is an interface to the web and therefore, should be the web. The result is making hacks 
in the interface pretty easy : just take a look a the github repo [here](https://github.com/mozilla-b2g/gaia), it looks really cool. I am 
starting to feel like making my next phone a firefox Os one.

The Os runs on an 3-layered permission system. For Mozilla, the idea is that an app should’nt need 
any permissions unless it is absolutely necessary. That’s why the basic level of permissions only 
gives access to basic phone apiS. No data can be created, or modified with this level. The next 
level gives access to more stuff but these apps need to be reviewed by Mozilla to get into the 
marketplace. Finally there is what we could call the root level with system application that can 
access pretty much anything on the phone. This level of permission would not be made available 
for the developer.

However, being aware of the kind of concern this policy might raise among mobile developers, 
Mozilla thought of an activity system that could enable to access services such as SMS or call 
without compromising security. The concept is to make a broadcast call for a specific service. 
The system will then prompt the user with all applications providing these services so that 
he can choose what to do.

There are two types of packaging of applications :

* *Full packaged apps* : all the content and files of the app are on the phone
* *Hosted App* : the content of the app is hosted in the cloud

This can allow to very fast and smooth integrations.

This is the main things I have taken out of this meeting. By the way, Mozilla is looking for some 
contributors to either make some tests, review apps or contribute to the code. As always with Mozilla, 
the project is completely open source so feel free to contribute.

You can look at these links on the same subject:

* [Poulpita article](http://poulpitablog.wordpress.com/2013/09/16/owasp-in-paris-diving-in-firefox-os-security/)
* [Firefox Os](http://www.mozilla.org/fr/firefox/os/)
* [Mozilla Developper Network](https://developer.mozilla.org/)
 
And also check out the video of the pitch below !

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymX3Ecly8RM" frameborder="0" allowfullscreen></iframe>