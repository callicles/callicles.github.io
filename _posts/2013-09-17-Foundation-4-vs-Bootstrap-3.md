---
layout: post
title:  "Foundation 4 vs Bootstrap 3"
date:   2013-09-17 10:48:00
categories: Reviews
---

Lately, as part of Quandora, I worked with both Foundation 4 and Bootstrap 3. This article is a 
snapshot of my thinking around both of them, including their developing environment. But first I 
would like to emphasize my background so that you can put my point of view into perspective. At this
moment I am a master engineering student at the Ecole des Mines de Nantes (France) majoring in
computer science. I started making websites from scratch when I was 13 and discovered CSS at that
time (the websites looked pretty bad though … :p ). I first found out about foundation and responsive 
design last year and used Foundation 3 for the former version of this website using CSS only. I 
also used Bootstrap as CSS in school projects  during last year.

At Quandora, one of my assignments was to build a new version of their website. As I was already 
familiar with it, I chose to use Foundation by using the WordPress Framework Reverie 4 
(also used in this website) . Then I had to update Bootstrap from 2.3.2 to 3.0 on Quandora 
which is using Bootswatch for theme management.

This should give you a snapshot of my brief experience with both frameworks.

## The Frameworks : fraternal twins
As far as the standard features are concerned and as both are now mobile first CSS frameworks, 
the use is pretty much the same. For example, here is how to make use of the grid :

{% highlight html %}
<div class="row">
  <div class="small-2 large-4 columns">...</div>
  <div class="small-4 large-4 columns">...</div>
  <div class="small-6 large-4 columns">...</div>
</div>
{% endhighlight %}

{% highlight html %}
<div class="row">
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
</div>
{% endhighlight %}

You can see there is not much of a difference. However, I will point out that Bootstrap handles 
3 grids size (Desktop, Tablet and Mobile) whereas Foundation handles 2 (the tablet one is beta for now). 
Foundation also needs more code to get the work done (one more class). I think that may be for 
optimization purposes (not to repeat codes in two classes) but still.

When you go through both documentations, you realize that both frameworks have the overall same
components. There are some Bootstrap specific features such as Affix.js, collapse.js or popover.js 
and some Foundation specifics’ : Interchange, Pricing tables or Joyride.

On the responsiveness end, I have only worked with Foundation 4, which works great, I can’t really 
testify as far as Bootstrap is concerned. Although I think they should be equal


What I can talk about is customization. In my experience, Foundation is much more flexible than in 
bootstrap is. In bootstrap customization comes with the bundle : the standard way to do things is 
to download a css file that you have customized on the website. Although this can seems handy, 
I don’t think it is : if you want to try several colors you have to each time fill in the huge form, 
download the css and then plug it in your website.

![Bootstrap customization screen]({{ site.url }}/assets/images/bootstrap-personalization.png)

In Foundation the standard way to do things is to install the Foundation gem and to create a 
foundation project in your developing folder. In that folder, a settings SCSS file is created 
with a list of all the variable available to customization. You just have to modify that file, 
and save it to see the change results. As a matter of fact, setup may be a bit longer but you 
gain a whole bunch of time later and that’s totally worth it

Moreover, all Foundation objects come with their mixin documentation. They are very well written 
and you can do pretty much anything with them. This makes it very quick to change components looks 
without having to develop one completly from scratch. In the end, you can do the same in bootstrap,
but it is not documented, you have to get your head inside their LESS and pretty much customize 
bootstrap itself. I find it much more time consuming.

## Developing environment, this is what makes the difference

To me, that is mainly why I prefer Foundation over Bootstrap. Bootstrap is written is LESS and 
needs some dependencies. Although Grunt is a great way to get all the dependencies right and to 
compile everything in one command, I found the error messages crappy.

One could say “if you have errors it is because you’re not a good developer”. Well, 
who hasn’t forgotten a semicolon ? Probably nobody. Well, to me the LESS compiler is not really good. 
Furthermore, the fact that Bootstrap needs different dependencies to compile and that these dependencies 
change over versions, is also painful.

With foundation, you install the gem, install the compass compiler and you are ready to go ! And 
the compass compiler is great. Whatever error you may have, the error message is embedded into the 
web page so that you get it right away. The error messages are clear and accurate.

## Conclusion
I will conclude by putting things into perspective. If you only need a css to have a good looking 
website fast and don’t bother for how things look in detail, go for Bootstrap. It is well 
documented and there is a huge community to help you with any problem you might face. However, 
if you want something highly customizable to use with a CSS preprocessor, go for Foundation. 
It’s a really great Framework that uses great tools,

