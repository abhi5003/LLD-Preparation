## Solid Principles

![](https://33333.cdn.cke-cs.com/kSW7V9NHUXugvhoQeFaf/images/b31923f9492a9cc99d1c2648e592ae11831d0f3ec312608c.png)

**Advantage of following these principles :-**

*   Help's to write better code
*   Avoid duplicate code
*   Easy maintain
*   Easy understand
*   Flexible Software
*   Reduce complexity

### 👉 Single Responsibility Principle (SRP)

> **The Single Responsibility Principle (SRP) states that a class should have only one reason to change, meaning it should have only one responsibility.**

**❌ Before**

```plaintext
// Original User class with multiple responsibilities
public class User {
    private String username;
    private String password;

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    public void save() {
        // Logic to save user to database
    }

    public boolean authenticate(String username, String password) {
        // Logic to authenticate user
    }
}
```

**✔️  Refactored version:**

```java
// User class with a single responsibility: managing user information
public class User {
    private String username;
    private String password;

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    public void save() {
        // Logic to save user to database
    }
}
```

```java
// AuthenticationService class with a single responsibility: handling user authentication
public class AuthenticationService {
    public boolean authenticate(User user, String username, String password) {
        // Logic to authenticate user
    }
}
```

**Note :-** In this refactored version, the **User** class is responsible only for managing user information (e.g., storing username and password, saving user to the database), while the **AuthenticationService** class is responsible solely for handling user authentication. This separation of concerns adheres to the Single Responsibility Principle, making the code easier to understand, maintain, and extend.



### 👉 Open/Closed Principle (OCP)

> The Open/Closed Principle (OCP) states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, you should be able to extend the behavior of a module without modifying its source code.

```java
// Shape interface representing a geometric shape
public interface Shape {
    double area();
}

// Rectangle class implementing the Shape interface
public class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    public double area() {
        return width * height;
    }
}

// Circle class implementing the Shape interface
public class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double area() {
        return Math.PI * radius * radius;
    }
}

// AreaCalculator class responsible for calculating the total area of shapes
public class AreaCalculator {
    public double calculateTotalArea(Shape[] shapes) {
        double totalArea = 0;
        for (Shape shape : shapes) {
            totalArea += shape.area();
        }
        return totalArea;
    }
}
```

Now, let's say we want to extend our application to support calculating the area of a triangle without modifying the existing code. We can achieve this by creating a new class that implements the **Shape** interface for triangles:

```java
// Triangle class implementing the Shape interface
public class Triangle implements Shape {
    private double base;
    private double height;

    public Triangle(double base, double height) {
        this.base = base;
        this.height = height;
    }

    public double area() {
        return 0.5 * base * height;
    }
}
```

**Note** :- With the addition of the **Triangle** class, we've extended the behavior of our application without modifying the existing classes (**Rectangle**, **Circle**, **AreaCalculator**). This adherence to the Open/Closed Principle allows for easy extension and maintenance of the codebase.
