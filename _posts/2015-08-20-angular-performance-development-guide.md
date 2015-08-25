---
layout: post
title: "Angular performance extension development guide"
date: "2015-08-20"
categories: "Angular chrome-extension performance"
---

[Angular performance](https://github.com/Linkurious/angular-performance) is a chrome extension I developed while working for [Linkurious](http://linkurio.us) to get concrete performance metrics about any angular application. As of now, I try to maintain it on my free time, which I don't have that much since I am also working on another open source project called [GitRank](https://github.com/gitlinks/github-rank-project) and is enrolled in a master engineering degree at Cornell Tech. As a consequence, I am trying to make it easier for anyone to make pull requests and try to fix or improve stuff in the extension by providing this guide.

Please give me any feedback you feel necessary in the comments below, I will try to improve this according to them.

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

We use npm scripts as build tasks. Node is completely able to handle build without having to require a build tool like grunt. However, by using npm, we cannot specify the directory in which the dependencies will be imported. As a result the first tasks of the build process consist in copying the right files into the right directories. Then we aggregate and minify all the css files and finally, we  [browserify](http://browserify.org/) all the panel files, aggregate them and put the result into panel.js.

We use browserify as a way to structure the browser code in the extension. Thanks to that we are able to write node js like code and access functionalities like `require`. At compile time, browserify gets all the required dependencies from the `node_modules` folder and creates a js file that can be understood by the browser by mocking some of node functions.

![Schema of the build process](https://docs.google.com/drawings/d/1cpGahfztH7ZcJb4fnzc4Jy6VxkGMJG4bJR3ygsamGv0/pub?w=1478&h=150)

## The extension architecture
First one important thing to understand about extensions is that they have a background script that is instantiated once and serves as a the vertebral column of the extension. Each tab connects to the same background.js instance.

The devtools are just the same as tabs. They can be seen as tab that connect to the background script. For each tab you have a unique tuple of (tab, background, devtool) and you have to keep track of them to be able to communicate between the tab and the devtools.

In all tabs the extension injects the content-script located in the `injected` folder. This content-script initiate connection with the background page. It only injects the inspector in the tab if the devtools are opened.

![Architecture of the extension](https://docs.google.com/drawings/d/1ZrT5lxe7K34IPcJxXZs0d4brqftGJXYk5RWBm9qpR9w/pub?w=1361&h=1078)

Once injected, the inspector determines if angular is used in the webpage. If it is not, it doesn't do anything. Else, it instruments the application and starts sending measurements to the content-script, that follows it to the background page that finally relays it to the panel.

The devtools page is only used to instantiate a panel in which the UI of the extension lives. Once that done, the devtools page is not useful anymore.

The setting up of the content-script, the background page and the devtools page are done in the `manifest.json` file at the root of the extension folder. This file describes all the metadata of the chrome extension.

## The registry


## UI (TODO)

### Tab Handler (TODO)

### Panels (TODO)

## Resources

* [Chrome extension getting started](https://developer.chrome.com/extensions/getstarted)
* [Ember extension](https://github.com/emberjs/ember-inspector)
