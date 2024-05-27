# Spring Project with XML Configuration

This project serves as an introduction to the Spring framework using XML configuration. It covers the basic concepts of dependency injection, bean lifecycle management, and component scanning.

## How Spring Works

Spring is a powerful framework for building Java applications. At its core, Spring promotes the principle of dependency injection, where objects are given their dependencies rather than creating them themselves. This inversion of control allows for loose coupling between components and facilitates easier testing and maintenance.

In this project, we use XML configuration to define beans and their dependencies. The Spring container manages these beans and injects dependencies where needed. By defining the application's configuration in XML files, we can easily modify and manage the application's components.

## Annotations Used

### @Component

The `@Component` annotation is used to mark classes as Spring-managed components. These components are eligible for auto-detection and wiring by Spring's component scanning mechanism.

### @Autowired

The `@Autowired` annotation is used for automatic dependency injection. When Spring sees a class with this annotation, it automatically wires the dependencies by type. In the `Computer` class, for example, `MusicPlayer` is autowired into the constructor.

### @Value

The `@Value` annotation is used to inject values from properties files, environment variables, or other Spring beans into fields in a Spring-managed component. In the `MusicPlayer` class, it's used to inject the `name` and `volume` properties.

### @Qualifier

The `@Qualifier` annotation is used in combination with `@Autowired` to specify which bean should be injected when multiple beans of the same type are available. In the `MusicPlayer` constructor, it ensures that the correct `Music` implementations are injected.

### @Scope

The `@Scope` annotation is used to define the scope of a Spring-managed bean. In the `ClassicalMusic` class, it's used to define the prototype scope, which means a new instance will be created each time it's requested.

## Components

### 1. MusicPlayer

The `MusicPlayer` component is responsible for playing music. It uses two types of music, which are injected into it as dependencies.

#### Properties
- **Name:** The name of the music player.
- **Volume:** The volume level of the music player.

#### Methods
- **playMusic():** Plays the selected music.

### 2. Music

The `Music` interface defines a method for getting the song.

### 3. ClassicalMusic

A class implementing the `Music` interface, providing classical music.

#### Lifecycle Methods
- **doMyInit():** Initialization method.
- **doMyDestroy():** Destruction method (not called for prototype-scoped beans).

### 4. RockMusic

A class implementing the `Music` interface, providing rock music.

### 5. Computer

A simple class representing a computer, which utilizes the `MusicPlayer` to play music.

#### Properties
- **ID:** Unique identifier for the computer.

## Running the Application

To run the application, execute the `TestSpring` class. It will load the Spring application context from the `applicationContext.xml` file and demonstrate the functionality of the music player.
