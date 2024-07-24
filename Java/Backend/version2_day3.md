
### Introducing Services in Spring Boot

#### **1. What is a Service?**
A service in Spring Boot is a class that contains business logic. It is a way to organize code that handles the core functionality of your application. Services help separate the business logic from the controller, which handles HTTP requests and responses.

#### **2. Why Use a Service?**
Using services helps keep your code clean and maintainable. It makes it easier to manage changes and additions to your business logic without affecting your controllers. This separation of concerns makes your application more modular and testable.

#### **3. Implementing Services in Your Application**

##### **Step-by-Step Code Explanation**

**Directory Structure:**
```
src/
├── main/
│   ├── java/
│   │   └── com/
│   │       └── example/
│   │           └── demo/
│   │               ├── controller/
│   │               │   └── JavaController.java
│   │               ├── service/
│   │               │   └── GreetingService.java
│   │               └── model/
│   │                   └── Greeting.java
│   └── resources/
│       └── application.properties
```

### **Creating a Service**

Let's create a simple service that generates greeting messages.

**GreetingService.java**
```java
package com.example.demo.service;

import com.example.demo.model.Greeting;
import org.springframework.stereotype.Service;

@Service
public class GreetingService {

    // This method returns a greeting message as a string
    public String greet(String name) {
        return "Hello, " + name + "!";
    }

    // This method returns a Greeting object
    public Greeting getGreeting(String name) {
        return new Greeting(name);
    }
}
```

1. **`@Service`:** This annotation tells Spring that this class is a service. Spring will manage it as a bean (an object whose lifecycle is managed by the Spring container).
2. **`greet(String name)`:** This method takes a name as a parameter and returns a greeting message as a string.
3. **`getGreeting(String name)`:** This method takes a name as a parameter and returns a `Greeting` object.

### **Updating the Controller to Use the Service**

The controller will use the service to handle HTTP requests.

**JavaController.java**
```java
package com.example.demo.controller;

import com.example.demo.model.Greeting;
import com.example.demo.service.GreetingService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
public class JavaController {

    @Autowired
    private GreetingService greetingService;

    @GetMapping("/hello")
    public String hello(@RequestParam(value = "name", defaultValue = "World") String name) {
        return greetingService.greet(name);
    }

    @GetMapping("/hello/{name}")
    public String hello(@PathVariable String name) {
        return greetingService.greet(name);
    }

    @PostMapping("/greet")
    public String greet(@RequestBody Greeting greeting) {
        return greetingService.greet(greeting.getName());
    }

    @GetMapping("/json-hello")
    public Greeting jsonHello(@RequestParam(value = "name", defaultValue = "World") String name) {
        return greetingService.getGreeting(name);
    }
}
```

1. **`@RestController`:** This annotation marks the class as a controller where every method returns a domain object instead of a view.
2. **`@Autowired`:** This annotation tells Spring to inject the `GreetingService` bean into this controller.
3. **Methods:**
   - `hello(@RequestParam ...)`: Handles GET requests with a query parameter.
   - `hello(@PathVariable ...)`: Handles GET requests with a path variable.
   - `greet(@RequestBody ...)`: Handles POST requests with a request body.
   - `jsonHello(@RequestParam ...)`: Handles GET requests with a query parameter and returns a `Greeting` object.

### **Model Class for Greeting**

The model class represents the data structure of the response.

**Greeting.java**
```java
package com.example.demo.model;

import java.time.LocalDateTime;

public class Greeting {
    private String name;
    private String message;
    private LocalDateTime timestamp;

    public Greeting(String name) {
        this.name = name;
        this.message = "Hello, " + name + "!";
        this.timestamp = LocalDateTime.now();
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getMessage() {
        return message;
    }

    public LocalDateTime getTimestamp() {
        return timestamp;
    }
}
```

1. **Attributes:**
   - `name`: The name of the person to greet.
   - `message`: The greeting message.
   - `timestamp`: The time the greeting was created.
2. **Constructor:** Initializes the name, message, and timestamp.
3. **Getters and Setters:** Provide access to the attributes.

### **Postman Testing**

#### 1. **GET Request with Query Parameter**

- **URL:** `http://localhost:8080/hello?name=John`
- **Response:** `"Hello, John!"`

#### 2. **GET Request with Path Variable**

- **URL:** `http://localhost:8080/hello/John`
- **Response:** `"Hello, John!"`

#### 3. **POST Request with JSON Body**

- **URL:** `http://localhost:8080/greet`
- **Body:**
  ```json
  {
      "name": "John"
  }
  ```
- **Response:** `"Hello, John!"`

#### 4. **GET Request with JSON Response**

- **URL:** `http://localhost:8080/json-hello?name=John`
- **Response:**
  ```json
  {
      "name": "John",
      "message": "Hello, John!",
      "timestamp": "2024-07-24T12:34:56.789"
  }
  ```

### Summary

By introducing services, you separate the business logic from the controllers. The `GreetingService` class handles the core functionality of generating greetings. The controller (`JavaController`) handles HTTP requests and delegates the business logic to the service. This separation makes the code more organized, easier to maintain, and more testable. The `Greeting` class encapsulates the greeting data, providing a structured response for the API clients.
