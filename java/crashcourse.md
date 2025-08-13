# Java

Some basic Java fundamentals to remember how to use it.

When compiling a Java program, the Java compiler javac converts code into bytecode, which is a set of instructions that the JVM can understand and execute.

### Important Java Components

1. Java Language and API

- Syntax and semantics of the Java programming language.

2. Java Virtual Machine (JVM)

- That bytecode can be run by the JVM on the underlying hardware. For example, the JVM will interpret the Java for windows or for linux.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

The most basic program.

### Keywords

`private` - can restrict access to a member or method of a specific class.
`package-private behaviour` - we can access members of classes in the same package, but when trying to do so with an external package, you won't be able to.
`protected` - can be accessed by any class belonging to the same package and any subclass of this class.
`final` - this class cannot be extended. with a method - it can't be overridden in a subclass. for attributes can't be changed / assigned to a new value.
`abstract` - when applied to class, it can't be instantiated on its own. it needs to be implemented by a class that implements it.

### Sources

- [50 Questions from Github](https://github.com/Devinterview-io/java-interview-questions)
