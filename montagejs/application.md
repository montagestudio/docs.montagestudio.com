---
layout: docs
title: MontageJS Application

this-page: application
---


MontageJS Application
===

* TOC
{:toc}

[Application API Reference]({{site.baseurl}}/api/Application.html)

## Global Configuration

Define global constants to be used app-wide via [Application.delegate]({{site.baseurl}}/api/Application.html#delegate), which observes your app's loading state.

1. Define custom app delegate with your desired name in serialization in `index.html` then assign to `Application.delegate`:

```json
{
    "application": {
        "prototype": "montage/core/application",
        "properties": {
            "delegate": {"@": "customAppDelegate"}
        }
    },
    "customAppDelegate": {
        "prototype": "custom-app-delegate"
    }
}
```

2. Define custom app delegate class in `custom-app-delegate.js`. Define config values in its `willFinishLoading` method:

```js
var Montage = require("montage/core/core").Montage;

exports.AppDelegate = Montage.specialize({
    willFinishLoading: {value: function (app) {
        // can assign any property to app with any name
        app.config = {
            // Define app-wide global config var here
            // e.g. DEBUG_MODE, etc.
            APP_VERSION: 1
        };
    }}
});
```

3. Now you can get the config values anywhere in the app, e.g. in `ui/main.reel/main.js`

```js
var Component = require("montage/ui/component").Component;

exports.Main = Component.specialize({
    constructor: {value: function () {
        console.log(this.application.config.APP_VERSION); // 1
    }}
});
```
