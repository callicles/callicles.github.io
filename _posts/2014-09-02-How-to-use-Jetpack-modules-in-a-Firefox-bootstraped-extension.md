---
layout: post
title:  "How to use Jetpack modules in a Firefox bootstraped extension"
date:   2014-09-02 14:33:00
categories: Tutorials
---

I recently worked on a firebug extension. As such it is also a Firefox bootstrap extension. 
However, I needed some of the modules provided by the jetpack SDK and here is how I used it.

## Get the loader

The first set is to get the CommonJs jetpack loader and configure it so that it can be used to 
load jetpack modules. This should be done inside the bootstrap.js file

{% highlight javascript %}

// Get the loader
let { Loader } = Components.utils.import("resource://gre/modules/commonjs/toolkit/loader.js", {});

// Instanciate it with the correct options
let loader = Loader.Loader({
  paths: {
    "sdk/": "resource://gre/modules/commonjs/sdk/",
    "": "resource://gre/modules/commonjs/"
  },
  modules: {
    "toolkit/loader": Loader,
    "@test/options": {}
  },
  resolve: function(id, base) {
    if (id == "chrome" || id.startsWith("@"))
    	return id;
    return Loader.resolve(id, base);
  }
});

// Here you configure the requirer id and URI. The URI can be the chrome root of your addOn.
let requirer = Loader.Module("main", "chrome://URItoRequire");

// Finaly you get the corresponding require to use to load jetpack modules.
let require = Loader.Require(loader, requirer);

{% endhighlight %}

##Use it
It should be as simple as calling the ‘require’ function, but it is not really. 
What you need to know is that the loader initialisation takes time, and not completely sequential. 
What I mean by that is: if you try to call the require function on line 32 of the previous snippet, 
it will fail. What you need to do it to call it from a different file or try invoking it with a setTimeout.

Another thing to consider is that, in a jetpack addon, jetpack initializes some variables and
 services that may be used by the module you are trying to load. In that case, if you try to use 
 that very same module, you will probably end up having unusual behaviour.

One of those module is the window module which is needed by the page-worker module.

{% highlight javascript %}
const { ready } = require("sdk/addon/window");

ready.then(
  function onfullFill(){
    // load the module after init
    let pageWorkerBuilder = require("sdk/page-worker");
  },
  function onRejection(rejection){
  	// Do something here if init failed.
  }
);

{% endhighlight %}

Thanks to ZERO for helping out with this.

[Loader MDN doc](https://developer.mozilla.org/en-US/Add-ons/SDK/Low-Level_APIs/_loader)