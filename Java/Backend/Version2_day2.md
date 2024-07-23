```java
package com.example.demo;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class JavaController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello, World!";
    }
}

````

### 1. Adding Request Parameters

**Code Changes:**
```java
package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class JavaController {

    @GetMapping("/hello")
    public String hello(@RequestParam(value = "name", defaultValue = "World") String name) {
        return "Hello, " + name + "!";
    }
}
```

**Postman Testing:**
1. **Open Postman.**
2. **Create a new GET request.**
3. **Enter the URL**: `http://localhost:8080/hello?name=John`.
4. **Click on `Send`.**
5. **Check the response**: You should see `"Hello, John!"`.

### 2. Using Path Variables

**Code Changes:**
```java
package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class JavaController {

    @GetMapping("/hello/{name}")
    public String hello(@PathVariable String name) {
        return "Hello, " + name + "!";
    }
}
```

**Postman Testing:**
1. **Open Postman.**
2. **Create a new GET request.**
3. **Enter the URL**: `http://localhost:8080/hello/John`.
4. **Click on `Send`.**
5. **Check the response**: You should see `"Hello, John!"`.

### 3. Handling POST Requests

**Code Changes:**
```java
package com.example.demo;

import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class JavaController {

    @PostMapping("/greet")
    public String greet(@RequestBody Greeting greeting) {
        return "Hello, " + greeting.getName() + "!";
    }
}

class Greeting {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

**Postman Testing:**
1. **Open Postman.**
2. **Create a new POST request.**
3. **Enter the URL**: `http://localhost:8080/greet`.
4. **Go to the `Body` tab and select `raw` and `JSON` format.**
5. **Enter the JSON data**:
   ```json
   {
       "name": "John"
   }
   ```
6. **Click on `Send`.**
7. **Check the response**: You should see `"Hello, John!"`.

### 4. Working with JSON Responses

**Code Changes:**
```java
package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class JavaController {

    @GetMapping("/hello")
    public Greeting hello(@RequestParam(value = "name", defaultValue = "World") String name) {
        return new Greeting(name);
    }
}

class Greeting {
    private String name;

    public Greeting(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

**Postman Testing:**
1. **Open Postman.**
2. **Create a new GET request.**
3. **Enter the URL**: `http://localhost:8080/hello?name=John`.
4. **Click on `Send`.**
5. **Check the response**: You should see a JSON object:
   ```json
   {
       "name": "John"
   }
   ```

