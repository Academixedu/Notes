Here's a comprehensive step-by-step tutorial for building the Spring Boot Movie API application, including downloading the initializer, setting up the project structure, database initialization, and testing with Postman.

### 1. Download and Set Up the Spring Boot Project

1. **Go to [Spring Initializr](https://start.spring.io/):**

2. **Configure the Project:**
   - **Project:** Maven Project
   - **Language:** Java
   - **Spring Boot:** 3.1.x (latest stable version)
   - **Group:** `com.example`
   - **Artifact:** `demo`
   - **Name:** `MovieApiApplication`
   - **Description:** Movie API using Spring Boot
   - **Package Name:** `com.example.demo`
   - **Packaging:** Jar
   - **Java Version:** 17 or 20

3. **Add Dependencies:**
   - **Spring Web**
   - **Spring Data JPA**
   - **H2 Database**

4. **Generate the Project:**
   - Click on the "Generate" button to download the zip file.
   - Unzip the downloaded file to a directory of your choice, such as `C:\Users\gonch\demo`.

### 2. Import the Project into Your IDE

1. **Open Your IDE (e.g., IntelliJ IDEA, Eclipse, or VS Code).**
2. **Import the Project:**
   - Choose "Import Project" and select the unzipped directory.
   - Let the IDE resolve dependencies and build the project.

### 3. Project Structure and Files

Ensure your project structure looks like this:

```
demo/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── example/
│   │   │           └── demo/
│   │   │               ├── MovieApiApplication.java
│   │   │               ├── controller/
│   │   │               │   └── MovieController.java
│   │   │               ├── model/
│   │   │               │   └── Movie.java
│   │   │               ├── repository/
│   │   │               │   └── MovieRepository.java
│   │   │               └── service/
│   │   │                   └── MovieService.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/
│           └── com/
│               └── example/
│                   └── demo/
│                       └── DemoApplicationTests.java
└── pom.xml
```

### 4. Configure the `pom.xml`

Your `pom.xml` should already have the necessary dependencies. Ensure it looks like this:

**File:** `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>demo</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>demo</name>
    <description>Movie API using Spring Boot</description>
    <packaging>jar</packaging>

    <properties>
        <java.version>17</java.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```

### 5. Create the Main Application File

**File:** `C:\Users\gonch\demo\src\main\java\com\example\demo\MovieApiApplication.java`

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MovieApiApplication {
    public static void main(String[] args) {
        SpringApplication.run(MovieApiApplication.class, args);
    }
}
```

### 6. Create the Entity Class

**File:** `C:\Users\gonch\demo\src\main\java\com\example\demo\model\Movie.java`

```java
package com.example.demo.model;

import javax.persistence.*;
import java.util.List;

@Entity
public class Movie {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String backdropPath;
    private String originalLanguage;
    private String originalTitle;
    private String overview;

    @ElementCollection
    private List<Integer> genreIds;

    // Getters and Setters

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getBackdropPath() {
        return backdropPath;
    }

    public void setBackdropPath(String backdropPath) {
        this.backdropPath = backdropPath;
    }

    public String getOriginalLanguage() {
        return originalLanguage;
    }

    public void setOriginalLanguage(String originalLanguage) {
        this.originalLanguage = originalLanguage;
    }

    public String getOriginalTitle() {
        return originalTitle;
    }

    public void setOriginalTitle(String originalTitle) {
        this.originalTitle = originalTitle;
    }

    public String getOverview() {
        return overview;
    }

    public void setOverview(String overview) {
        this.overview = overview;
    }

    public List<Integer> getGenreIds() {
        return genreIds;
    }

    public void setGenreIds(List<Integer> genreIds) {
        this.genreIds = genreIds;
    }
}
```

### 7. Create the Repository Interface

**File:** `C:\Users\gonch\demo\src\main\java\com\example\demo\repository\MovieRepository.java`

```java
package com.example.demo.repository;

import com.example.demo.model.Movie;
import org.springframework.data.jpa.repository.JpaRepository;

public interface MovieRepository extends JpaRepository<Movie, Long> {
    // JpaRepository provides CRUD operations and more
}
```

### 8. Create the Service Layer

**File:** `C:\Users\gonch\demo\src\main\java\com\example\demo\service\MovieService.java`

```java
package com.example.demo.service;

import com.example.demo.model.Movie;
import com.example.demo.repository.MovieRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.HashMap;
import java.util.List;
import java.util.Map;

@Service
public class MovieService {
    @Autowired
    private MovieRepository movieRepository;

    public List<Movie> getAllMovies() {
        return movieRepository.findAll();
    }

    public Map<String, Object> getPopularMoviesResponse() {
        List<Movie> movies = getAllMovies();
        Map<String, Object> response = new HashMap<>();
        response.put("results", movies);
        return response;
    }
}
```

### 9. Create the Controller

**File:** `C:\Users\gonch\demo\src\main\java\com\example\demo\controller\MovieController.java`

```java
package com.example.demo.controller;

import com.example.demo.service.MovieService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.Map;

@RestController
@RequestMapping("/api/movies")
public class MovieController {

    @Autowired
    private MovieService movieService;

    @GetMapping("/popular")
    public ResponseEntity<Map<String, Object>> getPopularMovies() {
        Map<String, Object> response = movieService.getPopularMoviesResponse();
        return ResponseEntity.ok(response);
    }
}
```

### 10. Configure the Application Properties

**File:** `C:\Users\gonch\demo\src\main\resources\application.properties`

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
```

### 11. Initialize the Database

By default, Spring Boot will initialize an H2 in-memory database using the `application.properties` configuration. You don't need to perform any extra steps for database initialization.

### 12. Create a Basic

 Test Case

**File:** `C:\Users\gonch\demo\src\test\java\com\example\demo\DemoApplicationTests.java`

```java
package com.example.demo;

import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;

@SpringBootTest
class DemoApplicationTests {

	@Test
	void contextLoads() {
	}

}
```

### 13. Run the Application

1. **Navigate to the Project Directory:**
   ```bash
   cd C:\Users\gonch\demo
   ```

2. **Run the Spring Boot Application:**
   ```bash
   mvn spring-boot:run
   ```

### 14. Test the API using Postman

1. **Open Postman.**
2. **Create a New GET Request:**
   - **URL:** `http://localhost:8080/api/movies/popular`
3. **Send the Request.**
4. **Check the Response:**
   - You should receive a JSON response with a "results" key containing an empty array (since no movies are in the database initially).

### 15. Access the H2 Database Console (Optional)

1. **Go to:** `http://localhost:8080/h2-console`
2. **JDBC URL:** `jdbc:h2:mem:testdb`
3. **Username:** `sa`
4. **Password:** `password`
5. **Click "Connect"** to access the database.

### Summary

This step-by-step tutorial walks you through the entire process of setting up a Spring Boot Movie API application, from project initialization to testing with Postman. You now have a functional REST API that can be further extended with additional features like authentication, data validation, and custom error handling.
