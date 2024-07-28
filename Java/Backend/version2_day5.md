

### Step 1: Database Integration

1. **Setting up dependencies**

   We add necessary dependencies to `pom.xml`:
   - `spring-boot-starter-web`: For creating web applications.
   - `spring-boot-starter-data-jpa`: For database operations.
   - `h2`: In-memory database for development/testing.

   ```
   +---------------------------------------------------+
   | Dependencies                                      |
   |---------------------------------------------------|
   | spring-boot-starter-web                           |
   | spring-boot-starter-data-jpa                      |
   | h2                                                |
   +---------------------------------------------------+
   ```

2. **Creating the Greeting entity**

   Define a `Greeting` class representing a table in the database.

   ```
   +---------------------+
   | Greeting            |
   |---------------------|
   | id (Primary Key)    |
   | name                |
   | message             |
   +---------------------+
   ```

3. **Creating the repository**

   Define `GreetingRepository` interface for database operations.

   ```
   +---------------------+
   | GreetingRepository  |
   |---------------------|
   | save()              |
   | findAll()           |
   +---------------------+
   ```

4. **Creating the service**

   Define `GreetingService` for business logic.

   ```
   +----------------------+
   | GreetingService      |
   |----------------------|
   | saveGreeting(name)   |
   | getAllGreetings()    |
   +----------------------+
   ```

5. **Creating the controller**

   Define `GreetingController` for handling HTTP requests.

   ```
   +----------------------+
   | GreetingController   |
   |----------------------|
   | POST /greet?name=    |
   | GET /greetings       |
   +----------------------+
   ```

### Step 2: Exception Handling and Validation

1. **Adding validation**

   Add validation annotations to `Greeting` fields.

   ```
   +---------------------+
   | Greeting            |
   |---------------------|
   | id (Primary Key)    |
   | name (NotBlank)     |
   | message             |
   +---------------------+
   ```

2. **Creating custom exception**

   Define `GreetingException` for custom error handling.

   ```
   +---------------------+
   | GreetingException   |
   |---------------------|
   | message             |
   +---------------------+
   ```

3. **Creating global exception handler**

   Define `GlobalExceptionHandler` to handle exceptions globally.

   ```
   +-----------------------------+
   | GlobalExceptionHandler      |
   |-----------------------------|
   | handleGreetingException()   |
   +-----------------------------+
   ```

4. **Updating service to throw exceptions**

   Modify `GreetingService` to throw `GreetingException`.

   ```
   +----------------------------+
   | GreetingService            |
   |----------------------------|
   | saveGreeting(name)         |
   | - throws GreetingException |
   +----------------------------+
   ```

5. **Updating controller to handle validation**

   Modify `GreetingController` to handle validation.

   ```
   +----------------------------+
   | GreetingController         |
   |----------------------------|
   | POST /greet?name= (Valid)  |
   +----------------------------+
   ```

### Step 3: RESTful API Design

1. **Designing RESTful endpoints**

   Modify `GreetingController` to follow RESTful principles.

   ```
   +------------------------------------+
   | GreetingController                 |
   |------------------------------------|
   | POST /api/v1/greetings             |
   | GET /api/v1/greetings              |
   | GET /api/v1/greetings/{id}         |
   | PUT /api/v1/greetings/{id}         |
   | DELETE /api/v1/greetings/{id}      |
   +------------------------------------+
   ```

2. **Updating service to support CRUD operations**

   Modify `GreetingService` to support CRUD operations.

   ```
   +-------------------------------+
   | GreetingService               |
   |-------------------------------|
   | saveGreeting(name)            |
   | getAllGreetings()             |
   | getGreetingById(id)           |
   | updateGreeting(id, greeting)  |
   | deleteGreeting(id)            |
   +-------------------------------+
   ```

### Step 4: Security Implementation

1. **Adding security dependencies**

   Add `spring-boot-starter-security` to `pom.xml`.

   ```
   +--------------------------------+
   | Dependencies                   |
   |--------------------------------|
   | spring-boot-starter-security   |
   +--------------------------------+
   ```

2. **Configuring security**

   Define `SecurityConfig` for basic authentication.

   ```
   +-------------------------------+
   | SecurityConfig                |
   |-------------------------------|
   | securityFilterChain(http)     |
   | userDetailsService()          |
   +-------------------------------+
   ```

3. **Securing endpoints**

   Modify `GreetingController` to secure endpoints with `@PreAuthorize`.

   ```
   +---------------------------------------+
   | GreetingController                    |
   |---------------------------------------|
   | @PreAuthorize("hasRole('USER')")      |
   | POST /api/v1/greetings                |
   | PUT /api/v1/greetings/{id}            |
   | DELETE /api/v1/greetings/{id}         |
   +---------------------------------------+
   ```

### Summary Diagram



```
+-------------------+      +-----------------+     +--------------------+
| Client            | ---> | GreetingController  | ---> | GreetingService   |
| (Postman, Browser)|      +-----------------+     +--------------------+
|                   | <--- |  @RestController  | <--- |  Business Logic  |
+-------------------+      +-----------------+     +--------------------+
                                  |                         |
                                  V                         V
                          +---------------+          +------------------+
                          | GreetingRepository  |    | GreetingEntity   |
                          +---------------+          +------------------+
                                  |
                                  V
                          +-----------------+
                          |  H2 Database   |
                          +-----------------+
```

### Detailed Flow

1. **Client (Postman, Browser)**
   - Sends HTTP requests to the application.

2. **GreetingController**
   - Handles incoming HTTP requests and maps them to the appropriate service methods.
   - Example Endpoints: 
     - `POST /api/v1/greetings`
     - `GET /api/v1/greetings`
     - `GET /api/v1/greetings/{id}`
     - `PUT /api/v1/greetings/{id}`
     - `DELETE /api/v1/greetings/{id}`

3. **GreetingService**
   - Contains the business logic.
   - Interacts with the `GreetingRepository` to perform CRUD operations on the database.
   - Methods:
     - `saveGreeting(String name)`
     - `getAllGreetings()`
     - `getGreetingById(Long id)`
     - `updateGreeting(Long id, Greeting greeting)`
     - `deleteGreeting(Long id)`

4. **GreetingRepository**
   - Interface for database operations.
   - Extends `JpaRepository` which provides methods like `save()`, `findAll()`, `findById()`, `deleteById()`.

5. **GreetingEntity**
   - Represents the `Greeting` table in the database.
   - Annotated with `@Entity`.

6. **H2 Database**
   - In-memory database used for storing `Greeting` entities.

### Flow Example

1. **Client Request**: Sends a `POST` request to `/api/v1/greetings` with a greeting name.
2. **GreetingController**: Receives the request and calls the `GreetingService.saveGreeting(name)` method.
3. **GreetingService**: Validates the name, creates a new `Greeting` entity, and calls `GreetingRepository.save(greeting)`.
4. **GreetingRepository**: Saves the `Greeting` entity to the H2 database.
5. **Response**: The saved `Greeting` entity is returned back through the service and controller to the client.

This diagram and explanation should clarify the proper flow of interactions in your Spring Boot application.
