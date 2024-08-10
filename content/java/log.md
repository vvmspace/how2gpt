---
title: Logging
date: 2023-10-01
tags: [log4j, logging, interview questions]
---

# Interview Questions

[Interview Questions](README.md)

# Logging

-   [What types of logs exist?](#what-types-of-logs-exist)
-   [What are the components of the log4j logging system?](#what-are-the-components-of-the-log4j-logging-system)
-   [What is a _Logger_ in log4j?](#what-is-a-logger-in-log4j)
-   [What is an _Appender_ in log4j?](#what-is-an-appender-in-log4j)
-   [What is a _Layout_ in log4j?](#what-is-a-layout-in-log4j)
-   [List the logging levels in log4j. What is their priority order?](#list-the-logging-levels-in-log4j-what-is-their-priority-order)
-   [What configuration methods exist for log4j?](#what-configuration-methods-exist-for-log4j)

## What types of logs exist?

-   System;
-   Security;
-   Application (Business).

> A user logs into the application, and their password is verified. This action pertains to security. Next, they launch a module. This event is at the application level. The module then requests additional data from another module and makes further calls—these are system actions.

[Back to Table of Contents](#logging)

## What are the components of the log4j logging system?

The logging system consists of three main parts:

-   A logging controller - **logger**;
-   A mechanism that writes to the log - **appender**;
-   A format definition for added logs - **layout**.

[Back to Table of Contents](#logging)

## What is a _Logger_ in log4j?

A **Logger** is an object of the class `org.apache.log4j.Logger`, which serves as the control interface for logging messages and can set the level of detail. The logger checks whether a message needs to be processed, and if logging is necessary, it passes the message to the appender; if not, processing of that message is terminated.

[Back to Table of Contents](#logging)

## What is an _Appender_ in log4j?

An **Appender** is a named event logging object that implements the `org.apache.log4j.Appender` interface and writes events to the log. The appender can call various helper tools—like a layout, filter, or error handler (if defined and needed). During this process, the necessity of recording the message is definitively established, and the message is given its final content and form.

In log4j, a log can represent:

-   Console;
-   File;
-   Socket;
-   An object of a class implementing `java.io.Writer` or `java.io.OutputStream`;
-   JDBC storage;
-   JMS topic;
-   NT Event Log;
-   SMTP;
-   Syslog;
-   Telnet.

The most commonly used log4j appenders include:

-   `org.apache.log4j.ConsoleAppender` - for console output;
-   `org.apache.log4j.FileAppender` - for file logging;
-   `org.apache.log4j.DailyRollingFileAppender` - for file logging with file rotation at specified intervals;
-   `org.apache.log4j.RollingFileAppender` - for file logging with file rotation upon reaching a certain size;
-   `org.apache.log4j.varia.ExternallyRolledFileAppender` - an extension of _RollingFileAppender_ that rotates files based on commands received from a specified port;
-   `org.apache.log4j.net.SMTPAppender` - for message sending via SMTP;
-   `org.apache.log4j.AsyncAppender` - allows asynchronous logging using a separate thread, where messages are only recorded when a certain level of the intermediate buffer is filled.
-   `org.apache.log4j.nt.NTEventLogAppender` - for logging to NT Event Log;
-   `org.apache.log4j.net.SyslogAppender` - for logging to Syslog;
-   `org.apache.log4j.jdbc.JDBCAppender` - for JDBC storage logging;
-   `org.apache.log4j.lf5.LF5Appender` - sends messages to a special GUI interface called LogFactor5;
-   `org.apache.log4j.net.SocketAppender` - for broadcasting messages to a specified address and port;
-   `org.apache.log4j.net.SocketHubAppender` - for sending messages to multiple remote servers connected via a specified port;
-   `org.apache.log4j.net.TelnetAppender` - for message sending via the Telnet protocol;
-   `org.apache.log4j.net.JMSAppender` - for logging messages in JMS.

[Back to Table of Contents](#logging)

## What is a _Layout_ in log4j?

A **Layout** is a subclass of `org.apache.log4j.Layout` that provides the ability to format messages before adding them to the log.

There are the following types of layouts in log4j:

-   `org.apache.log4j.SimpleLayout` - produces a string containing only the output level and the message;
-   `org.apache.log4j.HTMLLayout` - formats the message as an HTML table element;
-   `org.apache.log4j.xml.XMLLayout` - formats the message in XML format;
-   `org.apache.log4j.TTCCLayout` - appends time, thread, logger name, and nested diagnostic context information to the output message;
-   `org.apache.log4j.PatternLayout` / `org.apache.log4j.EnhancedPatternLayout` - allows custom formatting of messages using user-defined templates.

[Back to Table of Contents](#logging)

## List the logging levels in log4j. What is their priority order?

-   **OFF** - no logging;
-   **FATAL** - severe error;
-   **ERROR** - error;
-   **WARN** - warning;
-   **INFO** - informational message;
-   **DEBUG** - detailed debugging message;
-   **TRACE** - tracing all messages.

The priority order among the logging levels is as follows:

`ALL < TRACE < DEBUG < INFO < WARN < ERROR < FATAL < OFF`

[Back to Table of Contents](#logging)

## What configuration methods exist for log4j?

To begin working with log4j, you need to provide it with a configuration. This can be done in several ways:

-   Create the configuration programmatically, i.e., obtain a logger, set the logging level, attach an appender, and specify the formatting method.
-   Provide a file or URL as an argument when starting the Java machine using `-Dlog4j.configuration=path/to/configuration/file`, then read it in the program using `PropertyConfigurator.configure(...)` / `DOMConfigurator.configure(...)` for `.properties` or `XML` formats, respectively.
-   Load the configuration from an XML file or `.properties` file: log4j searches for the configuration file in the classpath. It first looks for `log4j.xml`, and if it does not find it, it looks for `log4j.properties`.

[Back to Table of Contents](#logging)

# Sources

-   [Quizful](http://www.quizful.net/)
-   [Skipy](http://skipy.ru/useful/logging.html#log4j_concepts_logger)

[Interview Questions](README.md)
