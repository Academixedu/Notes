```markdown
# Control Flow (Part 2) Tutorial

```java
public class SwitchExample {
    public static void main(String[] args) {
        int day = 3;
        String dayName;

        switch (day) {
            case 1:
                dayName = "Monday";
                break;
            case 2:
                dayName = "Tuesday";
                break;
            default:
                dayName = "Invalid day";
                break;
        }

        System.out.println("The day is: " + dayName);
    }
}
```


## Objective
- Understand `&&` and `||` logic
- Implement loops in Java (`for`, `while`, `do-while`)
- Learn about nested loops
- Apply loops to solve real-world problems

## Schedule

### First Hour:

#### Review of Day 2 (10 minutes):
- Recap basic input/output and conditional statements.
- Review logical operators (`&&`, `||`) used in conditions.

#### Understanding Logical Operators (10 minutes):
- Explain the use of `&&` (logical AND) and `||` (logical OR) in conditions.
- Show examples of how these operators work.

```java
// Example of logical AND (&&)
int age = 20;
boolean hasLicense = true;
if (age >= 18 && hasLicense) {
    System.out.println("You can drive.");
}

// Example of logical OR (||)
boolean isWeekend = true;
boolean isHoliday = false;
if (isWeekend || isHoliday) {
    System.out.println("You can relax today.");
}
```

#### Introduction to Loops (15 minutes):
- Explain the purpose of loops.
- Discuss `for`, `while`, and `do-while` loops.
- Show syntax and examples for each loop.

```java
// For Loop Example
for (int i = 0; i < 5; i++) {
    System.out.println("Count: " + i);
}

// While Loop Example
int count = 0;
while (count < 5) {
    System.out.println("Count: " + count);
    count++;
}



#### Live Coding Session (15 minutes):
- Demonstrate writing programs using each type of loop.
- Highlight differences and use cases.

```java
public class Main {
    public static void main(String[] args) {
        // For loop
        for (int i = 0; i < 5; i++) {
            System.out.println("For Loop Count: " + i);
        }

        // While loop
        int count = 0;
        while (count < 5) {
            System.out.println("While Loop Count: " + count);
            count++;
        }

        // Do-while loop
        int doCount = 0;
        do {
            System.out.println("Do-While Loop Count: " + doCount);
            doCount++;
        } while (doCount < 5);
    }
}
```

#### Hands-on Practice (20 minutes):
- Students write their programs using each type of loop.
- Assist students as needed.

### Second Hour:

#### Introduction to Nested Loops (15 minutes):
- Explain nested loops and their applications.
- Show examples of nested loops.

```java
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        System.out.println("i = " + i + ", j = " + j);
    }
}
```

#### Real-World Example: Multiplication Table (10 minutes):
- Use nested loops to generate a multiplication table.

```java
public class Main {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            for (int j = 1; j <= 10; j++) {
                System.out.print(i * j + "\t");
            }
            System.out.println();
        }
    }
}
```

#### Hands-on Practice (20 minutes):
- Students create programs using nested loops.
- Assign tasks like generating patterns or processing 2D arrays.
- Assist students as needed.

#### Complex Real-World Example: Simple ATM System (10 minutes):
- Demonstrate a simple ATM system using loops and conditionals.

```java


```

#### Q&A Session (10 minutes):
- Address any questions related to the topics covered.
- Provide additional examples if needed.

#### Recap and Summary (5 minutes):
- Review key points covered during the session.
- Emphasize the importance of loops in solving repetitive tasks and real-world problems.
```
