Tutorial: Understanding Dependency Injection

Part 1: Simple Dependency Injection

Let's start with a basic example of a `Car` that depends on an `Engine`.

1. Create the `Engine` interface:

```java
public interface Engine {
    void start();
}
```

2. Create two implementations of `Engine`:

```java
public class GasolineEngine implements Engine {
    @Override
    public void start() {
        System.out.println("Gasoline engine starting...");
    }
}

public class ElectricEngine implements Engine {
    @Override
    public void start() {
        System.out.println("Electric engine starting...");
    }
}
```

3. Create the `Car` class with constructor injection:

```java
public class Car {
    private Engine engine;

    // Constructor Injection
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
        System.out.println("Car is driving...");
    }
}
```

4. Main application:

```java
public class Application {
    public static void main(String[] args) {
        // Create a car with a gasoline engine
        Engine gasolineEngine = new GasolineEngine();
        Car gasolineCar = new Car(gasolineEngine);
        gasolineCar.drive();

        // Create a car with an electric engine
        Engine electricEngine = new ElectricEngine();
        Car electricCar = new Car(electricEngine);
        electricCar.drive();
    }
}
```

In this simple example, we're manually performing dependency injection by passing the `Engine` object to the `Car` constructor.

Part 2: Advanced Dependency Injection

Now, let's create a more advanced example with multiple dependencies and different types of injection.

1. Create additional components:

```java
public interface Transmission {
    void shift();
}

public class AutomaticTransmission implements Transmission {
    @Override
    public void shift() {
        System.out.println("Automatic transmission shifting...");
    }
}

public interface FuelInjector {
    void inject();
}

public class StandardFuelInjector implements FuelInjector {
    @Override
    public void inject() {
        System.out.println("Standard fuel injector injecting fuel...");
    }
}
```

2. Create a `CarFactory` to manage object creation and dependency injection:

```java
public class CarFactory {
    public static Car createCar(String engineType, String transmissionType) {
        Engine engine = createEngine(engineType);
        Transmission transmission = createTransmission(transmissionType);
        FuelInjector fuelInjector = new StandardFuelInjector();

        return new Car(engine, transmission, fuelInjector);
    }

    private static Engine createEngine(String engineType) {
        if ("electric".equalsIgnoreCase(engineType)) {
            return new ElectricEngine();
        } else {
            return new GasolineEngine();
        }
    }

    private static Transmission createTransmission(String transmissionType) {
        if ("automatic".equalsIgnoreCase(transmissionType)) {
            return new AutomaticTransmission();
        } else {
            throw new IllegalArgumentException("Unsupported transmission type");
        }
    }
}
```

3. Update the `Car` class to use different types of injection:

```java
public class Car {
    private Engine engine;
    private Transmission transmission;
    private FuelInjector fuelInjector;

    // Constructor Injection
    public Car(Engine engine, Transmission transmission) {
        this.engine = engine;
        this.transmission = transmission;
    }

    // Setter Injection
    public void setFuelInjector(FuelInjector fuelInjector) {
        this.fuelInjector = fuelInjector;
    }

    public void drive() {
        engine.start();
        transmission.shift();
        if (fuelInjector != null) {
            fuelInjector.inject();
        }
        System.out.println("Car is driving...");
    }
}
```

4. Main application:

```java
public class Application {
    public static void main(String[] args) {
        // Create a gasoline car with automatic transmission
        Car gasolineCar = CarFactory.createCar("gasoline", "automatic");
        gasolineCar.drive();

        System.out.println();

        // Create an electric car with automatic transmission
        Car electricCar = CarFactory.createCar("electric", "automatic");
        electricCar.drive();
    }
}
```

In this advanced example:

1. We've introduced multiple dependencies (`Engine`, `Transmission`, `FuelInjector`).
2. We're using both constructor injection (for `Engine` and `Transmission`) and setter injection (for `FuelInjector`).
3. We've created a `CarFactory` to manage the creation of objects and their dependencies. This is a simple implementation of the Factory pattern and Dependency Injection Container.
4. The `CarFactory` allows us to create different types of cars without changing the `Car` class itself.

Benefits of this approach:

1. Flexibility: We can easily change the type of engine or transmission without modifying the `Car` class.
2. Testability: We can easily mock dependencies for unit testing.
3. Loose coupling: The `Car` class doesn't need to know about the specific implementations of its dependencies.
4. Separation of concerns: The `CarFactory` handles object creation and wiring, separating this concern from the `Car` class.
