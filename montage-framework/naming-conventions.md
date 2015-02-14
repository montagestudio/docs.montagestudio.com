---
layout: docs
title: Naming Conventions
this-page: naming-conventions
redirect_from: /docs/Naming-Conventions.html
---

Naming Conventions
===

* TOC
{:toc}

This document summarizes MontageJS-specific naming conventions and recommendations for modules, components, and CSS classes. Please refer to these conventions when creating MontageJS packages or contributing to the MontageJS framework.


## Modules

All module and package names are written in lowercase letters or numbers and delimited by dashes (for example, `child-package`).


## Components (`.reel` directories)

User interface components are stored in the ui directory of your MontageJS project and identified by a .reel extension.

The following naming conventions apply for `.reel` directories:

* Component names are always spelled in lowercase letters.
* If a name uses multiple words, follow a dash-delimited `"word-word"` pattern; for example, `radio-button.reel` or `text-field.reel`.


## CSS Classes

CSS class names follow a dash-delimited `package-Component` and `package-Component-childElement` pattern. For variations and states, double dash is used. For example, for the Digit Progress component it would be:

```css
.digit-Progress          /* package-Component */
.digit-Progress-bar      /* package-Component-childElement */
.digit-Progress--small   /* package-Component--variation */
.digit-Progress--loading /* package-Component--state */
```

More specifically, the following conventions apply:

- **Components:** All CSS classes are namespaced with _package_ + _dash_, e.g. `montage-`, `digit-`, `montage-digit-`, and followed by the CapCase component name. E.g. a button component would be `digit-Button`:

```html
<button class="digit-Button">
```

If a component name consists of more than one word, each new word also starts with an uppercase letter, a convention commonly referred to as _UpperCamelCase_ ("CamelCaps") formatting; for example, `montage-InputRange`.

- CSS classes should always be qualified, e.g. `.digit-Slider .digit-Slider-knob`, not `.digit-Slider .knob` to avoid collision of `.knob` elsewhere.

- **Composite components:** For components with children follow these conventions:

    * Only component itself should be UpperCamelCase, e.g. `FooComponent`
    * If a component has a child element, the child's name is written in lowercase (to signal the distinction between parent and child) and follows the component’s name separated by a dash; for example, `digit-Slider-thumb`

- **Variations:** If a component offers variations, a double-dash is used; for example: `digit-Button--primary`, `digit-Slider--vertical`.

* **States:** If a component uses different states, an `is-` prefix is used; for example: `is-hidden`, `is-active`. It's advised to not style them globally because each component could handle a state differently. Limit it on a per component level: `.Component.is-hidden { display: none; }`.


### Rationale

These CSS naming conventions are similar to the [BEM](http://bem.info/method/) methodology with some minor syntax changes:

* Name-spacing classes with the package avoids name collisions when multiple packages are in use.
* Not using underscores ( _ ) increases usability because you can double-click each part to quickly select and edit it. (Try it: `digit-Slider-thumb` versus `digit_Slider_thumb`.)
* Using upper CamelCase for components highlights component/child relationship.
* Using lower camelCase for multiword names increases readability, but still keeps each part grouped together.
