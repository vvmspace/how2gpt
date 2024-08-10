---
title: "Java Collections Framework"
date: 2023-10-02
tags: [Java, Collections, Interview Questions, Technical Concepts]
---

[Interview Questions](README.md)

# Java Collections Framework

-   [What is a _"collection"_?](#What-is-a-"collection"?)
-   [Name the main interfaces of the JCF and their implementations.](#Name-the-main-interfaces-of-the-JCF-and-their-implementations.)
-   [Arrange the following interfaces in a hierarchy: `List`, `Set`, `Map`, `SortedSet`, `SortedMap`, `Collection`, `Iterable`, `Iterator`, `NavigableSet`, `NavigableMap`.](#Arrange-the-following-interfaces-in-a-hierarchy-List-Set-Map-SortedSet-SortedMap-Collection-Iterable-Iterator-NavigableSet-NavigableMap)
-   [Why is `Map` not a `Collection`, while `List` and `Set` are `Collection`?](#Why-is-Map-not-a-Collection-while-List-and-Set-are-Collection)
-   [What is the difference between `java.util.Collection` and `java.util.Collections`?](#What-is-the-difference-between-javautilCollection-and-javautilCollections)
-   [What is "fail-fast behavior"?](#What-is-fail-fast-behavior?)
-   [What is the difference between fail-fast and fail-safe?](#What-is-the-difference-between-fail-fast-and-fail-safe?)
-   [Provide examples of iterators that implement fail-safe behavior.](#Provide-examples-of-iterators-that-implement-fail-safe-behavior)
-   [What is the difference between `Enumeration` and `Iterator`?](#What-is-the-difference-between-Enumeration-and-Iterator)
-   [How are `Iterable` and `Iterator` related?](#How-are-Iterable-and-Iterator-related?)
-   [How are `Iterable`, `Iterator`, and "for-each" related?](#How-are-Iterable-Iterator-and-for-each-related?)
-   [Compare `Iterator` and `ListIterator`.](#Compare-Iterator-and-ListIterator)
-   [What will happen when calling `Iterator.next()` without a preceding call to `Iterator.hasNext()`?](#What-will-happen-when-calling-Iteratornext-without-a-preceding-call-to-IteratorhasNext)
-   [How many elements are skipped if `Iterator.next()` is called after 10 calls to `Iterator.hasNext()`?](#How-many-elements-are-skipped-if-Iteratornext-is-called-after-10-calls-to-IteratorhasNext)
-   [How will the collection behave if `iterator.remove()` is called?](#How-will-the-collection-behave-if-iteratorremove-is-called?)
-   [How will an already instantiated iterator for `collection` behave if `collection.remove()` is called?](#How-will-an-already-instantiated-iterator-for-collection-behave-if-collectionremove-is-called?)
-   [How to avoid `ConcurrentModificationException` while iterating through the collection?](#How-to-avoid-ConcurrentModificationException-while-iterating-through-the-collection?)
-   [Which collection implements FIFO discipline?](#Which-collection-implements-FIFO-discipline?)
-   [Which collection implements FILO discipline?](#Which-collection-implements-FILO-discipline?)
-   [What is the difference between `ArrayList` and `Vector`?](#What-is-the-difference-between-ArrayList-and-Vector?)
-   [Why was `ArrayList` added if `Vector` already existed?](#Why-was-ArrayList-added-if-Vector-already-existed?)
-   [What is the difference between `ArrayList` and `LinkedList`? In which cases is it better to use the first and which the second?](#What-is-the-difference-between-ArrayList-and-LinkedList-In-which-cases-is-it-better-to-use-the-first-and-which-the-second?)
-   [Which works faster: `ArrayList` or `LinkedList`?](#Which-works-faster-ArrayList-or-LinkedList?)
-   [What is the worst-case time complexity of the `contains()` method for an element that exists in `LinkedList`?](#What-is-the-worst-case-time-complexity-of-the-contains-method-for-an-element-that-exists-in-LinkedList?)
-   [What is the worst-case time complexity of the `contains()` method for an element that exists in `ArrayList`?](#What-is-the-worst-case-time-complexity-of-the-contains-method-for-an-element-that-exists-in-ArrayList?)
-   [What is the worst-case time complexity of the `add()` method for `LinkedList`?](#What-is-the-worst-case-time-complexity-of-the-add-method-for-LinkedList?)
-   [What is the worst-case time complexity of the `add()` method for `ArrayList`?](#What-is-the-worst-case-time-complexity-of-the-add-method-for-ArrayList?)
-   [If you need to add 1 million elements, which structure would you use?](#If-you-need-to-add-1-million-elements-which-structure-would-you-use?)
-   [How does element removal from `ArrayList` occur? How does this change the size of the `ArrayList`?](#How-does-element-removal-from-ArrayList-occur-How-does-this-change-the-size-of-the-ArrayList?)
-   [Suggest an efficient algorithm for removing several adjacent elements from the middle of a list implemented with `ArrayList`.](#Suggest-an-efficient-algorithm-for-removing-several-adjacent-elements-from-the-middle-of-a-list-implemented-with-ArrayList.)
-   [How much additional memory is needed when calling `ArrayList.add()`?](#How-much-additional-memory-is-needed-when-calling-ArrayListadd?)
-   [How much additional memory is allocated when calling `LinkedList.add()`?](#How-much-additional-memory-is-allocated-when-calling-LinkedListadd?)
-   [Estimate the amount of memory needed to store a single primitive type `byte` in `LinkedList`?](#Estimate-the-amount-of-memory-needed-to-store-a-single-primitive-type-byte-in-LinkedList?)
-   [Estimate the amount of memory needed to store a single primitive type `byte` in `ArrayList`?](#Estimate-the-amount-of-memory-needed-to-store-a-single-primitive-type-byte-in-ArrayList?)
-   [For which is the operation of adding an element to the middle slower: `ArrayList` or `LinkedList`?](#For-which-is-the-operation-of-adding-an-element-to-the-middle-slower-ArrayList-or-LinkedList?)
-   [In the implementation of the `ArrayList` class, there are the following fields: `Object[] elementData`, `int size`. Explain why it is necessary to store `size` separately if you can always get `elementData.length`?](#In-the-implementation-of-the-ArrayList-class-there-are-the-following-fields-Object-elementData-int-size-Explain-why-it-is-necessary-to-store-size-separately-if-you-can-always-get-elementDatalength?)
-   [Compare the `Queue` and `Deque` interfaces.](#Compare-the-Queue-and-Deque-interfaces.)
-   [Which extends which: `Queue` extends `Deque`, or `Deque` extends `Queue`?](#Which-extends-which-Queue-extendsDeque-or-Dequeue-extends-Queue)
-   [Why does `LinkedList` implement both `List` and `Deque`?](#Why-does-LinkedList-implement-both-List-and-Deque?)
-   [`LinkedList` - is it a singly linked, doubly linked or quadruple linked list?](#LinkedList---is-it-a-singly-linked-doubly-linked-or-quadruple-linked-list?)
-   [How to traverse the elements of `LinkedList` in reverse order without using the slow `get(index)`?](#How-to-traverse-the-elements-of-LinkedList-in-reverse-order-without-using-the-slow-getindex?)
-   [What can you do with `PriorityQueue`?](#What-can-you-do-with-PriorityQueue?)
-   [The `Stack` is considered "deprecated." What is it recommended to replace it with? Why?](#The-Stack-is-considered-deprecated-What-is-it-recommended-to-replace-it-with-Why?)
-   [Why is `HashMap` necessary if `Hashtable` exists?](#Why-is-HashMap-necessary-if-Hashtable-exists?)
-   [What is the difference between `HashMap` and `IdentityHashMap`? For what purpose is `IdentityHashMap`?](#What-is-the-difference-between-HashMap-and-IdentityHashMap-For-what-purpose-is-IdentityHashMap?)
-   [What is the difference between `HashMap` and `WeakHashMap`? For what purpose is `WeakHashMap` used?](#What-is-the-difference-between-HashMap-and-WeakHashMap-For-what-purpose-is-WeakHashMap-used?)
-   [In `WeakHashMap`, WeakReferences are used. Why not create a `SoftHashMap` based on SoftReferences?](#In-WeakHashMap-WeakReferences-are-used-Why-not-create-a-SoftHashMap-based-on-SoftReferences?)
-   [In `WeakHashMap`, WeakReferences are used. Why not create a `PhantomHashMap` based on PhantomReferences?](#In-WeakHashMap-WeakReferences-are-used-Why-not-create-a-PhantomHashMap-based-on-PhantomReferences?)
-   [What does `LinkedHashMap` have from `LinkedList`, and what from `HashMap`?](#What-does-LinkedHashMap-have-from-LinkedList-and-what-from-HashMap?)
-   [How does the "sorted" characteristic of `SortedMap` manifest itself other than that `toString()` outputs all elements in order?](#How-does-the-sorted-characteristic-of-SortedMap-manifest-itself-other-than-that-toString-outputs-all-elements-in-order?)
-   [How is `HashMap` structured?](#How-is-HashMap-structured?)
-   [According to Knuth and Cormen, there are two basic implementations of a hash table: based on open addressing and based on chaining. How is `HashMap` implemented? Why do you think this implementation was chosen? What are the pros and cons of each approach?](#According-to-Knuth-and-Cormen-there-are-two-basic-implementations-of-a-hash-table-based-on-open-addressing-and-based-on-chaining-How-is-HashMap-implemented-Why-do-you-think-this-implementation-was-chosen-What-are-the-pros-and-cons-of-each-approach?)
-   [How does `HashMap` work when trying to store two elements under keys with the same `hashCode()`, but for which `equals() == false`?](#How-does-HashMap-work-when-trying-to-store-two-elements-under-keys-with-the-same-hashCode-but-for-which-equals--false?)
-   [What is the initial number of buckets in `HashMap`?](#What-is-the-initial-number-of-buckets-in-HashMap?)
-   [What is the estimated time complexity of operations on elements from `HashMap`? Does `HashMap` guarantee the indicated complexity for retrieving an element?](#What-is-the-estimated-time-complexity-of-operations-on-elements-from-HashMap-Does-HashMap-guarantee-the-indicated-complexity-for-retrieving-an-element?)
-   [Is it possible for `HashMap` to degenerate into a list even with keys having different `hashCode()`?](#Is-it-possible-for-HashMap-to-degenerate-into-a-list-even-with-keys-having-different-hashCode?)
-   [In what case can an element be lost in `HashMap`?](#In-what-case-can-an-element-be-lost-in-HashMap?)
-   [Why can't you use `byte[]` as a key in `HashMap`?](#Why-can't-you-use-byte-as-a-key-in-HashMap?)
-   [What is the role of `equals()` and `hashCode()` in `HashMap`?](#What-is-the-role-of-equals-and-hashCode-in-HashMap?)
-   [What is the maximum number of `hashCode()` values?](#What-is-the-maximum-number-of-hashCode-values?)
-   [What is the worst-case time complexity of the `get(key)` method for a key that is not in `HashMap`?](#What-is-the-worst-case-time-complexity-of-the-getkey-method-for-a-key-that-is-not-in-HashMap?)
-   [What is the worst-case time complexity of the `get(key)` method for a key that is in `HashMap`?](#What-is-the-worst-case-time-complexity-of-the-getkey-method-for-a-key-that-is-in-HashMap?)
-   [Why, despite the fact that a key in `HashMap` does not have to implement the `Comparable` interface, can a doubly linked list always be transformed into a red-black tree?](#Why-despite-the-fact-that-a-key-in-HashMap-does-not-have-to-implement-the-Comparable-interface-can-a-doubly-linked-list-always-be-transformed-into-a-red-black-tree?)
-   [How many transitions occur at the moment of calling `HashMap.get(key)` for a key that exists in the table?](#How-many-transitions-occur-at-the-moment-of-calling-HashMapgetkey-for-a-key-that-exists-in-the-table?)
-   [How many new objects are created when you add a new element to `HashMap`?](#How-many-new-objects-are-created-when-you-add-a-new-element-to-HashMap?)
-   [How and when does the number of buckets in `HashMap` increase?](#How-and-when-does-the-number-of-buckets-in-HashMap-increase?)
-   [Explain the meaning of the parameters in the constructor `HashMap(int initialCapacity, float loadFactor)`.](#Explain-the-meaning-of-the-parameters-in-the-constructor-HashMapint-initialCapacity-float-loadFactor)
-   [Will `HashMap` work if all added keys have the same `hashCode()`?](#Will-HashMap-work-if-all-added-keys-have-the-same-hashCode?)
-   [How to iterate through all keys of a `Map`?](#How-to-iterate-through-all-keys-of-a-Map?)
-   [How to iterate through all values of a `Map`?](#How-to-iterate-through-all-values-of-a-Map?)
-   [How to iterate through all key-value pairs in a `Map`?](#How-to-iterate-through-all-key-value-pairs-in-a-Map?)
-   [What are the distinctions between `TreeSet` and `HashSet`?](#What-are-the-distinctions-between-TreeSet-and-HashSet?)
-   [What happens if you add elements to `TreeSet` in ascending order?](#What-happens-if-you-add-elements-to-TreeSet-in-ascending-order?)
-   [How does `LinkedHashSet` differ from `HashSet`?](#How-does-LinkedHashSet-differ-from-HashSet?)
-   [For `Enum`, there is a special class `java.util.EnumSet`. Why? What didn't the authors like about `HashSet` or `TreeSet`?](#For-Enum-there-is-a-special-class-javautilEnumSet-Why-What-didn't-the-authors-like-about-HashSet-or-TreeSet?)
-   [What methods exist to iterate through the elements of a list?](#What-methods-exist-to-iterate-through-the-elements-of-a-list?)
-   [How can you get synchronized objects of standard collections?](#How-can-you-get-synchronized-objects-of-standard-collections?)
-   [How to obtain a read-only collection?](#How-to-obtain-a-read-only-collection?)
-   [Write a single-threaded program that causes a collection to throw `ConcurrentModificationException`.](#Write-a-single-threaded-program-that-causes-a-collection-to-throw-ConcurrentModificationException.)
-   [Provide an example where a collection throws `UnsupportedOperationException`.](#Provide-an-example-where-a-collection-throws-UnsupportedOperationException.)
-   [Implement the symmetric difference of two collections using `Collection` methods (`addAll(...)`, `removeAll(...)`, `retainAll(...)`).](#Implement-the-symmetric-difference-of-two-collections-using-Collection-methods-addAll-removeAll-retainAll.)
-   [How to create a cache with an "invalidation policy" using LinkedHashMap?](#How-to-create-a-cache-with-an-invalidation-policy-using-LinkedHashMap?)
-   [How to copy elements of any `collection` into an array in a single line?](#How-to-copy-elements-of-any-collection-into-an-array-in-a-single-line?)
-   [How to get a `List` with all elements except the first and last 3 in a single call from `List`?](#How-to-get-a-List-with-all-elements-except-the-first-and-last-3-in-a-single-call-from-List?)
-   [How to convert `HashSet` to `ArrayList` in a single line?](#How-to-convert-HashSet-to-ArrayList-in-a-single-line?)
-   [How to convert `ArrayList` to `HashSet` in a single line?](#How-to-convert-ArrayList-to-HashSet-in-a-single-line?)
-   [Create a `HashSet` from the keys of a `HashMap`.](#Create-a-HashSet-from-the-keys-of-a-HHashMap?)
-   [Create a `HashMap` from `HashSet<Map.Entry<K, V>>`.](#Create-a-HashMap-from-HashSetMapEntryKV?)

## What is a _"collection"_?

A _"collection"_ is a data structure, a set of objects. The data (objects in the set) can be numbers, strings, user-defined class objects, etc.

[Back to Table of Contents](#java-collections-framework)

## Name the main interfaces of the JCF and their implementations.

At the top of the Java Collections Framework hierarchy are two interfaces: `Collection` and `Map`. These interfaces divide all collections in the framework into two parts based on the type of data storage: simple sequential sets of elements and sets of "key-value" pairs, respectively.

The `Collection` interface is extended by the following interfaces:

-   `List` (list) represents a collection that allows duplicate values. Implementations:
    -   `ArrayList` - encapsulates a regular array, the length of which automatically increases when new elements are added. The elements of this collection are indexed starting from zero, and can be accessed by index.
    -   `LinkedList` (doubly linked list) - consists of nodes, each containing both the actual data and two references to the next and previous node.
    -   `Vector` - an implementation of a dynamic array of objects, whose methods are synchronized.
    -   `Stack` - an implementation of a LIFO (last-in-first-out) stack.
-   `Set` (set) describes an unordered collection that does not contain duplicate elements. Implementations:
    -   `HashSet` - uses HashMap to store data. The key is the added element, and the value is a placeholder Object. Due to the implementation details, the order of elements is not guaranteed upon addition.
    -   `LinkedHashSet` - guarantees that the order of elements during traversal will be the same as the order in which elements were added.
    -   `TreeSet` - allows management of the order of elements in the collection using a `Comparator` object or retains elements using "natural ordering".
-   `Queue` (queue) is intended for storing elements with a predefined way of inserting and retrieving them in FIFO (first-in-first-out) order:
    -   `PriorityQueue` - allows management of the order of elements in the collection using a `Comparator` object or retains elements using "natural ordering".
    -   `ArrayDeque` - implements the `Deque` interface which extends the `Queue` interface with methods to implement a LIFO (last-in-first-out) structure.

The `Map` interface is implemented by the classes:

-   `Hashtable` - a hash table with synchronized methods. It does not allow using `null` as a value or key and is unordered.
-   `HashMap` - a hash table. It allows using `null` as a value or key and is unordered.
-   `LinkedHashMap` - an ordered implementation of a hash table.
-   `TreeMap` - an implementation based on red-black trees. It is ordered and provides the ability to manage the order of elements in the collection using a `Comparator` object or retains elements with "natural ordering".
-   `WeakHashMap` - an implementation of a hash table organized using _weak references_ for keys (the garbage collector will automatically remove the element from the collection during the next garbage collection if there are no strong references to the key of that element).

[Back to Table of Contents](#java-collections-framework)

## Arrange the following interfaces in a hierarchy: `List`, `Set`, `Map`, `SortedSet`, `SortedMap`, `Collection`, `Iterable`, `Iterator`, `NavigableSet`, `NavigableMap`.

-   `Iterable`
    -   `Collection`
        -   `List`
        -   `Set`
            -   `SortedSet`
                -   `NavigableSet`
-   `Map`
    -   `SortedMap`
        -   `NavigableMap`
-   `Iterator`

[Back to Table of Contents](#java-collections-framework)

## Why is `Map` not a `Collection`, while `List` and `Set` are `Collection`?

`Collection` represents a collection of certain elements. `Map` is a collection of "key-value" pairs.

[Back to Table of Contents](#java-collections-framework)

## What is the difference between `java.util.Collection` and `java.util.Collections`?

`java.util.Collections` - a set of static methods for operating with collections.

`java.util.Collection` - one of the main interfaces in the Java Collections Framework.

[Back to Table of Contents](#java-collections-framework)

## What is "fail-fast behavior"?

**Fail-fast behavior** means that upon the occurrence of an error or a state that might lead to an error, the system immediately ceases further operations and notifies about it. Employing a fail-fast approach helps to avoid indeterministic behavior of the program over time.

In the Java Collections API, certain iterators behave in a fail-fast manner and throw a `ConcurrentModificationException` if the collection was modified after its creation, i.e., an element was added or removed directly from the collection instead of using the iterator's methods.

This behavior is implemented through counting the number of modifications to the collection (modification count):

-   upon modification of the collection, the modification count is also modified;
-   when creating an iterator, the current value of the count is passed to it;
-   at each access to the iterator, the stored count value is compared to the current one and, if they do not match, an exception is thrown.

[Back to Table of Contents](#java-collections-framework)

## What is the difference between fail-fast and fail-safe?

In contrast to fail-fast, fail-safe iterators do not throw exceptions when the structure is modified because they work with a clone of the collection instead of the original.

[Back to Table of Contents](#java-collections-framework)

## Provide examples of iterators that implement fail-safe behavior.

The iterator for the `CopyOnWriteArrayList` collection and the view iterator of the `keySet` collection of `ConcurrentHashMap` are examples of fail-safe iterators.

[Back to Table of Contents](#java-collections-framework)

## What is the difference between `Enumeration` and `Iterator`?

Although both interfaces are intended for traversing collections, there are significant differences between them:

-   with `Enumeration`, you cannot add/remove elements;
-   in `Iterator`, the method names are fixed for better code readability (`Enumeration.hasMoreElements()` corresponds to `Iterator.hasNext()`, `Enumeration.nextElement()` corresponds to `Iterator.next()`, etc.);
-   `Enumeration` is present in deprecated classes such as `Vector`/`Stack`, while `Iterator` is found in all modern collection classes.

[Back to Table of Contents](#java-collections-framework)

## How are `Iterable` and `Iterator` related?

The `Iterable` interface has only one method - `iterator()`, which returns an `Iterator`.

[Back to Table of Contents](#java-collections-framework)

## How are `Iterable`, `Iterator`, and "for-each" related?

Classes implementing the `Iterable` interface can be used in a `for-each` structure which employs an `Iterator`.

[Back to Table of Contents](#java-collections-framework)

## Compare `Iterator` and `ListIterator`.

-   `ListIterator` extends the `Iterator` interface.
-   `ListIterator` can only be used for traversing elements of a `List` collection.
-   `Iterator` allows traversing elements only in one direction, using the `next()` method. However, `ListIterator` lets you traverse the list in both directions with the `next()` and `previous()` methods.
-   `ListIterator` does not point to a specific element: its current position lies between the elements returned by the `previous()` and `next()` methods.
-   Using a `ListIterator`, you can modify the list by adding/removing elements with the `add()` and `remove()` methods. The `Iterator` does not support this functionality.

[Back to Table of Contents](#java-collections-framework)

## What will happen when calling `Iterator.next()` without a preceding call to `Iterator.hasNext()`?

If the iterator points to the last element of the collection, a `NoSuchElementException` will occur; otherwise, the next element will be returned.

[Back to Table of Contents](#java-collections-framework)

## How many elements are skipped if `Iterator.next()` is called after 10 calls to `Iterator.hasNext()`?

None - `hasNext()` merely checks for the presence of the next element.

[Back to Table of Contents](#java-collections-framework)

## How will the collection behave if `iterator.remove()` is called?

If the `iterator.remove()` call is preceded by a call to `iterator.next()`, then `iterator.remove()` will remove the element from the collection that the iterator is pointing to; otherwise, an `IllegalStateException` will be thrown.

[Back to Table of Contents](#java-collections-framework)

## How will an already instantiated iterator for `collection` behave if `collection.remove()` is called?

A `ConcurrentModificationException` will be thrown on the next call to the iterator's methods.

[Back to Table of Contents](#java-collections-framework)

## How to avoid `ConcurrentModificationException` while iterating through the collection?

-   Try to find or implement another iterator that operates on a fail-safe principle.
-   Use `ConcurrentHashMap` and `CopyOnWriteArrayList`.
-   Transform the list into an array and iterate through the array.
-   Lock changes to the list while iterating using a `synchronized` block.

The downside of the last two options is a decrease in performance.

[Back to Table of Contents](#java-collections-framework)

## Which collection implements FIFO discipline?

FIFO, First-In-First-Out - this principle is employed by the `Queue` collection.

[Back to Table of Contents](#java-collections-framework)

## Which collection implements FILO discipline?

FILO, First-In-Last-Out - this principle is employed by the `Stack` collection.

[Back to Table of Contents](#java-collections-framework)

## What is the difference between `ArrayList` and `Vector`?

## Why was `ArrayList` added if `Vector` already existed?

-   Methods of the `Vector` class are synchronized, while `ArrayList` methods are not;
-   By default, `Vector` doubles its size when the allocated memory for elements is exhausted. `ArrayList`, on the other hand, only increases its size by half.

`Vector` is a deprecated class and its usage is not recommended.

[Back to Table of Contents](#java-collections-framework)

## What is the difference between `ArrayList` and `LinkedList`? In which cases is it better to use the first and which the second?

`ArrayList` is a list implemented based on an array, while `LinkedList` is a classic doubly linked list, built on objects linked between each other.

`ArrayList`:

-   Accessing any element by index takes _constant_ time _O(1)_;
-   Accessing elements by value takes _linear_ time _O(N)_;
-   Insertion at the end is typically done in _constant_ time _O(1)_;
-   Removing an arbitrary element from the list takes significant time since all elements to the "right" are shifted one space to the left (the actual size of the array (capacity) does not change);
-   Inserting an element in an arbitrary place in the list takes significant time as all elements to the "right" are shifted one space to the right;
-   Minimum overhead for storage.

`LinkedList`:

-   Accessing an element by index or value will require _linear_ time _O(N)_;
-   However, access to the first and last elements of the list is always done in _constant_ time _O(1)_ - references are constantly stored to the first and last elements;
-   Adding and removing at the beginning or end of the list requires _constant_ _O(1)_;
-   Inserting or removing in/from an arbitrary position is _constant_ _O(1)_;
-   But finding the position for insertion and removal takes _linear_ time _O(N)_;
-   Requires more memory to store the same number of elements, as it stores pointers to the next and previous elements of the list as well as the element itself.

Overall, `LinkedList` underperforms `ArrayList` in both memory consumption and speed of operations. It is advisable to use `LinkedList` when frequent insert/remove operations are needed or when guaranteed time for adding an element to the list is necessary.

[Back to Table of Contents](#java-collections-framework)

## Which works faster: `ArrayList` or `LinkedList`?

It depends on the actions that will be performed on the structure.

See [What is the difference between `ArrayList` and `LinkedList`?](#What-is-the-difference-between-ArrayList-and-LinkedList-In-which-cases-is-it-better-to-use-the-first-and-which-the-second?)

[Back to Table of Contents](#java-collections-framework)

## What is the worst-case time complexity of the `contains()` method for an element that exists in `LinkedList`?

_O(N)_. The time to find an element is linearly proportional to the number of elements in the list.

[Back to Table of Contents](#java-collections-framework)

## What is the worst-case time complexity of the `contains()` method for an element that exists in `ArrayList`?

_O(N)_. The time to find an element is linearly proportional to the number of elements in the list.

[Back to Table of Contents](#java-collections-framework)

## What is the worst-case time complexity of the `add()` method for `LinkedList`?

_O(N)_. Adding to the start/end of the list occurs in _O(1)_ time.

[Back to Table of Contents](#java-collections-framework)

## What is the worst-case time complexity of the `add()` method for `ArrayList`?

_O(N)_. Inserting an element at the end of the list occurs in _O(1)_ time, but if the array's capacity is insufficient, a new larger array is created, and all elements from the old array are copied to it.

[Back to Table of Contents](#java-collections-framework)

## If you need to add 1 million elements, which structure would you use?

A definitive answer can only be given based on information about which part of the list the elements will be added to, what will happen to the elements, and whether there are any memory or execution speed constraints.

See [What is the difference between `ArrayList` and `LinkedList`](#What-is-the-difference-between-ArrayList-and-LinkedList-In-which-cases-is-it-better-to-use-the-first-and-which-the-second?)

[Back to Table of Contents](#java-collections-framework)

## How does element removal from `ArrayList` occur? How does this change the size of the `ArrayList`?

When an arbitrary element is removed from the list, all elements to the "right" are shifted one space to the left and the actual size of the array (its capacity) does not change in any way. While automatic "expansion" of the array exists, automatic "compression" does not; one can only explicitly perform "compression" with the `trimToSize()` command.

[Back to Table of Contents](#java-collections-framework)

## Suggest an efficient algorithm for removing several adjacent elements from the middle of a list implemented with `ArrayList`.

Assuming that you need to remove `n` elements from the position `m` in the list. Instead of performing the removal for one element `n` times (each time shifting the elements to the "right" one position), shift all elements located to the right of `n + m` to `n` positions "left" to the start of the list. Consequently, instead of performing `n` iterations for moving the elements of the list, it is all done in one pass. However, if considering overall performance - the fastest method will utilize `System.arraycopy()`, and access to it can be achieved through the method - `subList(int fromIndex, int toIndex)`.

Example:

```java
import java.io.*;
import java.util.ArrayList;

public class Main {
    // Position from which we are removing
    private static int m = 0;
    // Number of elements to remove
    private static int n = 0;
    // Number of elements in the list
    private static final int size = 1000000;
    // Main list (for removal via calling remove()) and its copy (for removal via rewriting)
    private static ArrayList<Integer> initList, copyList;

    public static void main(String[] args) {
        initList = new ArrayList<>(size);
        for (int i = 0; i < size; i++) {
            initList.add(i);
        }
        System.out.println("List with 1,000,000 elements populated");

        copyList = new ArrayList<>(initList);
        System.out.println("A copy of the list has been created\n");

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        try {
            System.out.print("From which position do we remove? > ");
            m = Integer.parseInt(br.readLine());
            System.out.print("How many do we remove? > ");
            n = Integer.parseInt(br.readLine());
        } catch(IOException e) {
            System.err.println(e.toString());
        }
        System.out.println("\nPerforming removal using the remove() call...");
        long start = System.currentTimeMillis();

        for (int i = m - 1; i < m + n - 1; i++) {
            initList.remove(i);
        }

        long finish = System.currentTimeMillis() - start;
        System.out.println("Time to remove using remove(): " + finish);
        System.out.println("Size of the original list after removal: " + initList.size());

        System.out.println("\nPerforming removal via rewriting...\n");
        start = System.currentTimeMillis();

        removeEfficiently();

        finish = System.currentTimeMillis() - start;
        System.out.println("Time for removal via shifting: " + finish);
        System.out.println("Size of the copy list: " + copyList.size());

        System.out.println("\nPerforming removal through SubList...\n");
        start = System.currentTimeMillis();

        initList.subList(m - 1, m + n).clear();

        finish = System.currentTimeMillis() - start;
        System.out.println("Time for removal through sublist: " + finish);
        System.out.println("Size of the copy list: " + copyList.size());
    }

    private static void removeEfficiently() {
        // If we need to remove all elements starting from a specified one,
        // then delete elements from the end to m
        if (m + n >= size) {
            int i = size - 1;
            while (i != m - 1) {
                copyList.remove(i);
                i--;
            }
        } else {
            // Variable k is needed for the shift counting from the insertion location
            for (int i  = m + n, k = 0; i < size; i++, k++) {
                copyList.set(m + k, copyList.get(i));
            }

            // Remove unwanted elements from the end of the list
            // Always the last element is removed, as the time for this operation
            // is fixed and does not depend on the list size
            int i = size - 1;
            while (i != size - n - 1) {
                copyList.remove(i);
                i--;
            }
            // Reduce the length of the list by removing empty slots
            copyList.trimToSize();
        }
    }
}
```

Execution result:

```
run:
List with 1,000,000 elements populated
A copy of the list has been created

From which position do we remove? > 600000
How many do we remove? > 20000

Performing removal using the remove() call...
Time to remove using remove(): 928
Size of the original list after removal: 980000

Performing removal via rewriting...

Time for removal via shifting: 17
Size of the copy list: 980000

Performing removal through SubList...

Time for removal through sublist: 1
Size of the copy list: 980000
BUILD SUCCESSFUL (total time: 33 seconds)
```

[Back to Table of Contents](#java-collections-framework)

## How much additional memory is needed when calling `ArrayList.add()`?

If there is enough space in the array to accommodate a new element, no additional memory is required. Otherwise, a new array of 1.5 times the existing size is created (this is valid for JDK versions above 1.7; prior versions have a different resize size).

[Back to Table of Contents](#java-collections-framework)

## How much additional memory is allocated when calling `LinkedList.add()`?

One new instance of the embedded class `Node` is created.

[Back to Table of Contents](#java-collections-framework)

## Estimate the amount of memory needed to store a single primitive type `byte` in `LinkedList`?

Each element of `LinkedList` holds a reference to the previous element, the next element, and a reference to the data.

```java
private static class Node<E> {
        E item;
        Node<E> next;
        Node<E> prev;
//...
}
```

For 32-bit systems, each reference takes 32 bits (4 bytes). The object (header) of the embedded class `Node` takes 8 bytes. So, 4 + 4 + 4 + 8 = 20 bytes, and since the size of each object in Java is a multiple of 8, we get 24 bytes. The primitive type `byte` takes 1 byte of memory, but in the JCF, primitives are boxed: the object of type `Byte` occupies 16 bytes in memory (8 bytes for the object header, 1 byte for the field of type `byte`, and 7 bytes to reach 8). It should also be noted that the values from -128 to 127 are cached, and new objects are not created for them each time. Therefore, in x32 JVM, 24 bytes are consumed to store one element in the list and 16 bytes for storing a boxed object of type `Byte`. In total, this results in 40 bytes.

In a 64-bit JVM, each reference occupies 64 bits (8 bytes), and the header size of each object is 16 bytes (two machine words). The calculations are similar: 8 + 8 + 8 + 16 = 40 bytes and 24 bytes. Therefore, in total, there are 64 bytes.

[Back to Table of Contents](#java-collections-framework)

## Estimate the amount of memory needed to store a single primitive type `byte` in `ArrayList`?

`ArrayList` is based on an array, and for primitive data types, automatic boxing occurs, so 16 bytes are consumed to store the boxed object, plus 4 bytes (8 for x64) are needed to store a reference to this object within the data structure. Thus, in a x32 JVM, 4 bytes are spent on storing one element and 16 bytes on storing the boxed object of type `Byte`. For x64, the figures are 8 bytes and 24 bytes, respectively.

[Back to Table of Contents](#java-collections-framework)

## For which is the operation of adding an element to the middle slower: `ArrayList` or `LinkedList`?

For `ArrayList`:

-   Checking the array for capacity. If the capacity is insufficient, then resizing the array and copying all elements to the new array takes _O(N)_;
-   Copying all elements located to the right of the insertion position by one position to the right takes _O(N)_;
-   Inserting the element takes _O(1)_.

For `LinkedList`:

-   Finding the insertion position takes _O(N)_;
-   Inserting the element takes _O(1)_.

In the worst case, insertion in the middle of the list is more efficient for `LinkedList`. In other cases, `ArrayList` is typically preferable, since copying elements is done by calling the fast system method `System.arraycopy()`.

[Back to Table of Contents](#java-collections-framework)

## In the implementation of the `ArrayList` class, there are the following fields: `Object[] elementData`, `int size`. Explain the necessity of storing `size` separately if you can always get `elementData.length`?

The size of the `elementData` array represents the capacity of the `ArrayList`, which is always greater than the `size` variable - the actual number of stored elements. The capacity automatically increases when necessary.

[Back to Table of Contents](#java-collections-framework)

## Compare the `Queue` and `Deque` interfaces.

## Which extends which: `Queue` extends `Deque`, or `Deque` extends `Queue`?

`Queue` is a collection that is generally (but not necessarily) built based on FIFO (First-In-First-Out) - as such, extracting an element is done from the front of the queue, while insertion is done at the back. Although this principle is violated by, for example, `PriorityQueue`, which uses "natural ordering" or a passed `Comparator` when inserting a new element.

`Deque` (Double Ended Queue) extends `Queue` and according to the documentation, it is a linear collection that supports inserting/removing elements from both ends. Moreover, implementations of the `Deque` interface can be built based on either FIFO or LIFO principles.

The implementations of both `Deque` and `Queue` typically do not override the `equals()` and `hashCode()` methods, instead using inherited methods from the Object class based on reference comparison.

[Back to Table of Contents](#java-collections-framework)

## Why does `LinkedList` implement both `List` and `Deque`?

`LinkedList` allows adding elements at both the beginning and the end of the list in constant time, which aligns well with the behavior of the `Deque` interface.

[Back to Table of Contents](#java-collections-framework)

## `LinkedList` - is it a singly linked, doubly linked or quadruple linked list?

Double linked: each element of `LinkedList` holds a reference to both the previous and next elements.

[Back to Table of Contents](#java-collections-framework)

## How to traverse the elements of `LinkedList` in reverse order without using the slow `get(index)`?

To achieve this, `LinkedList` has a reverse iterator, which can be obtained by calling the `descendingIterator()` method.

[Back to Table of Contents](#java-collections-framework)

## What can you do with `PriorityQueue`?

The key feature of `PriorityQueue` is the ability to control the order of elements. By default, elements are sorted using their "natural ordering", but this behavior can be overridden by providing a `Comparator` upon queue creation. This collection does not support `null` as elements.

Using `PriorityQueue`, one can, for example, implement Dijkstra's algorithm to find the shortest path from one vertex to another in a graph. It can also be used to store objects according to a specified property.

[Back to Table of Contents](#java-collections-framework)

## The `Stack` is considered "deprecated." What is it recommended to replace it with? Why?

`Stack` was added in Java 1.0 as an implementation of a LIFO (last-in-first-out) stack and is an extension of the `Vector` collection, although this somewhat violates the concept of a stack (for example, `Vector` provides the ability to access any element by index). It is a partially synchronized collection (except for the `push()` method), with consequent negative effects on performance. After the introduction of the `Deque` interface in Java 1.6, it is recommended to use implementations of this interface, such as `ArrayDeque`.

[Back to Table of Contents](#java-collections-framework)

## Why is `HashMap` necessary if `Hashtable` exists?

-   The methods of the `Hashtable` class are synchronized, which leads to reduced performance, while `HashMap` methods are not synchronized;
-   `HashTable` cannot contain `null` elements, whereas `HashMap` can contain one `null` key and any number of `null` values;
-   The iterator of the `HashMap`, unlike Enumeration of the `Hashtable`, operates on a "fail-fast" basis (it throws exceptions in case of any data inconsistencies).

`Hashtable` is a deprecated class and its usage is not recommended.

[Back to Table of Contents](#java-collections-framework)

## What is the difference between `HashMap` and `IdentityHashMap`? For what purpose is `IdentityHashMap`?

`IdentityHashMap` is a data structure that also implements the `Map` interface and uses reference comparison when comparing keys (values) rather than calling the `equals()` method. In other words, in `IdentityHashMap`, two keys `k1` and `k2` are considered equal if they refer to the same object, i.e., it holds true that `k1` == `k2`.

`IdentityHashMap` does not use the `hashCode()` method, instead utilizing the method `System.identityHashCode()`. For this reason, `IdentityHashMap` has higher performance compared to `HashMap`, especially when the latter is storing objects with expensive `equals()` and `hashCode()` methods.

One of the main requirements for using `HashMap` is the immutability of the key, while `IdentityHashMap` does not utilize `equals()` and `hashCode()` methods, hence this rule does not apply to it.

`IdentityHashMap` can be employed to implement serialization/cloning. When executing such algorithms, the program needs to maintain a hash table with all references to objects that have already been processed. This structure should not consider unique objects as equal, even if the `equals()` method returns `true`.

Example code:

```java
import java.util.HashMap;
import java.util.IdentityHashMap;
import java.util.Map;

public class Q2 {

    public static void main(String[] args) {
        Q2 q = new Q2();
        q.testHashMapAndIdentityHashMap();
    }

    private void testHashMapAndIdentityHashMap() {
        CreditCard visa = new CreditCard("VISA", "04/12/2019");

        Map<CreditCard, String> cardToExpiry = new HashMap<>();
        Map<CreditCard, String> cardToExpiryIdentity = new IdentityHashMap<>();

        System.out.println("adding to HM");
        // inserting objects to HashMap
        cardToExpiry.put(visa, visa.getExpiryDate());

        // inserting objects to IdentityHashMap
        cardToExpiryIdentity.put(visa, visa.getExpiryDate());
        System.out.println("adding to IHM");

        System.out.println("before modifying keys");
        String result = cardToExpiry.get(visa) != null ? "Yes" : "No";
        System.out.println("Does VISA card exists in HashMap? " + result);

        result = cardToExpiryIdentity.get(visa) != null ? "Yes" : "No";
        System.out.println("Does VISA card exists in IdentityHashMap? " + result);

        // modifying value object
        visa.setExpiryDate("02/11/2030");

        System.out.println("after modifying keys");
        result = cardToExpiry.get(visa) != null ? "Yes" : "No";
        System.out.println("Does VISA card exists in HashMap? " + result);

        result = cardToExpiryIdentity.get(visa) != null ? "Yes" : "No";
        System.out.println("Does VISA card exists in IdentityHashMap? " + result);

        System.out.println("cardToExpiry.containsKey");
        System.out.println(cardToExpiry.containsKey(visa));
        System.out.println("cardToExpiryIdentity.containsKey");
        System.out.println(cardToExpiryIdentity.containsKey(visa));
    }

}

class CreditCard {
    private String issuer;
    private String expiryDate;

    public CreditCard(String issuer, String expiryDate) {
        this.issuer = issuer;
        this.expiryDate = expiryDate;
    }

    public String getIssuer() {
        return issuer;
    }

    public String getExpiryDate() {
        return expiryDate;
    }

    public void setExpiryDate(String expiry) {
        this.expiryDate = expiry;
    }

    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + ((expiryDate == null) ? 0 : expiryDate.hashCode());
        result = prime * result + ((issuer == null) ? 0 : issuer.hashCode());
        System.out.println("hashCode = " + result);
        return result;
    }

    @Override
    public boolean equals(Object obj) {
        System.out.println("equals !!! ");
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        CreditCard other = (CreditCard) obj;
        if (expiryDate == null) {
            if (other.expiryDate != null)
                return false;
        } else if (!expiryDate.equals(other.expiryDate))
            return false;
        if (issuer == null) {
            if (other.issuer != null)
                return false;
        } else if (!issuer.equals(other.issuer))
            return false;
        return true;
    }

}
```

Execution result of the code:

```
adding to HM
hashCode = 1285631513
adding to IHM
before modifying keys
hashCode = 1285631513
Does VISA card exists in HashMap? Yes
Does VISA card exists in IdentityHashMap? Yes
after modifying keys
hashCode = 791156485
Does VISA card exists in HashMap? No
Does VISA card exists in IdentityHashMap? Yes
cardToExpiry.containsKey
hashCode = 791156485
false
cardToExpiryIdentity.containsKey
true
```

[Back to Table of Contents](#java-collections-framework)

## What is the difference between `HashMap` and `WeakHashMap`? For what purpose is `WeakHashMap` used?

In Java, there are four types of references: _strong references_, _soft references_, _weak references_, and _phantom references_. The peculiarities of each reference type are tied to the work of the Garbage Collector. If an object can only be reached through a chain of WeakReference (i.e., it has no strong or soft references), that object will be marked for removal.

`WeakHashMap` is a data structure that implements the `Map` interface and is based on using weak references for storing keys. Thus, the "key-value" pair will be removed from the `WeakHashMap` when there are no stronger references to the key object.

An example use case of such a data structure can involve situations where there are objects that need to be extended with additional information, but changing the class of these objects is undesirable or impossible. In this case, you add each object to the `WeakHashMap` as a key and the corresponding additional information as a value. Thus, as long as there is a strong (or soft) reference to the object, it can be checked against the hash table and the information extracted. Once the object is removed, the weak reference for that key will be placed in a ReferenceQueue, and subsequently, the entry for this weak reference will be removed from the `WeakHashMap`.

[Back to Table of Contents](#java-collections-framework)

## In `WeakHashMap`, WeakReferences are used. Why not create a `SoftHashMap` based on SoftReferences?

`SoftHashMap` is available in third-party libraries, such as `Apache Commons`.

[Back to Table of Contents](#java-collections-framework)

## In `WeakHashMap`, WeakReferences are used. Why not create a `PhantomHashMap` based on PhantomReferences?

PhantomReference returns `null` when the `get()` method is invoked, making it difficult to conceive of the purpose of such a data structure.

[Back to Table of Contents](#java-collections-framework)

## What does `LinkedHashMap` have from `LinkedList`, and what from `HashMap`?

The implementation of `LinkedHashMap` differs from `HashMap` by supporting a doubly linked list that determines the order of iteration across the elements of the data structure. By default, the elements of the list are ordered according to their order of addition to the `LinkedHashMap` (insertion-order). However, the iteration order can be modified by setting the `accessOrder` constructor parameter to `true`. In this case, access is carried out according to the last access order of the element.

When adding an element that is already present in `LinkedHashMap` (i.e., with an identical key), the order of iteration over the elements does not change.

[Back to Table of Contents](#java-collections-framework)

## How does the "sorted" characteristic of `SortedMap` manifest itself other than that `toString()` outputs all elements in order?

It is also manifested during iteration over the collection.

[Back to Table of Contents](#java-collections-framework)

## How is `HashMap` structured?

`HashMap` consists of "buckets". Technically, the "buckets" are the elements of an array that store references to the lists of elements. When adding a new "key-value" pair, it computes the hash code of the key, based on which the bucket index (the array cell number) to which the new element will be added is calculated. If the bucket is empty, it saves the reference to the newly added element; if there is already an element in the bucket, it sequentially traverses the references between the elements in the chain until the last element is reached, to which a reference to the newly added element is then placed. If an element with the same key is found in the list, it will be replaced.

[Back to Table of Contents](#java-collections-framework)

## According to Knuth and Cormen, there are two basic implementations of a hash table: based on open addressing and based on chaining. How is `HashMap` implemented? Why do you think this implementation was chosen? What are the pros and cons of each approach?

`HashMap` is implemented using chaining, meaning that each element of the array (bucket) corresponds to its own linked list, and when collisions occur, new elements are added to that list.

For the chaining method, the load factor can exceed 1, and with an increasing number of elements, performance declines linearly. Such tables are convenient to use when the number of elements is unknown, or it could be sufficiently large, leading to high load factor values.

Among the open addressing methods, there are distinctions such as:

-   linear probing;
-   quadratic probing;
-   double hashing.

The downsides of data structures using open addressing include:

-   The number of elements in a hash table cannot exceed the size of the array. As the number of elements increases and the load factor rises, the performance of the structure sharply declines, necessitating rehashing.
-   It can be complicated to organize element deletion.
-   The first two methods of open addressing result in primary and secondary clustering issues.

The advantages of the hash table with open addressing include:

-   the absence of costs associated with creating and storing list objects;
-   the simplicity of organizing serialization/deserialization of an object.

[Back to Table of Contents](#java-collections-framework)

## How does `HashMap` work when trying to store two elements under keys with the same `hashCode()`, but for which `equals() == false`?

The index of the array cell is calculated based on the `hashCode()`, determining which list this element will be added to. Before adding, a check for the presence of elements in that cell is conducted. If elements with such a `hashCode()` are already present, but their `equals()` methods are not equal, then the new element will be added to the end of the list.

[Back to Table of Contents](#java-collections-framework)

## What is the initial number of buckets in `HashMap`?

By default in the constructor, it is set to 16, but using constructors with parameters allows for an arbitrary initial number of buckets to be specified.

[Back to Table of Contents](#java-collections-framework)

## What is the estimated time complexity of operations on elements from `HashMap`? Does `HashMap` guarantee the indicated complexity for retrieving an element?

In general, operations for adding, searching, and deleting elements take _constant time_.

This complexity is not guaranteed, as if the hash function distributes elements across buckets evenly, the time complexity can achieve no worse than _logarithmic time_ O(log(N)), whereas if the hash function consistently returns the same value, `HashMap` can degenerate into a linked list, leading to O(n) time complexity.

Example code of binary search:

```java
public class Q {
    public static void main(String[] args) {
        Q q = new Q();
        q.binSearch();
    }

    private void binSearch() {
        int[] inpArr = {1, 2, 3, 4, 5, 6, 7, 8, 9};
        Integer result = binSearchF(inpArr, 1, 0, inpArr.length - 1);
        System.out.println("-----------------------");
        result = binSearchF(inpArr, 2, 0, inpArr.length - 1);
        System.out.println("Found at position " + result);
    }

    private Integer binSearchF(int[] inpArr, int searchValue, int low, int high) {
        Integer index = null;
        while (low <= high) {
            System.out.println("New iteration, low = " + low + ", high = " + high);
            int mid = (low + high) / 2;
            System.out.println("trying mid = " + mid + " inpArr[mid] = " + inpArr[mid]);
            if (inpArr[mid] < searchValue) {
                low = mid + 1;
                System.out.println("inpArr[mid] (" + inpArr[mid] + ") < searchValue(" + searchValue + "), mid = " + mid
                        + ", setting low = " + low);
            } else if (inpArr[mid] > searchValue) {
                high = mid - 1;
                System.out.println("inpArr[mid] (" + inpArr[mid] + ") > searchValue(" + searchValue + "), mid = " + mid
                        + ", setting high = " + high);
            } else if (inpArr[mid] == searchValue) {
                index = mid;
                System.out.println("found at index " + mid);
                break;
            }
        }
        return index;
    }
}
```

[Back to Table of Contents](#java-collections-framework)

## Is it possible for `HashMap` to degenerate into a list even with keys having different `hashCode()`?

This can occur if the method that determines the bucket index consistently returns the same value.

[Back to Table of Contents](#java-collections-framework)

## In what case can an element be lost in `HashMap`?

Assume a non-primitive key object with multiple fields. After adding an element to `HashMap`, one changes a field that influences the hash code computation on that object. Consequently, upon trying to locate the element with its original key, the right bucket will be accessed, but `equals()` will no longer find the indicated key in that list. However, even if `equals()` is designed in such a way that altering that field does not affect the result, after the number of buckets increases and hash codes of the elements are recalculated, that specified element having a modified field value will likely occupy a different bucket entirely, leading to loss.

[Back to Table of Contents](#java-collections-framework)

## Why can't you use `byte[]` as a key in `HashMap`?

The hash code of an array is not dependent on the elements stored within it; it is assigned upon the creation of the array (the hash code calculation method for an array is not overridden and is derived from the standard `Object.hashCode()` based on a prime number generation algorithm). Additionally, arrays do not override `equals`, leading to pointer comparison. As such, accessing an element saved with a key-array element cannot be done using another array of the same size and elements; this can occur only when using the same array reference that was used to store the element.

[Back to Table of Contents](#java-collections-framework)

## What is the role of `equals()` and `hashCode()` in `HashMap`?

`hashCode` helps identify the appropriate bucket for element searching, while `equals` is utilized for comparing the keys of elements in the bucket list and the target key.

[Back to Table of Contents](#java-collections-framework)

## What is the maximum number of `hashCode()` values?

The number of values follows from the signature `int hashCode()` and equals the range of the `int` type — **2<sup>32</sup>**.

[Back to Table of Contents](#java-collections-framework)

## What is the worst-case time complexity of the `get(key)` method for a key that is not in `HashMap`?

## What is the worst-case time complexity of the `get(key)` method for a key that is in `HashMap`?

**_O(N)_**. The worst-case scenario is searching for a key in a `HashMap` that has degenerated into a list, due to matching keys based on `hashCode()`, and to verify if an element with a particular key exists might require iterating through the entire list.

However, starting from Java 8, once a certain number of elements is reached in the list, the linked list is transformed into a red-black tree, which ensures logarithmic time complexity, even in cases of poor hash function performance, amounting to no worse than _O(log(N))_.

[Back to Table of Contents](#java-collections-framework)

## Why, despite the fact that a key in `HashMap` does not have to implement the `Comparable` interface, can a doubly linked list always be transformed into a red-black tree?

A red-black tree is a self-balancing binary search tree. This means that in order to build it, there should be some method to compare elements.

In Java, comparison of objects usually occurs via the method `compareTo()`, which is defined in the `Comparable` interface. At first glance, it might seem logical that after Java 8, an additional requirement for keys in `HashMap` should be to implement `Comparable`.

To avoid this, the following algorithm is used during key comparison:

1. First, it attempts to compare the hash codes of the keys;
2. If the hash codes are equal and both keys implement `Comparable`, the `compareTo()` method is called for comparison;
3. If the keys do not implement `Comparable`, they are compared using the method `tieBreakOrder()`, where
    - first, an attempt to compare keys via their class names (`getClass().getName()`) is made;
    - if the keys are instances of the same class, their results are compared using `System.identityHashCode()`.

[Back to Table of Contents](#java-collections-framework)

## How many transitions occur at the moment of calling `HashMap.get(key)` for a key that exists in the table?

-   For the key equal to `null`: **1** - only the `getForNullKey()` method is executed.
-   For any key other than `null`: **4** - calculation of the key's hash code; determination of the bucket number; search for the value; return the value.

[Back to Table of Contents](#java-collections-framework)

## How many new objects are created when you add a new element to `HashMap`?

**One** new object of the static nested class `Entry<K,V>` is created.

[Back to Table of Contents](#java-collections-framework)

## How and when does the number of buckets in `HashMap` increase?

Apart from `capacity`, `HashMap` also has a `loadFactor` field, based on which the maximum number of occupied buckets is calculated `capacity * loadFactor`. By default, `loadFactor = 0.75`. Upon reaching this maximum value, the number of buckets is increased by double, and new "positions" for all stored elements are recalculated based on the new number of buckets.

[Back to Table of Contents](#java-collections-framework)

## Explain the meaning of the parameters in the constructor `HashMap(int initialCapacity, float loadFactor)`.

-   `initialCapacity` - the initial size of the `HashMap`, the number of buckets in the hash table at the time of its creation.
-   `loadFactor` - the load factor of the `HashMap`, which dictates when the number of buckets is increased and automatic rehashing occurs. It is equal to the ratio of the already stored items in the table to its size.

[Back to Table of Contents](#java-collections-framework)

## Will `HashMap` work if all added keys have the same `hashCode()`?

Yes, it will work, but in this case, `HashMap` degenerates into a linked list and loses its benefits.

## How to iterate through all keys of a `Map`?

Use the `keySet()` method, which returns a `Set<K>` of keys.

[Back to Table of Contents](#java-collections-framework)

## How to iterate through all values of a `Map`?

Use the `values()` method, which returns a `Collection<V>` of values.

[Back to Table of Contents](#java-collections-framework)

## How to iterate through all key-value pairs in a `Map`?

Use the `entrySet()` method, which returns a `Set<Map.Entry<K, V>>` of "key-value" pairs.

[Back to Table of Contents](#java-collections-framework)

## What are the distinctions between `TreeSet` and `HashSet`?

`TreeSet` provides ordered storage of elements in the form of a red-black tree. The time complexity for the main operations is at least _O(log(N))_ (logarithmic time).

`HashSet` employs the same approach for storing elements as `HashMap`, with the exception that in `HashSet`, the element itself acts as both key and value, moreover, `HashSet` does not support ordered storage of elements and provides operation time complexity analogous to that of `HashMap`.

[Back to Table of Contents](#java-collections-framework)

## What happens if you add elements to `TreeSet` in ascending order?

`TreeSet` is based on a red-black tree, which can balance itself. As a result, `TreeSet` does not care in what order the elements are added; the advantages of this data structure are preserved.

[Back to Table of Contents](#java-collections-framework)

## How does `LinkedHashSet` differ from `HashSet`?

`LinkedHashSet` differs from `HashSet` only in that it is based on `LinkedHashMap` instead of `HashMap`. Thanks to this, the order of elements during traversal is identical to the order in which elements were added (insertion-order). When adding an element that is already present in the `LinkedHashSet` (i.e., with an identical key), the order of traversal over the elements does not change.

[Back to Table of Contents](#java-collections-framework)

## For `Enum`, there is a special class `java.util.EnumSet`. Why? What didn't the authors like about `HashSet` or `TreeSet`?

`EnumSet` is an implementation of the `Set` interface for use with enumerations (`Enum`). The data structure stores objects of only one `Enum` type specified at creation. For storing values, `EnumSet` utilizes a bit vector, which allows for high compactness and efficiency. Iterating through `EnumSet` proceeds according to the order of declaration of elements within the enumeration.

All main operations execute in _O(1)_ time and generally (but not guaranteed) faster than their `HashSet` counterparts, while batch operations (such as `containsAll()` and `retainAll()`) are even faster.

Furthermore, `EnumSet` offers numerous static initialization methods for simplified and convenient creation of instances.

[Back to Table of Contents](#java-collections-framework)

## What methods exist to iterate through the elements of a list?

-   Iterator loop

```java
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    //iterator.next();
}
```

-   For loop

```java
for (int i = 0; i < list.size(); i++) {
    //list.get(i);
}
```

-   While loop

```java
int i = 0;
while (i < list.size()) {
    //list.get(i);
    i++;
}
```

-   "for-each"

```java
for (String element : list) {
    //element;
}
```

[Back to Table of Contents](#java-collections-framework)

## How can you get synchronized objects of standard collections?

Using the static methods `synchronizedMap()` and `synchronizedList()` of the `Collections` class. These methods return a synchronized decorator for the provided collection. Nevertheless, even when iterating over the collection, manual synchronization is required.

```java
  Map m = Collections.synchronizedMap(new HashMap());
  List l = Collections.synchronizedList(new ArrayList());
```

Starting from Java 6, the JCF was expanded with specialized collections that support multithreaded access, such as `CopyOnWriteArrayList` and `ConcurrentHashMap`.

[Back to Table of Contents](#java-collections-framework)

## How to obtain a read-only collection?

Using:

-   `Collections.unmodifiableList(list)`;
-   `Collections.unmodifiableSet(set)`;
-   `Collections.unmodifiableMap(map)`.

These methods take a collection as a parameter, returning a read-only collection with the same internal elements.

[Back to Table of Contents](#java-collections-framework)

## Write a single-threaded program that causes a collection to throw `ConcurrentModificationException`.

```java
public static void main(String[] args) {
    List<Integer> list = new ArrayList<>();
    list.add(1);
    list.add(2);
    list.add(3);

    for (Integer integer : list) {
        list.remove(1);
    }
}
```

[Back to Table of Contents](#java-collections-framework)

## Provide an example where a collection throws `UnsupportedOperationException`.

```java
public static void main(String[] args) {
    List<Integer> list = Collections.emptyList();
    list.add(0);
}
```

[Back to Table of Contents](#java-collections-framework)

## Implement the symmetric difference of two collections using `Collection` methods (`addAll(...)`, `removeAll(...)`, `retainAll(...)`).

The symmetric difference of two collections is the set of elements belonging to either of the two initial collections, but not both.

```java
<T> Collection<T> symmetricDifference(Collection<T> a, Collection<T> b) {
    // Combine collections.
    Collection<T> result = new ArrayList<>(a);
    result.addAll(b);

    // Get the intersection of collections.
    Collection<T> intersection = new ArrayList<>(a);
    intersection.retainAll(b);

    // Remove elements located in both collections.
    result.removeAll(intersection);

    return result;
}
```

[Back to Table of Contents](#java-collections-framework)

## How to create a cache with an "invalidation policy" using LinkedHashMap?

It is necessary to use an _LRU algorithm (Least Recently Used algorithm)_ and `LinkedHashMap` with access-order. In this case, upon accessing an element, it will shift to the end of the list, and the least used elements will gradually cluster at the beginning of the list. Additionally, in the standard implementation `LinkedHashMap`, there is a method `removeEldestEntries()` that returns `true` if the current `LinkedHashMap` object should remove the least used element from the collection when using `put()` and `putAll()` methods.

```java
public class LRUCache<K, V> extends LinkedHashMap<K, V> {
    private static final int MAX_ENTRIES = 10;

    public LRUCache(int initialCapacity) {
        super(initialCapacity, 0.85f, true);
    }

    @Override
    protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
        return size() > MAX_ENTRIES;
    }
}
```

It is worth noting that `LinkedHashMap` does not completely implement the LRU algorithm, since when an already existing item in the collection is inserted, the order of iteration across the elements does not change.

[Back to Table of Contents](#java-collections-framework)

## How to copy elements of any `collection` into an array in a single line?

```java
Object[] array = collection.toArray();
```

[Back to Table of Contents](#java-collections-framework)

## How to get a `List` with all elements except the first and last 3 in a single call from `List`?

```java
List<Integer> subList = list.subList(3, list.size() - 3);
```

[Back to Table of Contents](#java-collections-framework)

## How to convert `HashSet` to `ArrayList` in a single line?

```java
ArrayList<Integer> list = new ArrayList<>(new HashSet<>());
```

[Back to Table of Contents](#java-collections-framework)

## How to convert `ArrayList` to `HashSet` in a single line?

```java
HashSet<Integer> set = new HashSet<>(new ArrayList<>());
```

[Back to Table of Contents](#java-collections-framework)

## Create a `HashSet` from the keys of a `HashMap`.

```java
HashSet<Object> set = new HashSet<>(map.keySet());
```

[Back to Table of Contents](#java-collections-framework)

## Create a `HashMap` from `HashSet<Map.Entry<K, V>>`.

```java
HashMap<K,V> map = new HashMap<>(set.size());
for (Map.Entry<K,V> entry : set) {
    map.put(entry.getKey(), entry.getValue());
}
```

[Back to Table of Contents](#java-collections-framework)

# Source

-   [parshinpn.pro](http://www.parshinpn.pro/content/voprosy-i-otvety-na-sobesedovanii-po-teme-java-collection-framework-chast-1)
-   [Habr](https://habrahabr.ru/post/162017/)
-   [Quizful](http://www.quizful.net/interview/java)
-   [JavaRush](http://info.javarush.ru/)
-   [Habr: Java Collections Framework Guide](https://habrahabr.ru/post/237043/)

[Interview Questions](README.md)
