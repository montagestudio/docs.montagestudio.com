---

layout: docs
title: MontageJS Event Handling

this-page: event-handling

redirect_from: "/docs/Event-handling.html"

---

Event Handling
===

* TOC
{:toc}

Montage includes a custom event manager that transparently wraps the browser’s native event handling mechanism. This enables several features in Montage, including simpler event handling code, property change observing, and results in better performing web applications.

## About Event Delegation

Montage uses _event delegation_ to manage event handling and dispatching. With event delegation, instead of installing event listeners on every element that may dispatch an event, a single event listener is installed on a parent element that listens for and responds to events that target its children. This is made possible by the standard event “flow” defined by the [DOM Level 3 Event Specification](http://www.w3.org/TR/DOM-Level-3-Events/#event-flow).

Event delegation provides several benefits. For instance, application performance is improved since the number of event listeners is reduced. In a Montage application there is only one “native” event listener, which acts as the primary event responder and dispatcher of all events. It also enables Montage applications to observe changes to property values and arrays.

## Creating Event Handlers

You use the standard `addEventListener()` method to register an event handler on a target object. In Montage, the `target` object can be any JavaScript object, not just a DOM element.

`target.addEventListener(eventType, listener[, useCapture]);`

* `eventType ` A string representing the event type.
* `listener` An object that implements the Montage event listener interface, or a function to call directly.
* `useCapture` boolean; if true, causes all events of the specified type to be dispatched to the registered listener before being dispatched down to children targets' listeners. Default is `false`, i.e. uses **bubble** to propagate upward, opposit of **capture**.

### Montage Event Listener Interface
The Montage event listener interface extends the [DOM Level 3 EventListener interface](http://dev.w3.org/2006/webapi/DOM-Level-3-Events/html/DOM3-Events.html#interface-EventListener) specification implemented by all modern web browsers. In the standard interface you specify an object as a “listener” object for an event type. The listener object defines an `handleEvent()` method that is invoked by the browser whenever the specified event occurs:

```js
// DOM Level 3 EventListener interface
var listenerObj = {};
listenerObj.handleEvent = function(event) {
     alert("Got 'mousedown' event.");
}
var loginBtn = document.querySelector("#loginBtn");
loginBtn.addEventListener("mousedown", listenerObj);
```

Montage extends this interface to make it more useful for developers. Instead of calling the same `handleEvent()` method on the listener object, Montage infers the name of the specific event handler method to call from below information:

* The event’s phase, prefixed by `handle` for bubble, `capture` for capture
* The event name, e.g. `action`
* The Monrage component's name
* Optionally, a string `identifier` property on the target element or object, which overrides component's name

E.g. to handle a click event during bubble phase for a component named `FooComponent` without an `identifier` property on `FooComponent`, Montage will invoke the `handleFooComponentClick()` method on the listener object. If we define `identifier` as `bar`, Montage will invoke `handleBarClick()`. Note the method name will be automatically lowerCamelCased.

### Examples

The following code is almost identical to the previous example without Montage, except that the handler method is named `handleMousedown()` instead of `handleEvent()`. This method will be invoked automatically by the event manager when the `mousedown` event occurs on `loginBtn`, but only during the event’s bubble phase.

```js
// Listening for mousedown event during bubble phase
var listenerObj = {};
listenerObj.handleMousedown = function(event) {
     alert("Got 'mousedown' event.");
}
var loginBtn = document.querySelector("#loginBtn");
loginBtn.addEventListener("mousedown", listenerObj);
```

To listen for the same event during its capture phase, you pass `true` as the third parameter to `addEventListener()`, and change the name of the event handler from `handleMousedown()` to `captureMousedown()`.

```js
// Listening for capture events on same element
var listenerObj = {};
listenerObj.captureMousedown = function(event) {
     alert("Got 'mousedown' event during bubble phase.");
}
var loginBtn = document.querySelector("#loginBtn");
loginBtn.addEventListener("mousedown", listenerObj, true); // useCapture = true
```

You can further specialize the event handler name by adding an `identifier` to the event target. The event manager includes this string, with its first letter capitalized, in the method name it composes. In the following example, the string “__login__” is assigned to the `loginBtn`‘s `identifier` property, so the event listener defines a `handleLoginMousedown()` function.

```js
// Using identifier strings on target elements
var listenerObj = {};
// Listener for loginBtn
listenerObj.handleLoginMousedown = function(event) {
    console.log("mousedown on loginBtn");
}
var loginBtn = document.querySelector("#loginBtn");
// Assign string identifier to button
loginBtn.identifier = "login";
loginBtn.addEventListener("mousedown", listenerObj);
```

### Event handler precedence
The event manager will always invoke the most specific event handler. For instance, in the following example the listener object defines two event handlers, one that includes the target’s identifier string (`handleLoginMousedown()`) and one that doesn’t (`handleMousedown()`). Montage will always invoke `handleLoginMousedown()` as its purpose is more specific than the other.

```js
// Event handler precedence
var listenerObj = {};
listenerObj.handleMousedown = function(event) {
     // This won't get called.
     alert("Got 'mousedown' event.");
}
listenerObj.handleLoginMousedown = function (event) {
     alert("Got 'mousedown' event on event.target");
}
var loginBtn = document.querySelector("#loginBtn");
loginBtn.identifier = "login";
loginBtn.addEventListener("mousedown", listenerObj);
```

Note that if `loginBtn` did not define an `identifier` property, the event manager would invoke `handleMousedown()`.

Also, Montage will invoke the listener’s generic `handleEvent()` method, if it exists, and if a more specifically named handler is not declared. This provides a fallback mechanism to respond to “generic” events.

```js
// Using default handleEvent() handler
var listenerObj = {};
listenerObj.captureClickEvent = function(event) {
     alert("Got click event");
}
listenerObj.handleEvent = function(event) {
     alert("No specific handler for " + event.type);
}
loginBtn.addEventListener("mousedown", listenerObj);
loginBtn.addEventListener("click", listenerObj, true);
```

## Declaring event listeners in a serialization
Each object in a serialization may include a "listeners" object that specifies the event type, listener object, and (optionally) whether to enable capture for the event.

First you create the listener object, which contains a `handleAction()` method. This method changes the `value` property of the Montage Button component that dispatched the event, setting its label.

```js
// controller.js
var Montage = require("montage/core/core").Montage;

exports.Controller = Montage.create(Montage, {
    handleAction: {
        value: function(event) {
            event.target.value = "Well done";
        }
    }
})
```

Next we create the HTML page that declares the Button component and the custom Controller object. The Button component’s `listeners` property specifies the type of event to listen for (`action`) and the listener object that will handle the event.

```html
<html>
 ...
<script type="text/montage-serialization">
{
    "button" : {
        "name": "Button",
        "module": "montage/ui/button.reel",
        "properties": {
            "element": {"#": "btn"}
        },
        "listeners": [
            {
                "type": "action",
                "listener": {"@": "controller"}
            }
        ]
    },

    "controller": {
        "name": "Controller",
        "module": "controller"
    }
}
</script>
 ...
</html>
```

You can also specify the `identifier` string in the serialization, as shown below:

```json
{
    "button" : {
        "name": "Button",
        "module": "montage/ui/button.reel",
        "properties": {
            "element": {"#": "btn"},
            "identifier": "purchase"
        },
        "listeners": [
            {
                "type": "action",
                "listener": {"@": "controller"}
            }
        ]
    },

    "controller": {
        "name": "Controller",
        "module": "controller"
    }
}
```
