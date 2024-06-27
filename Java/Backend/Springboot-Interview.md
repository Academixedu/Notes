### Spring Boot Interview Questions

**Q: What is Spring Boot and how does it differ from the traditional Spring Framework?**

**A**: Spring Boot is an extension of the Spring Framework that simplifies the setup and development of new Spring applications. It provides a range of features, such as auto-configuration, stand-alone applications, and embedded servers, that reduce the amount of boilerplate code and configuration required. Unlike the traditional Spring Framework, Spring Boot offers opinionated defaults and a streamlined development process.

**Q: Explain the concept of auto-configuration in Spring Boot.**

**A**: Auto-configuration in Spring Boot automatically configures beans and settings based on the classpath contents, other beans, and various property settings. This feature allows developers to get started quickly by minimizing the amount of explicit configuration needed. Auto-configuration can be customized or disabled using properties or annotations.

**Q: What are Spring Boot starters and how do they help in application development?**

**A**: Spring Boot starters are a set of convenient dependency descriptors that you can include in your project. These starters provide a ready-to-use set of dependencies for a specific functionality, such as web development (`spring-boot-starter-web`), JPA (`spring-boot-starter-data-jpa`), and security (`spring-boot-starter-security`). They simplify the process of adding dependencies to a project by bundling commonly used libraries.

**Q: How do you create a Spring Boot application?**

**A**: To create a Spring Boot application, you can use Spring Initializr (https://start.spring.io/) to generate a project with the desired dependencies. Alternatively, you can manually create a Maven or Gradle project and add the necessary Spring Boot dependencies. Then, you create a main class annotated with `@SpringBootApplication` to bootstrap the application.

Example:
```java
@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

**Q: Explain the purpose of the `@SpringBootApplication` annotation.**

**A**: The `@SpringBootApplication` annotation is a convenience annotation that combines three annotations:
- `@Configuration`: Indicates that the class can be used as a source of bean definitions.
- `@EnableAutoConfiguration`: Enables Spring Boot’s auto-configuration mechanism.
- `@ComponentScan`: Enables component scanning, allowing Spring to find and register beans.

**Q: How do you configure properties in a Spring Boot application?**

**A**: Properties in a Spring Boot application can be configured using application properties or YAML files (e.g., `application.properties` or `application.yml`). These files can be placed in the `src/main/resources` directory. You can also use environment variables or command-line arguments to set properties.

Example (application.properties):
```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=secret
```

**Q: What are profiles in Spring Boot and how do you use them?**

**A**: Profiles in Spring Boot allow you to segregate parts of your application configuration and make them available only in certain environments. You can define profile-specific properties in separate property files (e.g., `application-dev.properties`, `application-prod.properties`) and activate a profile using the `spring.profiles.active` property.

Example:
```properties
# application.properties
spring.profiles.active=dev

# application-dev.properties
spring.datasource.url=jdbc:mysql://localhost:3306/devdb

# application-prod.properties
spring.datasource.url=jdbc:mysql://localhost:3306/proddb
```

**Q: Explain the difference between `@RestController` and `@Controller` annotations.**

**A**: Both `@RestController` and `@Controller` are used to define web controllers in Spring MVC. The key difference is that `@RestController` is a convenience annotation that combines `@Controller` and `@ResponseBody`. It is used for RESTful web services where the response is typically in JSON or XML format.

- `@RestController`: Every method in the controller returns a response body.
- `@Controller`: Used for traditional MVC controllers where views are returned.

Example:
```java
@RestController
@RequestMapping("/api")
public class MyRestController {
    @GetMapping("/greet")
    public String greet() {
        return "Hello, World!";
    }
}
```

**Q: How do you handle exceptions in Spring Boot?**

**A**: Exceptions in Spring Boot can be handled using `@ControllerAdvice` and `@ExceptionHandler` annotations. `@ControllerAdvice` is a specialization of `@Component` that allows you to handle exceptions across the whole application in one global handling component.

Example:
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleResourceNotFoundException(ResourceNotFoundException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(ex.getMessage());
    }
    
    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleGeneralException(Exception ex) {
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body("An error occurred: " + ex.getMessage());
    }
}
```

**Q: What is Spring Data JPA and how is it used in a Spring Boot application?**

**A**: Spring Data JPA is a part of the larger Spring Data family and provides a way to easily interact with databases using the Java Persistence API (JPA). It simplifies database access by providing a repository abstraction. In a Spring Boot application, you can use Spring Data JPA by including the `spring-boot-starter-data-jpa` dependency and defining repository interfaces.

Example:
```java
public interface UserRepository extends JpaRepository<User, Integer> {
    List<User> findByUsername(String username);
}
```

**Q: What is the purpose of the `@Entity` annotation in Spring Data JPA?**

**A**: The `@Entity` annotation specifies that the class is an entity and is mapped to a database table. It is used in JPA to mark a Java class as a persistent entity, which means its instances can be stored in the database.

Example:
```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int userId;
    
    private String username;
    private String email;
    
    // getters and setters
}
```

**Q: How do you perform dependency injection in Spring Boot?**

**A**: Dependency injection in Spring Boot can be performed using annotations such as `@Autowired`, `@Inject`, or by defining beans in configuration classes using `@Bean`.

Example using `@Autowired`:
```java
@Service
public class MyService {
    
    private final MyRepository myRepository;
    
    @Autowired
    public MyService(MyRepository myRepository) {
        this.myRepository = myRepository;
    }
    
    public List<MyEntity> findAll() {
        return myRepository.findAll();
    }
}
```

Example using `@Bean`:
```java
@Configuration
public class MyConfiguration {
    
    @Bean
    public MyService myService(MyRepository myRepository) {
        return new MyService(myRepository);
    }
}
```

**Q: Explain the role of `application.properties` and `application.yml` in Spring Boot.**

**A**: `application.properties` and `application.yml` are configuration files used to define properties for a Spring Boot application. These files allow you to externalize configuration so that you can easily change the configuration without modifying the code.

**Q: How does Spring Boot handle security?**

**A**: Spring Boot handles security through the Spring Security framework, which provides comprehensive security services for Java applications. By including the `spring-boot-starter-security` dependency, you can leverage features like authentication, authorization, password management, and protection against common security vulnerabilities.

Example of basic security configuration:
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
            .antMatchers("/public/**").permitAll()
            .anyRequest().authenticated()
            .and()
            .formLogin()
            .and()
            .httpBasic();
    }
    
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication()
            .withUser("user").password("{noop}password").roles("USER")
            .and()
            .withUser("admin").password("{noop}admin").roles("ADMIN");
    }
}
```

These questions and answers should give a solid overview of Spring Boot concepts and practices, helping you prepare for a Spring Boot interview.
