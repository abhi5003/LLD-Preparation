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
