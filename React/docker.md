
1. Create a Dockerfile:
In the root directory of your project, create a file named `Dockerfile` with the following content:

```dockerfile
FROM openjdk:11-jdk-slim

WORKDIR /app

COPY target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
```

This Dockerfile:
- Uses OpenJDK 11 (matching your Java version)
- Sets the working directory to `/app`
- Copies the JAR file from the `target` directory
- Exposes port 8080
- Specifies the command to run the application

2. Create a .dockerignore file:
Create a `.dockerignore` file in the root directory with the following content:

```
target/
!target/*.jar
```

This prevents unnecessary files from being copied into the Docker image.

3. Build the application:
Run the following command to build your Spring Boot application:

```bash
mvn clean package
```

This will create a JAR file in the `target` directory.

4. Build the Docker image:
Run the following command to build your Docker image:

```bash
docker build -t blogapp .
```

This builds a Docker image named `blogapp` based on your Dockerfile.

5. Run the Docker container:
To run your application in a Docker container, use:

```bash
docker run -p 8080:8080 blogapp
```

This maps port 8080 from the container to port 8080 on your host machine.

6. (Optional) Create a docker-compose.yml file:
If you want to use Docker Compose, create a `docker-compose.yml` file in your project root:

```yaml
version: '3'
services:
  blogapp:
    build: .
    ports:
      - "8080:8080"
    environment:
      - SPRING_DATASOURCE_URL=jdbc:h2:mem:testdb
      - SPRING_DATASOURCE_USERNAME=sa
      - SPRING_DATASOURCE_PASSWORD=
```

Then you can start your application using:

```bash
docker-compose up --build
```

These steps will containerize your Spring Boot application using Docker, based on your existing pom.xml file. The application will use the H2 in-memory database as configured in your application.properties.

Remember that with this setup, your data will not persist between container restarts. If you need data persistence, you might want to consider using a persistent database in the future.

Is there anything else you'd like me to explain or help with regarding the Docker setup?
