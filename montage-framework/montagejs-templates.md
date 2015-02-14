---
layout: docs
title: MontageJS Components

this-page: montagejs-templates
---

MontageJS Templates
===

* TOC
{:toc}

Templates are full HTML5 documents

deserialize serialization
`body` content gets cloned

Components don't serialize/deserialize anything, they use Component.innerTemplate to access content

## Component Composition

Static - composition doesn't change

Dynamic

Pass content to another component by:

- Passing in a component via `Slot` component
- Passing in a `DOM` element as `domContent`, can only pass in 1 element
- Use template parameters, 100% markup based

## Template Arguments / Parameters

New in `v0.13.0`

Attributes:

- `data-param` use when declaring component's template, to be replaced with `data-arg` element
- `data-arg` use when using the component, will replace component template's `data-param` element

The element with above attributes becomes the parameter / argument.

Can use these attributes directly on a component's element, no need to create wrappers, e.g.:

```html
<!-- text is montage/ui/text.reel -->
<h1 data-arg="*" data-montage-id="text"></h1>
```

`data-param="*"` - will replace everything inside, `*` cannot be used together with other named params

Will be replaced by markup that was given to the component

Can give multiple named template params, e.g.: `data-param="title"` `data-param="message"`

No optional params yet.

---

For more info and a video walkthrough with examples of various composition patterns, please watch:

[![Montage Template](https://img.youtube.com/vi/CeuG2zptrtM/0.jpg)](https://www.youtube.com/watch?v=CeuG2zptrtM)









DOM arguments

Components can now receive DOM arguments. A DOM argument is specified in the component markup by adding a data-arg attribute and assign a name to its value. DOM arguments can be referenced after the first enterDocument with the extractDomArgument(name) method. When a component has a Template with parameters, each template parameter element is replaced with the corresponding component argument element.

Template

Templates can now have DOM parameters. A DOM parameter is specified in a template using the data-param attribute on the DOM node that represents the parameter. data-param has the value of the parameter name.