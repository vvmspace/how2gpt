---
title: Understanding the JVM
date: 2023-10-15
tags: [JVM, Java, Programming, Technology]
---

## JVM

-   [What Does the JVM Do?](jvm.md#What-Does-the-JVM-Do)
-   [Classloader](jvm.md#Classloader)
-   [Runtime Data Areas](jvm.md#Runtime-Data-Areas)
-   [Frames](jvm.md#Frames)
-   [Execution Engine](jvm.md#Execution-Engine)
-   [Useful Links](jvm.md#Useful-Links)

## What Does the _JVM_ Do?

-   Loads, verifies, and executes bytecode;
-   Provides a runtime environment for executing bytecode;
-   Manages memory and performs garbage collection;

The Java Virtual Machine (JVM) is a mechanism that provides a runtime environment for managing Java code or applications.
It is an independent execution shell for code, enabling it to run on any operating system without the operating system affecting the executing program.

The JVM works with two types of data: primitive types and reference types.

**Primitive Types**

The JVM operates on primitive values (integers and floating-point numbers). Essentially, the JVM is a 32-bit machine.
The `long` and `double` types, which are 64-bit, are supported but occupy two memory units in a `frame's local` or operand stack, as each unit is 32 bits.
The `boolean`, `byte`, `short`, and `char` types extend the sign (except for `char`, which has zero extension) and function as 32-bit integers, just like `int` types.
Smaller types have only a few type-specific instructions for loading, storing, and type conversion.
A `boolean` value operates as an 8-bit `byte` value, with 0 representing **false** and 1 representing **true**.

**Reference Types and Values**

There are three types of reference types: class types, array types, and interface types. Their values are references to dynamically created instances of classes, arrays, or instances of classes that implement interfaces, respectively.

[Back to Table of Contents](#jvm)

## Classloader

The classloader is part of the JRE that dynamically loads Java classes into the JVM. Classes are typically loaded on demand. The Java execution system does not need to know about files and file systems due to the classloader. **Delegation is an important concept** performed by the classloader. The classloader is responsible for finding libraries, reading their contents, and loading the classes contained within those libraries.
This **loading** is usually done **"on demand"**, as it doesn't happen until the program calls for a class. **A class with a specific name can only be loaded once by a given classloader.**

When the JVM starts, three classloaders are used:

-   Bootstrap class loader
-   Extensions class loader
-   System class loader

**The Bootstrap Class Loader** loads the core Java libraries located in the `<JAVA_HOME>/jre/lib` folder. This loader is part of the JVM's core, written in native code.

**The Extensions Class Loader** loads code from extension directories (`<JAVA_HOME>/jre/lib/ext`, or any other directory specified by the system property `java.ext.dirs`).

**The System Class Loader** loads code found in `java.class.path`, corresponding to the `CLASSPATH` environment variable. This is implemented by the `sun.misc.Launcher$AppClassLoader`.

The classloader performs three main actions in strict order:

-   Loading: finds and imports the binary data for the type.
-   Linking: performs verification, preparation, and (optionally) resolution.
    -   Verification: ensures the correctness of the imported type.
    -   Preparation: allocates memory for class variables and initializes memory with default values.
    -   Resolution: converts symbolic references from type to direct references.
-   Initialization: invokes Java code that initializes class variables with their correct initial values.

**Custom Class Loaders**

Class loaders are written in Java. Thus, it's possible to create a custom class loader without delving into the intricate details of the JVM.
Every Java class loader has a parent class loader defined either upon the creation of a new class loader instance or as the default system class loader for the virtual machine.

This makes it possible to:

-   Load or unload classes at runtime (e.g., dynamically load libraries during execution, even from an HTTP resource).
    This is a significant feature for:
    -   Implementing scripting languages;
    -   Using bean builders;
    -   Adding custom extensions;
    -   Allowing multiple namespaces to communicate. For example, this is one of the foundations of CORBA / RMI protocols;
-   Change the way bytecode is loaded (e.g., encrypted Java class bytecode can be utilized);
-   Modify loaded bytecode (e.g., for aspect weaving during loading using aspect-oriented programming).

[Back to Table of Contents](#jvm)

## Runtime Data Areas

Runtime Data Areas. The JVM allocates various data areas during runtime, which are used during the execution of the program. Some data areas are created by the JVM at startup and are destroyed when it shuts down. Others are created for each thread and are destroyed when the thread is terminated.

**The PC Register (PCR)**

The Java Virtual Machine can support multiple threads of execution simultaneously. Each thread of the JVM has its own PC (program counter) register. At any point, each JVM thread executes code from one method, specifically the current method for that thread.
If this method is not native, the PC register contains the address of the currently executing instruction of the Java Virtual Machine.

In short: for one thread, there is one PCR, created when the thread starts. The PCR stores the address of the currently executing instruction of the JVM.

**Java Virtual Machine Stacks**

Each thread in the JVM has its own stack, created simultaneously with the thread. The stack in the JVM stores frames. Stacks in the JVM can have a fixed size or dynamically expand and shrink based on computation needs.

**Heap**

The JVM has a heap used by all threads of the Java Virtual Machine. The heap is a runtime data area from which memory is allocated for all class instances and arrays. The heap is created when the virtual machine starts. Storage for objects is reclaimed by an automatic memory management system (known as a garbage collector); objects are never explicitly freed.
The JVM does not assume any specific type of automatic memory management, and the management method can be chosen according to the developer's system requirements.
The heap can have a fixed size or can be expanded according to computation needs and can be contracted if a large heap becomes unnecessary. Memory for the heap does not need to be contiguous.

**Method Area**

The JVM has a method area that is shared among all threads. It holds structures for each class, such as a constant pool, field and method data, as well as the code for methods and constructors, including special methods utilized during class and instance initialization, and interface initialization.
Although the method area is logically part of the heap, simple implementations may not be garbage collected. The size of the method area can be fixed or can be expanded based on computation needs and can be contracted if a large method area becomes unnecessary.

**Run-Time Constant Pool**

A run-time constant pool exists for each class or interface at runtime and is represented by the constant_pool table in the \*.class file.
It contains several types of constants: from numeric literals known at compile time to references to methods and fields that must be resolved at runtime. The run-time constant pool functions similarly to the symbol table for traditional programming languages, though it contains a broader range of data than a typical symbol table. Each run-time constant pool is separate from the JVM's method area. The JVM creates a run-time constant pool along with class or interface creation.

**Native Method Stacks**

The implementation of the Java Virtual Machine may use conventional stacks, often referred to as "C stacks," to support native methods (methods written in languages other than Java).

[Back to Table of Contents](#jvm)

## Frames

A frame is used to store data and partial results, as well as to perform dynamic linking, return values for methods, and send exceptions. A new frame is created every time a method is invoked. A frame is destroyed when the method call completes, whether this completion is normal or abrupt (it generates an uncaught exception). Frames are allocated from the stack of the thread that creates the frame.
Each frame has its own array of local variables, its own operand stack, and a reference to the run-time constant pool of the current method's class.
The sizes of the local variable array and the operand stack are defined at compile time and provided along with the code for the method associated with the frame.
Thus, the size of the data structure for the frame depends solely on the implementation of the Java Virtual Machine, and memory for these structures can be allocated simultaneously when the method is called.

Only one frame is active at any point in a given control thread - the executing method, and this frame is called the current frame, with its method known as the current method. The class in which the current method is defined is the current class. Operations on local variables and the operand stack are typically performed with regard to the current frame.

The frame ceases to be current if its method calls another method or if its method completes. When a method is called, a new frame is created and becomes the current one when control transfers to the new method. When the method returns, the current frame passes the method call's result, if any, to the previous frame.
The current frame is then discarded as the previous frame becomes current. Note that the frame created by a thread is local to that thread and cannot be referenced by any other thread.

**Local Variables**

Each frame contains an array of variables known as its local variables. The length of the frame’s local variable array is defined at compile time and provided in the binary representation of the class or interface along with the code for the method associated with the frame.
A single local variable can store a value of type: boolean, byte, char, short, int, float, reference, or returnAddress.
A pair of local variables can store values of types: long or double.

Local variables are addressed via indexing. The index of the first local variable is zero.

A `long` or `double` type value occupies two consecutive local variables.

The JVM uses local variables to pass parameters when a method is called. When a class method is invoked, all parameters are passed in consecutive local variables, starting from local variable 0.
When an instance method is called, local variable 0 is always used to pass a reference to the object for which the instance method is invoked (this in Java). Any subsequent parameters are passed in consecutive local variables, starting from local variable 1.

**Operand Stacks**

Each frame contains a last-in-first-out (LIFO) stack known as the operand stack. The maximum depth of the operand stack for the frame is determined at compile time and is provided along with the code for the method associated with the frame.

The operand stack is empty at the creation of the frame that contains it. The JVM provides instructions to load constants or values from local variables or fields onto the operand stack. Other JVM instructions take operands from the operand stack, operate on them, and place the result back onto the operand stack. The operand stack is also used for preparing parameters to be passed to methods and for retrieving method results.

For example, the **iadd** instruction sums two `int` values. The operand stack requires that two `int` values be on top of the stack. The values are removed from the stack with the **pop** operation. They are added together and their sum is placed on the operand stack.

**Dynamic Linking**

Each frame contains a reference to the run-time constant pool for the type of the current method to support dynamic linking of method code.
Access to called methods and variables is performed via symbolic references from the class file. Dynamic linking converts these symbolic references to methods into specific method references, loading classes as necessary to resolve yet undefined symbols, and converts variable references into the corresponding offsets in the storage structures associated with the location of those variables during runtime.

Late binding of methods and variables makes it less likely that changes in other classes that the method uses will break this code.

**Normal Method Call Completion**

A method call completes normally if it does not raise an exception, either directly from the JVM or as a result of executing an explicit throw statement. If the current method call completes normally, a value may be returned to the calling method. This occurs when the called method executes one of the return instructions, the selection of which must match the return value type (if any).

In this case, the current frame is used to restore the state of the initiator, including its local variables and operand stack, with an appropriately incremented program counter of the initiator to skip the method call instruction. The execution generally continues in the frame of the calling method, placing the returned value (if any) onto the operand stack of that frame.

**Abrupt Method Call Completion**

A method call completes abruptly if executing an instruction of the JVM in the method raises an exception that is not handled within the method. Executing the **throw** statement also leads to an explicit throwing of an exception, and if the exception is not caught by the current method, it leads to an abrupt completion of the method call. A method call that completes abruptly never returns a value to its caller.

[Back to Table of Contents](#jvm)

## Execution Engine

The bytecode assigned to **run-time data areas** will be executed by the **execution engine**. The execution engine reads the bytecode and executes it piece by piece.

**Interpreter**

The interpreter quickly interprets the bytecode but executes it slowly. The drawback of the interpreter is that when one method is invoked multiple times, it requires a new interpretation each time.

**JIT Compiler**

The JIT (Just-In-Time) compiler eliminates the interpreter's weaknesses. The execution engine will utilize the interpreter's assistance while converting bytecode, but when it finds repeated code, it utilizes the JIT compiler, which compiles the entire bytecode and converts it into its own code.
This native code is then used directly for repeated method calls, enhancing system performance.

-   Intermediate Code Generator: Produces intermediate code.
-   Code Optimizer: Responsible for optimizing the above-generated intermediate code.
-   Target Code Generator: Responsible for generating machine code or native code.
-   Profiler: A special component responsible for finding hotspots, that is, whether a method is called multiple times or not.

**Garbage Collector**

[Back to Table of Contents](#jvm)

## Useful Links:

-   https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-2.html
-   https://www.developer.com/java/data/understanding-the-jvm-architecture.html
-   https://dzone.com/articles/understanding-jvm-internals

[Back to Table of Contents](#jvm)
