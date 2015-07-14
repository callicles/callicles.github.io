---
layout: post
title:  "Owasp France September 2014 meeting"
date:   2014-09-22 11:08:00
categories: Meetups
---

On the 11 of September 2014 night was held the first owasp France meeting of the year.

On the menu:

* SonarQube : How improving code quality will help you improve level of security
* JavaScript and HTML5 : XSS have never been that powerful

##SonarQube
SonarQube is a tool for checking code quality that was presented by Sebastien Gioria. 
It checks code quality by checking compliance to sets of rules defined in profiles. 
But the question is : where does security comes in and how come a code quality analysis tool is presented at an owasp meeting ?

Well, having a code of great quality does diminish the risk of having security issues. Let’s take what SonarQube covers point by point:

* Architecture and Design
* Duplications
* Comments
* Coding rules
* Unit tests
* Potential bugs
* Complexity

Let’s look at those on a security standpoint. With duplications security flaws can occur several times. 
Not really good, if you patch something, somewhere, you will have to patch it several times. 
A very complex code is difficult to maintain and updates can break the code. Some very basic coding 
rules can be used to avoid some common programming mistakes. And Finally comments are always useful 
to get a hold of what the previous programmer did.

All these points can be enforced as rules in the application. Rules can be grouped in profiles 
to check the code specifically and add-ons can be used to add rules or programming language coverage. 
I believe to have answered the question, why a code analysis tool ? Now why at an OWASP meeting ?

It was announced that OWASP and SonarSource are going to release a security plugin mid october 
to check for common pitfalls in Java and C/C++ (as a starting point). This is very good news 
since this plugin will be supported and free. It will be a great way to enforce security in projects 
from the ground up.

## XSS exploits using HTML5

The second talk by Laurent Levi was about 4 xss exploits using HTML5.

* How an XSS vulnerable page compromise the whole website
* How to use XSS to map a client’s network
* How to break an HTML5 sandbox
* How to use HTML5 to trick the user into allowing special autorisations (Webcam Use, microphone …)

I won’t go through the details of each exploit, feel free to go through the video below or ask for details if you wish.

What this presentation really underlines is the power that cross-site scripting has today. JavaScript has become so powerful that you can nearly do anything. I guess, what you can take out of it is: beware of XSS !

Here is the complete talk (FR):
<iframe src="https://air.mozilla.org/owasp-france-meeting-mozilla-paris/video/" width="640" height="380" frameborder="0" allowfullscreen></iframe>