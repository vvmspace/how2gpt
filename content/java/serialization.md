---
title: "Understanding Serialization in Java"
date: "2023-10-10"
tags: ["Java", "Serialization", "Programming", "Software Development"]
description: "A comprehensive guide to understanding serialization in Java, including key concepts and best practices."
languageCode: "en-CA"
---

# Understanding Serialization in Java

## What is _«Serialization»_?

**Serialization** is the process of converting data structures or object states into a linear sequence of bytes. This is done for the purposes of storage, transmission, or persistence of data. In Java, serialized objects can subsequently be deserialized, which means the original structure can be reconstructed.

According to the Java Object Serialization specification, there are two main methods of serialization: standard serialization via the `java.io.Serializable` interface and "enhanced" serialization using `java.io.Externalizable`.

Serialization allows for certain changes to the class definition. Key changes that can be managed automatically include:

-   Adding new fields to the class.
-   Changing fields from static to non-static.
-   Changing fields from transient to non-transient.

However, reversing these changes or removing fields necessitates additional handling based on the level of backward compatibility required.

[back to top](#Understanding-Serialization-in-Java)

## Describe the Serialization/Deserialization Process Using `Serializable`.

When the `Serializable` interface is utilized, the serialization algorithm employs reflection (using the Reflection API) to perform the following tasks:

-   Writing class metadata associated with the object to the stream (class name, `SerialVersionUID`, field identifiers).
-   Recursively writing the description of superclasses up to `java.lang.Object` (exclusive).
-   Writing primitive values of the serializable instance's fields, starting with the topmost superclass fields.
-   Recursively writing objects that are fields of the serializable object.

Notably, previously serialized objects do not get serialized again, allowing the algorithm to correctly handle cyclic references.

During the deserialization process, memory is allocated for the object, and its fields are populated with values from the stream; the object's constructor is not invoked. However, the no-argument constructor of any non-serializable parent class will be called, and its absence will lead to a deserialization error.

[back to top](#Understanding-Serialization-in-Java)

## How to Modify Default Serialization/Deserialization Behavior?

To customize serialization and deserialization:

-   Implement the `java.io.Externalizable` interface, which enables the use of custom serialization logic. The serialization and deserialization methods are defined in `writeExternal()` and `readExternal()`, respectively.
-   If the serializable object implements any of the following methods, the serialization mechanism will utilize these instead of the default methods:
    -   `writeObject()`: Writes the object to the stream.
    -   `readObject()`: Reads the object from the stream.
    -   `writeReplace()`: Replaces the object with an instance of another class before serialization.
    -   `readResolve()`: Allows replacing the object with another after deserialization.

[back to top](#Understanding-Serialization-in-Java)

## How to Exclude Fields from Serialization?

To manage serialization, you can use the `transient` keyword to exclude certain fields from the serialization process.

[back to top](#Understanding-Serialization-in-Java)

## What Does the `transient` Keyword Mean?

Fields marked with the `transient` modifier do not get serialized. Typically, these fields hold intermediate state information that may be simpler to compute, or references to objects that do not require serialization or cannot be serialized.

[back to top](#Understanding-Serialization-in-Java)

## How Do `static` and `final` Modifiers Affect Serialization?

In standard serialization, fields with the `static` modifier are not serialized. Therefore, their values remain unchanged after deserialization. Although it is technically possible to serialize and deserialize static fields using an `Externalizable` implementation, it is discouraged due to potential elusive bugs.

Fields marked as `final` are serialized like regular fields but must be initialized in the constructor. When using `Externalizable`, you cannot modify the value of `final` fields in `readExternal()`. Thus, to serialize objects with `final` fields, you should revert to standard serialization.

[back to top](#Understanding-Serialization-in-Java)

## How to Prevent Serialization?

To prevent automatic serialization, you can override `private` methods to create an exception condition `NotSerializableException`.

```java
private void writeObject(ObjectOutputStream out) throws IOException {
    throw new NotSerializableException();
}

private void readObject(ObjectInputStream in) throws IOException {
    throw new NotSerializableException();
}
```

Any attempt to write or read this object will now result in an exception being thrown.

[back to top](#Understanding-Serialization-in-Java)

## How to Create Custom Serialization Protocols?

To create a custom serialization protocol, you need to implement the `Externalizable` interface, which includes two methods:

```java
public void writeExternal(ObjectOutput out) throws IOException;
public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException;
```

[back to top](#Understanding-Serialization-in-Java)

## What is the Role of `serialVersionUID` in Serialization?

The `serialVersionUID` field is used to indicate the version of the serialized data. When you don't explicitly declare `serialVersionUID` in your class, the Java runtime generates one for you based on several metadata aspects of the class, such as field count and types, access modifiers, and implemented interfaces.

It's recommended to declare `serialVersionUID` explicitly; otherwise, dynamically generated values may change upon adding or removing class attributes, potentially leading to an `InvalidClassException` at runtime.

```java
private static final long serialVersionUID = 20161013L;
```

[back to top](#Understanding-Serialization-in-Java)

## When Should You Change the `serialVersionUID` Value?

You should change `serialVersionUID` when incompatible changes are made to the class, such as removing one of its attributes.

[back to top](#Understanding-Serialization-in-Java)

## What is the Problem with Serializing Singleton?

The issue with serializing a singleton is that it allows a second instance of the singleton to be created upon deserialization. To tackle this, you can either:

-   Explicitly prohibit serialization, or
-   Define a method with the signature `(default/public/private/protected/) Object readResolve() throws ObjectStreamException` to return a replacement object instead of the one being deserialized.

[back to top](#Understanding-Serialization-in-Java)

## What Are the Ways to Control the Values of Deserialized Objects?

To validate the values of deserialized objects, you can use the `ObjectInputValidation` interface with an overridden method `validateObject()`.

```java
// Invoking validateObject() after deserialization will throw InvalidObjectException if the age is out of bounds.
public class Person implements java.io.Serializable,
                               java.io.ObjectInputValidation {
    ...
    @Override
    public void validateObject() throws InvalidObjectException {
        if ((age < 39) || (age > 60))
            throw new InvalidObjectException("Invalid age");
    }
}
```

Additionally, there are methods for signing and encrypting that ensure the data has not been altered:

-   By implementing logic in `writeObject()` and `readObject()`.
-   By wrapping an object in `javax.crypto.SealedObject` and/or `java.security.SignedObject`. These classes are serializable, creating a sort of "gift wrap" around the original object. For encryption, a symmetric key must be created, which should be managed separately. Similarly, for data validation, the `SignedObject` class can be used, which also requires a separately managed symmetric key.

[back to top](#Understanding-Serialization-in-Java)

# Conclusion: Understanding Serialization in Java

Serialization is a crucial concept for Java developers, especially when it comes to the transmission and persistence of objects. Understanding how to effectively manage serialization, the implications of different modifiers, and how to handle custom scenarios can significantly improve your software development skills.

If you need further insights on serialization in Java, feel free to reach out!

For more information, explore the terms of serialization, the importance of `serialVersionUID`, and the potential pitfalls, especially with singletons, to ensure robust programming practices. This knowledge will empower you as a developer to make informed decisions regarding object serialization and deserialization in Java.
