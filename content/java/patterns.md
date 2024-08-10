---
title: "Design Patterns"
date: 2023-10-01
tags: ["design patterns", "software development", "interview questions"]
---

# Design Patterns

-   [What is a _"design pattern"_?](#what-is-a-design-pattern)
-   [Name the main characteristics of design patterns.](#name-the-main-characteristics-of-design-patterns)
-   [Types of design patterns.](#types-of-design-patterns)
-   [Provide examples of main design patterns.](#provide-examples-of-main-design-patterns)
-   [Provide examples of creational design patterns.](#provide-examples-of-creational-design-patterns)
-   [Provide examples of structural design patterns.](#provide-examples-of-structural-design-patterns)
-   [Provide examples of behavioral design patterns.](#provide-examples-of-behavioral-design-patterns)
-   [What is an _"anti-pattern"_? What anti-patterns do you know?](#what-is-an-anti-pattern-what-anti-patterns-do-you-know)
-   [What is _Dependency Injection_?](#what-is-dependency-injection)

## What is a _"design pattern"_?

A **design pattern** is a proven and ready-to-use solution. It is not a class or a library that can be plugged into a project; it's something more than that – it is language-independent, not a finished example that can be directly converted into code, and it can be implemented in different ways across various programming languages.

### Advantages of Using Patterns:

-   Reduces development complexity by providing ready abstractions for solving an entire class of problems.
-   Eases communication among developers by allowing references to known patterns.
-   Standardizes the details of solutions: modules and project elements.
-   Enables the reuse of successful solutions repeatedly.
-   Assists in choosing the most suitable design option.

### Disadvantages:

-   Blindly following a chosen pattern can lead to increased complexity in the program.
-   The desire to try out a pattern without solid justification.

[Back to Table of Contents](#design-patterns)

## Name the main characteristics of design patterns.

-   **Name** - all patterns have a unique name that serves to identify them;
-   **Purpose** - the intended use of the pattern;
-   **Problem** - the problem the pattern addresses;
-   **Solution** - the method proposed in the pattern for solving the problem within the context where the pattern was found;
-   **Participants** - entities involved in solving the problem;
-   **Consequences** - the consequences of using the pattern as a result of the actions performed within it;
-   **Implementation** - a possible way to implement the pattern.

[Back to Table of Contents](#design-patterns)

## Types of Design Patterns.

-   Fundamental - the basic building blocks for other patterns. Most other patterns use these patterns in some form.
-   Creational Patterns - design patterns that abstract the process of instance creation. They allow the system to be independent of the way objects are created, composed, and represented. A class-creating pattern uses inheritance to alter the created instance, whereas an object-creating pattern delegates the creation of objects to another object.
-   Structural Patterns - define various complex structures that modify the interface of existing objects or their implementations, facilitating development and optimizing the program.
-   Behavioral Patterns - define interactions between objects, thereby increasing flexibility.

[Back to Table of Contents](#design-patterns)

## Provide examples of main design patterns.

-   **Delegation Pattern** - An entity externally expresses certain behavior but actually delegates the responsibility for that behavior to a related object.
-   **Functional Design** - Ensures that each entity has only one responsibility and performs it with minimal side effects on others.
-   **Immutable Interface** - Creates an immutable object.
-   **Interface** - A common method of structuring entities, making them easier to understand.
-   **Marker Interface** - As an attribute (like labeling an object), the presence or absence of the implementation of a marker interface is used. Modern programming languages often use attributes or annotations instead.
-   **Property Container** - Allows adding additional properties to an entity within this container instead of extending it with new properties.
-   **Event Channel** - Creates a centralized channel for events. Uses a representative entity for subscribing and another representative entity for publishing an event in the channel. The representative exists separately from the actual publisher or subscriber. A subscriber can receive published events from more than one entity, even if registered only on one channel.

[Back to Table of Contents](#design-patterns)

## Provide examples of creational design patterns.

-   **Abstract Factory** - A class that represents an interface for creating other classes.
-   **Builder** - A class that represents an interface for creating a complex object.
-   **Factory Method** - Delegates the creation of objects to child classes. This allows the program code to manipulate abstract objects at a higher level instead of specific classes.
-   **Prototype** - Defines an interface for creating an object by cloning another object instead of creating it through a constructor.
-   **Singleton** - A class that can have only one instance.

[Back to Table of Contents](#design-patterns)

## Provide examples of structural design patterns.

-   **Adapter** - An object that facilitates interaction between two other objects, one of which uses and the other provides an interface that is incompatible with the first.
-   **Bridge** - A structure that allows changing the interface for accessing and the implementation interface of a class independently.
-   **Composite** - An object that combines similar objects into itself.
-   **Decorator** - A class that extends the functionality of another class without using inheritance.
-   **Facade** - An object that abstracts working with several classes, combining them into a whole.
-   **Flyweight** - An object that represents itself as a unique instance in different parts of the program but is not actually so.
-   **Proxy** - An object that acts as an intermediary between two other objects, implementing/restricting access to the object that is accessed through it.

[Back to Table of Contents](#design-patterns)

## Provide examples of behavioral design patterns.

-   **Chain of Responsibility** - Designed to organize levels of responsibility in the system.
-   **Command** - Represents an action. A command object encapsulates the action itself and its parameters.
-   **Interpreter** - Resolves commonly encountered yet change-prone tasks.
-   **Iterator** - Represents an object that allows sequential access to the elements of an aggregate object without exposing the details of each plus \_\_of the objects within the aggregation.
-   **Mediator** - Facilitates the interaction of many objects, achieving loose coupling and freeing objects from the need to explicitly reference one another.
-   **Memento** - Allows capturing and saving the internal states of an object without violating encapsulation so that it can be restored to those states later.
-   **Observer** - Defines a one-to-many dependency between objects in such a way that when one object's state changes, all its dependents are notified of this event.
-   **State** - Used when an object should change its behavior based on its state during program execution.
-   **Strategy** - Designed to define a family of algorithms, encapsulating each one and providing them interchangeably.
-   **Template Method** - Defines the skeleton of an algorithm and allows subclasses to redefine certain steps of the algorithm without changing its overall structure.
-   **Visitor** - Describes an operation that is performed on objects of other classes. Changing the visitor class doesn't require changing the serviced classes.

[Back to Table of Contents](#design-patterns)

## What is an _"anti-pattern"_? What anti-patterns do you know?

An **anti-pattern** is a common approach to solving a class of frequently encountered problems that is ineffective, risky, or unproductive.

**Poltergeists** - Classes with limited responsibility and role in the system, whose sole purpose is to pass information to other classes. Their effective lifecycle is short. Poltergeists disrupt the cohesion of software architecture by creating redundant abstractions; they are overly complex, difficult to understand, and hard to maintain. Such classes are often designed as controller classes that exist solely to invoke methods on other classes, frequently in a predefined sequence.

### Signs of Appearance and Consequences of the Anti-Pattern:

-   Redundant inter-class connections.
-   Temporary associations.
-   Stateless classes (containing only methods and constants).
-   Temporary objects and classes (with short lifespans).
-   Classes with a single method intended solely for creating or invoking other classes through temporary association.
-   Classes with method names in a management style, such as startProcess.

### Typical Causes:

-   Lack of object-oriented architecture (the architect does not understand the object-oriented paradigm).
-   Incorrect choice of solution paths.
-   Assumptions about the application's architecture during the requirements analysis phase can also lead to problems resembling this anti-pattern.

**Introduced Complexity**: Optional design complexity. Instead of having a single simple class, an entire hierarchy of interfaces and classes is created. A typical example is "Interface - Abstract Class - Only Class Implementing Interface based on Abstract".

**Abstraction Inversion**: Hiding part of the functionality from external use, hoping that no one will use it.

**Ambiguous Viewpoint**: Presenting a model without specifying its viewpoint.

**Big Ball of Mud**: A system with unrecognizable structure.

**God Object**: Concentration of too many functions in one part of the system (class).

**Input Kludge**: Forgetfulness in specifying and performing support for potential incorrect input.

**Interface Bloat**: Development of an interface that is too powerful and very complex to implement.

**Magic Pushbutton**: Performing user action results through an unsuitable (not abstract enough) interface. For example, writing application logic in button click handlers.

**Re-Coupling**: The process of introducing unnecessary dependencies.

**Stovepipe System**: A rarely maintained assembly of poorly connected components.

**Race Hazard**: The unforeseen possibility of events occurring in a different order than expected.

**Mutilation**: Excessive "sharpening" of an object for a very narrow task, rendering it incapable of working with any other tasks, even very similar ones.

**Save or Die**: Saving changes only upon application exit.

[Back to Table of Contents](#design-patterns)

## What is _Dependency Injection_?

**Dependency Injection** is a set of patterns and principles in software development that allow you to write loosely coupled code. In full accordance with the single responsibility principle, an object delegates the responsibility for constructing the required dependencies to an external mechanism specifically designed for this purpose.

[Back to Table of Contents](#design-patterns)

# Sources

-   [Wikipedia](https://en.wikipedia.org/wiki/Design_pattern)
-   [Javenue](http://www.javenue.info/post/56)

[Interview Questions](README.md)
