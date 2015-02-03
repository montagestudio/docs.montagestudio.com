---
layout: docs
title: Gestures & Composers

this-page: gestures-composers

---

Gestures & Composers
===

* TOC
{:toc}

Montage provides a [`Composer` API](https://github.com/montagejs/montage/tree/master/composer) for supporting commonly used gestures. Typically `DOM` events are device specific such as click or touch events. The `Composer` API abstracts these into higher order events such as press, so that you can focus on handling a specific action rather than the multiple ways that action could be carried out. Montage currently supports below actions:

- press / long press
- swipe
- key press
- drag

## `PressComposer`
The Press Composer handles both press and long press gestures. These abstract mouse clicks and touch events into a common event. The events that are handled include:

**`pressStart`**
This is the event that is dispatched when the `mousedown` or `touchstart` events are fired.

**`press`**
After the `pressStart` event is fired, the `press` event will fire when releasing the mouse button (`mouseup` event) or lifting your finger (`touchend` event). This will also fire when a `longPress` event is fired, so can be cancelled with a `pressCancel` event.

**`longPress`**
A `press` gesture becomes a `longPress` gesture when it is active for longer than the specified `longPressTimeout` duration. To avoid a `press` event firing after a `longPress` event, it should be cancelled in the `longPressHandler` by calling the `cancelPress()` method.

**`pressCancel`**
This is fired when the `press` event is cancelled. This can either be because it was manually cancelled by the developer by calling `cancelPress()`, another element claims the event pointer, or is automatically cancelled due to:

- Browser firing the touch cancel event
- User cancels the event by moving away from the element when the `mouseup` event fires due to releasing the mouse button

### `press` and `longPress` gestures usage examples
We will create an example that handles a `press` event, changing the colour and text of the element, and showing a JavaScript `alert` when a `longPress` event is fired.

### Setting up your composers
As with anything in Montage, you first have import the module into your Javascript file. Both press and long press functionality can be found in the press-composer:

```js
var Montage = require("montage/core/core").Montage,
    Component = require("montage/ui/component").Component,
    PressComposer = require("montage/ui/composer/press-composer").PressComposer;
```

You then have to create and add the `PressComposer`:

```js
exports.PressExample = Montage.create(Component, {
     didCreate: {
        value: function() {
            this._pressComposer = PressComposer.create();
            this.addComposer(this._pressComposer);
        }
    }
});
```

### Handle the events
Once we have a `PressComposer` we can add the events we want to listen to. In this case both the `press` and `longPress` events:

```js
prepareForActivationEvents: {
        value: function() {
            this._pressComposer.addEventListener("press", this, false);
            this._pressComposer.addEventListener("longPress", this, false);
        }
    }
```

Finally we need to handle this events in the regular Montage way by implementing a method that prefixes the event name with `handle`.

For the `press` event, we add an additional class to the element so that we can style it differently after the user presses the button, and change the text using `innerHTML`:

```js
handlePress: {
    value: function(event) {
        this.element.classList.toggle("press-active");
        if (this.element.classList.contains("press-active")) {
            this.element.innerHTML = "I’m active!";
        } else {
            this.element.innerHTML = "Now deactivated";
        }
    }
}
```

For the `longPress` event we create a JavaScript `alert`, and also cancel the `press` event:

```js
handleLongPress: {
    value: function(event) {
        this._pressComposer.cancelPress();
        alert("Long press event fired.");
   }
}
```

In a real world app you may do something like creating a context menu with a number of items for the user to select.

### Hooking everything up
The only thing left is to hook the JavaScript up to some HTML using the Montage serialization, and add the styles using CSS:

HTML:

```html
<div data-montage-id="pressme" class="press-target">
    Click or long click me!
</div>
```

Serialization:

```json
{
    "pressExample": {
        "prototype": "PressExample",
        "properties": {
            "element": {"#": "pressme"},
            "hasTemplate": false
        }
    }
}
```

If you click or touch the element for a short time the `PressComposer` will fire. If you keep the button pressed or your finger down the `longPress` event will fire.

## `SwipeComposer`

Montage currently supports swipe gestures only for touch screen enabled devices, excluding desktop platforms. The spec and implementation of the `SwipeComposer` is currently being updated for a future release of Montage.

## `KeyComposer`

TBD

## `TranslateComposer`

TBD