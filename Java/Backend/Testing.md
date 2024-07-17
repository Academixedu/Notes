# Quick Tutorial: Testing Spring Boot Applications

## 1. Types of Tests

Spring Boot supports several types of tests:

- Unit Tests
- Integration Tests
- Slice Tests (e.g., @WebMvcTest, @DataJpaTest)
- Full Application Tests

## 2. Dependencies

Add these to your `pom.xml` or `build.gradle`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

## 3. Writing a Simple Unit Test

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class SimpleServiceTest {

    @Test
    void testAddition() {
        SimpleService service = new SimpleService();
        assertEquals(4, service.add(2, 2));
    }
}
```

## 4. Writing an Integration Test

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.web.client.TestRestTemplate;
import org.springframework.boot.test.web.server.LocalServerPort;

import static org.assertj.core.api.Assertions.assertThat;

@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
public class HttpRequestTest {

    @LocalServerPort
    private int port;

    @Autowired
    private TestRestTemplate restTemplate;

    @Test
    public void greetingShouldReturnDefaultMessage() throws Exception {
        assertThat(this.restTemplate.getForObject("http://localhost:" + port + "/",
                String.class)).contains("Hello, World");
    }
}
```

## 5. Using @WebMvcTest for Controller Tests

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
import org.springframework.test.web.servlet.MockMvc;

import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.content;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;

@WebMvcTest(HomeController.class)
public class WebLayerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    public void shouldReturnDefaultMessage() throws Exception {
        this.mockMvc.perform(get("/")).andExpect(status().isOk())
                .andExpect(content().string(containsString("Hello, World")));
    }
}
```

## 6. Using @DataJpaTest for Repository Tests

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import org.springframework.boot.test.autoconfigure.orm.jpa.TestEntityManager;

import static org.assertj.core.api.Assertions.assertThat;

@DataJpaTest
public class UserRepositoryTest {

    @Autowired
    private TestEntityManager entityManager;

    @Autowired
    private UserRepository userRepository;

    @Test
    public void whenFindByName_thenReturnUser() {
        User user = new User("test@example.com");
        entityManager.persist(user);
        entityManager.flush();

        User found = userRepository.findByEmail(user.getEmail());

        assertThat(found.getEmail()).isEqualTo(user.getEmail());
    }
}
```

## 7. Best Practices

- Use meaningful test names
- Follow the Arrange-Act-Assert pattern
- Mock external dependencies
- Use profiles for different test configurations
- Leverage Spring Boot's `@TestConfiguration` for test-specific beans
