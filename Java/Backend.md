
Step 1: Setting Up Our Project

Why: We need a starting point for our app, like a blank canvas for a painting.

How:
1. Go to https://start.spring.io/
2. Choose:
   - Project: Maven (it's a tool that helps manage our project)
   - Language: Java
   - Spring Boot: Pick the latest stable version
   - Group: com.example
   - Artifact: blogapp
3. Add Dependencies: Spring Web, Spring Data JPA, H2 Database
4. Click "Generate" and unzip the downloaded file

Think of this like getting all your art supplies ready before starting a painting.

Test: Open the folder in your code editor. If you see a structure with folders and a file called 'pom.xml', you're ready for the next step!

Step 2: Creating Our User

Why: We need to tell the computer what a "user" is in our blog.

How:
Create a new file called User.java in src/main/java/com/example/blogapp/models and add this code:

```java
package com.example.blogapp.models;

import javax.persistence.*;

@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int userId;
    private String username;
    private String email;

    // Add getters and setters here
}
```

This is like describing a person: they have a unique ID (like a social security number), a username, and an email.

Test: Try to run your application. If there are no red error messages, you've described a User correctly!

Step 3: Creating Our Post

Why: We need to tell the computer what a "post" is in our blog.

How:
Create a new file called Post.java in the same folder and add:

```java
package com.example.blogapp.models;

import javax.persistence.*;

@Entity
@Table(name = "posts")
public class Post {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int postId;
    private String title;
    private String content;
    private boolean approved;

    @ManyToOne
    @JoinColumn(name = "user_id")
    private User user;

    // Add getters and setters here
}
```

This is like describing a blog post: it has a unique ID, a title, some content, whether it's approved, and who wrote it.

Test: Run your application again. No red errors? Great! You've described a Post correctly.

Step 4: Creating Our User Actions

Why: We need to tell the computer how to save and find users.

How:
Create a new file called UserRepository.java in src/main/java/com/example/blogapp/repositories:

```java
package com.example.blogapp.repositories;

import com.example.blogapp.models.User;
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Integer> {
}
```

This is like giving the computer a filing cabinet for users.

Test: Run your application. If it starts without errors, your UserRepository is set up correctly!

Step 5: Creating Our Post Actions

Why: We need to tell the computer how to save and find posts.

How:
Create a new file called PostRepository.java in the same folder:

```java
package com.example.blogapp.repositories;

import com.example.blogapp.models.Post;
import org.springframework.data.jpa.repository.JpaRepository;

public interface PostRepository extends JpaRepository<Post, Integer> {
}
```

This is like giving the computer another filing cabinet, but for posts this time.

Test: Run your application. No errors? Your PostRepository is good to go!

Step 6: Creating User Rules

Why: We need to define what actions we can do with users.

How:
Create a new file called UserService.java in src/main/java/com/example/blogapp/services:

```java
package com.example.blogapp.services;

import com.example.blogapp.models.User;
import com.example.blogapp.repositories.UserRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class UserService {
    @Autowired
    private UserRepository userRepository;

    public User createUser(User user) {
        return userRepository.save(user);
    }
}
```

This tells the computer how to create a new user.

Test: Run your application. If it starts without errors, your UserService is set up correctly!

Step 7: Creating Post Rules

Why: We need to define what actions we can do with posts.

How:
Create a new file called PostService.java in the same folder:

```java
package com.example.blogapp.services;

import com.example.blogapp.models.Post;
import com.example.blogapp.repositories.PostRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class PostService {
    @Autowired
    private PostRepository postRepository;

    public Post createPost(Post post) {
        return postRepository.save(post);
    }

    public Post approvePost(int postId) {
        Post post = postRepository.findById(postId).orElseThrow(() -> new RuntimeException("Post not found"));
        post.setApproved(true);
        return postRepository.save(post);
    }
}
```

This tells the computer how to create a new post and how to approve a post.

Test: Run your application. No errors? Your PostService is ready!

Step 8: Creating User Controls

Why: We need a way for people to interact with our app to create users.

How:
Create a new file called UserController.java in src/main/java/com/example/blogapp/controllers:

```java
package com.example.blogapp.controllers;

import com.example.blogapp.models.User;
import com.example.blogapp.services.UserService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/users")
public class UserController {
    @Autowired
    private UserService userService;

    @PostMapping
    public User createUser(@RequestBody User user) {
        return userService.createUser(user);
    }
}
```

This is like creating a button that people can press to create a new user.

Test: Run your application. If it starts without errors, your UserController is set up correctly!

Step 9: Creating Post Controls

Why: We need a way for people to interact with our app to create and approve posts.

How:
Create a new file called PostController.java in the same folder:

```java
package com.example.blogapp.controllers;

import com.example.blogapp.models.Post;
import com.example.blogapp.services.PostService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/posts")
public class PostController {
    @Autowired
    private PostService postService;

    @PostMapping
    public Post createPost(@RequestBody Post post) {
        return postService.createPost(post);
    }

    @PutMapping("/{postId}/approve")
    public Post approvePost(@PathVariable int postId) {
        return postService.approvePost(postId);
    }
}
```

This is like creating two buttons: one to create a new post, and another to approve a post.

Test: Run your application. If it starts without errors, congratulations! Your basic blog application is now complete!

Final Test: Let's use our app!

1. Create a user:
   - Use Postman or any API testing tool
   - Send a POST request to http://localhost:8080/api/users
   - With body:
     ```json
     {
       "username": "testuser",
       "email": "test@example.com"
     }
     ```
   - You should get a response with the created user and an ID

2. Create a post:
   - Send a POST request to http://localhost:8080/api/posts
   - With body:
     ```json
     {
       "title": "My First Post",
       "content": "Hello, World!",
       "user": {
         "userId": 1
       }
     }
     ```
   - You should get a response with the created post, including its ID and approved status (false)

3. Approve the post:
   - Send a PUT request to http://localhost:8080/api/posts/1/approve
   - You should get a response with the updated post, now with approved status true

