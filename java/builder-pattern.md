# Builder Pattern

A builder pattern helps you create complex objects using the same construction code.

It solves the telescoping problem that happens when you overload a class with too many constructors.

It overcomes the JavaBeans issue of needing several setter lines to create the desired object.

```java
package Chapter2;

public class Car {
    private final String make;
    private final String model;

    // In order for build to return properly
    //    Car(String make, String model) {
    //        this.make = make;
    //        this.model = model;
    //    }

    Car(Builder builder) {
        this.make = builder.make;
        this.model = builder.model;
    }

    public String getMake() {
        System.out.println(make);
        return make;
    }
    public String getModel() {
        System.out.println(model);
        return model;
    }

    public static class Builder {
        private String make;
        private String model;

        public Builder make(String make) {
            this.make = make;
            return this;
        };

        public Builder model(String model) {
            this.model = model;
            return this;
        };

        public Car build() {
            return new Car(this);
        }
    }
}

public class Main {
    public static void main(String[] args) {

        Car car = new Car.Builder().make("Honda").model("Civic").build();
        car.getMake();
        car.getModel();
    }
}

```

- Since each method call, make() for example, returns this, we can directly chain these calls together.
