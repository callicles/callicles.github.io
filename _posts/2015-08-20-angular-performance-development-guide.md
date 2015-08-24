---
layout: post
title: "Angular performance extension development guide"
date: "2015-08-20"
categories: "Angular chrome-extension performance"
---

[Angular performance](https://github.com/Linkurious/angular-performance) is a chrome extension I developed while working for [Linkurious](http://linkurio.us) to get concrete performance metrics about any angular application. As of now, I try to maintain it on my free time, which I don't have that much since I am also working on another open source project called [GitRank](https://github.com/gitlinks/github-rank-project). As a consequence, I am trying to make it easier for anyone to make pull requests and try to fix or improve stuff in the extension by providing this guide.

Please provide any feedback you feel necessary in the comments below, I will try to improve this according to them.

* TOC
{:toc}

------

## Folder structure
~~~
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
~~~

## The Build process & dependencies
The extension uses npm as the dependency manager. It is used to manage these depenencies:

* [Bootstrap](http://getbootstrap.com/)
* [Font-awesome](https://fortawesome.github.io/Font-Awesome/)
* [Lodash](https://lodash.com/)
* [JQuery](https://jquery.com/)
* [JQuery UI](http://jqueryui.com/)
* [Metis Menu](https://github.com/onokumus/metisMenu)
* [Rickshaw](http://code.shutterstock.com/rickshaw/)

We use npm scripts as build tasks. Node is completely able to handle build without having to require a build too like grunt. As a result the build is divided into some substasks. First, by using npm, we cannot specify the directory in which the dependencies will be imported. As a result the first tasks are bout copying the right files into the right directories. Then we minify all the css files, [browserify](http://browserify.org/) all the panel files in the right folders.

We use browserify as a way to structure the browser code in the extension. Thanks to that we are able to write node js like code and access functionalities like `require`. At compile time, browserify gets all the required dependencies from the `node_modules` folder and creates a js file that can be understood by the browser by mocking some of node functions.

![Schema of the build process](https://docs.google.com/drawings/d/1cpGahfztH7ZcJb4fnzc4Jy6VxkGMJG4bJR3ygsamGv0/pub?w=1478&h=150)

## The extension lifecycle (TODO)

## The registry (TODO)

## UI (TODO)

### Tab Handler (TODO)

### Panels (TODO)

## Resources

* [Chrome extension getting started](https://developer.chrome.com/extensions/getstarted)
* [Ember extension](https://github.com/emberjs/ember-inspector)
