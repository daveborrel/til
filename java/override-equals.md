# Override Equals and Hashcode

In Java, by default, the == operator checks for the identity of an object.

```java
public static void main(String args[]) {
    DJ a = new DJ("blue");
    DJ b = new DJ("blue");
    if (a == b) {
        System.out.println("A is equal to B");
    }
}
```

In this example, `a` and `b` are not equal here because the equals operator tests on identiity.

### Object Class

The class object has an `equals` method which just calls the equals operator.

This means that we need to override the equals method to define what this means for our classes.

```java
@Override
public boolean equals(Object obj) {
    // The instance must be equal to itself
    if (this == obj) {
        return true;
    }

    // Check if the parameter instance is null, equals instance exist and null doesn't
    if (obj == null) {
        return false;
    }

    // Check each attribute of the class.
    if (obj instanceof DJ) {
        DJ test = (DJ) obj;
        if (test.myShirtColor == this.myShirtColor) {
            return true;
        }
    }
}
```

### hashCode

In short, we use a hash function to create a hashcode for an object to which we can use to store them in a bucket.

We need to override `hashCode` as well because, two instances that evaluate to true will be stored with different hashCodes.

Overriding `hashCode` ensures that:

1. Equal instances always produce the same hashcode
