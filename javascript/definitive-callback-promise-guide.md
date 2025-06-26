# Definitive Callback, Promise and Asynchronous Coding Guide

JavaScript is a single threaded language. So we need to figure out ways to do things in the background, in order to avoid stopping out programs in their entirety (UI Just freezing up)

### Callbacks

One of the first ways to do things asynchronously. A callback function is a function that is passed as an argument to another function, and only executed after that other function finished.

```js
// In this example, setTimeout is an asynchronous function.
// It takes a callback function (the arrow function) and a delay.
// This callback function is placed into the event loop.
// After approximately 1000ms, the event loop will execute this callback.
setTimeout(() => {
  console.log("After one second");
}, 1000);
```

However, we run into the case of callback hell, which nests callback functions within one another.

This can be troublesome because:

- Its hard to read and understand
- Difficult to maintain
- Challenging for Error Handling

### Promises

This is where Promises are useful. A promise represents the eventual completion or failure of an operation. A promise can either be `pending`, `fulfilled`, or `rejected`.

```js
// fetch returns a Promise. When the network request is complete,
// the promise will either resolve (successful response) or reject (network error, etc.).
// The .then() method is called when the promise is successfully fulfilled.
fetch("/api/get-data").then((response) => {
  console.log(response);
  // Example: Response { type: 'basic', status: 200, ...}
});
```

By leveraging promises, we can create more readable code

```js
doSomething()
  .then((result1) => doSomethingElse(result1))
  .then((result2) => doAnotherThing(result2))
  .then((result3) => {
    console.log("Final result:", result3);
  })
  .catch((error) => {
    // .catch() handles errors anywhere in the chain
    console.error("An error occurred:", error);
  });
```

#### What if we wanted to make our own promises?

Often times we need functionality that extends beyond `setTimeout` or `fetch`.

To create a promise, we can use the Promise constructor -

`new Promise(/* executorFunction */);`

- the promise constructor will take a singular parameter, which is the executor function. This executor function is executed by the promise constructor and takes two arguments, the `resolve` and `reject` parameters.
  - resolve changes state from pending to fulfilled
  - reject changes state from pending to rejected

```js
function wait(duration) {
  return new Promise((resolve) => {
    setTimeout(resolve, duration);
  });
}
const timeoutPromise = wait(1000);
timeoutPromise.then(() => {
  console.log("1 second later!");
});
```

- Its important to note that the `resolve()` function will change the state of the promise from **pending** to **fullfilled**.
- Whenever you call the Promise constructor, it has a `new Promise((resolve) => { ... })` executor function that receives resolve and reject.

### Driving the point home for the resolve()

```js
// This is WRONG because the Promise constructor expects a function as an argument.
// Here, you are passing the *result* of setTimeout (which is a timer ID, undefined after the setTimeout executes).
// The promise itself will never transition from 'pending' because `resolve` or `reject` are never called within its context.
const promise1 = new Promise(
  setTimeout(() => {
    console.log("foo");
  }, 300)
);

// If you were to try:
// promise1.then(() => console.log("Promise resolved"));
// This .then() would never execute because promise1 is forever pending.
```

- the promise constructor requires a function as the argument.
- lack of resolve or reject would mean the promise would remain in pending state.
- It would just log foo and any .then() that wants to use the promise won't be able to.

```js
const promise2 = new Promise((resolve, reject) => {
  // Correct: Pass an executor function
  setTimeout(() => {
    resolve("foo"); // Call `resolve` when the async operation is done.
    // This changes the promise state to 'fulfilled' with value "foo".
  }, 300);
});

promise2.then((value) => {
  console.log(value); // Logs: "foo"
});
```

### An extension to make it even more clear

Let's say that we have a limited queue where we want to limit the amount of active tasks.

```js
class LimitedQueue {
  constructor(limit) {
    this.limit = limit;
    this.queue = []; // Stores actual items or tasks
    // Stores functions that, when called, will resolve a waiting Promise.
    // Each function corresponds to a Promise returned when enqueue was called on a full queue.
    this.waitingResolvers = [];
  }
```

To make this easier to understand think of:

- limit : as the maximum number of people allowed in the shop
- queue : the people waiting for an order
- waitingResolvers : the people waiting outside with a ticket (Promise) that needs to be marked done (Fulfilled) in order to be placed into the queue.

```js
  enqueue(item) {
    if (this.queue.length >= this.limit) {
      return new Promise((resolve, reject) => {
        this.waitingResolvers.push(() => {
          this.queue.push(item);
          resolve();
        });
      });
    } else {
      this.queue.push(item);

      // !!!! We call resolve here because the if case returns a promise and we must also return a promise even though .resolve() - static method in this example - resolves as undefined.
      return Promise.resolve();
    }
  }
```

Here we have an implementation of a queue that has a list of async promises.

When the queue is full, we create a promise, and push an anonymous function into `waitingResolvers` so that when dequeue is called, it can then be called.

### Enqueue and how it uses these resolvers

When there is space in the queue, we pop off the `waitingResolvers` queue, which is a function [remember what we pushed into waitingResolvers in the first place.](#an-extension-to-make-it-even-more-clear)

```js
if (this.waitingResolvers.length > 0) {
  const resolver = this.waitingResolvers.shift();
  resolver();
}
```

We then call `resolver()` which is:

```js
() => {
  this.queue.push(item);
  resolve();
};
```

This action is added into the queue and then we call resolve which marks it as "fulfilled"

### Sources

- [Useful Blog](https://www.joshwcomeau.com/javascript/promises/)
- [Resolving a promise makes it thenable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)
- Some combination of ChatGPT, Gemini, and Claude Explanations.
