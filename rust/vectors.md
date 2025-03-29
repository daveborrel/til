# Rust - Vectors

These are re-sizable arrays.

### Different ways to create a rust vector

```rust
// You can explicitly create a new vec with Vec::new
let v: Vec<i32> = Vec::new();

// Using the vec! macro
let v: Vec<i32> = vec![];
```

### Pushing and popping off a Vector

make sure that you add `mut` so that you can actually call `push` and `pop`

```rust
let mut v: Vec<i32> = vec![];

v.push(3);

v.pop();
```

### Source

[std::vec docs](https://doc.rust-lang.org/std/vec/struct.Vec.html)

