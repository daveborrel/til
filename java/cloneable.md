# Clonable Interface

The `Cloneable` interface defines the clone method for comparing objects. This interface needs to be implemented if you want to use the `clone()` method.

```java
Cat garfield = new Cat();
Cat healthcliff = garfield;
```

This is problematic because if we make any changes to healthcliff, it will also change garfield.

```java
Cat garfield = new Cat();
Cat heathcliff = garfield.clone();
```

This solution will duplicate all the variables from garfield and makes a new instance of Cat in heathcliff.

```java
public class Student implements Cloneable {
    public Student(String name) {}

    @Override
    public Object clone() throws CloneNotSupportedException {
        return super.clone()
    }
}
```

Anytime we try to use clone() we have to wrap it in a try catch block to see if we are able to clone that object in the first place.
