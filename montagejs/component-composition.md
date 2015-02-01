---

layout: docs
title: Component Composition

this-page: component-composition

---

Component Composition
===

The way to create and compose the UI for your application using MontageJS is primarily by expressing composition in the markup of your templates.

## `Repetition`

We a `content` array to the `Repetition` component, and this will tell `Repetition` to repeat the `li` and its associated `Text` component as many times as there are values in the `content` array (in this case three times).

```html
<script type="text/montage-serialization">
{
    "repetition": {
        "prototype": "montage/ui/repetition.reel",
        "properties": {
            "element": {"#": "repetition"},
            "content": [1,2,3]
        }
    }
    "text": {
        "prototype": "montage/ui/text.reel",
        "properties": {
            "element": {"#": "text"},
            "value": "hello"
        }
    }
}
</script>

<body>
    <ul data-montage-id="repetition">
        <li data-montage-id="text"></li>
    </ul>
</body>
```

## `Condition`

The `Condition` component tells `span` to show the `value` "This is the truth" when the `condition` property is `true`. In this case the `condition` will make sure the `span` is not visible.

```html
<script type="text/montage-serialization">
{
    "condition": {
        "prototype": "montage/ui/condition.reel",
        "properties": {
            "element": {"#": "condition"},
            "condition": false
        }
    }
    "text": {
        "prototype": "montage/ui/text.reel",
        "properties": {
            "element": {"#": "text"},
            "value": "This is the truth"
        }
    }
}
</script>

<body>
    <div data-montage-id="condition">
        <span data-montage-id="text"></span>
    </div>
</body>
```

## `Substitution`

The `Substitution` component allows you to branch the component tree based on a key in your data.

```html
<script type="text/montage-serialization">
{
    "customerNameSubstitution": {
        "prototype": "montage/ui/substitution.reel"
        "properties": {
            "element": {"#": "customerNameSubstitution"},
            "switchComponents": {
                "read" : "montage/ui/text.reel"
                "edit" : "montage/ui/input-text.reel"
            }
            "switchValue": "read"
        },
        "bindings": {
            "value": {
                "<-": "@customer.name"
            }
        }
    }
}
</script>

<body>
    Customer name: <div data-montage-id="customerNameSubstitution"></div>
</body>
```

## `Exposition`

The `Exposition` component allows you to specify components that may be related and need to occupy the same space in the `DOM`.

```html
<script type="text/montage-serialization">{
    "preferences": {
        "prototype": "montage/ui/exposition.reel"
        "properties": {
            "element": {"#": "preferences"}
        },
        "bindings": {
            "value": {
                "<-": "@customer.name"
            }
        }
    },
    "displayPanel": {...},
    "networkPanel": {...},
    "usersPanel": {...}
}</script>

<body>
    <div data-montage-id="preferences">
        <div data-param="display" data-montage-id="displayPanel"></div>
        <div data-param="network" data-montage-id="networkPanel"></div>
        <div data-param="users" data-montage-id="usersPanel"></div>
    </div>
</body>
```

## Implementing a Custom Component

The `CustomComponent` can make use of a _template argument_ to include all the contents of it's _inner template_. A template argument is an element that has the attribute `data-arg`. This marks the element as a placeholder that will replaced by the inner template.

```html
<script type="text/montage-serialization">{
    "CustomComponent": {
        "prototype": "my/custom-component.reel",
        "properties": {
            "element": {"#": "CustomComponent"}
        }
    }
    "text": {
        "prototype": "montage/ui/text.reel",
        "properties": {
            "element": {"#": "text"},
            "value": "I'm included."
        }
    }
}</script>

<body>
    <div data-montage-id="CustomComponent">
        <!-- inner template -->
        <span data-montage-id="text"></span>
    </div>
</body>
```

`CustomComponent`'s template: `my/custom-component.reel/custom-component.html`

```html
<script type="text/montage-serialization">{
    "owner": {
        "prototype": "my/custom-component.reel"
    }
}</script>

<body>
    <div>
        <!-- template argument to be replaced by inner template -->
        <span data-arg="*"></span>
    </div>
</body>
```
