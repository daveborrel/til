# Override toString

By default, the Object `toString()` method will print out the Class Name, an @ 'at' sign and then the ending hashCode.

#### Example from [how.dev](https://how.dev/answers/how-to-override-the-tostring-method-in-java)

```java
class Student {
   private int id;
   private String name;

   public Student(int id, String name) {
      this.id = id;
      this.name = name;
   }
}
// Driver class to test the Student class
public class Demo {
   public static void main(String[] args) {
      Student s = new Student(101, "James Bond");
      System.out.println("The student details are: "+s);
   }
}
```

##### Output

The student details are: Student@28d93b30

Often times, we override the `toString()` method in order to get a meaningful representation of the object.

#### Example but overriding the toString()

```java
class Student {
   private int id;
   private String name;

   public Student(int id, String name) {
      this.id = id;
      this.name = name;
   }

  @Override
   public String toString() {
      return id + " " + name;
   }
}
// Driver class to test the Student class
public class Demo {
   public static void main(String[] args) {
      Student s = new Student(101, "James Bond");
      System.out.println("The student details are: "+s);
   }
}
```

##### output

The student details are: 101 James Bond
