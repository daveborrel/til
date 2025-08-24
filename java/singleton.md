# Singleton

Singleton is a creational design pattern that ensures that a class only has one instance.

Why would we want this?

1. Controlling access to a shared resource.
2. Providing global access point to an instance.

```java
public class Elvis {
    public static final INSTANCE = new Elvis();

    private Elvis() {};

    public static Elvis getInstance() {
        return INSTANCE;
    }
}
```

All the calls to getInstance will return the same object reference.
