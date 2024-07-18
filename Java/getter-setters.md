
### Getters and Setters in Java

#### Step 1: Creating a Class with Private Fields

Start by creating a class with private fields. For this example, we'll create a `Person` class with private fields for `name` and `age`.

```java
public class Person {
    private String name;
    private int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

#### Step 2: Adding Getter Methods

Getter methods are used to retrieve the value of a private field. They are typically named `getFieldName`. For the `Person` class, we'll create getter methods for `name` and `age`.

```java
public class Person {
    private String name;
    private int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter for name
    public String getName() {
        return name;
    }

    // Getter for age
    public int getAge() {
        return age;
    }
}
```

#### Step 3: Adding Setter Methods

Setter methods are used to update the value of a private field. They are typically named `setFieldName`. For the `Person` class, we'll create setter methods for `name` and `age`.

```java
public class Person {
    private String name;
    private int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter for name
    public String getName() {
        return name;
    }

    // Getter for age
    public int getAge() {
        return age;
    }

    // Setter for name
    public void setName(String name) {
        this.name = name;
    }

    // Setter for age
    public void setAge(int age) {
        if (age > 0) { // Adding a basic validation
            this.age = age;
        } else {
            System.out.println("Age must be positive");
        }
    }
}
```

#### Step 4: Using Getters and Setters

Now that we have getters and setters in place, we can create a `Person` object and use these methods to access and modify its fields.

```java
public class Main {
    public static void main(String[] args) {
        // Creating a Person object
        Person person = new Person("John", 25);

        // Using getters
        System.out.println("Name: " + person.getName());
        System.out.println("Age: " + person.getAge());

        // Using setters
        person.setName("Jane");
        person.setAge(30);

        // Using getters again to see the changes
        System.out.println("Updated Name: " + person.getName());
        System.out.println("Updated Age: " + person.getAge());

        // Attempting to set an invalid age
        person.setAge(-5); // This will trigger the validation in the setter
    }
}
```

### Explanation

- **Encapsulation**: By making fields private and providing public getter and setter methods, we encapsulate the internal representation of the object. This way, we control how the fields are accessed and modified.
- **Validation**: Setters can include validation logic to ensure that the fields are set to valid values.
- **Readability and Maintainability**: Using getters and setters makes the code more readable and maintainable, as it clearly shows the points where data is accessed and modified.

### Conclusion

Getters and setters are a fundamental part of object-oriented programming in Java. They help enforce encapsulation, provide a controlled way to access and modify private fields, and can include validation logic to ensure data integrity. This tutorial covers the basics, but getters and setters can be customized further to fit the specific needs of your application.

Feel free to experiment with the code and explore more advanced concepts related to getters and setters!
