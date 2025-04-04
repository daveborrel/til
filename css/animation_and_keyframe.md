# CSS keyframes and animations

**animation** - this is a css property that applies an animation for different styles.

```css
.element {
  animation: pulse 5s infinite;
}
```

**@keyframe** - Each animation needs to be defined by a @keyframe. A category of at-rules that helps you control what happens with each animation at a specific point in time.

```css
@keyframes pulse {
  0% {
    background-color: #001f3f;
  }
  100% {
    background-color: #ff4136;
  }
}
```

- For example, 0% refers to the start of the animation and 100% refers to the end of the animation.

### Sources

[animation](https://developer.mozilla.org/en-US/docs/Web/CSS/animation)
[keyframe](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)
