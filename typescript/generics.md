# Generics

The issue with this function is that if we wanted this to work with a `number`, we could use `any` in place of the type. However, we lose out on the context of what the string was.

So in order to fix this, we can use generics.

```ts
function printSomething3(arg: string): string {
  console.log(arg);
  return arg;
}`
```

```ts
function printSomething<Type>(arg: Type): Type {
  console.log(arg);
  return arg;
}

//And then you can call it through either of these ways
let someValue = printSomething<string>("something");
// Type argument intereference.
let someValue3 = printSomething("some other thing");
```

You can even define the generics within the classes themselves or use them in functions.

```ts
// Class definition
class KeyValuePair<K, V> {
  private key: K;
  private value: V;

  constructor(key: K, value: V) {
    this.key = key;
    this.value = value;
  }

  // accessors

  displayPair(): void {
    console.log(`Key: ${this.key} - Value: ${this.value}`);
  }
}

let pair = new KeyValuePair<string, string>("url", "something.com");
pair.displayPair();

// Using within methods
export class Queue<T> {
  private storage: T[] = [];

  enqueue(item: T) {
    this.storage.push(item);
  }
```

You can use generic constraints to access fields like `length` or define `functions`.

```ts
function printSomething<T>(arg: T): T {
  console.log(arg.length); // error! since T might not have length
  return arg;
}

function logLength<T extends { length: number }>(item: T): void {
  console.log(item.length);
}
```

You can use generics to validate keys of specific types. In this example, we could have used a different type because:
getConfigValue will return something if the Key you passed in exists on the Type of the object you have.

```ts
import { AppConfig } from "./AppConfig";

function getConfigValue<Type, Key extends keyof Type>(config: Type, key: Key) {
  return config[key];
}

// Example usage:
const appConfig: AppConfig = {
  debug: true,
  logLevel: "info",
  port: 3000,
};

const debugStatus = getConfigValue(appConfig, "debug");
const appPort = getConfigValue(appConfig, "port");
```

### Sources

[Generics Official Documentation](https://www.typescriptlang.org/docs/handbook/2/generics.html)
[Code snippets taken from LinkedIn Learning Course](https://www.linkedin.com/learning/advanced-typescript-concepts/generics?autoSkip=true&resume=false)
