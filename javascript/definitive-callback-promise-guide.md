# Definitive Callback, Promise and Asynchronous Coding Guide

JavaScript is a single threaded language. So we need to figure out ways to do things in the background, in order to avoid stopping out programs in their entirety.

### Callbacks

One of the first ways to do things asynchronously.

```js
// In this example, we will put this into the event loop.
// It will wait 1000ms before printing out that statement.
setTimeout(() => {
  console.log("After one second");
}, 1000);
```

However, we run into the case of callback hell, which nests callback functions within one another.

### Promises

This is where Promises are useful.

```js
// fetch will return a promise, once that work is complete, .then() will do something with the resolved value that we got.
fetch("/api/get-data").then((response) => {
  console.log(response);
  // Response { type: 'basic', status: 200, ...}
});
```

What if we wanted to make our own promises?

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

The first one is wrong because

- the promise constructor requires a function as the argument.
- lack of resolve or reject would mean the promise would remain in pending state.
- It would just log foo and any .then() that wants to use the promise won't be able to.

```js
const promise1 = new Promise(
  setTimeout(() => {
    console.log("foo")
  }, 300);

const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("foo");
  }, 300);
});
```

### An extension to make it even more clear

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

Meaning, when this item is pushed into the queue, what ever was `.then()` -ing our promise that we returned from `enqueue`, will now resolve.

### Sources

- [Useful Blog](https://www.joshwcomeau.com/javascript/promises/)
- [Resolving a promise makes it thenable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)
- Some combination of ChatGPT, Gemini, and Claude Explanations.
