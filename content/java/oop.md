---
title: "Interview Questions"
date: 2023-10-01
tags: ["OOP", "interview", "programming"]
---

[Interview Questions](README.md)

# OOP

-   [What is _OOP_?](#What-is-OOP)
-   [Name the main principles of _OOP_.](#Name-the-main-principles-of-OOP)
-   [What is \_“encapsulation”?](#What-is-encapsulation)
-   [What is \_“inheritance”?](#What-is-inheritance)
-   [What is \_“polymorphism”?](#What-is-polymorphism)
-   [What is \_“abstraction”?](#What-is-abstraction)
-   [What does _“message passing”_ represent?](#What-does-message-passing-represent)
-   [Describe the basic concepts of OOP: _“class”_, _“object”_, _“interface”_.](#Describe-the-basic-concepts-of-OOP-class-object-interface)
-   [What are the advantages and disadvantages of the object-oriented approach in programming?](#What-are-the-advantages-and-disadvantages-of-the-object-oriented-approach-in-programming)
-   [What do the expressions _“is”_ and _“has”_ imply in the context of OOP principles?](#What-do-the-expressions-is-and-has-imply-in-the-context-of-OOP-principles)
-   [What is the difference between _composition_ and _aggregation_?](#What-is-the-difference-between-composition-and-aggregation)
-   [What are _static_ and _dynamic binding_?](#What-are-static-and-dynamic-binding)

## What is _OOP_?

**Object-Oriented Programming (OOP)** is a programming methodology based on representing a program as a collection of objects, where each object is an instance of a specific class, and classes form a hierarchy of inheritance.

-   OOP uses objects as the primary logical constructs instead of algorithms;
-   Each object is an instance of a specific class;
-   Classes create hierarchies.

A program is considered object-oriented only if all three requirements are met. In particular, programming that does not use inheritance is called non-object-oriented and is considered programming with abstract data types.

According to the OOP paradigm, a program consists of objects that exchange messages. Objects can have state, and the only way to change an object's state is to send it a message, to which the object can respond by changing its own state.

[Back to contents](#OOP)

## Name the main principles of _OOP_.

-   _Encapsulation_ - hiding implementation details.
-   _Inheritance_ - creating a new entity based on an existing one.
-   _Polymorphism_ - the ability to take on different forms for the same entity.
-   _Abstraction_ - a set of common characteristics.
-   _Message Passing_ - a form of interaction between entities.
-   _Reusability_ - all of the above principles promote code reuse.

This is the only correct order of OOP paradigms, as each subsequent one builds upon the previous ones.

[Back to contents](#OOP)

## What is _“encapsulation”?_

**Encapsulation** is a system property that allows combining data and the methods that work with that data within a class while hiding implementation details from the user, exposing only what is necessary for subsequent use.

The goal of encapsulation is to decouple the external interface of the class (what other classes may use) from its implementation. This ensures that minor changes in the class do not lead to changes in the external behavior of the class.

Imagine for a moment that we are at the end of the 19th century, when Henry Ford had not yet invented the assembly line, and the first attempts to create a car faced criticism from authorities about how these smoke-belching monsters were polluting the air and frightening horses. Let’s suppose that to operate the first steam car, one needed to understand how a steam boiler works, constantly add coal, and monitor the temperature and water level. Additionally, turning the wheels required using two levers, each controlling one wheel separately. I think we can agree that driving a car of that time was quite an inconvenient and difficult task.

Now, let’s return to today with modern automotive wonders equipped with automatic transmissions. In essence, nothing has changed. The fuel pump still supplies gas to the engine, differentials allow the wheels to turn at different angles, and the crankshaft converts the translational motion of the pistons into rotational motion of the wheels. The progress lies elsewhere. All these actions are now hidden from the user, allowing them to turn the steering wheel and press the gas pedal without considering what happens with the fuel injector, throttle, and camshaft. It is the concealment of internal processes that occur in a vehicle that allows even those who are not professional auto mechanics with twenty years of experience to use it effectively. This concealment in OOP is known as encapsulation.

Example:

```java
public class SomePhone {

    private int year;
    private String company;

    public SomePhone(int year, String company) {
        this.year = year;
        this.company = company;
    }

    private void openConnection(){
        //findComutator
        //openNewConnection...
    }

    public void call() {
        openConnection();
        System.out.println("Calling number");
    }

    public void ring() {
        System.out.println("Ding-ding");
    }
}
```

The private modifier restricts access to class fields and methods from outside the class. This means that accessing private fields from outside is impossible, as is calling private methods.

Hiding access to the openConnection method also allows for the freedom to change the internal implementation of that method without affecting other objects, since that method is guaranteed not to be used by them.

To interact with our object, we keep the call and ring methods open using the public modifier. Providing public methods to interact with the object is also part of the encapsulation mechanism because if access to the object were completely closed, it would become useless.

[Back to contents](#OOP)

## What is _“inheritance”?_

**Inheritance** is a system property that allows describing a new class based on an already existing one with partially or fully borrowed functionality.

The class from which inheritance is derived is called the _ancestor_, _base_, or _parent_ class. The new class is referred to as the _descendant_, _heir_, or _derived_ class.

Imagine for a moment that we are engineers at a car factory. Our task is to develop a modern car. We already have a previous model that has performed excellently over many years of use. All is well, but times and technologies change, and our modern factory needs to strive to enhance convenience and comfort in the products it produces, aligning with modern standards.

We need to release an entire range of vehicles: a sedan, a station wagon, and a compact hatchback. It is clear that we are not going to design a new car from scratch; instead, we will take the previous generation as a foundation and make several constructive changes. For instance, we might add power steering and reduce the gaps between the fenders and the hood, as well as install fog lamps. Moreover, the bodyshape will vary across each model.

It is evident that all three modifications will inherit most of the properties from the previous model (the trusty old engine from 1970, the indestructible undercarriage that has performed excellently on domestic roads, the gearbox, etc.) while each model will implement some new functionality or design feature. Here, we are dealing with inheritance.

Example:
Let’s consider an example of creating a smartphone class using inheritance. All wireless phones operate on batteries that have a certain operational life in hours. Therefore, we add this property to the wireless phone class:

```java
public abstract class WirelessPhone extends AbstractPhone {

    private int hour;

    public WirelessPhone(int year, int hour) {
        super(year);
        this.hour = hour;
    }
}
```

Cell phones inherit properties from wireless phones while we also implement call and ring methods in this class:

```java
public class CellPhone extends WirelessPhone {

    public CellPhone(int year, int hour) {
        super(year, hour);
    }

    @Override
    public void call(int outputNumber) {
        System.out.println("Calling number " + outputNumber);
    }

    @Override
    public void ring(int inputNumber) {
        System.out.println("Incoming call from " + inputNumber);
    }
}
```

Finally, here’s the smartphone class, which, unlike traditional cell phones, features a full operating system. You can add new programs supported by this operating system to the smartphone, thus expanding its functionality. Here’s how to describe the class with code:

```java
public class Smartphone extends CellPhone {

    private String operationSystem;

    public Smartphone(int year, int hour, String operationSystem) {
        super(year, hour);
        this.operationSystem = operationSystem;
    }

    public void install(String program){
        System.out.println("Installing " + program + " for " + operationSystem);
    }
}
```

As you can see, we created very little new code to define the Smartphone class, but we obtained a new class with new functionality. Using this OOP principle in Java allows significantly reducing code volume, and thus easing the programmer's workload.

[Back to contents](#OOP)

## What is _“polymorphism”?_

**Polymorphism** is a system property that allows the use of objects with the same interface without knowledge of the type and internal structure of the object.

The advantage of polymorphism is that it helps reduce program complexity by allowing one interface to be used to specify a unified set of actions. The specific action determined by the situation is left to the programming language’s compiler. Hence, the key feature of polymorphism is the use of a derived class object instead of a base class object (descendants can alter the parent’s behavior even when accessed via a reference of the parent type).

Any driving lesson would be pointless if a learner who learned to drive, say, a VAZ 2106 could not later drive a VAZ 2110 or a BMW X3. On the other hand, it is hard to picture someone ideally handling a vehicle where the gas pedal is to the left of the brake pedal and instead of a steering wheel, there is a joystick.

The essence is that the main controls of a car have the same design and principle of operation. A driver knows that to turn left, they must turn the steering wheel, regardless of whether there’s power steering or not.
Should a person need to drive from work to home, they will get behind the wheel and perform the same actions, regardless of which type of car they are using. In essence, it can be said that all cars have the same interface, while the driver, abstracting from the essence of the car, operates through that interface. If a driver needs to drive on the German autobahn, they might choose a fast sports car, while if they were to return from a remote area in the Altai Mountains after rain, they might choose a UAZ with military axles. However, regardless of how movement and the internal functioning of the car are implemented, the interface remains the same.

_A polymorphic variable_ is a variable that can take values of different types, while a _polymorphic function_ is a function that has at least one argument that is a polymorphic variable.
There are two types of polymorphic functions:

-   _ad hoc_, where the function behaves differently for different argument types (e.g., the `draw()` function draws different shapes);
-   _parametric_, where the function behaves the same for arguments of different types (e.g., the `add()` function adds items of different types into a container).

The principle in OOP that allows a program to use objects with the same interface without knowing the internal workings of the object is called polymorphism.

Example:

Let’s assume that in our program we need to describe a user who can use any phone model to call another user. Here’s how we can do it:

```java
public class User {
    private String name;

    public User(String name) {
        this.name = name;
    }

    public void callAnotherUser(int number, AbstractPhone phone) {
        // Here is polymorphism - using an abstract type AbstractPhone phone in the code!
        phone.call(number);
    }
}
```

Now let’s describe different phone models. One of the earliest phone models:

```java
public class ThomasEdisonPhone extends AbstractPhone {

    public ThomasEdisonPhone(int year) {
        super(year);
    }

    @Override
    public void call(int outputNumber) {
        System.out.println("Turn the crank");
        System.out.println("Please provide the subscriber’s number, sir");
    }

    @Override
    public void ring(int inputNumber) {
        System.out.println("The phone is ringing");
    }
}
```

A regular landline phone:

```java
public class Phone extends AbstractPhone {

    public Phone(int year) {
        super(year);
    }

    @Override
    public void call(int outputNumber) {
        System.out.println("Calling number " + outputNumber);
    }

    @Override
    public void ring(int inputNumber) {
        System.out.println("The phone is ringing");
    }
}
```

And finally, a cool video phone:

```java
public class VideoPhone extends AbstractPhone {

    public VideoPhone(int year) {
        super(year);
    }

    @Override
    public void call(int outputNumber) {
        System.out.println("Connecting video channel for subscriber " + outputNumber);
    }

    @Override
    public void ring(int inputNumber) {
        System.out.println("You have an incoming video call from " + inputNumber);
    }
}
```

Let’s create objects in the main() method and test the callAnotherUser method:

```java
AbstractPhone firstPhone = new ThomasEdisonPhone(1879);
AbstractPhone phone = new Phone(1984);
AbstractPhone videoPhone = new VideoPhone(2018);
User user = new User("Andrew");
user.callAnotherUser(224466, firstPhone);
// Turn the crank
// Please provide the subscriber’s number, sir
user.callAnotherUser(224466, phone);
// Calling number 224466
user.callAnotherUser(224466, videoPhone);
// Connecting video channel for subscriber 224466
```

By invoking the same user method, we obtained different results. The choice of the specific implementation of the call method within callAnotherUser was dynamically made based on the specific type of the object invoking it during program execution. That’s the main advantage of polymorphism – the selection of implementation during runtime.

In the provided phone class examples above, we used method overriding — a technique in which the implementation of a method defined in the base class is modified without changing the method’s signature. Essentially, this constitutes a method replacement, and the newly defined method in the subclass is called during program execution.

Typically, when overriding a method, the @Override annotation is used, which informs the compiler to check the signatures of the overridden and overriding methods.

[Back to contents](#OOP)

## What is _“abstraction”?_

_Abstraction_ is the method of extracting a set of common characteristics of an object, excluding specific and insignificant details. Accordingly, **abstraction** is the set of all such characteristics.

Imagine a driver going through a busy traffic area in a car. It’s evident that at that moment they won’t be thinking about the chemical composition of the car's paint, the specific interactions of gears in the transmission, or how the shape of the body affects speed (unless, of course, the car is stuck in a traffic jam and the driver has absolutely nothing else to occupy themselves with). However, they will be regularly using the steering wheel, pedals, and turn signals.

Example:

```java
// Abstract class
abstract class Animal {
    // Abstract method (does not have a body)
    public abstract void animalSound();

    // Regular method
    public void sleep() {
        System.out.println("Zzz");
    }
}

// Subclass (inherit from Animal)
class Pig extends Animal {
    public void animalSound() {
        // The body of animalSound() is provided here
        System.out.println("The pig says: wee wee");
    }
}

class MyMainClass {
    public static void main(String[] args) {
        Pig myPig = new Pig(); // Create a Pig object
        myPig.animalSound();
        myPig.sleep();
    }
}
```

[Back to contents](#OOP)

## What does _“message passing”_ represent?

Objects interact by sending and receiving messages. A message is a request to perform an action, supplemented by a set of arguments that may be needed during the action’s execution. In OOP, message passing (method invocation) is the only way to transfer control to an object. If an object needs to “respond” to this message, it must have a method that corresponds to the message. Likewise, objects can send messages to other objects using their methods. Message exchange is implemented through dynamic calls, leading to extremely late binding.

Suppose there’s a need to create a physical model describing colliding balls of different sizes. The traditional approach to solving this problem roughly goes as follows: a set of data describing each ball (for example, its coordinates, mass, and acceleration) is determined; each ball is assigned a unique identifier (for example, an array where the index value corresponds to the ball number), allowing each ball to be distinguished from all others. Finally, a subroutine named `bounce` is written; this procedure should appropriately change the data describing the ball based on its number and initial parameters. In contrast to the traditional approach, the object-oriented version of the program models each ball by means of an object. In this case, the object corresponding to a specific ball contains not only its parameters but also the entire code describing the behavior of that ball during various interactions. Thus, each ball will have its own `bounce()` method. Rather than calling the `bounce` subroutine with an argument identifying, say, ball #3, a message is sent to the object “ball #3” instructing it to perform a bounce.

[Back to contents](#OOP)

## Describe the basic concepts of OOP: _“class”_, _“object”_, _“interface”_.

**Class** is a way to describe an entity, defining its state and behavior, depending on that state, as well as the rules for interacting with that entity (a contract).

From a programming perspective, a class can be viewed as a group of data (fields, attributes, members of the class) and functions to work with that data (methods).

From the perspective of program structure, a class is a complex data type.

**Object (instance)** is a specific instance of a class, having a particular state and behavior, fully defined by the class. Each object has specific values of attributes and methods that operate on those values based on the rules specified in the class.

**Interface** is the set of methods of a class that are available for use. The class’s interface will consist of all its public methods along with a set of public attributes. Essentially, the interface specifies the class by clearly defining all possible operations on it.

[Back to contents](#OOP)

## What are the advantages and disadvantages of the object-oriented approach in programming?

Advantages:

-   The object model is quite natural, as it is primarily oriented toward the human perception of the world rather than computer implementation.
-   Classes allow for construction from useful components that have simple tools, thereby enabling abstraction from implementation details.
-   Data and operations on them form a specific entity and are not scattered throughout the program as is often the case with procedural programming; instead, they are described together. Code and data localization enhances understandability and maintainability of software.
-   Encapsulation introduces the property of modularity, which facilitates parallel processing of tasks between several executors and the updating of versions of individual components.
-   The ability to create extendable systems.
-   Utilizing polymorphism proves advantageous for:
    -   Processing heterogeneous data structures. Programs can operate without distinguishing between object types, simplifying the code significantly. New types can be added at any time.
    -   Changing behavior during execution. At runtime, one object can be replaced with another, allowing algorithms to adapt easily based on which object is in use, all without changing the code.
    -   Implementing operations with descendants. Algorithms can be generalized such that they can work with more than one type of object.
    -   Describing parts of the subject area independent of the application in the form of a set of universal classes or a framework, which can later be expanded by adding parts specific to a particular application.
-   Code reuse:
    -   Development time is reduced, allowing that time to be allocated to other tasks.
    -   Reusable components usually contain far fewer bugs than newly developed ones, as they have undergone testing multiple times.
    -   When a component is used by multiple clients, improvements made to its code simultaneously positively affect numerous programs that utilize it.
    -   If the program relies on standardized components, its structure and user interface become more uniform, enhancing both comprehensibility and usability.

Disadvantages:

-   In complex class hierarchies, fields and methods are often inherited from various levels. It is not always easy to determine which fields and methods pertain to a particular class.
-   The message handling code is sometimes “spread out” across many methods (in other words, the processing of the message requires not one but many methods, which may be described in different classes).
-   Documenting classes is a more challenging task than it was for procedures and modules. Since any method can be overridden, the documentation should specify not just what the method does but also the context in which it is called.
-   Inefficiency and non-optimal memory allocation at runtime (due to overhead from dynamic binding and type checking during execution).
-   Excessive generality. There are often more methods included than are actually needed by the current program. And since unnecessary methods cannot be removed, they become dead weight.

[Back to contents](#OOP)

## What do the expressions _“is”_ and _“has”_ imply in the context of OOP principles?

**“is”** implies inheritance.
**“has”** implies association (aggregation or composition).

[Back to contents](#OOP)

## What is the difference between _composition_ and _aggregation_?

Association denotes a relationship between objects. Composition and aggregation are specific cases of the "part-whole" association.

Aggregation implies that objects are related with a “part-of” relationship. Composition is a stricter form of aggregation. In addition to the requirement of “part-of,” there is a condition that an instance of a “part” can belong to only one whole (or not belong to any), while in the case of aggregation, an instance of a “part” can belong to multiple wholes.

> For example, a book consists of pages, and we cannot tear a page out of the book and put it in another book. The pages are clearly tied to a specific book, so this is composition. At the same time, we can take a book and move it from one library to another - that is aggregation.

[Back to contents](#OOP)

## What are _static_ and _dynamic binding_?

Binding a method call to its method body is known as binding. If the binding occurs at compile time (linker) before the program runs, it is called _static_ or _early binding_.

In turn, _late binding_ is binding that is carried out during program execution, depending on the object type. Late binding is also known as _dynamic binding_ or _runtime binding_. In languages that implement late binding, there must be a mechanism for determining the actual type of an object during program execution to call the appropriate method. In other words, the compiler does not know the object type, but the method invocation mechanism identifies it and calls the corresponding method body. The mechanism of late binding depends on the specific language, but it is easy to assume that in order to implement it, objects must include some additional information.

For all methods in Java, late (dynamic) binding is used unless the method is declared as `final`, `static`, or `private` (private methods are `final` by default).

[Back to contents](#OOP)

# Sources

-   [DevColibri](https://devcolibri.com/%d1%87%d1%82%d0%be-%d1%82%d0%b0%d0%ba%d0%be%d0%b5-%d0%be%d0%be%d0%bf-%d0%b8-%d1%81-%d1%87%d0%b5%d0%bc-%d0%b5%d0%b3%d0%be-%d0%b5%d0%b4%d1%8f%d1%82/)
-   [Habr](https://habrahabr.ru/post/87119/)
-   [Wikipedia](https://en.wikipedia.org/wiki/Object-oriented_programming)

[Interview Questions](README.md)
