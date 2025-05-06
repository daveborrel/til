# Passing Props with Spread Operator

Passing in props with a spread operator is useful because you can pass down all of the props from the parent component.

```ts
// Instead of doing this, especially when the Avatar component is the one using this,
function Profile({ person, size, isSepia, thickBorder }) {
  return (
    <div className="card">
      <Avatar
        person={person}
        size={size}
        isSepia={isSepia}
        thickBorder={thickBorder}
      />
    </div>
  );
}

// You can just pass it down here to make it succint
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />
    </div>
  );
}
```

There is also a great use case here where we can override a prop and still pass down everything that we need.

```ts
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} url="https://example.com/custom-avatar.mp4" />
    </div>
  );
}
```
