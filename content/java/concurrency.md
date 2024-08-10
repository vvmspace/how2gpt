---
title: Java Concurrency Interview Questions
date: 2023-10-01
tags: [Java, Multithreading, Interview, Concurrency]
---

# Interview Questions

## Multithreading

-   [Tell us about the Java memory model?](#Tell-us-about-the-java-memory-model)
-   [What is "thread safety"?](#What-is-thread-safety)
-   [What is the difference between "concurrency" and "parallelism"?](#What-is-the-difference-between-concurrency-and-parallelism)
-   [What is "cooperative multitasking"? What type of multitasking does Java use? What is the reasoning behind this choice?](#What-is-cooperative-multitasking-What-type-of-multitasking-does-java-use-What-is-the-reasoning-behind-this-choice)
-   [What are _ordering_, _as-if-serial semantics_, _sequential consistency_, _visibility_, _atomicity_, _happens-before_, _mutual exclusion_, _safe publication_?](#What-are-ordering-as-if-serial-semantics-sequential-consistency-visibility-atomicity-happens-before-mutual-exclusion-safe-publication)
-   [What is the difference between a process and a thread?](#What-is-the-difference-between-a-process-and-a-thread)
-   [What are "green threads," and does Java have them?](#What-are-green-threads-and-does-java-have-them)
-   [How can a thread be created?](#How-can-a-thread-be-created)
-   [What are the differences between `Thread` and `Runnable`?](#What-are-the-differences-between-Thread-and-Runnable)
-   [What is the difference between the `start()` and `run()` methods?](#What-is-the-difference-between-the-start-and-run-methods)
-   [How can you forcibly start a thread?](#How-can-you-forcibly-start-a-thread)
-   [What is a "monitor" in Java?](#What-is-a-monitor-in-java)
-   [Define the concept of "synchronization."](#Define-the-concept-of-synchronization)
-   [What synchronization methods exist in Java?](#What-synchronization-methods-exist-in-java)
-   [What states can a thread be in?](#What-states-can-a-thread-be-in)
-   [Can new instances of a class be created while a `static synchronized` method is executing?](#Can-new-instances-of-a-class-be-created-while-a-static-synchronized-method-is-executing)
-   [Why would a `private` mutex be necessary?](#Why-would-a-private-mutex-be-necessary)
-   [How do `wait()` and `notify()`/`notifyAll()` methods work?](#How-do-wait-and-notifynotifyall-methods-work)
-   [What is the difference between `notify()` and `notifyAll()`?](#What-is-the-difference-between-notify-and-notifyall)
-   [Why are the `wait()` and `notify()` methods called only in a synchronized block?](#Why-are-the-wait-and-notify-methods-called-only-in-a-synchronized-block)
-   [What is the difference between the `wait()` method with a parameter and without it?](#What-is-the-difference-between-the-wait-method-with-a-parameter-and-without-it)
-   [What are the differences between the `Thread.sleep()` and `Thread.yield()` methods?](#What-are-the-differences-between-the-threadsleep-and-threadyield-methods)
-   [How does the `Thread.join()` method work?](#How-does-the-Threadjoin-method-work)
-   [What is a _deadlock_?](#What-is-a-deadlock)
-   [What is a _livelock_?](#What-is-a-livelock)
-   [How can you check if a thread holds the monitor of a certain resource?](#How-can-you-check-if-a-thread-holds-the-monitor-of-a-certain-resource)
-   [On which object does synchronization occur when calling a `static synchronized` method?](#On-which-object-does-synchronization-occur-when-calling-a-static-synchronized-method)
-   [What is the purpose of the keywords `volatile`, `synchronized`, `transient`, `native`?](#What-is-the-purpose-of-the-keywords-volatile-synchronized-transient-native)
-   [What are the differences between `volatile` and _Atomic_ variables?](#What-are-the-differences-between-volatile-and-atomic-variables)
-   [What are the differences between `java.util.concurrent.Atomic*.compareAndSwap()` and `java.util.concurrent.Atomic*.weakCompareAndSwap()`?](#What-are-the-differences-between-javautilconcurrentatomiccompareandswap-and-javautilconcurrentatomicweakcompareandswap)
-   [What does _"thread priority"_ mean?](#What-does-thread-priority-mean)
-   [What are _"daemon threads"_?](#What-are-daemon-threads)
-   [Can the main thread of a program be a daemon?](#Can-the-main-thread-of-a-program-be-a-daemon)
-   [What does it mean to _"sleep"_ a thread?](#What-does-it-mean-to-sleep-a-thread)
-   [What are the differences between the `Runnable` and `Callable` interfaces?](#What-are-the-differences-between-the-Runnable-and-Callable-interfaces)
-   [What is `FutureTask`?](#What-is-FutureTask)
-   [What are the differences between `CyclicBarrier` and `CountDownLatch`?](#What-are-the-differences-between-CyclicBarrier-and-CountDownLatch)
-   [What is a _race condition_?](#What-is-a-race-condition)
-   [Is there a way to solve the _race condition_ problem?](#Is-there-a-way-to-solve-the-race-condition-problem)
-   [How can you stop a thread?](#How-can-you-stop-a-thread)
-   [Why is it not recommended to use the `Thread.stop()` method?](#Why-is-it-not-recommended-to-use-the-Threadstop-method)
-   [What happens when an exception is thrown in a thread?](#What-happens-when-an-exception-is-thrown-in-a-thread)
-   [What is the difference between `interrupted()` and `isInterrupted()`?](#What-is-the-difference-between-interrupted-and-isinterrupted)
-   [What is a _thread pool_?](#What-is-a-thread-pool)
-   [What should the size of a thread pool be?](#What-should-the-size-of-a-thread-pool-be)
-   [What happens if the thread pool queue is already full, but a new task is submitted?](#What-happens-if-the-thread-pool-queue-is-already-full-but-a-new-task-is-submitted)
-   [What is the difference between the `submit()` and `execute()` methods of a thread pool?](#What-is-the-difference-between-the-submit-and-execute-methods-of-a-thread-pool)
-   [What are the differences between a stack and a heap in terms of multithreading?](#What-are-the-differences-between-a-stack-and-a-heap-in-terms-of-multithreading)
-   [How can you share data between two threads?](#How-can-you-share-data-between-two-threads)
-   [Which JVM startup option is used to control the size of a thread's stack?](#Which-JVM-startup-option-is-used-to-control-the-size-of-a-threads-stack)
-   [How do you get a thread dump?](#How-do-you-get-a-thread-dump)
-   [What is a _ThreadLocal variable_?](#What-is-a-ThreadLocal-variable)
-   [What are the differences between `synchronized` and `ReentrantLock`?](#What-are-the-differences-between-synchronized-and-ReentrantLock)
-   [What is `ReadWriteLock`?](#What-is-ReadWriteLock)
-   [What is a _blocking method_?](#What-is-a-blocking-method)
-   [What is the _Fork/Join framework_?](#What-is-the-ForkJoin-framework)
-   [What is a `Semaphore`?](#What-is-a-Semaphore)
-   [What is a _double-checked locking Singleton_?](#What-is-a-double-checked-locking-Singleton)
-   [How do you create a thread-safe Singleton?](#How-do-you-create-a-thread-safe-Singleton)
-   [What are the benefits of immutable objects?](#What-are-the-benefits-of-immutable-objects)
-   [What is _busy spin_?](#What-is-busy-spin)
-   [List the principles you follow in multithreaded programming.](#List-the-principles-you-follow-in-multithreaded-programming)
-   [Which of the following statements about threads is incorrect?](#Which-of-the-following-statements-about-threads-is-incorrect)
-   [Given three threads T1, T2, and T3. How to implement execution in the sequence T1, T2, T3?](#Given-three-threads-T1-T2-and-T3-How-to-implement-execution-in-the-sequence-T1-T2-T3)
-   [Write a minimal non-blocking stack (only two methods — `push()` and `pop()`).](#Write-a-minimal-non-blocking-stack-only-two-methods----push-and-pop)
-   [Write a minimal non-blocking stack (only two methods — `push()` and `pop()`) using `Semaphore`.](#Write-a-minimal-non-blocking-stack-only-two-methods----push-and-pop-using-Semaphore)
-   [Write a minimal non-blocking ArrayList (only four methods — `add()`, `get()`, `remove()`, `size()`).](#Write-a-minimal-non-blocking-ArrayList-only-four-methods----add-get-remove-size)
-   [Write a thread-safe implementation of a class with a non-blocking method `BigInteger next()` that returns elements of the sequence: `[1, 2, 4, 8, 16, ...]`.](#Write-a-thread-safe-implementation-of-a-class-with-a-non-blocking-method-BigInteger-next-that-returns-elements-of-the-sequence-1-2-4-8-16-)
-   [Write the simplest multithreaded bounded buffer using `synchronized`.](#Write-the-simplest-multithreaded-bounded-buffer-using-synchronized)
-   [Write the simplest multithreaded bounded buffer using `ReentrantLock`.](#Write-the-simplest-multithreaded-bounded-buffer-using-ReentrantLock)

## Tell us about the Java memory model?

The **Java Memory Model (JMM)** describes the behavior of threads in the Java runtime environment. It is part of the semantics of the Java language, a set of rules that define the execution of multithreaded programs and the rules by which threads can interact with each other through main memory.

Formally, the memory model defines a set of actions for inter-thread interaction (these actions include, in particular, reading and writing a variable, acquiring and releasing a monitor, reading and writing to a volatile variable, starting a new thread), and it also defines the relationship between these actions - the _happens-before_ relationship - an abstraction that indicates if operation _X_ is happens-before operation _Y_, then all code following operation _Y_ performed in one thread will see all changes made by another thread before operation _X_.

Several fundamental rules govern the happens-before relationship:

-   Within a single thread, any operation happens-before any operation that follows it in the source code;
-   Unlocking a monitor happens-before locking the same monitor;
-   Exiting a `synchronized` block/method happens-before entering a `synchronized` block/method on the same monitor;
-   Writing to a `volatile` field happens-before reading that same `volatile` field;
-   The completion of the `run()` method of a `Thread` instance happens-before exiting the `join()` method or returning `false` from the `isAlive()` method of that same thread instance;
-   Calling the `start()` method of a `Thread` instance happens-before the beginning of the `run()` method of that same thread instance;
-   The completion of a constructor happens-before entering the `finalize()` method of that class;
-   Calling the `interrupt()` method on a thread happens-before the thread detects that this method was called either by throwing an `InterruptedException` or by using the `isInterrupted()` or `interrupted()` methods.
-   The happens-before relationship is transitive; that is, if _X_ happens-before _Y_, and _Y_ happens-before _Z_, then _X_ happens-before _Z_.
-   Releasing/locking a monitor and writing/reading to a `volatile` variable are related by the happens-before relationship only if the operations are performed on the same instance of an object.
-   The happens-before relationship involves only two threads; nothing can be said about the behavior of other threads until each of them reaches a happens-before relationship with another thread.

Several main areas relevant to the memory model can be identified:

_Visibility._ One thread may temporarily hold the value of some fields not in main memory, but in registers or the local cache of the processor, so another thread running on another processor, reading from main memory, may not see the latest changes to the field. Conversely, if a thread has been working with registers and local caches for a period, reading data from there, it may not immediately see changes made by another thread in main memory.

The following Java keywords relate to visibility: `synchronized`, `volatile`, `final`.

From the Java perspective, all variables (except for local variables declared inside a method) are stored in main memory, which is accessible to all threads. Moreover, each thread has a local working memory where it stores copies of the variables it works with, and during program execution, the thread works only with these copies. It should be noted that this description does not impose a requirement for implementation, it is merely a model that explains program behavior; thus, local memory does not necessarily have to be cache memory; it can be processor registers, or threads may not even have local memory.

When entering a `synchronized` method or block, a thread updates the contents of local memory, and when exiting a `synchronized` method or block, the thread writes changes made in local memory back to main memory. This behavior of `synchronized` methods and blocks follows from the rules for the happens-before relationship: since all operations on memory occur before the monitor is released and the monitor's release occurs before the monitor is acquired, all memory operations made by a thread before leaving the `synchronized` block must be visible to any thread that enters the `synchronized` block for the same monitor. It is very important that this rule works only if threads synchronize using the same monitor!

Regarding `volatile` variables, writing to such variables occurs in main memory, bypassing local memory, and reading a `volatile` variable is also performed from main memory, meaning the variable value cannot be stored in registers or local memory of the thread, and the read operation of this variable will reliably return the last value written to it.

Additionally, the memory model defines extra semantics for the `final` keyword regarding visibility: after an object has been correctly constructed, any thread can see the values of its `final` fields without further synchronization. "Correctly constructed" means that the reference to the object being instantiated must not be accessed until the constructor has completed. Such semantics for the `final` keyword enable the creation of immutable objects containing only `final` fields; such objects can be freely passed between threads without synchronization guarantees being required during the transfer.

One issue related to `final` fields is that the implementation allows changing the values of such fields after the object has been created (this can happen, for example, using reflection). If the value of a `final` field is a constant known at compile time, changes to such a field may have no effect, as accesses to this variable may have been replaced by the compiler with the constant. The specification also allows for other optimizations related to `final` fields; for example, operations reading a `final` variable may be reordered with operations that could potentially modify such a variable. Therefore, it is recommended to change `final` fields of an object only within the constructor; otherwise, the behavior is unspecified.

_Reordering._ To increase performance, the processor/compiler may rearrange some instructions/operations. Or rather, from the perspective of a thread observing the execution of operations in another thread, the operations can be executed out of the order they appear in the source code. The same effect can be observed when one thread places results of the first operation in a register or local cache, while the result of the second operation goes directly into main memory. Then, when the second thread accesses main memory, it may see the result of the second operation before seeing the result of the first operation, when all registers or caches synchronize with main memory. Another reason for reordering could be that the processor might decide to change the order of execution of operations if, for example, it believes that such an ordering would execute faster.

The issue of reordering is also governed by a set of rules for the happens-before relationship, and these rules have a consequence concerning the order of operations that is relevant in practice: the read and write operations of `volatile` variables cannot be reordered with the read and write operations of other `volatile` and non-volatile variables. This consequence allows a `volatile` variable to be used as a flag signaling the completion of some action. In other instances, the rules concerning the ordering of execution of operations guarantee the ordering of operations for specific cases (such as acquiring and releasing a monitor), while leaving the compiler and processor free to optimize in all other cases.

[Back to the Table of Contents](#Multithreading)

## What is "thread safety"?

Thread safety is a property of an object or code that guarantees that during execution or use by multiple threads, the code will behave as expected. For example, a thread-safe counter will not miss any counts, even if the same instance of this counter is used by multiple threads.

[Back to the Table of Contents](#Multithreading)

## What is the difference between _"concurrency"_ and _"parallelism"_?

Concurrency is a way to simultaneously solve multiple tasks.

Signs:

-   Presence of multiple control threads (for example, _Thread_ in Java, _coroutine_ in Kotlin); if there is only one control thread, then concurrent execution cannot exist.
-   Undetermined result of execution. The result depends on random events, implementation, and how synchronization was performed. Even if each thread is completely deterministic, the final result will be non-deterministic.

Parallelism is a way of executing different parts of one task.

Signs:

-   It does not necessarily have multiple control threads.
-   It can lead to a deterministic result; for example, the result of multiplying each element of an array by a number will not change if it is multiplied in parts concurrently.

[Back to the Table of Contents](#Multithreading)

## What is _"cooperative multitasking"_? What type of multitasking does Java use? What is the reasoning behind this choice?

**Cooperative multitasking** is a way of dividing CPU time among threads, where each thread must voluntarily yield control to the next.

The advantages of this approach are simplicity of implementation and lower overhead for context switching.

The disadvantages are that if one thread hangs or behaves incorrectly, the entire system hangs, and other threads may never gain control.

Java uses **preemptive multitasking**, where the operating system makes the decision to switch between threads of a process.

In contrast to cooperative multitasking, control is passed to the operating system regardless of the state of running applications, which means that individual hanging threads of a process generally do not "freeze" the entire system. Regular switching between tasks also improves application responsiveness and enhances the promptness of freeing resources that are no longer in use.

In implementation, preemptive multitasking differs from cooperative multitasking, particularly in that it requires handling system interrupts from a hardware timer.

[Back to the Table of Contents](#Multithreading)

## What are _ordering_, _as-if-serial semantics_, _sequential consistency_, _visibility_, _atomicity_, _happens-before_, _mutual exclusion_, _safe publication_?

**Ordering** is a mechanism that defines when one thread can see the _out-of-order_ execution of instructions from another thread. The CPU can reorder processor instructions and execute them in arbitrary order as long as there are no observable differences for the thread inside. The guarantee provided by this mechanism is called **as-if-serial semantics**.

**Sequential consistency** is the same as _as-if-serial semantics_, guaranteeing that within a single thread, the side effects of all operations will be such as if all operations were executed sequentially.

**Visibility** determines when actions in one thread become visible to another thread.

**Happens-before** is a logical constraint on the order of execution of the program's instructions. If it is specified that writing to a variable and subsequently reading it are related by this dependency, it does not matter how instructions are reordered during execution; at the time of reading, all writes associated with the process will already be committed and visible.

**Atomicity** refers to the atomicity of operations. An atomic operation appears as a single indivisible command to the processor, which can either be fully executed or not executed at all.

**Mutual exclusion** (mutual exclusion lock, semaphore with one state) is the mechanism that guarantees a thread exclusive access to a resource. This is used to prevent concurrent access to a shared resource. At any given time, only one thread can own such a resource. A simple example: `synchronized(obj) { … }`.

**Safe publication**? - the act of making objects visible to other threads from the current one while respecting the constraints of _visibility_. Ways of such publication in Java:

-   `static{}` initializer;
-   `volatile` variables;
-   `atomic` variables;
-   storing in a shared variable, correctly protected using `synchronized()`, synchronizers, or other constructs that create _read/write memory barriers_;
-   `final` variables in shared objects that have been correctly initialized.

[Back to the Table of Contents](#Multithreading)

## What is the difference between a process and a thread?

**A process** - is an instance of a program during execution, an independent object that has been allocated system resources (such as CPU time and memory). Each process runs in a separate address space: one process cannot access the variables and data structures of another. If a process wants access to foreign resources, inter-process communication must be used. This could be pipes, files, communication channels between computers, and much more.

For each process, the OS creates what is referred to as "virtual address space," to which the process has direct access. This space belongs to the process, contains only its data, and is entirely at its disposal. The operating system is responsible for how the virtual space of a process is mapped to physical memory.

**A thread** (thread) - is a specific way of executing a process, defining the sequence in which code is executed within the process. Threads are always created in the context of some process, and their entire lifecycle occurs only within its boundaries.
Threads can execute the same code and manipulate the same data, and they share kernel object descriptors since the descriptor table is created not per thread, but per process.
Since threads consume considerably fewer resources than processes, it is often better to create additional threads during the execution of a task and avoid the creation of new processes.

[Back to the Table of Contents](#Multithreading)

## What are "green threads," and does Java have them?

**Green threads** (lightweight threads) are threads emulated by the virtual machine or execution environment. Creating a green thread does not imply the creation of an actual OS thread.

The Java virtual machine takes care of switching between different green threads, whereas the machine operates as a single OS thread. This has several advantages. OS threads are relatively expensive on most POSIX systems. Furthermore, switching between native threads is considerably slower than switching between green threads.

This all means that in certain situations, green threads are much more beneficial compared to native threads. The system may support a significantly higher number of green threads than OS threads. For instance, it is much more practical to launch a new green thread for a new HTTP connection to a web server instead of creating a new native thread.

However, there are drawbacks. The biggest one is that you cannot execute two threads simultaneously. Since there is only one native thread, it is the only one called by the OS scheduler. Even if you have multiple processors and several green threads, only one processor can invoke a green thread. This is because, from the OS job scheduler's point of view, it all appears as a single thread.

Starting from version 1.2, Java supports native threads, and since then, they have been used by default.

[Back to the Table of Contents](#Multithreading)

## How can a thread be created?

-   Create a subclass of the `Thread` class and override its `run()` method;
-   Create an instance of the `Thread` class, passing in a class instance that implements the `Runnable` interface in the constructor. This interface contains the `run()` method that will execute in the new thread. The thread will finish execution when its `run()` method completes.
-   Call the `submit()` method of an instance of a class implementing the `ExecutorService` interface, passing it an instance of a class implementing the `Runnable` or `Callable` interface (which contains a `call()` method defining the execution logic).

[Back to the Table of Contents](#Multithreading)

## What are the differences between `Thread` and `Runnable`?

`Thread` is a class, a kind of wrapper around a physical thread.

`Runnable` is an interface that represents an abstraction of an executing task.

In addition to helping resolve the multiple inheritance problem, a significant advantage of using `Runnable` is that it allows you to logically separate the task execution logic from the direct thread management.

[Back to the Table of Contents](#Multithreading)

## What is the difference between the `start()` and `run()` methods?

Although `start()` invokes the `run()` method within itself, this is not the same as simply calling `run()`. If `run()` is called as a regular method, it executes in the same thread, and no new thread is started, as happens when the `start()` method is called.

[Back to the Table of Contents](#Multithreading)

## How can you forcibly start a thread?

There is no way to forcibly start a thread in Java. This is managed by the JVM, and Java does not provide any API to control this process.

[Back to the Table of Contents](#Multithreading)

## What is a "monitor" in Java?

A **monitor**, or mutex - is a means of controlling access to a resource. A monitor can have at most one owner at any given moment. Thus, if someone is using the resource and has captured the monitor for exclusive access, then another thread wanting to use the same resource must wait for the monitor to be released, acquire it, and only then start using the resource.

It's convenient to represent a monitor as the ID of the object that has captured it. If this ID equals 0 – the resource is free. If not 0 – the resource is occupied. You can queue up and wait for its release.

In Java, every object instance has a monitor that is controlled directly by the virtual machine. It is used as follows: any non-static `synchronized` method, when called, first attempts to capture the monitor of the object it is called on (to which it can reference as `this`). If successful, the method executes. If not, the thread stops and waits until the monitor is released.

[Back to the Table of Contents](#Multithreading)

## Define the concept of "synchronization."

Synchronization is the process that allows threads to execute concurrently.

In Java, every object has one lock, meaning that only one thread can access critical code within the object at a time. This synchronization helps prevent the corruption of the object's state. If a thread obtains the lock, no other thread can enter the synchronized code until the lock is released. When the thread holding the lock exits the synchronized code, the lock is released. Now another thread can acquire the object's lock and execute the synchronized code. If a thread attempts to acquire the object's lock while another thread owns it, the thread enters a Blocked state until the lock is released.

[Back to the Table of Contents](#Multithreading)

## What synchronization methods exist in Java?

-   **System synchronization using `wait()`/`notify()`.** A thread waiting for certain conditions calls the `wait()` method on the object, having first captured its monitor. This suspends its work. Another thread can call the `notify()` method on that same object (again, having first captured the object's monitor), causing the thread waiting on that object to "wake up" and continue its execution. In both cases, the monitor must be captured explicitly, through a `synchronized` block since the `wait()`/`notify()` methods are not synchronized!

-   **System synchronization using `join()`.** The `join()` method called on an instance of the `Thread` class allows the current thread to pause execution until the thread associated with that instance completes work.

-   **Using classes from the `java.util.concurrent` package**, which provides a set of classes for organizing inter-thread interactions. Examples of such classes include `Lock`, `Semaphore`, etc. The concept of this approach is based on the use of atomic operations and variables.

[Back to the Table of Contents](#Multithreading)

## What states can a thread be in?

Threads can be in one of the following states:

-   **New.** After an instance of a thread is created, it is in the New state until the `start()` method is called. In this state, the thread is not considered alive.
-   **Runnable.** The thread transitions to the Runnable state when the `start()` method is called. The thread may also enter this state from the Running or Blocked state. When the thread is in this state, it is considered alive.
-   **Running.** The thread enters the Running state from the Runnable state when the thread scheduler selects it to run.
-   **Alive, but not runnable.** The thread can be alive but not runnable for several reasons:
    -   **Waiting.** The thread enters the Waiting state by calling the `wait()` method. Calls to `notify()` or `notifyAll()` may transition the thread from the Waiting state to the Runnable state.
    -   **Sleeping.** The `sleep()` method pauses the thread for a specified period of time in milliseconds.
    -   **Blocked.** The thread may enter this state while waiting for a resource, such as I/O or due to the lock of another object. In this case, the thread enters the Runnable state when the resource becomes available.
    -   **Dead.** The thread is considered dead when its `run()` method has fully executed. A dead thread cannot transition to any other state, even if the `start()` method is called for it.

[Back to the Table of Contents](#Multithreading)

## Can new instances of a class be created while a `static synchronized` method is executing?

Yes, new instances of the class can be created since static fields do not belong to the class instances.

[Back to the Table of Contents](#Multithreading)

## Why would a `private` mutex be necessary?

An object for synchronization is made `private` so that external code cannot synchronize on it and inadvertently cause a deadlock.

[Back to the Table of Contents](#Multithreading)

## How do `wait()` and `notify()`/`notifyAll()` methods work?

These methods are defined in the `Object` class and are meant for inter-thread interaction during inter-thread synchronization.

-   `wait()`: releases the monitor and puts the calling thread in a waiting state until another thread calls `notify()`/`notifyAll()`;
-   `notify()`: continues the work of the thread that previously called `wait()`;
-   `notifyAll()`: resumes the work of all threads that previously called `wait()`.

When the `wait()` method is called, the thread releases the lock on the object and transitions from the Running state to the Waiting state. The `notify()` method signals one of the waiting threads to transition back to the Runnable state. However, it is impossible to determine which of the waiting threads will become runnable. The `notifyAll()` method causes all waiting threads for the object to return to the Runnable state. If no thread is waiting on the `wait()` method, calling `notify()` or `notifyAll()` does nothing.

A thread can only call the `wait()` or `notify()` methods for a specific object if it currently holds the lock on that object. `wait()`, `notify()`, and `notifyAll()` must only be called from synchronized code.

[Back to the Table of Contents](#Multithreading)

## What is the difference between `notify()` and `notifyAll()`?

The point is that there may be multiple threads waiting on the `wait()` method of a single monitor. When `notify()` is called, only one of them exits `wait()` and attempts to acquire the monitor, thus continuing work from the next operation after the `wait()` call. Which one will exit is unknown beforehand. However, when `notifyAll()` is called, all threads waiting on `wait()` exit `wait()`, and all attempt to acquire the monitor. It is clear that at any moment in time, the monitor can only be held by one thread, while the others wait in line. The order of the queue is determined by the Java thread scheduler.

[Back to the Table of Contents](#Multithreading)

## Why are the `wait()` and `notify()` methods called only in a synchronized block?

The monitor must be captured explicitly (via a `synchronized` block) because the `wait()` and `notify()` methods are not synchronized.

[Back to the Table of Contents](#Multithreading)

## What is the difference between the `wait()` method with a parameter and without it?

`wait()`

-   **Without parameters** releases the monitor and puts the calling thread in a waiting state until another thread calls `notify()`/`notifyAll()`,
-   **With parameters** will cause the thread to wait for the specified amount of time or for the call of `notify()`/`notifyAll()`.

[Back to the Table of Contents](#Multithreading)

## What are the differences between the `Thread.sleep()` and `Thread.yield()` methods?

The `yield()` method causes the current thread to move from the running state to the runnable state, giving other threads the opportunity to be activated. However, the next thread chosen for execution may not be another.

The `sleep()` method causes the current thread to sleep for a specified amount of time, changing its state from running to waiting.

[Back to the Table of Contents](#Multithreading)

## How does the `Thread.join()` method work?

When a thread calls `join()` on another thread, the currently executing thread will wait until the other thread it is joining is finished:

```java
void join()
void join(long millis)
void join(long millis, int nanos)
```

[Back to the Table of Contents](#Multithreading)

## What is a _deadlock_?

**Deadlock** is a phenomenon in which all threads are in a waiting state. This occurs when the following conditions are met:

1. mutual exclusion: at least one resource is held in non-shareable mode, meaning only one thread can use the resource at any given time.
2. hold and wait: a thread holds at least one resource and is waiting for additional resources that are held by other threads.
3. no preemption: the operating system does not forcibly release resources; if they are held, they must be returned by the holding threads immediately.
4. circular wait: a thread is waiting for a resource held by another thread, which in turn is waiting for a resource locked by the first thread.

The simplest way to avoid deadlock is to prevent circular wait. This can be achieved by obtaining monitors for shared resources in a predetermined order and releasing them in reverse order.

[Back to the Table of Contents](#Multithreading)

## What is a _livelock_?

A _livelock_ is a type of deadlock where several threads are performing useless work in an endless loop while trying to acquire any resources. Their states continually change in relation to each other. No actual error occurs, but the system's efficiency drops to 0. This often arises from attempts to prevent deadlock.

> A real example of livelock is when two people meet in a narrow hallway and each steps aside to be polite, leading them to move back and forth infinitely without making any progress in the direction they want to go.

[Back to the Table of Contents](#Multithreading)

## How can you check if a thread holds the monitor of a certain resource?

The `Thread.holdsLock(lock)` method returns `true` when the current thread holds the monitor on a given object.

[Back to the Table of Contents](#Multithreading)

## On which object does synchronization occur when calling a `static synchronized` method?

A synchronized static method does not have access to `this`, but has access to the `Class` object; there is only one instance of it, and it serves as the monitor for synchronizing static methods. Thus, the following construction:

```java
public class SomeClass {

    public static synchronized void someMethod() {
        // code
    }
}
```

is equivalent to this:

```java
public class SomeClass {

    public static void someMethod(){
        synchronized(SomeClass.class){
            // code
        }
    }
}
```

[Back to the Table of Contents](#Multithreading)

## What is the purpose of the keywords `volatile`, `synchronized`, `transient`, `native`?

**`volatile`** - this modifier forces threads to disable access optimization and use the single instance of the variable. If the variable is a primitive type, this suffices to ensure thread safety. However, if the variable is a reference to an object, the synchronization only concerns the value of that reference. The actual data contained within the object will not be synchronized!

**`synchronized`** - this reserved word allows achieving synchronization in methods or blocks of code marked with it.

The keywords `transient` and `native` have nothing to do with multithreading; the first is used to indicate fields of a class that should not be serialized, while the second signals that the method is implemented in platform-dependent code.

[Back to the Table of Contents](#Multithreading)

## What are the differences between `volatile` and _Atomic_ variables?

`volatile` forces the use of a single instance of the variable but does not guarantee atomicity. For example, the operation `count++` will not become atomic simply because `count` is declared `volatile`. On the other hand, the class `AtomicInteger` provides an atomic method to perform such complex operations atomically, for instance, `getAndIncrement()` is an atomic replacement for the increment operator, and it can be used to atomically add one to the current value. Similarly, atomic versions are constructed for other data types.

[Back to the Table of Contents](#Multithreading)

## What are the differences between `java.util.concurrent.Atomic*.compareAndSwap()` and `java.util.concurrent.Atomic*.weakCompareAndSwap()`?

-   `weakCompareAndSwap()` does not create a _memory barrier_ and does not guarantee _happens-before_;
-   `weakCompareAndSwap()` is heavily dependent on cache/CPU and may return `false` for invisible reasons;
-   `weakCompareAndSwap()` is a lighter operation but isn’t universally supported across architectures, nor is it always efficient.

[Back to the Table of Contents](#Multithreading)

## What does _"thread priority"_ mean?

Thread priorities are used by the thread scheduler to make decisions about when each thread is allowed to run. Theoretically, high-priority threads receive more CPU time than low-priority threads. In practice, the share of CPU time allotted to a thread often depends on various factors beyond its priority.

To set a thread's priority, the `final void setPriority(int level)` method of the `Thread` class is used. The `level` value ranges from `Thread.MIN_PRIORITY = 1` to `Thread.MAX_PRIORITY = 10`. The default priority is `Thread.NORM_PRIORITY = 5`.

The current thread priority can be obtained by calling the method: `final int getPriority()` on an instance of the `Thread` class.

[Back to the Table of Contents](#Multithreading)

## What are _"daemon threads"_?

Daemon threads run in the background with the application but are not integral to its operation. If a process can operate in the background to serve the main execution threads and its activity serves solely to support the main application threads, this process can be started as a daemon thread using the `setDaemon(boolean value)` method called on the thread before it starts. The method `boolean isDaemon()` allows checking whether a specified thread is a daemon or not. The fundamental property of daemon threads is that the main application thread can terminate the daemon thread when the `main` method's code concludes, regardless of whether the daemon thread is still running.

[Back to the Table of Contents](#Multithreading)

## Can the main thread of a program be a daemon?

No. Daemon threads are designed to describe background processes that serve only the main execution threads and cannot exist without them.

[Back to the Table of Contents](#Multithreading)

## What does it mean to _"sleep"_ a thread?

It means to suspend it for a specified period of time by calling the static method `Thread.sleep()`, passing the required amount of time in milliseconds. Before this time elapses, the thread may be awoken from its waiting state calls to `interrupt()` that throw `InterruptedException`.

[Back to the Table of Contents](#Multithreading)

## What are the differences between the `Runnable` and `Callable` interfaces?

-   The `Runnable` interface was introduced in Java 1.0, while the `Callable` interface was introduced in Java 5.0 as part of the `java.util.concurrent` library;
-   Classes implementing the `Runnable` interface to execute a task must implement the `run()` method. Classes implementing the `Callable` interface must implement the `call()` method;
-   The `Runnable.run()` method returns no value, while `Callable.call()` returns a `Future` object that may contain the result of the computation;
-   The `run()` method cannot throw checked exceptions, while the `call()` method can.

[Back to the Table of Contents](#Multithreading)

## What is `FutureTask`?

`FutureTask` is an cancellable asynchronous computation within a concurrent Java application. This class provides a basic implementation of `Future`, with methods to start and stop the computation, request the state of the computation, and extract results. The result can be obtained only when the computation has finished; the retrieval method will block if the computation has not yet completed. `FutureTask` objects can be used to wrap `Callable` and `Runnable` objects. Since `FutureTask` implements `Runnable`, it can be passed to an `Executor` for execution.

[Back to the Table of Contents](#Multithreading)

## What are the differences between `CyclicBarrier` and `CountDownLatch`?

`CountDownLatch` (countdown latch) allows any number of threads in a code block to wait until a specific number of operations being executed in other threads has finished before they are released to continue their activity. When creating a `CountDownLatch(int count)` object, the number of operations that must complete for the latch to release the blocked threads is provided as an argument.

> A life example of `CountDownLatch` could be collecting a tour group: the tour does not start until a certain number of people have gathered.

`CyclicBarrier` implements the "Barrier" synchronization pattern. A cyclic barrier is a synchronization point where a specified number of parallel threads meet and block. Once all threads arrive, an optional action is performed (or not, if the barrier was initialized without it), and after it is performed, the barrier breaks, releasing the waiting threads. The number of parties that must "meet" is provided as an argument to the constructors of `CyclicBarrier(int parties)` and `CyclicBarrier(int parties, Runnable barrierAction)`, along with an optional action that must occur when the parties meet, but before they are released.

> `CyclicBarrier` is an alternative to the `join()` method, which only “collects” threads after they have completed execution.

`CyclicBarrier` is similar to `CountDownLatch`, but the main difference between them is that a "latch" can only be used once—once its count reaches zero, while a "barrier" can be reused multiple times, even after it "breaks."

[Back to the Table of Contents](#Multithreading)

## What is a _race condition_?

A **race condition** is a design error in a multithreaded system or application where the behavior of the code depends directly on the order in which threads are executed. A race condition occurs when a thread that should execute first loses the race and another thread executes first: this changes the behavior of the code, leading to non-deterministic errors.

[Back to the Table of Contents](#Multithreading)

## Is there a way to solve the _race condition_ problem?

Common solutions include:

-   **Using a local copy** - copying a shared variable to a thread's local variable. This method works only when there is only one variable, and the copy is made atomically (in one machine command), using `volatile`.
-   **Synchronization** - operations on a shared resource occur in a synchronized block (using the `synchronized` keyword).
-   **Combining methods** - the above methods can be combined by copying "dangerous" variables in a synchronized block. This removes the atomicity restriction while allowing you to avoid overly large synchronized blocks.

There are no obvious ways to detect and fix race conditions. The best way to prevent races is correct design of a multi-threaded system.

[Back to the Table of Contents](#Multithreading)

## How can you stop a thread?

Currently, Java follows a notification-based order for stopping threads (although JDK 1.0 had several methods for controlling thread execution, such as `stop()`, `suspend()`, and `resume()` - in later versions of JDK, all of these were marked as `deprecated` due to potential risks of deadlocks).

To stop a thread properly, you can use the `interrupt()` method of the `Thread` class. This method sets an internal interrupt status flag. The state of this flag can later be checked with methods like `isInterrupted()` or `Thread.interrupted()` (for the current thread). The `interrupt()` method can also wake a thread out of a waiting or sleeping state; i.e., if methods like `sleep()` or `wait()` were called on the thread, the current state would be interrupted, and an `InterruptedException` would be thrown. In this case, the flag will not be set.

The action scheme would be as follows:

-   Implement the thread.
-   In the thread, periodically check the interrupt status by calling `isInterrupted()`.
-   If the flag status changes or an exception is thrown during waiting/sleeping, then the thread is being stopped externally.
-   Decide to either continue working (if stopping for some reason is impossible) or to free the resources locked by the thread and finish execution.

A potential issue with this approach is blocking on thread I/O. If a thread is blocked on reading data, calling `interrupt()` in that state will not wake it. Solutions can vary depending on the type of data source. If reading from a file, a prolonged block is very unlikely, and one could simply wait for the exit from the `read()` method. If, however, reading is somehow related to networking, it’s advisable to use non-blocking I/O from Java NIO.

Another option for implementing the stop method (as well as the suspend one) is to create your own version of `interrupt()`. That is, declare flags in the thread class for stopping and/or suspending and set them using predefined methods from outside. The action process remains the same: check the flag's setting and decide based on any changes. However, this approach has its disadvantages. First, it doesn't "revive" threads in the waiting state. Secondly, setting a flag in one thread does not mean that another thread will immediately see it. The virtual machine uses a thread's data cache, meaning the update of the variable in the second thread may happen after an indefinite time span (although permissible is to declare the flag variable as `volatile`).

[Back to the Table of Contents](#Multithreading)

## Why is it not recommended to use the `Thread.stop()` method?

The forced stopping (suspension) of a thread, `stop()` interrupts the thread at an indeterminate execution point, making it entirely unclear what to do with the resources it owns. The thread may open a network connection—what then should be done with the data that has not yet been read? What guarantees are there that after the thread is restarted (if suspended) it can continue reading them? If the thread locked a shared resource, how to release that lock without risking inconsistency in the system? The same applies to database connections—if a thread is stopped in the middle of a transaction, who will close it? Who and how will release resources?

[Back to the Table of Contents](#Multithreading)

## What happens when an exception is thrown in a thread?

-   If the exception is unhandled, the thread "dies" (enters the dead state).
-   If there is an uncaught exception handler, it will take over control. The `Thread.UncaughtExceptionHandler` is an interface defined as a nested interface for other handlers called when a thread stops suddenly due to an uncaught exception. If a thread is about to stop due to an uncaught exception, the JVM checks it for an `UncaughtExceptionHandler` using `Thread.getUncaughtExceptionHandler()`, and if such a handler is found, it will invoke the `uncaughtException()` method, passing the thread and the exception as arguments.

[Back to the Table of Contents](#Multithreading)

## What is the difference between `interrupted()` and `isInterrupted()`?

The interruption mechanism in Java is implemented using an internal flag called the interrupt status. Interrupting a thread by calling `Thread.interrupt()` sets this flag. The methods `Thread.interrupted()` and `isInterrupted()` allow checking whether a thread is interrupted.

When an interrupted thread checks the interrupt status by calling the static method `Thread.interrupted()`, the interrupt status is reset.

The non-static method `isInterrupted()` is used by one thread to check the interrupt status of another thread without altering the interrupt flag.

[Back to the Table of Contents](#Multithreading)

## What is a _thread pool_?

Creating a thread is a time- and resource-intensive operation. The number of threads that can be launched within a single process is also limited. To avoid these issues and, in general, manage multiple threads more efficiently, Java has implemented a mechanism for thread pools, created when the application starts, from which threads for processing requests are then taken and reused. Thus, there's no loss of threads, the application can be balanced in terms of the number of threads and their creation frequency.

Starting from Java 1.5, the Java API provides the `Executor` framework, which allows creating various types of thread pools:

-   `Executor` - a simplified pool interface containing one method for submitting tasks;
-   `ExecutorService` - an extended pool interface that allows shutting down all threads;
-   `AbstractExecutorService` - a base class of the pool that implements the `ExecutorService` interface;
-   `Executors` - a factory of objects related to the thread pool, which also creates the main types of pools;
-   `ThreadPoolExecutor` - a flexible thread pool that can serve as a base class for custom thread pools;
-   `ForkJoinPool` - a pool for executing `ForkJoinTask` type tasks;
-   ... and others.

`Executors` methods for creating pools:

-   `newCachedThreadPool()` - if a free thread is available, the task executes in it; otherwise, a new thread is added to the pool. Threads not used for more than a minute are terminated and removed from the cache. The pool size is unlimited. It is designed to execute a large number of small asynchronous tasks;
-   `newCachedThreadPool(ThreadFactory threadFactory)` - similar to the previous, but with a custom thread factory;
-   `newFixedThreadPool(int nThreads)` - creates a pool of a specified number of threads. If new tasks are added while all threads are active, they will be stored in the queue for later execution. If one of the threads exits due to an error, another thread will be started to take its place. Threads live until the pool is explicitly closed using the `shutdown()` method.
-   `newFixedThreadPool(int nThreads, ThreadFactory threadFactory)` - similar to the previous, but with a custom thread factory;
-   `newSingleThreadScheduledExecutor()` - a single-threaded pool with the ability to execute a task after a specified delay or periodically. If the thread is terminated due to errors, a new thread is created for the next task's execution.
-   `newSingleThreadScheduledExecutor(ThreadFactory threadFactory)` - similar to the previous, but with a custom thread factory;
-   `newScheduledThreadPool(int corePoolSize)` - a pool for executing tasks after a specified delay or periodically;
-   `newScheduledThreadPool(int corePoolSize, ThreadFactory threadFactory)` - similar to the previous, but with a custom thread factory;
-   `unconfigurableExecutorService(ExecutorService executor)` - a wrapper on the pool that prevents changes to its configuration;

[Back to the Table of Contents](#Multithreading)

## What should the size of a thread pool be?

When configuring the size of a thread pool, it is essential to avoid two mistakes: having too few threads (the queue for execution will grow, consuming a lot of memory) or too many threads (slowing down the entire system due to frequent context switches).

The optimal size of a thread pool depends on the number of available processors and the nature of the tasks in the working queue. On an N-processor system for a workload that will be performing purely CPU-bound tasks, maximum CPU utilization can be achieved with a thread pool containing either N or N+1 threads.
For tasks that might be waiting for I/O (input-output) – for example, tasks reading an HTTP request from a socket – the size of the pool may need to be greater than the number of available processors because not all threads will be working all the time. With profiling, one can assess the relationship of wait time (`WT`) to processing time (`ST`) for a typical request. If we label this ratio `WT/ST`, then on an N-processor system, approximately `N*(1 + WT/ST)` threads will be needed for full processor utilization.

CPU usage is not the only factor to consider when configuring the size of a thread pool. As the thread pool grows, one might encounter constraints from the scheduler, available memory, or other system resources such as the number of sockets, open file descriptors, or database connection channels.

[Back to the Table of Contents](#Multithreading)

## What happens if the thread pool queue is already full, but a new task is submitted?

If the thread pool queue is full, the submitted task will be "rejected." For example, the `submit()` method of the `ThreadPoolExecutor` throws a `RejectedExecutionException`, after which the `RejectedExecutionHandler` is invoked.

[Back to the Table of Contents](#Multithreading)

## What is the difference between the `submit()` and `execute()` methods of a thread pool?

Both methods serve to submit tasks to the thread pool, but there is a small difference between them.

`execute(Runnable command)` is defined in the `Executor` interface and runs the submitted task without returning anything.

`submit()` is an overloaded method defined in the `ExecutorService` interface. It can accept `Runnable` and `Callable` tasks and returns a `Future` object that can be used to control and manage the execution process, obtaining its result.

[Back to the Table of Contents](#Multithreading)

## What are the differences between a stack and a heap in terms of multithreading?

**Stack** - is a memory segment closely associated with threads. Each thread has its own stack, which stores local variables, method parameters, and the call stack. A variable stored in the stack of one thread is not visible to other threads.

**Heap** - is a shared memory segment accessible to all threads. Objects, regardless of their locality, are created in the heap. To improve performance, a thread usually caches values from the heap in its stack; in this case, to indicate to the thread that a variable should be read from the heap, the `volatile` keyword is used.

[Back to the Table of Contents](#Multithreading)

## How can you share data between two threads?

Data can be shared between threads using a shared object or concurrent data structures, such as `BlockingQueue`.
The `Exchanger` class synchronizer is designed for data exchange between threads. It is parameterized with the type of data that must be exchanged between threads.
Data exchange occurs through the single method of this class, `exchange()`. To work, an instance of the `Exchanger` must be passed to the constructors of the threads, and access it in the `run()` method. This method blocks the thread until another thread passes its data into the `Exchanger`.

[Back to the Table of Contents](#Multithreading)

## Which JVM startup option is used to control the size of a thread's stack?

`-Xss`

[Back to the Table of Contents](#Multithreading)

## How do you get a thread dump?

Java execution environments based on HotSpot only generate a dump in HPROF format. Developers have several interactive methods for generating dumps and one event-based method for generating dumps.

Interactive methods:

-   Using <kbd>Ctrl+Break</kbd>: if the command line option `-XX:+HeapDumpOnCtrlBreak` is set for the executing application, a dump in HPROF format is generated along with the thread dump when the `Ctrl+Break` event or `SIGQUIT` (usually generated with _kill -3_) is triggered from the console. This option may be unavailable in some versions. In that case, one can try using the following option:
    `-Xrunhprof:format=b,file=heapdump.hprof`
-   Using the _jmap_ tool: the _jmap_ utility, which comes with the JDK's `/bin/` directory, can request an HPROF dump from the executing process.
-   Using the operating system: To create a core file, one can use the non-destructive command _gcore_ or destructive commands _kill -6_ or _kill -11_. Then extract the heap dump from the core file using the _jmap_ utility.
-   Using the _JConsole_ tool. The operation `dumpHeap` is provided in _JConsole_ as an MBean component `HotSpotDiagnostic`. This operation requests the generation of a dump in HPROF format.

Event-based method:

-   `OutOfMemoryError` event: If the executing application has the command line option `-XX:+HeapDumpOnOutOfMemoryError` set, a dump in HPROF format is generated when `OutOfMemoryError` occurs. This is an ideal method for "production" systems, as it is essential for diagnosing memory issues and does not incur ongoing performance overhead. In older versions of Java execution environments based on HotSpot, there was no limit to the number of heap dumps created for this event per JVM instance; in newer versions, a maximum of one heap dump for this event is allowed for each run of the JVM.

[Back to the Table of Contents](#Multithreading)

## What is a _ThreadLocal variable_?

`ThreadLocal` is a class that allows having different values for a given variable for each thread.

Each thread, i.e., an instance of the `Thread` class, has an associated table of _ThreadLocal variables_. The keys in the table are references to objects of the `ThreadLocal` class, and the values are references to the objects "captured" by the ThreadLocal variables, implying that ThreadLocal variables differ from ordinary variables in that each thread has its own, individually initialized instance of the variable. Access to the value can be obtained through the `get()` or `set()` methods.

For example, if we declare a ThreadLocal variable: `ThreadLocal<Object> locals = new ThreadLocal<Object>();`. Then, in a thread, we call `locals.set(myObject)`, and the key in the table will be a reference to the `locals` object while the value will be a reference to the `myObject` object. At this point, another thread has the opportunity to "put" a different value inside `locals`.

It's important to note that `ThreadLocal` isolates not just the references to objects but also the objects themselves. If the isolated references within threads point to the same object, collisions may occur.

It is also crucial to emphasize that because ThreadLocal variables are isolated within threads, the initialization of such a variable must occur in the same thread where it will be used. It would be an error to initialize such a variable (invoke the `set()` method) in the main application thread since, in this case, the value passed in the `set()` method will be "captured" for the main thread, and when calling `get()` in the target thread, it will return `null`.

[Back to the Table of Contents](#Multithreading)

## What are the differences between `synchronized` and `ReentrantLock`?

Starting from Java 5, the `Lock` interface was introduced, providing more effective and finer control over resource locking. `ReentrantLock` is a popular implementation of `Lock`, which provides the same basic behavior and semantics as `synchronized`, but with extended capabilities such as lock polling, the ability to wait for a lock for a specified duration, and interruptible lock waiting. Moreover, it offers much higher performance in situations of high contention.

What is meant by reentrant locking? Simply put, there is a count associated with a lock, and if the thread that holds the lock acquires it again, the count increases, meaning that the lock is to be released twice for actual unlock. This is analogous to the semantics of synchronized; if a thread enters a synchronized block protected by a monitor it already owns, it will be allowed to continue functioning, and the lock will not be released when the thread exits the second (or subsequent) synchronized block; it will only be released when it exits the first synchronized block in which it entered under the protection of the monitor.

```java
Lock lock = new ReentrantLock();

lock.lock();
try {
  // update object state
}
finally {
  lock.unlock();
}
```

-   The implementation of `ReentrantLock` is usually more scalable in the context of contention than the `synchronized` implementation. This means that when many threads compete to acquire the lock, the overall throughput is often better with `ReentrantLock` than with `synchronized`. The JVM spends less time establishing the order of threads and more time executing.
-   With `ReentrantLock` (like other implementations of `Lock`), the lock must be released explicitly in a `finally` block (otherwise, if the guarded code throws an exception, the lock would not be released). When using synchronization, the JVM guarantees that the lock is automatically released.

In summary, it can be said that when contention for the lock is either absent or very low, `synchronized` may be faster. If there is significant contention for access to the resource, `ReentrantLock` will likely provide some advantage.

[Back to the Table of Contents](#Multithreading)

## What is `ReadWriteLock`?

`ReadWriteLock` is an interface extending the basic `Lock` interface. It is used to improve performance in a multithreaded process and operates with a pair of related locks (one for read operations, and one for write operations). The read lock can be held simultaneously by multiple reading threads until a writing lock is required. The write lock is exclusive.

The class `ReentrantReadWriteLock` implements the `ReadWriteLock` interface, which supports up to 65535 write locks and the same number of read locks.

```java
ReadWriteLock rwLock = new ReentrantReadWriteLock();
Lock rLock = rwLock.readLock();
Lock wLock = rwLock.writeLock();

wLock.lock();
try {
    // exclusive write
} finally {
    wLock.unlock();
}

rLock.lock();
try {
    // shared reading
} finally {
    rLock.unlock();
}
```

[Back to the Table of Contents](#Multithreading)

## What is a _blocking method_?

A **blocking method** is one that blocks until the task is done; for example, the `accept()` method in `ServerSocket` blocks while waiting for a client connection. Here, blocking means that control will not return to the calling method until the task completes. There are also asynchronous or non-blocking methods that may finish before the task is completed.

[Back to the Table of Contents](#Multithreading)

## What is the _Fork/Join framework_?

The Fork/Join framework, introduced in JDK 7, is a set of classes and interfaces that allow leveraging the advantages of modern multi-processor architecture. It is designed for executing tasks that can be recursively divided into smaller sub-tasks, which can then be solved in parallel.

-   Fork stage: a large task is divided into smaller subtasks, which in turn can also be split into smaller ones. And this continues until the task becomes trivial and solvable in a sequential manner.
-   Join stage: then (optionally) follows the process of "folding"—subtask solutions are combined in some way until the solution for the entire task is obtained.

The resolution of all subtasks (including the breaking down of tasks) occurs in parallel.

> For some tasks, the join phase is not required. For example, in parallel QuickSort—the array is recursively divided into smaller and smaller ranges until it reduces to a trivial case of one element. Although on some level a join will still be necessary since there still remains the need to wait until all subtasks have completed execution.

Another wonderful advantage of this framework is that it uses a work-stealing algorithm: threads that have completed their own subtasks can "steal" subtasks from other threads that are still busy.

[Back to the Table of Contents](#Multithreading)

## What is a `Semaphore`?

A semaphore is a new type of synchronizer: a counter semaphore implementing the semaphore synchronization pattern. Access is managed via a counter: the initial counter value is given in the constructor when creating the synchronizer; when a thread enters the designated code block, its counter value decreases by one, and when the thread exits, the counter increases. If the counter value is zero, the current thread blocks until someone exits the protected block. A semaphore is used for protecting expensive resources that are available in limited numbers, such as database connections in a pool.

[Back to the Table of Contents](#Multithreading)

## What is a _double-checked locking Singleton_?

The **double-checked locking Singleton** is one of the ways to create a thread-safe singleton class. This method attempts to optimize performance by locking only when the singleton instance is created for the first time.

```java
class DoubleCheckedLockingSingleton {
    private static volatile DoubleCheckedLockingSingleton instance;

    static DoubleCheckedLockingSingleton getInstance() {
        DoubleCheckedLockingSingleton current = instance;
        if (current == null) {
            synchronized (DoubleCheckedLockingSingleton.class) {
                current = instance;

                if (current == null) {
                    instance = current = new DoubleCheckedLockingSingleton();
                }
            }
        }
        return current;
    }
}
```

It is necessary to mention that the requirement for `volatile` is mandatory. The Double Checked Lock's issue lies in Java's memory model, specifically in the order of object creation, when there can be situations in which another thread may obtain and begin using (based on the condition that the pointer is non-null) an incompletely constructed object. Although this problem has been partially addressed in JDK 1.5, the recommendation to use `volatile` for Double Checked Lock remains in effect.

[Back to the Table of Contents](#Multithreading)

## How do you create a thread-safe Singleton?

-   **Static field**

```java
public class Singleton {
	public static final Singleton INSTANCE = new Singleton();
}
```

-   **Enum**

```java
public enum Singleton {
	INSTANCE;
}
```

-   **Synchronized Accessor**

```java
public class Singleton {
	private static Singleton instance;

	public static synchronized Singleton getInstance() {
		if (instance == null) {
			instance = new Singleton();
		}
		return instance;
	}
}
```

-   **Double Checked Locking & `volatile`**

```java
public class Singleton {
        private static volatile Singleton instance;

        public static Singleton getInstance() {
		SuperClass localInstance = instance;
		if (localInstance == null) {
			synchronized (Singleton.class) {
				localInstance = instance;
				if (localInstance == null) {
					instance = localInstance = new Singleton();
				}
			}
		}
		return localInstance;
	}
}
```

-   **On Demand Holder Idiom**

```java
public class Singleton {

	public static class SingletonHolder {
		public static final Singleton HOLDER_INSTANCE = new Singleton();
	}

	public static Singleton getInstance() {
		return SingletonHolder.HOLDER_INSTANCE;
	}
}
```

[Back to the Table of Contents](#Multithreading)

## What are the benefits of immutable objects?

Immutability helps simplify writing multithreaded code. An immutable object can be used without any synchronization. Unfortunately, Java does not have an `@Immutable` annotation to make an object immutable; therefore, developers must create a class with the required characteristics themselves. This involves following some general principles: initializing all fields only in the constructor, avoiding any methods like `setX()` that modify class fields, ensuring that there are no leaks of references, organizing separate storage for mutable objects, and so forth.

[Back to the Table of Contents](#Multithreading)

## What is _busy spin_?

**Busy spin** is a technique programmers use to make a thread wait under a certain condition. Unlike traditional methods like `wait()`, `sleep()` or `yield()`, which yield the processor's time, this method will instead execute an empty loop. This is necessary to maintain the processor cache since, in multi-core systems, there is a likelihood that the suspended thread will resume on another core, which will lead to reconstructing the state of the processor cache, a procedure that can be quite costly.

[Back to the Table of Contents](#Multithreading)

## List the principles you follow in multithreaded programming.

When writing multithreaded programs, it's important to adhere to certain rules that help ensure good performance of the application along with ease of debugging and simplicity of further code maintenance.

-   Always give meaningful names to your threads. Debugging, finding errors, or tracking exceptions in multithreaded code is quite a tough task. Names like `OrderProcessor`, `QuoteProcessor`, or `TradeProcessor` are far more informative than `Thread1`, `Thread2`, and `Thread3`. The name should reflect the task performed by that thread.
-   Avoid locks or try to minimize synchronization. Locking is expensive, and context switching is even more resource-intensive. Try to avoid synchronization and locking wherever possible, and design the critical section to be minimal in size. A synchronized block is always preferable to a synchronized method, additionally granting absolute control over the extent of locking.
-   Handle thread interruption with special care. There’s nothing worse than leaving a resource locked or a system in an inconsistent state due to an unconfirmed transaction.
-   Remember to handle exceptions. Thrown `InterruptedException`s should be handled properly, not just suppressed. Don't neglect `Thread.UncaughtExceptionHandler`. When using thread pools, it’s important to remember that they often simply "swallow" exceptions. If you submit a `Runnable` for execution, you must place the task execution code in a `try-catch` block. If a `Callable` is placed in the queue for execution, you must ensure that the result of the execution is always retrieved using the blocking `get()` so that in the event of an exception, the opportunity exists to rethrow the occurred exception.
-   Between synchronizers and `wait()` and `notify()`, you should choose synchronizers. First, synchronizers like `CountDownLatch`, `Semaphore`, `CyclicBarrier`, or `Exchanger` simplify code writing. Implementing complex flow control using `wait()` and `notify()` is very challenging. Secondly, these classes are written and maintained by true experts, and there is a chance that in subsequent JDK versions, they will be optimized internally or replaced with a more efficient external implementation.
-   It is almost always more advantageous to use Concurrent collections over Synchronized collections since the former are more modern (utilize all available advancements in the language at the time of their writing) and are more scalable than their synchronized counterparts.

[Back to the Table of Contents](#Multithreading)

## Which of the following statements about threads is incorrect?

1. If the `start()` method is called twice for the same `Thread` object, an exception is generated during execution.
2. The order in which threads were started may not match the order of their actual execution.
3. If the `run()` method is called directly for a `Thread` object, an exception is generated during execution.
4. If the `sleep()` method is called for a thread while it is executing synchronized code, the lock is not released.

The correct answer is 3. If the `run()` method is called directly for a `Thread` object, no exception is generated during execution. However, the code written in the `run()` method will be executed by the current thread, rather than a new one. Thus, the correct way to start the thread is to call the `start()` method, which leads to the `run()` method being executed in a new thread.

Calling the `start()` method twice on the same `Thread` object will lead to the generation of `IllegalThreadStateException` during execution; therefore, statement 1 is correct. Statement 2 is true, as the order of execution of threads is determined by the Thread Scheduler, independent of which thread was started first. Statement 4 is correct, as a thread will not release locks that it holds when it enters the Waiting state.

[Back to the Table of Contents](#Multithreading)

## Given three threads T1, T2, and T3. How to implement execution in the sequence T1, T2, T3?

Such a sequence of execution can be achieved in several ways, for example, by simply using the `join()` method to start a thread once another has completed its execution. To implement the specified sequence, you need to start the last thread first and then call the `join()` method in reverse order, meaning T3 calls `T2.join`, and T2 calls `T1.join`; thus, T1 will complete execution first, and T3 last.

[Back to the Table of Contents](#Multithreading)

## Write a minimal non-blocking stack (only two methods — `push()` and `pop()`).

```java
import java.util.concurrent.atomic.AtomicReference;

class NonBlockingStack<T> {
    private final AtomicReference<Element> head = new AtomicReference<>(null);

    NonBlockingStack<T> push(final T value) {
        final Element current = new Element();
        current.value = value;
        Element recent;
        do {
            recent = head.get();
            current.previous = recent;
        } while (!head.compareAndSet(recent, current));
        return this;
    }

    T pop() {
        Element result;
        Element previous;
        do {
            result = head.get();
            if (result == null) {
                return null;
            }
            previous = result.previous;
        } while (!head.compareAndSet(result, previous));
        return result.value;
    }

    private class Element {
        private T value;
        private Element previous;
    }
}
```

[Back to the Table of Contents](#Multithreading)

## Write a minimal non-blocking stack (only two methods — `push()` and `pop()`) using `Semaphore`.

```java
import java.util.concurrent.Semaphore;

class SemaphoreStack<T> {
    private final Semaphore semaphore = new Semaphore(1);
    private Node<T> head = null;

    SemaphoreStack<T> push(T value) {
        semaphore.acquireUninterruptibly();
        try {
            head = new Node<>(value, head);
        } finally {
            semaphore.release();
        }

        return this;
    }

    T pop() {
        semaphore.acquireUninterruptibly();
        try {
            Node<T> current = head;
            if (current != null) {
                head = head.next;
                return current.value;
            }
            return null;
        } finally {
            semaphore.release();
        }
    }

    private static class Node<E> {
        private final E value;
        private final Node<E> next;

        private Node(E value, Node<E> next) {
            this.value = value;
            this.next = next;
        }
    }
}
```
