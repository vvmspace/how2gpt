---
title: "DB Interview Questions"
date: 2023-10-20
tags: ["Databases", "Interview Questions", "SQL"]
---

# Databases

-   [What is a _"database"_?](#what-is-a-database)
-   [What is a _"database management system"_?](#what-is-a-database-management-system)
-   [What is a _"relational data model"_?](#what-is-a-relational-data-model)
-   [Define the terms _"simple"_, _"composite"_, _"candidate"_, and _"alternate"_ key.](#define-the-terms-simple-composite-candidate-and-alternate-key)
-   [What is a _"primary key"_? What are the criteria for its selection?](#what-is-a-primary-key-what-are-the-criteria-for-its-selection)
-   [What is a _"foreign key"_?](#what-is-a-foreign-key)
-   [What is _"normalization"_?](#what-is-normalization)
-   [What normal forms exist?](#what-normal-forms-exist)
-   [What is _"denormalization"_? What is it applied for?](#what-is-denormalization-what-is-it-applied-for)
-   [What types of relationships exist in a database? Provide examples.](#what-types-of-relationships-exist-in-a-database-provide-examples)
-   [What are _"indexes"_? Why are they used? What are their advantages and disadvantages?](#what-are-indexes-why-are-they-used-what-are-their-advantages-and-disadvantages)
-   [What types of indexes exist?](#what-types-of-indexes-exist)
-   [What is the difference between clustered and non-clustered indexes?](#what-is-the-difference-between-clustered-and-non-clustered-indexes)
-   [Does it make sense to index data with a small number of possible values?](#does-it-make-sense-to-index-data-with-a-small-number-of-possible-values)
-   [When is a full scan of the dataset more beneficial than indexed access?](#when-is-a-full-scan-of-the-dataset-more-beneficial-than-indexed-access)
-   [What is a _"transaction"_?](#what-is-a-transaction)
-   [Name the main properties of a transaction.](#name-the-main-properties-of-a-transaction)
-   [What levels of transaction isolation exist?](#what-levels-of-transaction-isolation-exist)
-   [What problems can arise during concurrent access using transactions?](#what-problems-can-arise-during-concurrent-access-using-transactions)

## What is a _"database"_?

A **database** is an organized collection of information that is structured to be processed by a computing system.

[Back to table of contents](#databases)

## What is a _"database management system"_?

A **database management system (DBMS)** is a set of tools, either general-purpose or specialized, that provides the ability to create, access, and manage a database.

The main functions of a DBMS include:

-   Data management
-   Data change logging
-   Data backup and recovery
-   Support for data definition and manipulation languages.

[Back to table of contents](#databases)

## What is a _"relational data model"_?

The **relational data model** is a logical framework for data representation and a theoretical foundation for constructing relational databases.

The relational data model comprises the following components:

-   _Structural aspect_ — data are represented as a set of relations.
-   _Integrity aspect_ — relations meet specific integrity conditions at domain (data type), relation, and database levels.
-   _Processing (manipulation) aspect_ — supports operators for manipulating relations (relational algebra, relational calculus).
-   _Normal form_ — the property of a relation in the relational data model that characterizes it in terms of redundancy and is defined as a set of requirements that must be satisfied by the relation.

[Back to table of contents](#databases)

## Define the terms _"simple"_, _"composite"_, _"candidate"_, and _"alternate"_ key.

A **simple key** consists of a single attribute (field). A **composite key** consists of two or more attributes.

A **candidate key** is either a simple or composite key that uniquely identifies each record in a dataset. It must satisfy the criterion of non-redundancy: removing any of the fields will cause the set of fields to no longer uniquely identify the record.

From the set of all candidate keys for a dataset, a primary key is chosen, while the remaining keys are referred to as **alternate keys**.

[Back to table of contents](#databases)

## What is a _"primary key"_? What are the criteria for its selection?

A **primary key** in the relational data model is one of the _candidate keys_ of a relation selected as the main key (default key).

If a relation has a single candidate key, it serves as the primary key. If there are multiple candidate keys, one is chosen as the primary, while the others are referred to as _"alternate keys"_.

Typically, the most convenient candidate key is selected as the primary key. Thus, the primary key is usually chosen to have the smallest size (physical storage) and/or include the fewest attributes. Another criterion for selecting a primary key is the preservation of its uniqueness over time. Therefore, it is preferable to choose a candidate key that is likely to maintain its uniqueness.

[Back to table of contents](#databases)

## What is a _"foreign key"_?

A **foreign key** is a subset of attributes of a relation A, whose values must match the values of a candidate key from another relation B.

[Back to table of contents](#databases)

## What is _"normalization"_?

_Normalization_ is the process of transforming database relations into a form that meets the normal forms (a step-by-step, reversible process of replacing an original schema with another schema in which data sets have a simpler and more logical structure).

Normalization aims to bring the database structure to a state that ensures minimal logical redundancy and is not intended to reduce or increase performance or to change the physical size of the database. The ultimate goal of normalization is to reduce the potential inconsistency of the data stored in the database.

[Back to table of contents](#databases)

## What normal forms exist?

The **First Normal Form (1NF)** — A relation is in 1NF if all its attributes' values are atomic (indivisible).

The **Second Normal Form (2NF)** — A relation is in 2NF if it is in 1NF, and all non-key attributes depend only on the key as a whole, not on any part of it.

The **Third Normal Form (3NF)** — A relation is in 3NF if it is in 2NF and all non-key attributes do not depend on one another.

The **Fourth Normal Form (4NF)** — A relation is in 4NF if it is in 3NF and does not contain independent groups of attributes between which there is a "many-to-many" relationship.

The **Fifth Normal Form (5NF)** — A relation is in 5NF when every non-trivial join dependency in it is defined by a candidate key(s) of that relation.

The **Sixth Normal Form (6NF)** — A relation is in 6NF when it satisfies all non-trivial join dependencies, meaning it is irreducible and cannot be further decomposed without loss. Every relation in 6NF is also in 5NF. It is introduced as a generalization of the fifth normal form for temporal databases.

The **Boyce-Codd Normal Form (BCNF)** — A relation is in BCNF when every non-trivial and irreducible left functional dependency has as its determinant a candidate key.

The **Domain-Key Normal Form (DKNF)** — A relation is in DKNF if every constraint imposed on it is a logical consequence of the domain and key constraints imposed on the given relation.

[Back to table of contents](#databases)

## What is _"denormalization"_? What is it applied for?

**Denormalization of a database** is the process of intentionally converting a database into a form that does not conform to normalization rules. This is usually necessary to improve performance and data extraction speed by increasing data redundancy.

[Back to table of contents](#databases)

## What types of relationships exist in a database? Provide examples.

-   **One-to-One** — Each value of attribute A corresponds to only one value of attribute B, and vice versa.

> Each university is guaranteed to have one rector: _1 university → 1 rector_.

-   **One-to-Many** — Each value of attribute A corresponds to 0, 1, or multiple values of attribute B.

> Every university has several faculties: _1 university → many faculties_.

-   **Many-to-Many** — Each value of attribute A corresponds to 0, 1, or multiple values of attribute B, and each value of attribute B corresponds to 0, 1, or multiple values of attribute A.

> One professor can teach in several faculties, while one faculty can have many professors: _Several professors ↔ Several faculties_.

[Back to table of contents](#databases)

## What are _"indexes"_? Why are they used? What are their advantages and disadvantages?

An **index** is a database object created to improve the performance of data retrieval.

Data sets can have a large number of records stored in arbitrary order, and searching them by a given criterion through sequential scanning one record at a time can take a long time. An index is formed from the values of one or several fields and pointers to the corresponding records in the dataset, thus achieving a significant speed increase in data retrieval.

### Advantages

-   Speeds up searches and sorting by a certain field or set of fields.
-   Ensures data uniqueness.

### Disadvantages

-   Requires additional disk and memory space, and the larger/longer the key, the larger the index size.
-   Slows down insert, update, and delete operations, as the indexes themselves must also be updated.

Indexes are preferable for:

-   Counter fields to avoid repetition of values in this field;
-   Fields used for sorting data;
-   Fields frequently used for joining data sets, as indexed data is arranged in ascending order which significantly speeds up the join process;
-   Fields declared as primary keys;
-   Fields from which data is selected from a certain range. Once the first record with the required value is found, all subsequent values will be adjacent.

Using indexes is not advisable for:

-   Fields that are rarely used in queries;
-   Fields containing only two or three values, such as: _male_, _female_ or values _"yes"_, _"no"_.

[Back to table of contents](#databases)

## What types of indexes exist?

### By sort order

-   _Ordered_ — indexes where elements are sorted;
-   _Ascending_;
-   _Descending_;
-   _Unordered_ — indexes where elements are not sorted.

### By data source

-   _View indexes_;
-   _Expression indexes_.

### By impact on data source

-   _Clustered index_ — physically reorganizes data within the dataset according to the structure of the index. In this case, the logical structure of the dataset resembles a dictionary more than an index. Data in the dictionary is physically sorted, e.g., alphabetically. Clustered indexes can significantly improve data search performance, especially with sequential data.
-   _Non-clustered index_ — the most typical representatives of the index family. Unlike clustered indexes, they do not reorganize the physical structure of the dataset but organize links to the corresponding records. To identify the required record within the dataset, a non-clustered index organizes special pointers containing: information about the file ID in which the record is stored; the page ID of relevant data; the record number on the corresponding page; the contents of the column.

### By structure

-   _B\*-trees_;
-   _B+-trees_;
-   _B-trees_;
-   _Hashes_.

### By numerical composition

-   _Simple index (single-key index)_ — builds on a single field;
-   _Composite (multi-key, compound) index_ — is built on multiple fields while the order of those fields matters;
-   _Index with included columns_ — a non-clustered index that additionally contains non-key columns alongside key columns;
-   _Primary index (index on primary key)_ — the index key currently managing the dataset. A dataset cannot be sorted by multiple index keys simultaneously. However, if the same dataset is opened in multiple workspaces, each instance can have its own primary index.

### By content characteristics

-   _Unique index_ consists of a set of unique field values;
-   _Dense index_ (NoSQL) — an index where each document in the indexed collection corresponds to a record in the index, even if the document lacks the indexed field.
-   _Sparse index_ (NoSQL) — one in which only those documents that have some specific value (exist) for the indexed key are represented.
-   _Spatial index_ — optimized for describing geographic locations. It is a multi-key index consisting of latitude and longitude.
-   _Composite spatial index_ — includes not only latitude and longitude but also other metadata (e.g., tags). However, geographical coordinates must come first.
-   _Full-text (inverted) index_ — a dictionary listing all words and their occurrences. When such an index exists, searching for words yields a list of documents in which they occur.
-   _Hash index_ stores not the actual values but their hashes, reducing the size (and hence increasing the processing speed) of indexes for large fields. Thus, when queries use hash indexes, hashes of the sought values are compared to field hashes instead.
    Due to the nonlinear nature of hash functions, this index cannot be sorted by value, making it impossible to use it in greater/less comparisons and for "is null". Additionally, since hashes are not unique, collision resolution methods are necessary for matching hashes.
-   _Bitmap index_ — methods of bitmap indexing involve creating separate bitmaps (sequences of 0s and 1s) for each possible value of a column, where each bit corresponds to a record with an indexed value, and a value of 1 indicates that the record corresponding to the bit position contains the indexed value for that column or attribute.
-   _Reverse index_ — a B-tree index with a reversed key, mainly used for monotonically increasing values (e.g., auto-incrementing IDs) in OLTP systems to reduce competition for the last leaf block of the index. By reversing the values, two adjacent index records end up in different blocks of the index. It cannot be used for range searches.
-   _Functional index, index on computed field_ — an index storing the results of user-defined functions. Functional indexes are often built for fields whose values undergo preprocessing before comparison in SQL queries. For example, when comparing string data without case sensitivity, the UPPER function is commonly used. Furthermore, functional indexes can serve to implement any other types of indexes that the current DBMS lacks.
-   _Primary index_ — a unique index on the primary key field.
-   _Secondary index_ — an index on fields other than the primary key field.
-   _XML index_ — a materialized slice of large binary XML objects (BLOBs) in a column with an XML data type.

### By update mechanism

-   _Fully rebuildable_ — the entire index is rebuilt when an element is added.
-   _Incremental (balanced)_ — the index is partially rebuilt during element addition (e.g., one branch) and is periodically balanced.

### By coverage of indexed content

-   _Fully covering (complete) index_ — covers all content of the indexed object.
-   _Partial index_ — an index built on a portion of the dataset that meets certain index conditions. This index is created to reduce index size.
-   _Incremental (delta) index_ — indexes a small portion of data (delta), typically after a certain duration. Used during intensive writes. For example, a complete index is rebuilt once a day while a delta index is constructed every hour. Essentially, a partial index with a timestamp.
-   _Real-time index_ — a special type of incremental index characterized by a high build speed. Designed for frequently changing data.

### Indexes in clustered systems

-   _Global index_ — an index covering all content of all database segments (shards).
-   _Segment index_ — a global index on a segmented key field. Used to quickly determine the segment storing data during query routing in a database cluster.
-   _Local index_ — an index covering the content of just one database segment.

[Back to table of contents](#databases)

## What is the difference between clustered and non-clustered indexes?

Non-clustered indexes have data physically arranged in arbitrary order but logically organized according to the index. This index type is suitable for frequently modified datasets.

In clustered indexing, data is physically ordered, significantly enhancing data retrieval speeds (but only during sequential data access). Only one clustered index can be created for any dataset.

[Back to table of contents](#databases)

## Does it make sense to index data with a small number of possible values?

A guiding rule when creating an index is: if the volume of information (in bytes) that does NOT meet the selection condition is less than the size of the index (in bytes) for that selection condition, then generally, this optimization will slow down retrieval.

[Back to table of contents](#databases)

## When is a full scan of the dataset more beneficial than indexed access?

A full scan is performed through multi-block reading. Index access is done through single-block reading. Additionally, when accessing via an index, the index must first be scanned, followed by reading blocks from the dataset. The number of blocks that need to be read from the dataset depends on the clustering factor. If the total cost of all necessary single block reads exceeds the cost of a full multi-block scan, then the full scan is chosen by the optimizer.

Thus, a full scan is typically chosen with weak selectivity of the query predicates and/or weak clustering of the data, or in cases of very small datasets.

[Back to table of contents](#databases)

## What is a _"transaction"_?

A **transaction** is an operation on the database that transforms it from one consistent state to another, manifested by changes to the data stored in the database.

[Back to table of contents](#databases)

## Name the main properties of a transaction.

**Atomicity** ensures that no transaction will be partially committed in the system. Either all its sub-operations will be executed or none at all.

**Consistency**. A transaction that reaches its normal conclusion and thereby commits its results maintains the consistency of the database.

**Isolation**. During the execution of a transaction, concurrent transactions should not affect its outcome.

**Durability**. Regardless of problems at lower levels (e.g., power failures or hardware faults), changes made by a successfully completed transaction must remain saved once the system is back online.

[Back to table of contents](#databases)

## What levels of transaction isolation exist?

In order of increasing isolation levels and therefore reliability in data handling:

-   **Read Uncommitted (dirty read)** — reading uncommitted changes from both its transaction and concurrent transactions. There is no guarantee that data changed by other transactions will not be changed again due to their rollback, making such reads a potential source of errors. Lost updates, non-repeatable reads, and phantom reads are possible.
-   **Read Committed** — reading all changes from its own transaction and the committed changes of concurrent transactions. Lost updates and dirty reads are not allowed, but non-repeatable reads and phantom reads are possible.
-   **Repeatable Read (snapshot)** — all changes from its transaction are read, and changes made by concurrent transactions after its start are not accessible. Lost updates, dirty, and non-repeatable reads are impossible, but phantom reads are possible.
-   **Serializable** — the result of concurrently executing a serializable transaction alongside other transactions should be logically equivalent to the result of any sequential execution of those transactions. Synchronization issues do not arise.

[Back to table of contents](#databases)

## What problems can arise during concurrent access using transactions?

When transactions are executed concurrently, the following issues may occur:

-   **Lost Update** — when two transactions concurrently alter the same data block, one of the updates gets lost;
-   **Dirty Read** — reading data added or changed by a transaction that later does not commit (rolls back);
-   **Non-repeatable Read** — when reading the same data multiple times within a single transaction gives modified results;
-   **Phantom Reads** — one transaction selects a set of records multiple times based on the same criteria during its execution. Another transaction between these selections adds, deletes, or modifies certain records used as selection criteria in the first transaction, completing successfully. This results in different sets of records from the same selection in the first transaction.
    Assume there are two transactions opened by different applications, executing the following SQL commands:

| Transaction 1                            | Transaction 2             |
| ---------------------------------------- | ------------------------- |
|                                          | SELECT SUM(f2) FROM tbl1; |
| INSERT INTO tbl1 (f1,f2) VALUES (15,20); |                           |
| COMMIT;                                  |                           |
|                                          | SELECT SUM(f2) FROM tbl1; |

In Transaction 2, a SQL command using all values of field f2 is executed. Then in Transaction 1, a new row insertion occurs, causing the re-execution of the SQL command in Transaction 2 to yield a different result. This situation is called phantom reading. It differs from non-repeatable reads in that the change occurs not due to updates or deletions of existing data, but due to the new phantom data emergence.

[Back to table of contents](#databases)

# Sources

-   [Wikipedia](https://en.wikipedia.org/wiki/)
-   [tokarchuk.ru](http://tokarchuk.ru/2012/08/indexes-classification/)
-   [Quizful](http://www.quizful.net/interview/sql/)
