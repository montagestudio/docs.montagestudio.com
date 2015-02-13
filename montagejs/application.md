---
layout: docs
title: MontageJS Application

this-page: application
---


MontageJS Application
===

* TOC
{:toc}


## Global Configuration

Instantiate app with global constants to be used app-wide using [Application.delegate](/api/Application.html#delegate).

Serialization in `index.html`

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

`custom-app-delegate.js`

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

`ui/main.reel/main.js`

```js
var Component = require("montage/ui/component").Component;

exports.Main = Component.specialize({
    constructor: {value: function () {
        console.log(this.application.config.APP_VERSION);
    }}
});
```
