---
title: Interview Questions for Java 8
date: 2023-10-10
tags: [Java, Interview, Java 8, Functional Programming]
---

# Interview Questions for Java 8

-   [What new features were introduced in Java 8 and JDK 8?](#what-new-features-were-introduced-in-java-8-and-jdk-8)
-   [What is a _"lambda"_? What is the structure and unique characteristics of using a lambda expression?](#what-is-a-lambda-what-is-the-structure-and-unique-characteristics-of-using-a-lambda-expression)
-   [What variables can lambda expressions access?](#what-variables-can-lambda-expressions-access)
-   [How can you sort a list of strings using a lambda expression?](#how-can-you-sort-a-list-of-strings-using-a-lambda-expression)
-   [What is a "method reference"?](#what-is-a-method-reference)
-   [What types of method references do you know?](#what-types-of-method-references-do-you-know)
-   [Explain the expression `System.out::println`.](#explain-the-expression-systemoutprintln)
-   [What are "functional interfaces"?](#what-are-functional-interfaces)
-   [What are the purposes of functional interfaces `Function<T,R>`, `DoubleFunction<R>`, `IntFunction<R>`, and `LongFunction<R>`?](#what-are-the-purposes-of-functional-interfaces-functiontr-doublefunctionr-intfunctionr-and-longfunctionr)
-   [What are the purposes of functional interfaces `UnaryOperator<T>`, `DoubleUnaryOperator`, `IntUnaryOperator`, and `LongUnaryOperator`?](#what-are-the-purposes-of-functional-interfaces-unaryoperatort-doubleunaryoperator-intunaryoperator-and-longunaryoperator)
-   [What are the purposes of functional interfaces `BinaryOperator<T>`, `DoubleBinaryOperator`, `IntBinaryOperator`, and `LongBinaryOperator`?](#what-are-the-purposes-of-functional-interfaces-binaryoperatort-doublebinaryoperator-intbinaryoperator-and-longbinaryoperator)
-   [What are the purposes of functional interfaces `Predicate<T>`, `DoublePredicate`, `IntPredicate`, and `LongPredicate`?](#what-are-the-purposes-of-functional-interfaces-predicatet-doublepredicate-intpredicate-and-longpredicate)
-   [What are the purposes of functional interfaces `Consumer<T>`, `DoubleConsumer`, `IntConsumer`, and `LongConsumer`?](#what-are-the-purposes-of-functional-interfaces-consumert-doubleconsumer-intconsumer-and-longconsumer)
-   [What are the purposes of functional interfaces `Supplier<T>`, `BooleanSupplier`, `DoubleSupplier`, `IntSupplier`, and `LongSupplier`?](#what-are-the-purposes-of-functional-interfaces-suppliert-booleansupplier-doublesupplier-intsupplier-and-longsupplier)
-   [What is the purpose of the functional interface `BiConsumer<T,U>`?](#what-is-the-purpose-of-the-functional-interface-biconsumertu)
-   [What is the purpose of the functional interface `BiFunction<T,U,R>`?](#what-is-the-purpose-of-the-functional-interface-bifunctiontur)
-   [What is the purpose of the functional interface `BiPredicate<T,U>`?](#what-is-the-purpose-of-the-functional-interface-bipredicatetu)
-   [What are the functional interfaces of the type `_To_Function` useful for?](#what-are-the-functional-interfaces-of-the-type-t_function-useful-for)
-   [What are the purposes of functional interfaces `ToDoubleBiFunction<T,U>`, `ToIntBiFunction<T,U>`, and `ToLongBiFunction<T,U>`?](#what-are-the-purposes-of-functional-interfaces-todoublebifunctiontu-tointbifunctiontu-and-tolongbifunctiontu)
-   [What are the purposes of functional interfaces `ToDoubleFunction<T>`, `ToIntFunction<T>`, and `ToLongFunction<T>`?](#what-are-the-purposes-of-functional-interfaces-todoublefunctiont-tointfunctiont-and-tolongfunctiont)
-   [What are the purposes of functional interfaces `ObjDoubleConsumer<T>`, `ObjIntConsumer<T>`, and `ObjLongConsumer<T>`?](#what-are-the-purposes-of-functional-interfaces-objdoubleconsumert-objintconsumert-and-objlongconsumert)
-   [What is `StringJoiner`?](#what-is-stringjoiner)
-   [What are `default` methods in an interface?](#what-are-default-methods-in-an-interface)
-   [How do you call a `default` method of an interface within a class that implements the interface?](#how-do-you-call-a-default-method-of-an-interface-within-a-class-that-implements-the-interface)
-   [What is a `static` method in an interface?](#what-is-a-static-method-in-an-interface)
-   [How do you call a `static` method in an interface?](#how-do-you-call-a-static-method-in-an-interface)
-   [What is `Optional`?](#what-is-optional)
-   [What is `Stream`?](#what-is-stream)
-   [What are the existing ways to create a stream?](#what-are-the-existing-ways-to-create-a-stream)
-   [What is the difference between `Collection` and `Stream`?](#what-is-the-difference-between-collection-and-stream)
-   [What is the purpose of the `collect()` method in streams?](#what-is-the-purpose-of-the-collect-method-in-streams)
-   [What is the purpose of the `forEach()` and `forEachOrdered()` methods in streams?](#what-is-the-purpose-of-the-foreach-and-foreachordered-methods-in-streams)
-   [What are the purposes of `map()` and `mapToInt()`, `mapToDouble()`, `mapToLong()` methods in streams?](#what-are-the-purposes-of-map-and-maptoint-maptodouble-maptolong-methods-in-streams)
-   [What is the purpose of the `filter()` method in streams?](#what-is-the-purpose-of-the-filter-method-in-streams)
-   [What is the purpose of the `limit()` method in streams?](#what-is-the-purpose-of-the-limit-method-in-streams)
-   [What is the purpose of the `sorted()` method in streams?](#what-is-the-purpose-of-the-sorted-method-in-streams)
-   [What are the purposes of `flatMap()`, `flatMapToInt()`, `flatMapToDouble()`, `flatMapToLong()` methods in streams?](#what-are-the-purposes-of-flatmap-flatmaptoint-flatmaptodouble-flatmaptolong-methods-in-streams)
-   [Discuss parallel processing in Java 8.](#discuss-parallel-processing-in-java-8)
-   [What terminal methods for streams do you know?](#what-terminal-methods-for-streams-do-you-know)
-   [What intermediate methods for streams do you know?](#what-intermediate-methods-for-streams-do-you-know)
-   [How can you print 10 random numbers using `forEach()`?](#how-can-you-print-10-random-numbers-using-foreach)
-   [How can you print unique squares of numbers using the `map()` method?](#how-can-you-print-unique-squares-of-numbers-using-the-map-method)
-   [How can you print the count of empty strings using the `filter()` method?](#how-can-you-print-the-count-of-empty-strings-using-the-filter-method)
-   [How can you print 10 random numbers in ascending order?](#how-can-you-print-10-random-numbers-in-ascending-order)
-   [How can you find the maximum number in a set?](#how-can-you-find-the-maximum-number-in-a-set)
-   [How can you find the minimum number in a set?](#how-can-you-find-the-minimum-number-in-a-set)
-   [How can you get the sum of all numbers in a set?](#how-can-you-get-the-sum-of-all-numbers-in-a-set)
-   [How can you get the average of all numbers?](#how-can-you-get-the-average-of-all-numbers)
-   [What additional methods for working with associative arrays (maps) were introduced in Java 8?](#what-additional-methods-for-working-with-associative-arrays-maps-were-introduced-in-java-8)
-   [What is `LocalDateTime`?](#what-is-localdatetime)
-   [What is `ZonedDateTime`?](#what-is-zoneddatetime)
-   [How can you get the current date using the Date Time API from Java 8?](#how-can-you-get-the-current-date-using-the-date-time-api-from-java-8)
-   [How can you add 1 week, 1 month, 1 year, or 10 years to the current date using the Date Time API?](#how-can-you-add-1-week-1-month-1-year-or-10-years-to-the-current-date-using-the-date-time-api)
-   [How can you get the next Tuesday using the Date Time API?](#how-can-you-get-the-next-tuesday-using-the-date-time-api)
-   [How can you get the second Saturday of the current month using the Date Time API?](#how-can-you-get-the-second-saturday-of-the-current-month-using-the-date-time-api)
-   [How can you get the current time with millisecond precision using the Date Time API?](#how-can-you-get-the-current-time-with-millisecond-precision-using-the-date-time-api)
-   [How can you get the current time in local time with millisecond precision using the Date Time API?](#how-can-you-get-the-current-time-in-local-time-with-millisecond-precision-using-the-date-time-api)
-   [How can you define a repeatable annotation?](#how-can-you-define-a-repeatable-annotation)
-   [What is `Nashorn`?](#what-is-nashorn)
-   [What is `jjs`?](#what-is-jjs)
-   [What class was introduced in Java 8 for encoding/decoding data?](#what-class-was-introduced-in-java-8-for-encodingdecoding-data)
-   [How can you create a Base64 encoder and decoder?](#how-can-you-create-a-base64-encoder-and-decoder)

## What new features were introduced in Java 8 and JDK 8?

-   Default interface methods;
-   Lambda expressions;
-   Functional interfaces;
-   Method and constructor references;
-   Repeating annotations;
-   Type annotations;
-   Reflection for method parameters;
-   _Stream API_ for working with collections;
-   Parallel sorting of arrays;
-   New API for working with date and time;
-   New JavaScript engine _Nashorn_;
-   Several new classes for thread-safe operations;
-   New API for `Calendar` and `Locale`;
-   Support for _Unicode 6.2.0_;
-   Standard class for working with _Base64_;
-   Support for unsigned arithmetic;
-   Improved performance of `java.lang.String(byte[], *)` constructor and `java.lang.String.getBytes()` method;
-   A new implementation of `AccessController.doPrivileged` allowing a subset of privileges to be set without needing to check all other access levels;
-   _Password-based_ algorithms became more resilient;
-   Support for _SSL/TLS Server Name Indication (SNI)_ in _JSSE Server_;
-   Improved key storage (KeyStore);
-   Added _SHA-224_ algorithm;
-   The _JDBC - ODBC_ bridge was removed;
-   The _PermGen_ space was removed, and the way metadata for classes is stored was changed;
-   The ability to create profiles for the Java SE platform that includes not the entire platform but only part of it;
-   Tooling:
    -   Added `jjs` utility for using _JavaScript Nashorn_;
    -   The `java` command can run _JavaFX_ applications;
    -   Added `jdeps` utility for analyzing _.class_ files.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is a _"lambda"_? What is the structure and unique characteristics of using a lambda expression?

A **lambda** is a set of instructions that can be separated into a standalone variable and then called multiple times in different parts of the program.

The core of a lambda expression consists of a _lambda operator_, represented by the arrow `->`. This operator separates the lambda expression into two parts: the left part contains the parameter list of the expression, while the right part provides the body of the lambda expression, where all actions are executed.

A lambda expression doesn’t execute by itself; it forms an implementation of a method defined in a functional interface. Importantly, the functional interface must contain only one abstract method with no implementation.

```java
interface Operationable {
    int calculate(int x, int y);
}

public static void main(String[] args) {
    Operationable operation = (x, y) -> x + y;
    int result = operation.calculate(10, 20);
    System.out.println(result); //30
}
```

In effect, lambda expressions are a sort of shorthand for the anonymous inner classes previously used in Java.

-   _Deferred execution of lambda expressions_ - defined once in one part of the program, called as necessary, any number of times, and in any part of the program.

-   _Lambda expression parameters_ must be of the same type as the parameters of the method in the functional interface:

```java
operation = (int x, int y) -> x + y;
//When defining the lambda expression itself, the type of parameters may be omitted:
(x, y) -> x + y;
//If the method does not take any parameters, empty parentheses are written, for example:
() -> 30 + 20;
//If the method accepts only one parameter, parentheses can be omitted:
n -> n * n;
```

-   _Terminal lambda expressions_ do not have to return any value.

```java
interface Printable {
    void print(String s);
}

public static void main(String[] args) {
    Printable printer = s -> System.out.println(s);
    printer.print("Hello, world");
}
```

-   _Block lambda expressions_ are enclosed in curly braces. Block lambda expressions can utilize inner nested blocks, loops, `if`, `switch` constructs, create variables, and so forth. If a block lambda expression is expected to return a value, the `return` operator must be explicitly used:

```java
Operationable operation = (int x, int y) -> {
    if (y == 0) {
        return 0;
    }
    else {
        return x / y;
    }
};
```

-   _Passing a lambda expression as a parameter to a method_:

```java
interface Condition {
    boolean isAppropriate(int n);
}

private static int sum(int[] numbers, Condition condition) {
    int result = 0;
    for (int i : numbers) {
        if (condition.isAppropriate(i)) {
            result += i;
        }
    }
    return result;
}

public static void main(String[] args) {
    System.out.println(sum(new int[] {0, 1, 0, 3, 0, 5, 0, 7, 0, 9}, (n) -> n != 0));
}
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What variables can lambda expressions access?

The access to variables in the outer scope from a lambda expression is very similar to access from anonymous objects. You can refer to:

-   Immutable (effectively final - not necessarily marked as `final`) local variables;
-   Class fields;
-   Static variables.

Access to default methods in the implementing functional interface is forbidden within the lambda expression.

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you sort a list of strings using a lambda expression?

```java
public static List<String> sort(List<String> list){
    Collections.sort(list, (a, b) -> a.compareTo(b));
    return list;
}
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is a "method reference"?

If an existing method within a class already does everything that is needed, you can use the mechanism of **method reference** to directly pass this method. Such a reference is passed in the form of:

-   `ClassName::staticMethodName` for a static method;
-   `objectName::instanceMethodName` for an instance method;
-   `ClassName::new` for a constructor.

The result will be exactly the same as defining a lambda expression that calls that method.

```java
private interface Measurable {
    public int length(String string);
}

public static void main(String[] args) {
    Measurable a = String::length;
    System.out.println(a.length("abc"));
}
```

Method references are potentially more efficient than using lambda expressions. Additionally, they provide the compiler with better information about the type, and whenever there is an option to choose between using a method reference and using a lambda expression, method reference should always be preferred.

[Back to Table of Contents](#interview-questions-for-java-8)

## What types of method references do you know?

-   to static methods;
-   to instance methods;
-   to constructors.

[Back to Table of Contents](#interview-questions-for-java-8)

## Explain the expression `System.out::println`.

This expression illustrates the mechanism of _instance method reference_: passing a reference to the `println()` method of the static field `out` from the `System` class.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are "functional interfaces"?

A **functional interface** is an interface that defines only one abstract method.

To explicitly define an interface as functional, the annotation `@FunctionalInterface` is added, working like `@Override`. It denotes intention and prevents defining a second abstract method in the interface.

An interface can include any number of `default` methods and still remain a functional interface since `default` methods are not abstract.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `Function<T,R>`, `DoubleFunction<R>`, `IntFunction<R>`, and `LongFunction<R>`?

**`Function<T, R>`** is an interface used to implement a function that takes an instance of class `T` as input and returns an instance of class `R`.

Default methods can be used to build call chains (`compose`, `andThen`).

```java
Function<String, Integer> toInteger = Integer::valueOf;
Function<String, String> backToString = toInteger.andThen(String::valueOf);
backToString.apply("123");     // "123"
```

-   `DoubleFunction<R>` - a function that takes `Double` as input and returns an instance of class `R`;
-   `IntFunction<R>` - a function that takes `Integer` as input and returns an instance of class `R`;
-   `LongFunction<R>` - a function that takes `Long` as input and returns an instance of class `R`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `UnaryOperator<T>`, `DoubleUnaryOperator`, `IntUnaryOperator`, and `LongUnaryOperator`?

**`UnaryOperator<T>` (Unary Operator)** takes an object of type `T` as a parameter, performs operations on it, and returns the result as an object of type `T`:

```java
UnaryOperator<Integer> operator = x -> x * x;
System.out.println(operator.apply(5)); // 25
```

-   `DoubleUnaryOperator` - unary operator taking `Double` as input;
-   `IntUnaryOperator` - unary operator taking `Integer` as input;
-   `LongUnaryOperator` - unary operator taking `Long` as input.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `BinaryOperator<T>`, `DoubleBinaryOperator`, `IntBinaryOperator`, and `LongBinaryOperator`?

**`BinaryOperator<T>` (Binary Operator)** is an interface used to implement a function that takes two instances of class `T` as input and returns an instance of class `T`.

```java
BinaryOperator<Integer> operator = (a, b) -> a + b;
System.out.println(operator.apply(1, 2)); // 3
```

-   `DoubleBinaryOperator` - binary operator taking `Double` as input;
-   `IntBinaryOperator` - binary operator taking `Integer` as input;
-   `LongBinaryOperator` - binary operator taking `Long` as input.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `Predicate<T>`, `DoublePredicate`, `IntPredicate`, and `LongPredicate`?

**`Predicate<T>` (Predicate)** is an interface used to implement a function that takes an instance of class `T` as input and returns a value of type `boolean`.

The interface contains various default methods allowing for building complex conditions (`and`, `or`, `negate`).

```java
Predicate<String> predicate = (s) -> s.length() > 0;
predicate.test("foo"); // true
predicate.negate().test("foo"); // false
```

-   `DoublePredicate` - predicate taking `Double` as input;
-   `IntPredicate` - predicate taking `Integer` as input;
-   `LongPredicate` - predicate taking `Long` as input.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `Consumer<T>`, `DoubleConsumer`, `IntConsumer`, and `LongConsumer`?

**`Consumer<T>` (Consumer)** is an interface used to implement a function that takes an instance of class `T`, performs an action with it, and returns nothing.

```java
Consumer<String> hello = (name) -> System.out.println("Hello, " + name);
hello.accept("world");
```

-   `DoubleConsumer` - consumer taking `Double` as input;
-   `IntConsumer` - consumer taking `Integer` as input;
-   `LongConsumer` - consumer taking `Long` as input.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `Supplier<T>`, `BooleanSupplier`, `DoubleSupplier`, `IntSupplier`, and `LongSupplier`?

**`Supplier<T>` (Supplier)** is an interface used to implement a function that takes no input but returns a result of class `T`;

```java
Supplier<LocalDateTime> now = LocalDateTime::now;
now.get();
```

-   `DoubleSupplier` - supplier returning `Double`;
-   `IntSupplier` - supplier returning `Integer`;
-   `LongSupplier` - supplier returning `Long`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the functional interface `BiConsumer<T,U>`?

**`BiConsumer<T,U>`** represents an operation that accepts two arguments of classes `T` and `U`, performs an action with them, and returns nothing.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the functional interface `BiFunction<T,U,R>`?

**`BiFunction<T,U,R>`** represents an operation that takes two arguments of classes `T` and `U` and returns a result of class `R`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the functional interface `BiPredicate<T,U>`?

**`BiPredicate<T,U>`** represents an operation that takes two arguments of classes `T` and `U` and returns a result of type `boolean`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the functional interfaces of the type `_To_Function` useful for?

-   `DoubleToIntFunction` - operation that takes an argument of class `Double` and returns a result of type `Integer`;
-   `DoubleToLongFunction` - operation that takes an argument of class `Double` and returns a result of type `Long`;
-   `IntToDoubleFunction` - operation that takes an argument of class `Integer` and returns a result of type `Double`;
-   `IntToLongFunction` - operation that takes an argument of class `Integer` and returns a result of type `Long`;
-   `LongToDoubleFunction` - operation that takes an argument of class `Long` and returns a result of type `Double`;
-   `LongToIntFunction` - operation that takes an argument of class `Long` and returns a result of type `Integer`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `ToDoubleBiFunction<T,U>`, `ToIntBiFunction<T,U>`, and `ToLongBiFunction<T,U>`?

-   `ToDoubleBiFunction<T,U>` - operation that takes two arguments of classes `T` and `U` and returns a result of type `Double`;
-   `ToLongBiFunction<T,U>` - operation that takes two arguments of classes `T` and `U` and returns a result of type `Long`;
-   `ToIntBiFunction<T,U>` - operation that takes two arguments of classes `T` and `U` and returns a result of type `Integer`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `ToDoubleFunction<T>`, `ToIntFunction<T>`, and `ToLongFunction<T>`?

-   `ToDoubleFunction<T>` - operation that takes an argument of class `T` and returns a result of type `Double`;
-   `ToLongFunction<T>` - operation that takes an argument of class `T` and returns a result of type `Long`;
-   `ToIntFunction<T>` - operation that takes an argument of class `T` and returns a result of type `Integer`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of functional interfaces `ObjDoubleConsumer<T>`, `ObjIntConsumer<T>`, and `ObjLongConsumer<T>`?

-   `ObjDoubleConsumer<T>` - operation that takes two arguments of classes `T` and `Double`, performs an action with them, and returns nothing;
-   `ObjLongConsumer<T>` - operation that takes two arguments of classes `T` and `Long`, performs an action with them, and returns nothing;
-   `ObjIntConsumer<T>` - operation that takes two arguments of classes `T` and `Integer`, performs an action with them, and returns nothing.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is `StringJoiner`?

The `StringJoiner` class is used to create a sequence of strings, separated by a specified delimiter, with the ability to attach a prefix and suffix to the resulting string:

```java
StringJoiner joiner = new StringJoiner(".", "prefix-", "-suffix");
for (String s : "Hello the brave world".split(" ")) {
    joiner.add(s);
}
System.out.println(joiner); //prefix-Hello.the.brave.world-suffix
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What are `default` methods in an interface?

Java 8 allows adding non-abstract method implementations in an interface using the `default` keyword:

```java
interface Example {
    int process(int a);
    default void show() {
        System.out.println("default show()");
    }
}
```

-   If a class implements an interface, it may, but is not obliged to, implement the `default` methods already implemented in the interface. The class inherits the default implementation.
-   If a class implements multiple interfaces that have the same default method, the class must implement the method with the matching signature itself. This is similar when one interface has a default method, and in another, the same method is abstract - no default implementation is inherited by the class.
-   A default method cannot override a method from the `java.lang.Object` class.
-   They help implement interfaces without fearing disrupting the functionality of other classes.
-   They can avoid the creation of utility classes since all necessary methods can be represented within the interfaces themselves.
-   They allow classes to choose which method to override.
-   One of the main reasons for implementing default methods is to enable collections in Java 8 to use lambda expressions.

[Back to Table of Contents](#interview-questions-for-java-8)

## How do you call a `default` method of an interface within a class that implements the interface?

Using the `super` keyword along with the interface name:

```java
interface Paper {
    default void show() {
        System.out.println("default show()");
    }
}

class Licence implements Paper {
    public void show() {
        Paper.super.show();
    }
}
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is a `static` method in an interface?

Static methods in interfaces are similar to default methods, except they cannot be overridden in the classes that implement the interface.

-   Static methods in an interface are part of the interface and cannot be overridden for objects of the implementation class;
-   Methods from the `java.lang.Object` class cannot be overridden as static methods;
-   Static methods in an interface are used to provide helper methods, such as null checks, sorting collections, etc.

[Back to Table of Contents](#interview-questions-for-java-8)

## How do you call a `static` method in an interface?

Using the interface name:

```java
interface Paper {
    static void show() {
        System.out.println("static show()");
    }
}

class Licence {
    public void showPaper() {
        Paper.show();
    }
}
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is `Optional`?

An optional value in `Optional` is a container for an object that may or may not contain a `null` value. This wrapper is a convenient way to prevent `NullPointerException`, as it has some higher-order functions that eliminate the need for repetitive `if-null/notNull` checks:

```java
Optional<String> optional = Optional.of("hello");

optional.isPresent(); // true
optional.ifPresent(s -> System.out.println(s.length())); // 5
optional.get(); // "hello"
optional.orElse("ops..."); // "hello"
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is `Stream`?

The `java.util.Stream` interface represents a sequence of elements that you can perform various operations on.

Stream operations are either _intermediate_ or _terminal_. Terminal operations return a result of a specific type, while intermediate operations return the same stream. Therefore, you can build chains of several operations on the same stream.

A stream can have any number of calls to intermediate operations and ends with a terminal operation. All intermediate operations execute lazily, meaning that until a terminal operation is called, no actions really take place (similar to creating a `Thread` or `Runnable` object without calling `start()`).

Streams are created based on various sources, such as classes from `java.util.Collection`.

Associative arrays (maps), for example, `HashMap`, are not supported.

Stream operations can be performed sequentially or in parallel.

Streams cannot be reused. Once a terminal operation has been called, the stream closes.

In addition to universal object-oriented streams, there are specific types of streams for dealing with primitive data types `int`, `long`, and `double`: `IntStream`, `LongStream`, and `DoubleStream`. These primitive streams operate similarly to regular object streams but have the following distinctions:

-   They use specialized lambda expressions, e.g., `IntFunction` or `IntPredicate` instead of `Function` and `Predicate`;
-   They support additional terminal operations like `sum()`, `average()`, `mapToObj()`.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the existing ways to create a stream?

1. From a collection:

```java
Stream<String> fromCollection = Arrays.asList("x", "y", "z").stream();
```

2. From specific values:

```java
Stream<String> fromValues = Stream.of("x", "y", "z");
```

3. From an array:

```java
Stream<String> fromArray = Arrays.stream(new String[]{"x", "y", "z"});
```

4. From a file (each line in the file becomes a separate element in the stream):

```java
Stream<String> fromFile = Files.lines(Paths.get("input.txt"));
```

5. From a string:

```java
IntStream fromString = "0123456789".chars();
```

6. Using `Stream.builder()`:

```java
Stream<String> fromBuilder = Stream.builder().add("z").add("y").add("z").build();
```

7. Using `Stream.iterate()` (infinite):

```java
Stream<Integer> fromIterate = Stream.iterate(1, n -> n + 1);
```

8. Using `Stream.generate()` (infinite):

```java
Stream<String> fromGenerate = Stream.generate(() -> "0");
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the difference between `Collection` and `Stream`?

Collections allow you to work with elements individually, while streams do not, but instead provide the ability to perform functions over data as a whole.

It’s also important to note the fundamental concept: a `Collection` primarily represents a _Data Structure_. For instance, a `Set` not only stores elements but embodies the idea of a collection with unique elements, whereas a `Stream` is primarily an abstraction necessary for implementing a _pipeline of computations_, hence the results of a pipeline yield certain _Data Structures_ or results of checks/searches, etc.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the `collect()` method in streams?

The `collect()` method is a terminal operation that is used to represent the result as a collection or some other data structure.

`collect()` takes a `Collector<SourceType, AccumulatorType, ResultType>` as input, which comprises four stages: _supplier_ - initializing the accumulator, _accumulator_ - processing each element, _combiner_ - combining two accumulators during parallel execution, _[finisher]_ - an optional method for final processing of the accumulator. In Java 8, several common collectors have been implemented in the `Collectors` class:

-   `toList()`, `toCollection()`, `toSet()` - represent the stream as a list, collection, or set;
-   `toConcurrentMap()`, `toMap()` - allow for transforming the stream into a `Map`;
-   `averagingInt()`, `averagingDouble()`, `averagingLong()` - return the average value;
-   `summingInt()`, `summingDouble()`, `summingLong()` - return the sum;
-   `summarizingInt()`, `summarizingDouble()`, `summarizingLong()` - return `SummaryStatistics` with various aggregate values;
-   `partitioningBy()` - splits the collection into two parts based on adherence to a condition and returns them as `Map<Boolean, List>`;
-   `groupingBy()` - splits the collection into several parts and returns `Map<N, List<T>>`;
-   `mapping()` - additional value transformations for complex `Collector`-s.

It is also possible to create a custom collector via `Collector.of()`:

```java
Collector<String, List<String>, List<String>> toList = Collector.of(
    ArrayList::new,
    List::add,
    (l1, l2) -> { l1.addAll(l2); return l1; }
);
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the `forEach()` and `forEachOrdered()` methods in streams?

-   The `forEach()` method applies a function to each object of the stream, without guaranteeing order during parallel execution;
-   The `forEachOrdered()` method applies a function to each object of the stream while maintaining the order of elements.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of `map()` and `mapToInt()`, `mapToDouble()`, `mapToLong()` methods in streams?

The `map()` method is an intermediate operation that transforms each element of the stream in a specified way.

`mapToInt()`, `mapToDouble()`, `mapToLong()` are analogous to `map()` but return the corresponding numeric stream (i.e., a stream composed of numeric primitives):

```java
Stream
    .of("12", "22", "4", "444", "123")
    .mapToInt(Integer::parseInt)
    .toArray(); //[12, 22, 4, 444, 123]
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the `filter()` method in streams?

The `filter()` method is an intermediate operation that takes a predicate which filters out all elements, returning only those that conform to the condition.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the `limit()` method in streams?

The `limit()` method is an intermediate operation that allows for limiting the selection to a specified number of leading elements.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is the purpose of the `sorted()` method in streams?

The `sorted()` method is an intermediate operation that allows for sorting values either in natural order or by specifying a `Comparator`.

The order of elements in the original collection remains unchanged - `sorted()` merely creates a sorted representation of it.

[Back to Table of Contents](#interview-questions-for-java-8)

## What are the purposes of `flatMap()`, `flatMapToInt()`, `flatMapToDouble()`, `flatMapToLong()` methods in streams?

The `flatMap()` method is similar to `map`, but it can create multiple objects from a single element. Therefore, each object will be transformed into zero, one, or multiple other objects supported by the stream. The most straightforward use case of this operation is transforming container elements with functions that return containers.

```java
Stream
    .of("H e l l o", "w o r l d !")
    .flatMap((p) -> Arrays.stream(p.split(" ")))
    .toArray(String[]::new);//["H", "e", "l", "l", "o", "w", "o", "r", "l", "d", "!"]
```

`flatMapToInt()`, `flatMapToDouble()`, `flatMapToLong()` are analogous to `flatMap()`, returning the corresponding numeric stream.

[Back to Table of Contents](#interview-questions-for-java-8)

## Discuss parallel processing in Java 8.

Streams can be sequential or parallel. Operations on sequential streams are executed in a single processor thread, while parallel streams utilize multiple processor threads. Parallel streams use a common `ForkJoinPool` accessible via the static `ForkJoinPool.commonPool()` method. If the environment is not multi-core, the stream will execute sequentially. Essentially, using parallel streams means that data in the streams will be divided into parts, each part processed on a separate processor core, and then those parts are merged back together, and terminal operations are performed on them.

You can also create a parallel stream from a collection using the `parallelStream()` method of the `Collection` interface.

To make a regular sequential stream parallel, call the `parallel()` method on the `Stream` object. The `isParallel()` method allows you to check whether the stream is parallel.

Using the `parallel()` and `sequential()` methods enables you to determine which operations can be parallelized and which should remain sequential. It is also possible to convert any sequential stream into a parallel one and vice versa:

```java
collection
.stream()
.peek(...) // this operation is sequential
.parallel()
.map(...) // this operation can run in parallel,
.sequential()
.reduce(...) // this operation is sequential again
```

Typically, elements are passed to the stream in the order in which they are defined in the source data. When working with parallel streams, the system retains the sequence of elements. An exception is the `forEach()` method, which may output elements in an arbitrary order. To maintain the sequence, the `forEachOrdered()` method must be employed.

Criteria that can influence performance in parallel streams include:

-   Size of data - the larger the data, the more challenging it will be to first separate the data and then combine it.
-   Number of processor cores. Theoretically, the more cores on the machine, the faster the program will run. If only one core is present, there’s no point in using parallel streams.
-   Simpler data structures will allow operations to proceed faster with streams. For instance, data from `ArrayList` is easy to use because its structure assumes the sequence of unrelated data. In contrast, a `LinkedList` is not an optimal option since, in a sequential list, all elements are linked to previous/subsequent ones. Hence, such data is difficult to parallelize.
-   Operations over primitive types will be performed faster than over class objects.
-   It is highly inadvisable to use parallel streams for long operations (like network connections) since all parallel streams work with a single ForkJoinPool; long operations may halt the work of all parallel streams in the JVM due to a lack of available threads in the pool. Therefore, parallel streams should only be used for shorter operations, where timing is in milliseconds, but not for those that may take seconds or even minutes.
-   Retaining order in parallel streams increases costs during execution. If order is unimportant, you have the chance to disable order retention and thus increase performance using the intermediate operation `unordered()`:

```java
collection.parallelStream()
    .sorted()
    .unordered()
    .collect(Collectors.toList());
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What terminal methods for streams do you know?

-   `findFirst()` returns the first element;
-   `findAny()` returns any suitable element;
-   `collect()` presents results in the form of collections and other data structures;
-   `count()` returns the number of elements;
-   `anyMatch()` returns `true` if the condition is met for at least one element;
-   `noneMatch()` returns `true` if the condition is not met for any element;
-   `allMatch()` returns `true` if the condition is met for all elements;
-   `min()` returns the minimum element using `Comparator` as the condition;
-   `max()` returns the maximum element using `Comparator` as the condition;
-   `forEach()` applies a function to each object (the order is not guaranteed during parallel execution);
-   `forEachOrdered()` applies a function to each object while maintaining element order;
-   `toArray()` returns an array of values;
-   `reduce()` allows for executing aggregate functions and returning a single result.

For numeric streams, additional methods are available:

-   `sum()` returns the sum of all numbers;
-   `average()` returns the average of all numbers.

[Back to Table of Contents](#interview-questions-for-java-8)

## What intermediate methods for streams do you know?

-   `filter()` filters entries, returning only those entries that adhere to the condition;
-   `skip()` allows you to skip a specified number of elements at the beginning;
-   `distinct()` returns a stream without duplicates (based on `equals()`);
-   `map()` transforms each element;
-   `peek()` returns the same stream, applying a function to each element;
-   `limit()` allows you to restrict the selection to a specified number of leading elements;
-   `sorted()` allows you to sort values either in natural order or by specifying a `Comparator`;
-   `mapToInt()`, `mapToDouble()`, `mapToLong()` - analogs of `map()` returning streams of numeric primitives;
-   `flatMap()`, `flatMapToInt()`, `flatMapToDouble()`, `flatMapToLong()` - similar to `map()`, but can create multiple objects from a single element.

For numeric streams, an additional method `mapToObj()` is available, which transforms a numeric stream back into an object stream.

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you print 10 random numbers using `forEach()`?

```java
(new Random())
    .ints()
    .limit(10)
    .forEach(System.out::println);
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you print unique squares of numbers using the `map()` method?

```java
Stream
    .of(1, 2, 3, 2, 1)
    .map(s -> s * s)
    .distinct()
    .forEach(System.out::println);
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you print the count of empty strings using the `filter()` method?

```java
System.out.println(
    Stream
        .of("Hello", "", ", ", "world", "!")
        .filter(String::isEmpty)
        .count());
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you print 10 random numbers in ascending order?

```java
(new Random())
    .ints()
    .limit(10)
    .sorted()
    .forEach(System.out::println);
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you find the maximum number in a set?

```java
Stream
    .of(5, 3, 4, 55, 2)
    .mapToInt(a -> a)
    .max()
    .getAsInt(); //55
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you find the minimum number in a set?

```java
Stream
    .of(5, 3, 4, 55, 2)
    .mapToInt(a -> a)
    .min()
    .getAsInt(); //2
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you get the sum of all numbers in a set?

```java
Stream
    .of(5, 3, 4, 55, 2)
    .mapToInt()
    .sum(); //69
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you get the average of all numbers?

```java
Stream
    .of(5, 3, 4, 55, 2)
    .mapToInt(a -> a)
    .average()
    .getAsDouble(); //13.8
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What additional methods for working with associative arrays (maps) were introduced in Java 8?

-   `putIfAbsent()` adds a key-value pair only if the key was absent:

`map.putIfAbsent("a", "Aa");`

-   `forEach()` takes a function that performs actions on each element:

`map.forEach((k, v) -> System.out.println(v));`

-   `compute()` creates or updates the current value based on calculations (it can use both the key and the current value):

`map.compute("a", (k, v) -> String.valueOf(k).concat(v)); //["a", "aAa"]`

-   `computeIfPresent()` if the key exists, updates the current value based on calculations (it can use both the key and the current value):

`map.computeIfPresent("a", (k, v) -> k.concat(v));`

-   `computeIfAbsent()` if the key is absent, it creates it with a value that is computed (it can use the key):

`map.computeIfAbsent("a", k -> "A".concat(k)); //["a","Aa"]`

-   `getOrDefault()` returns the specified default value if the key is absent:

`map.getOrDefault("a", "not found");`

-   `merge()` takes a key, value, and a function that combines the passed and current values. If there’s no value under the specified key, it writes the passed value.

`map.merge("a", "z", (value, newValue) -> value.concat(newValue)); //["a","Aaz"]`

[Back to Table of Contents](#interview-questions-for-java-8)

## What is `LocalDateTime`?

`LocalDateTime` combines `LocaleDate` and `LocalTime`, containing both date and time in the ISO-8601 calendar system without being bound to a time zone. The time is stored with precision up to nanoseconds. It contains many convenient methods, such as plusMinutes, plusHours, isAfter, toSecondOfDay, etc.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is `ZonedDateTime`?

`java.time.ZonedDateTime` is analogous to `java.util.Calendar`, a class with the most complete range of information about the time context in the ISO-8601 calendar system. It includes a time zone, hence all operations with time shifts conducted by this class consider it.

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you get the current date using the Date Time API from Java 8?

```java
LocalDate.now();
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you add 1 week, 1 month, 1 year, or 10 years to the current date using the Date Time API?

```java
LocalDate.now().plusWeeks(1);
LocalDate.now().plusMonths(1);
LocalDate.now().plusYears(1);
LocalDate.now().plus(1, ChronoUnit.DECADES);
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you get the next Tuesday using the Date Time API?

```java
LocalDate.now().with(TemporalAdjusters.next(DayOfWeek.TUESDAY));
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you get the second Saturday of the current month using the Date Time API?

```java
LocalDate
    .of(LocalDate.now().getYear(), LocalDate.now().getMonth(), 1)
    .with(TemporalAdjusters.nextOrSame(DayOfWeek.SATURDAY))
    .with(TemporalAdjusters.next(DayOfWeek.SATURDAY));
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you get the current time with millisecond precision using the Date Time API?

```java
new Date().toInstant();
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you get the current time in local time with millisecond precision using the Date Time API?

```java
LocalDateTime.ofInstant(new Date().toInstant(), ZoneId.systemDefault());
```

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you define a repeatable annotation?

To define a repeatable annotation, you need to create a container annotation for a list of repeatable annotations and designate the repeatable meta-annotation with `@Repeatable`:

```java
@interface Schedulers
{
    Scheduler[] value();
}

@Repeatable(Schedulers.class)
@interface Scheduler
{
    String birthday() default "Jan 8 1935";
}
```

[Back to Table of Contents](#interview-questions-for-java-8)

## What is `Nashorn`?

**Nashorn** is a JavaScript engine developed in Java by Oracle. Its purpose is to allow the embedding of JavaScript code within Java applications. Compared to _Rhino_, maintained by the Mozilla Foundation, Nashorn offers 2 to 10 times higher performance since it compiles code and directly hands over bytecode to the Java Virtual Machine in memory. Nashorn can compile JavaScript code and generate Java classes, which are loaded via a special class loader. It is also possible to call Java code directly from JavaScript.

[Back to Table of Contents](#interview-questions-for-java-8)

## What is `jjs`?

`jjs` is a command-line utility that allows you to run JavaScript programs directly from the console.

[Back to Table of Contents](#interview-questions-for-java-8)

## What class was introduced in Java 8 for encoding/decoding data?

`Base64` is a thread-safe class that implements a data encoder and decoder using the base64 encoding scheme according to _RFC 4648_ and _RFC 2045_.

Base64 contains 6 main methods:

`getEncoder()`/`getDecoder()` - returns the base64 encoder/decoder that corresponds to the _RFC 4648_ standard;
`getUrlEncoder()`/`getUrlDecoder()` - returns a URL-safe base64 encoder/decoder, corresponding to the _RFC 4648_ standard;
`getMimeEncoder()`/`getMimeDecoder()` - returns a MIME encoder/decoder that corresponds to the _RFC 2045_ standard.

[Back to Table of Contents](#interview-questions-for-java-8)

## How can you create a Base64 encoder and decoder?

```java
// Encode
String b64 = Base64.getEncoder().encodeToString("input".getBytes("utf-8")); //aW5wdXQ==
// Decode
new String(Base64.getDecoder().decode("aW5wdXQ=="), "utf-8"); //input
```

[Back to Table of Contents](#interview-questions-for-java-8)

# Sources

-   [Habr - New Features in Java 8](https://habrahabr.ru/post/216431/)
-   [Habr - Java Developer Cheat Sheet 4. Java Stream API](https://habrahabr.ru/company/luxoft/blog/270383/)
-   [METANIT.COM](http://metanit.com/java/tutorial/9.1.php)
-   [javadevblog.com](http://javadevblog.com/interfejsy-v-java-8-staticheskie-metody-metody-po-umolchaniyu-funktsional-ny-e-interfejsy.html)

[Back to Table of Contents](#interview-questions-for-java-8)
