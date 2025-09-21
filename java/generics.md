# Generics

Generic - a class or interface whose declaration has one or more type parameters.

For example `List<E>` is an interface that has a single type parameter E. The raw type would just be List.

The advantage of using generics is that you can spot mismatched element types in collections during compile time.
Otherwise you would need to spot these changes during Runtime.

```java
// Only contains Stamp instances
private final Collection stamps = ...;
stamps.add(new Coin( ... )) // Emits an 'unchecked' call warning.

// Raw iterator
for (Iterator i = stamps.iterator(); i.hasNext();) {
  Stamp stamp = (Stamp) i.next(); // Throws a ClassCastException
      stamp.cancel();
}
```

In contrast, using a parameterized type

```java
private final Collection<Stamp> stamps = ...;

stamps.add(new Coin( ... )); // Should throw an error.
```

### Glossary

Generic Type - `List<E>`
Parameterized Type - `List<String>`
Unbounded wildcard type - `List<?>`
Raw type - `List`
