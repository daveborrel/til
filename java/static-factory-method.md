# Static Factory Method

### Benefits

- Have names
- No need to create a new object each time they are invoked
- The return type can be of any subtype
- The returned object can vary from call to call

### Limitations

- Classes without public constructors can't be subclassed
- Hard to find

```Java
package Chapter2;

public class Factory {

    private String name;
    private Integer budget;

    // The more generic way to allow Clients to create an instance of a class
    public Factory(String name, Integer budget) {
        this.name = name;
        this.budget = budget;
    }

    // Returns an instance of a class
    public static Factory makeFactory(String name, Integer budget) {
        return new Factory(name, budget);
    }
}

```

### Common Naming Conventions

- `of()` - type conversion
- `valueOf()` - verbose alternative to of()
- `getInstance()` - returns an instance (possibly cached)
- `newInstance()` - guarantees a new instance
- `create()` - general factory method
- `from()` - type conversion from another type

### Common Examples

`Integer.valueOf()`, `Collections.emptyList()` and `LocalDate.of()`
