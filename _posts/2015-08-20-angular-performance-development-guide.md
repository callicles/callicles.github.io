---
layout: post
title: "Angular performance extension development guide"
date: "2015-08-20"
categories: "Angular chrome-extension performance"
---

[Angular performance](https://github.com/Linkurious/angular-performance) is a chrome extension I developed while working for [Linkurious](http://linkurio.us) to get concrete performance metrics about any angular application. As of now, I try to maintain it on my free time, which I don't have that much since I am also working on another open source project called [GitRank](https://github.com/gitlinks/github-rank-project). As a consequence, I am trying to make it easier for anyone to make pull requests and try to fix or improve stuff in the extension by providing this guide. It should be self sufficient, even though you don't have any experience in developing a chrome extension.

Please provide any feedback you feel necessary in the comments below, I will try to improve this according to them.

* TOC
{:toc}

------

## Folder structure
```
- + .scss          Stylesheets to be compiled with compass
- + extension +    Extension folder, this is the folder that
              |    represents the extension. If you want to install
              |    the extension manually, you should add this folder
              |    as the extension.
              |
              + _locales     containing translating files.
              + css          compiled and vendor css.
              + fonts
              + images
              + src      +   Containing the source files of the
                         |   extension (html/js)
                         |
                         + devtools    This is the devtools page.
                         + injected    Contains the content-script
                         |             the script injected in the
                         |             page
                         + panel       Contain the html and js of the
                         |             devtools panel
                         + vendors     js dependencies

- + panelApp +     Contains the panel code before built. The result
             |     of the build is output in the panel folder (above)
             |
             + models         Panel app models
             + panels         js behind each panel.
```

## The Build process & dependencies


## The extension lifecycle (TODO)

## The registry (TODO)

## UI (TODO)

### Tab Handler (TODO)

### Panels (TODO)

## Resources

* [Chrome extension getting started](https://developer.chrome.com/extensions/getstarted)
* [Ember extension](https://github.com/emberjs/ember-inspector)
