# Mutability

Mutable objects are data types that can be accessed and changed after they've been created and stored in memory. Immutability refers to data types that can't be changed after creating them.

In JavaScript, primitives (go on the stack, string, number, boolean, null) are immutable, but references (go on the heap, objects, functions, arrays) are mutable.

For example, after running this code snippet

```js
const staff = {
  name: "Strengthened",
  age: 43,
  Hobbies: ["reading", "Swimming"],
};

const staff2 = staff;

console.log(staff);

console.log(staff2);
```

![Image](/javascript/assets/mutable-vs-immutable-javascript.JPG)

You can use a spread operator to copy the exact properties of an object you are working with.

### Issues with directly modifying objects

- Hard to debug and can lead to unpredictable behaviour in shared states.
- This context can be hard to keep track of
