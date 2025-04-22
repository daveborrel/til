# Code Splitting

JavaScript bundle - combines multiple JavaScript files and their dependencies into a single file. Allows browsers to just look at one file in production.

Code splitting allows code to be split into various bundles that can then be loaded on demand or in parallel.

**Options**

(1) Lazy Loading

- `lazy` - allows components to be rendered later
- `<Suspense>` - while the component is loading, it will display the fallback while it is loading.

```ts
import React, { Suspense, lazy } from "react";

const MyComponent = lazy(() => import("./MyComponent"));

function App() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <MyComponent />
      </Suspense>
    </div>
  );
}

export default App;
```

(2) Dynamic Import with Webpack

- Allows some imports to be loaded later on

### Sources

[webpack: code splitting](https://webpack.js.org/guides/code-splitting/)
[lazy](https://react.dev/reference/react/lazy)
