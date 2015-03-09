---

layout: docs
title: MontageJS Objects

this-page: montagejs-objects

redirect_from: /docs/montage-objects.html

---

MontageJS Objects
===

* TOC
{:toc}


MontageJS provides a thin wrapper over the JavaScript object model. Types are represented by `constructor` functions. Constructor functions have a `prototype`. The `prototype` has a `constructor`. `instanceof` and `new` work as you would expect.

For example, following A and B examples are equivalent:


### Example A: JavaScript (ECMAScript 5)

```javascript
function Penguin() {
    Bird.call(this);
}

Penguin.prototype = Object.create(Bird.prototype);

Penguin.prototype.constructor = Penguin;

Penguin.prototype.fly = function () {
    return Bird.prototype.fly.call(this);
};

Object.defineProperty(Penguin.prototype, "habitat", {
    get: function () {
        return this._habitat;
    },
    set: function (value) {
        this._habitat = value;
    }
});

Penguin.staticMethod = function () {};
```

### Example B: Montage Framework

```javascript
var Penguin = Bird.specialize({
    constructor: {
        value: function Penguin() {
            this.super();
        }
    },
    fly: {
        value: function () {
            return this.super();
        }
    },
    _habitat: {value: null},
    habitat: {
        get: function () {
            return this._habitat;
        },
        set: function (value) {
            this._habitat = value;
        }
    }
}, {
    staticMethod: {
        value: function () {}
    }
});
```

The Montage `constructor` has a `specialize` method that accepts [ECMAScript 5 property descriptors](http://ecma-international.org/ecma-262/5.1/#sec-8.6) for the new prototype and another optional set of descriptors for properties of its constructor. It uses `Object.create` to extend the parent's prototype, and `Object.defineProperty` to apply the property descriptors. For the most part, this just provides a convenient and error-resistant way to declare new types, reinforcing the existing JavaScript conventions.


## Montage Methods

However, MontageJS does provide some additional features. Within any `Montage` method, `super(...args)` will call the eponymous method of the parent prototype. Likewise, `super()` within a getter will get a property according to the parent prototype, and `super(value)` within a setter will set a property according to the parent prototype.

In this example, the `Type` implements an `id` getter, where identifiers are granted in the order of first access. `Subtype` overrides the identifier property such that the identifier is a string with an underscore prefix.

```js
var ids = new WeakMap();
var nextId = 0;
var Type = Montage.specialize({
    id: {
        get: function () {
            if (!ids.has(this)) {
                ids.set(this, nextId++);
            }
            return ids.get(this);
        }
    }
});

var Subtype = Type.specialize({
    id: {
        get: function () {
            return "_" + this.super();
        }
    }
});
```

Montage also supports a small number of modifications to the [ES5 property-descriptor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty). Montage alters the defaults for `writable` and `configurable` properties are both writable and configurable unless you specify otherwise. In general properties continue are `enumerable` by default. The default is changed for properties with:

- Names that start with `_` - will not be `enumerable`
- Value is a function (methods)


## Extending the JavaScript Object Model

Perhaps the most subtle and interesting way that `Montage.specialize` extends the JavaScript object model is that it causes constructor functions to inherit from their parent constructor, in parallel the prototype chain. This makes it possible to use or override `Montage.specialize`, `defineProperties`, and `defineProperty` for subtrees of your object model. Montage implements `specialize` and `defineProperties` such that an overridden `defineProperty` is sufficient to specialize the property descriptor protocol for all descendent types. Overriding `specialize` gives you a hook to decorate the constructor for all descendent types.

```js
var Type = Montage.specialize({
}, {
    specialize: {
        value: function () {
            return this.super();
        }
    },
    defineProperty: {
        value: function (object, descriptor) {
            return this.super(object, descriptor);
        }
    }
});
```

For debugging, it is best to give your constructor a name. `Montage.specialize` permits a specialization to  provide the constructor among the `prototype` property descriptors. It lifts this property out instead of providing a default, anonymous constructor function then goes on to set up its prototype and inheritance chain as normal.

```js
var Type = Montage.specialize({
    constructor: {
        value: function Type() {
            this.super();
        }
    }
});

var Subtype = Type.specialize({
    constructor: {
        value: function Subtype() {
            return this.super();
        }
    }
});
```
