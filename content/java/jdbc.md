---
title: JDBC Interview Questions
date: 2023-10-10
tags: [JDBC, Java, Interview Questions, Database]
---

# JDBC

-   [What is _JDBC_?](#what-is-jdbc)
-   [What are the advantages of using JDBC?](#what-are-the-advantages-of-using-jdbc)
-   [What is a JDBC URL?](#what-is-a-jdbc-url)
-   [What components make up JDBC?](#what-components-make-up-jdbc)
-   [List the main classes and interfaces in JDBC.](#list-the-main-classes-and-interfaces-in-jdbc)
-   [Describe the main steps for working with the database using JDBC.](#describe-the-main-steps-for-working-with-the-database-using-jdbc)
-   [List the main data types used in JDBC. How are they related to Java types?](#list-the-main-data-types-used-in-jdbc-how-are-they-related-to-java-types)
-   [How do you register a JDBC driver?](#how-do-you-register-a-jdbc-driver)
-   [How do you establish a connection to a database?](#how-do-you-establish-a-connection-to-a-database)
-   [What transaction isolation levels are supported in JDBC?](#what-transaction-isolation-levels-are-supported-in-jdbc)
-   [How are database queries formed?](#how-are-database-queries-formed)
-   [What is the difference between Statement and PreparedStatement?](#what-is-the-difference-between-statement-and-preparedstatement)
-   [How is a database query executed and results processed?](#how-is-a-database-query-executed-and-results-processed)
-   [How do you call a stored procedure?](#how-do-you-call-a-stored-procedure)
-   [How do you close the connection to the database?](#how-do-you-close-the-connection-to-the-database)

## What is _JDBC_?

**JDBC, Java DataBase Connectivity** — an industry standard for connecting Java applications to various databases. It is implemented as part of the `java.sql` package that comes with Java SE.

JDBC is based on the concept of drivers that enable connecting to a database via a specially defined URL. When the driver is loaded, it registers itself with the system and is automatically invoked when the application requests a URL that contains the protocol for which the driver is responsible.

[Back to table of contents](#jdbc)

## What are the advantages of using JDBC?

The advantages of JDBC include:

-   Ease of development: developers are not required to know the specifics of the database they are working with.
-   Code remains largely unchanged when transitioning to a different database (the number of changes depends solely on the differences between SQL dialects).
-   No need to install a separate client application.
-   Any database can be connected through an easily described URL.

[Back to table of contents](#jdbc)

## What is a JDBC URL?

A **JDBC URL** consists of:

-   `<protocol>:` (protocol) - always `jdbc:`.
-   `<subprotocol>:` (subprotocol) - the name of the driver or the connection mechanism to the database. The subprotocol may be supported by one or more drivers. A prominent example of a subprotocol is "odbc", designated for URLs that denote the name of an ODBC data source. If a name service is necessary (i.e., the database name in the JDBC URL is not an actual database name), the subprotocol may refer to that name service.
-   `<subname>` (subname) - the identifier for the database. The value of the subname may vary depending on the subprotocol and may also have subdivisions whose syntax is defined by the driver developer. The purpose of the subname is to provide all the information required to locate the database. For example, if the database is located on the Internet, the subname of the JDBC URL should include a network address following the format: `//<hostname>:<port>/<subsubname>`.

An example of a JDBC URL for connecting to a MySQL database "Test" located at localhost and listening for connections on port 3306 would be: `jdbc:mysql://localhost:3306/Test`

[Back to table of contents](#jdbc)

## What components make up JDBC?

JDBC consists of two parts:

-   **JDBC API**, which contains a set of classes and interfaces that define access to databases. These classes and methods are declared in two packages: `java.sql` and `javax.sql`.
-   **JDBC driver**, a component specific to each database.

JDBC converts API-level calls into native commands for a particular database server.

[Back to table of contents](#jdbc)

## List the main classes and interfaces in JDBC.

-   `java.sql.DriverManager` - allows loading and registering the necessary JDBC driver, and subsequently obtaining a connection to the database.

-   `javax.sql.DataSource` - serves the same purposes as _DriverManager_ but in a more convenient and versatile way. There are also `javax.sql.ConnectionPoolDataSource` and `javax.sql.XADataSource`, which aim to support connection pooling.

-   `java.sql.Connection` - provides methods for forming queries against the data source and managing transactions. It also includes interfaces like `javax.sql.PooledConnection` and `javax.sql.XAConnection`.

-   `java.sql.Statement`, `java.sql.PreparedStatement`, and `java.sql.CallableStatement` - these interfaces allow sending queries to the data source.

-   `java.sql.ResultSet` - declares methods to traverse a set of data and read values from individual fields in the current record.

-   `java.sql.ResultSetMetaData` - allows obtaining information about the structure of the data set.

-   `java.sql.DatabaseMetaData` - allows obtaining information about the structure of the data source.

[Back to table of contents](#jdbc)

## List the main data types used in JDBC. How are they related to Java types?

|         JDBC Type | Java Object Type       |
| ----------------: | ---------------------- |
|          **CHAR** | `String`               |
|       **VARCHAR** | `String`               |
|   **LONGVARCHAR** | `String`               |
|       **NUMERIC** | `java.math.BigDecimal` |
|       **DECIMAL** | `java.math.BigDecimal` |
|           **BIT** | `Boolean`              |
|       **TINYINT** | `Integer`              |
|      **SMALLINT** | `Integer`              |
|       **INTEGER** | `Integer`              |
|        **BIGINT** | `Long`                 |
|          **REAL** | `Float`                |
|         **FLOAT** | `Double`               |
|        **DOUBLE** | `Double`               |
|        **BINARY** | `byte[]`               |
|     **VARBINARY** | `byte[]`               |
| **LONGVARBINARY** | `byte[]`               |
|          **DATE** | `java.sql.Date`        |
|          **TIME** | `java.sql.Time`        |
|     **TIMESTAMP** | `java.sql.Timestamp`   |
|          **CLOB** | `Clob`                 |
|          **BLOB** | `Blob`                 |
|         **ARRAY** | `Array`                |
|        **STRUCT** | `Struct`               |
|           **REF** | `Ref`                  |
|      **DISTINCT** | mapping of base type   |
|   **JAVA_OBJECT** | Java base class        |

[Back to table of contents](#jdbc)

## Describe the main steps for working with the database using JDBC.

-   Registering drivers;
-   Establishing a connection to the database;
-   Creating queries to the database;
-   Executing queries to the database;
-   Processing results;
-   Closing the connection to the database.

[Back to table of contents](#jdbc)

## How do you register a JDBC driver?

A driver can be registered in several ways:

-   `java.sql.DriverManager.registerDriver(driverObject);`.

-   `Class.forName("fully qualified driver class name").newInstance();`.

-   `Class.forName("fully qualified driver class name");`.

[Back to table of contents](#jdbc)

## How do you establish a connection to a database?

To establish a connection to a database, the static call `java.sql.DriverManager.getConnection(...)` is used.

You can pass as parameters:

-   Database URL

```java
static Connection getConnection(String url)
```

-   Database URL and a set of properties for initialization

```java
static Connection getConnection(String url, Properties info)
```

-   Database URL, username, and password

```java
static Connection getConnection(String url, String user, String password)
```

As a result of the call, a connection to the database will be established, and an object of the class `java.sql.Connection` will be created - a sort of "session" within which the further work with the database will occur.

[Back to table of contents](#jdbc)

## What transaction isolation levels are supported in JDBC?

**Transaction isolation level** - a value that defines how much a transaction is allowed to see uncommitted data, thus indicating the degree of isolation of one transaction from another. A higher isolation level increases data accuracy but may reduce the number of concurrent transactions. Conversely, a lower isolation level allows more concurrent transactions but reduces data accuracy.

When using transactions, to ensure data integrity, the DBMS uses locks to restrict access to data involved in the transaction. Such locks are necessary to prevent:

-   _Dirty reads_ - reading data that has been added or changed by a transaction that is subsequently rolled back.

-   _Non-repeatable reads_ - when the same data is read multiple times within a single transaction and the data is found to have changed.

-   _Phantom reads_ - when re-reading within a single transaction yields different sets of rows.

Transaction isolation levels are defined as constants in the `java.sql.Connection` interface:

-   `TRANSACTION_NONE` – the driver does not support transactions;

-   `TRANSACTION_READ_UNCOMMITTED` – allows transactions to see uncommitted data changes: permits dirty, non-repeatable, and phantom reads;

-   `TRANSACTION_READ_COMMITTED` – any change made in a transaction is not visible outside of it until it is committed: prevents dirty reads but allows non-repeatable and phantom reads;

-   `TRANSACTION_REPEATABLE_READ` – prevents dirty and non-repeatable reads but allows phantom reads;

-   `TRANSACTION_SERIALIZABLE` – prevents dirty, non-repeatable, and phantom reads.

> **NB!** The database server might not support all isolation levels. The `java.sql.DatabaseMetaData` interface provides information on the transaction isolation levels supported by a specific DBMS.

The isolation level used by the DBMS can be set using the method `setTransactionIsolation()` of the `java.sql.Connection` object. You can check the currently applied isolation level using the method `getTransactionIsolation()`.

[Back to table of contents](#jdbc)

## How are database queries formed?

In Java, three interfaces are used for executing database queries:

-   `java.sql.Statement` - for SQL statements without parameters;
-   `java.sql.PreparedStatement` - for SQL statements with parameters and frequently executed statements;
-   `java.sql.CallableStatement` - for executing stored procedures.

The objects implementing these interfaces are created using methods from the `java.sql.Connection` object:

-   `java.sql.createStatement()` returns a _Statement_ object;
-   `java.sql.prepareStatement()` returns a _PreparedStatement_ object;
-   `java.sql.prepareCall()` returns a _CallableStatement_ object;

[Back to table of contents](#jdbc)

## What is the difference between Statement and PreparedStatement?

-   **Statement**: used for simple queries without parameters.
-   **PreparedStatement**: precompiles the query, which may contain input parameters and can be executed multiple times with different sets of these parameters.

Before execution, the DBMS parses each query, optimizes it, and creates an execution "plan." If the same query is executed multiple times, the DBMS can cache the execution plan, avoiding the parsing and optimization steps again. This allows the query to execute faster.

In summary, _PreparedStatement_ is advantageous over _Statement_ in that its repeated use with one or multiple parameter sets allows one to take advantage of the precompiled and cached query, while also helping to avoid SQL Injection.

[Back to table of contents](#jdbc)

## How is a database query executed and results processed?

Query execution is performed by invoking methods on the object implementing the `java.sql.Statement` interface:

-   **`executeQuery()`** - for queries that return a single result set, such as `SELECT` queries. The result of the execution is an object of class `java.sql.ResultSet`;

-   **`executeUpdate()`** - for executing `INSERT`, `UPDATE`, or `DELETE` statements, as well as for _DDL_ (Data Definition Language) statements. The method returns an integer indicating how many records were modified;

-   **`execute()`** – executes SQL commands that may return various results. For example, it may be used for the `CREATE TABLE` operation. It returns `true` if the first result is a _ResultSet_ and `false` if the first result is a count of modified records or if no result exists. To retrieve the first result, you need to call the `getResultSet()` or `getUpdateCount()` methods. Any additional results can be accessed via calls to `getMoreResults()`, which may be called multiple times if necessary.

An object with the `java.sql.ResultSet` interface holds the result of the database query - a data set containing a cursor pointing to one of the elements in the set - the current record.

Using the cursor, you can navigate through the data set with the method `next()`.

> **NB!** Immediately after obtaining the data set, its cursor is positioned before the first record, and to make it current, you need to call the `next()` method.

The fields of the current record can be accessed using the methods `getInt()`, `getFloat()`, `getString()`, `getDate()`, and similar.

[Back to table of contents](#jdbc)

## How do you call a stored procedure?

**Stored procedures** are named sets of SQL statements stored on the server. You can call such a procedure from a Java class using the methods of an object implementing the `java.sql.Statement` interface.

The choice of object depends on the characteristics of the stored procedure:

-   without parameters → `Statement`
-   with input parameters → `PreparedStatement`
-   with input and output parameters → `CallableStatement`

> If you are unsure how the stored procedure is defined, you can use the `java.sql.DatabaseMetaData` methods to gather information about the structure of the data source, including names and types of parameters.

Example of calling a stored procedure with input and output parameters:

```java
public void runStoredProcedure(final Connection connection) throws Exception {
    // define the stored procedure
    String procedure = "{ call procedureExample(?, ?, ?) }";

    // prepare the statement
    CallableStatement cs = connection.prepareCall(procedure);

    // set input parameters
    cs.setString(1, "abcd");
    cs.setBoolean(2, true);
    cs.setInt(3, 10);

    // describe output parameters
    cs.registerOutParameter(1, java.sql.Types.VARCHAR);
    cs.registerOutParameter(2, java.sql.Types.INTEGER);

    // execute the stored procedure
    cs.execute();

    // obtain results
    String parameter1 = cs.getString(1);
    int parameter2 = cs.getInt(2);

    // finalize the request
    cs.close();
}
```

[Back to table of contents](#jdbc)

## How do you close the connection to the database?

The connection to the database is closed by calling the `close()` method on the corresponding `java.sql.Connection` object or by using the try-with-resources mechanism when creating such an object, which was introduced in Java 7.

> **NB!** You must first close all requests created by this connection.

[Back to table of contents](#jdbc)

# Sources

-   [Wikipedia - JDBC](https://en.wikipedia.org/wiki/Java_Database_Connectivity)
-   [IBM developerWorks®](http://www.ibm.com/developerworks/ru/library/dm-1209storedprocedures/)
-   [Java.sql Package Documentation](https://docs.oracle.com/javase/7/docs/api/java/sql/package-summary.html)
-   [Wikipedia - Transaction Isolation Level](https://en.wikipedia.org/wiki/Isolation_level)

[Back to interview questions](README.md)
