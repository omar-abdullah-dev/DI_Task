# DI Task - Spring Dependency Injection Demo

A Java application demonstrating **Dependency Injection (DI)** and **Inversion of Control (IoC)** using the Spring Framework. This project showcases different dependency injection patterns and bean configuration through XML.

## Overview

This project implements a shape drawing system where different shapes (Circle, Square) can be drawn in both 2D and 3D formats. The dependencies for drawing functionality are managed by the Spring IoC container, illustrating core Spring Framework concepts.

## Project Structure

```
DITask/
├── src/
│   ├── Main.java                    # Application entry point
│   ├── applicationContext.xml       # Spring bean configuration
│   └── com/DI/task/
│       ├── Shape.java              # Shape interface
│       ├── CircleShape.java         # Circle implementation
│       ├── SquareShape.java         # Square implementation
│       ├── Draw2dShape.java         # 2D drawing implementation
│       └── Draw3dShape.java         # 3D drawing implementation
├── libs/                            # External libraries
└── out/                             # Compiled output
```

## Key Concepts Demonstrated

### 1. **Dependency Injection Patterns**

#### Constructor Injection (CircleShape)
```xml
<bean id="circle" class="com.DI.task.CircleShape">
    <constructor-arg ref="draw2dShape"/>
    <constructor-arg ref="draw3dShape"/>
</bean>
```
Dependencies are injected through the constructor, making them immutable and mandatory.

#### Setter Injection (SquareShape)
```xml
<bean id="square" class="com.DI.task.SquareShape">
    <property name="draw2dSquare" ref="draw2dShape"/>
    <property name="draw3dSquare" ref="draw3dShape"/>
</bean>
```
Dependencies are injected through setter methods, providing flexibility for optional dependencies.

### 2. **Inversion of Control (IoC)**
The Spring IoC container manages object creation and dependency resolution, removing the need for manual instantiation and coupling.

### 3. **Bean Configuration**
XML-based bean configuration defines the application components and their relationships in `applicationContext.xml`.

## How It Works

1. **Spring Context Initialization**: The application creates an `ApplicationContext` from `applicationContext.xml`
2. **Bean Retrieval**: Beans are retrieved from the container using `getBean()` method
3. **Dependency Injection**: The container automatically injects dependencies based on configuration
4. **Execution**: Shape objects execute their 2D and 3D drawing operations

## Running the Application

### Prerequisites
- Java 8 or higher
- Spring Framework libraries in the `libs` folder

### Compilation
```bash
javac -cp "libs/*" -d out src/*.java src/com/DI/task/*.java
```

### Execution
```bash
java -cp "out:libs/*" Main
```

## Expected Output

```
Drawing 2D Circle
Drawing 3D Circle
Drawing 2D Square
Drawing 3D Square
```

## Technologies Used

- **Java**: Core programming language
- **Spring Framework**: Dependency injection and IoC container
- **XML Configuration**: Bean definition and wiring

## Learning Outcomes

This project demonstrates:
- ✅ How to configure beans in Spring XML
- ✅ Constructor vs. Setter injection patterns
- ✅ Bean dependencies and references
- ✅ ApplicationContext usage for IoC container management
- ✅ Separation of concerns through DI

## Future Enhancements

- Implement annotation-based configuration (`@Component`, `@Autowired`)
- Add support for 3D shapes (Sphere, Cube, etc.)
- Implement factory pattern for shape creation
- Add configuration using Java classes instead of XML

## Notes

- This is an educational project for understanding Spring Framework fundamentals
- The current implementation uses XML configuration, which can be replaced with annotations in modern Spring applications

## Author

DI Task - Bootcamp Exercise
