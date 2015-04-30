# Chapter 6 - Objects

#Objects
JavaScript's fundamental datatype. 

**6.1** Creating Objects

**Literals**
```javascript
var obj = {};
```

**New**
```javascript
var obj = new Object();
```

**Object.create**
```javascript
//obj1 inherits properties x and y
var obj1 = Object.create({x:1, y:2});

//obj2 inherits no properties or methods
var obj2 = Object.create(null);

//same as new Object or {}
var obj3 = Object.create(Object.prototype);
```
**Prototype**
If an _Object_ has a prototype, the prototype is also an _Object_. These _Objects_ all chain together until you reach _null_, which is the end of the _prototype chain_.

    // Object is a constructor
    Object.prototype; // Object {}, will be the prototype of `new Object`s
    // Object.prototype is an Object
    Object.getPrototypeOf(Object.prototype); // null, we are at the end of the chain

You should also note, however, that you can't keep accessing the `obj.prototype` property, as this is only applicable to _Constructors_, consider

    function Foo() {
    }
    Foo.prototype; // Foo {}
    // vs
    (new Foo).prototype; // undefined

The correct way to find the prototype of an _Object_ is by using `Object.getPrototypeOf(obj)`, 

    Object.getPrototypeOf(new Foo) === Foo.prototype; // true

---

It may also be of note that legacy browsers may not support `Object.getPrototypeOf`, in which case many offer the property `obj.__proto__`. However, try to avoid using `__proto__` outside of a shim for such browsers if you need to access the prototype chain.

---

Finally, using `new` with a _Constructor_ isn't the only way to create this chain, you can set them up using `Object.create`

    var a = Object.create(null),
        b = Object.create(a), // b will inherit from a
        c = Object.create(b); // c will inherit from b, hence also a
    a.foo = 'foo';
    b.bar = 'bar';

    a instanceof Object; // false

    a.bar; // undefined
    c.foo + c.bar === 'foobar'; // true
    
Also consider

    c.prototype; // undefined
    // vs
    Object.getPrototypeOf(c) === b; // true

**6.2**

**6.3**

**6.4**

**6.5**

**6.6**

**6.7**

**6.8**

**6.9**

**6.10**