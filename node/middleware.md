# Middleware in Node

Middleware functions have access to and can change the `req` and `res` objects, along with the `next` function. `next()` is a function in express that invokes the next function along the middleware chain.

**Example using "hello world"**

```javascript
app.get("/", (req, res) => {
  res.send("Hello World!");
});
```

**Middleware function**

```javascript
const myLogger = function (req, res, next) {
  console.log("LOGGED");
  next(); // This the next function we want to call
};
```

If we wanted to use `myLogger`, then we have to explicitly add it with `use()`

```javascript
const express = require("express");
const app = express();

app.use(myLogger);

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(3000);
```

**Middleware general structure**

```js
module.exports = function (options) {
  return function (req, res, next) {
    // Implement the middleware function based on the options object
    next();
  };
};
```

### Sources

[middleware](https://expressjs.com/en/guide/writing-middleware.html)
