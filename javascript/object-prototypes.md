# Object Prototyes

When you create an object like this:

```js
const myObject = {
  city: "Madrid",
  greet() {
    console.log(`Greetings from ${this.city}`);
  },
};
```

In addition to the city and greet properties, you'll also have access to a whole host of other properties like:

```
__defineGetter__
__defineSetter__
__lookupGetter__
__lookupSetter__
__proto__
city
constructor
greet
hasOwnProperty
isPrototypeOf
propertyIsEnumerable
toLocaleString
toString
valueOf
```

What are these things? Well every object in JavaScript has a built-in property called its prototype.

In this example, the methods are set in the prototype and the data is set in the constructor of the Person object directly.

by defining this function in the prototype you can save memory instead of having to reinstantiate it every time.

```js
const personPrototype = {
  greet() {
    console.log(`hello, my name is ${this.name}!`);
  },
};

function Person(name) {
  this.name = name;
}

Object.assign(Person.prototype, personPrototype);
// or
// Person.prototype.greet = personPrototype.greet;
```
