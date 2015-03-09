---

layout: docs
title: MontageJS Data Binding

this-page: data-binding
redirect_from: "/docs/Data-binding.html"
---


# Data Binding

>**Note:** We are currently in the process of updating our data bindings overview. In the meantime, please refer to the <a href="https://github.com/montagejs/frb/blob/master/README.md" target="_blank">Functional Reactive Bindings</a> document.

For a comparison between our old way of doing bindings and the new, FRB way of doing bindings, see our [FAQ for the FRB transition](/montagejs/frb.html).

Be careful w/ `cancelBindings()` as it cancels bindings on all of object's properties, including those that you didn't define. This may cause problems if a component `exitDocument()` then re-`enterDocument()`, e.g. via `Substitution`. Only cancel the bindings that you define.
