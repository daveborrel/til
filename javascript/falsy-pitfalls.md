# Falsy Pitfalls

In javaScript, falsy is a value that is considered false when encountered in a boolean context. Not understanding this can lead to unexpected results in your code.

Here are the all the falsy values:

- `null`
- `undefined`
- `false`
- `NaN`
- `0`
- `-0`
- `0n`
- `""` as well as `''`
- `document.all`

## Pitfalls

- Inside of an if block, it will be treated as false.
- Inside of a logical AND / && , it will return that object instead of returning false.

```js
console.log(0 && "dog");
// this will return 0, instead of false
```

This is why it is crucial to use === and !== because these do not use type coercion.
