---
title: "Input/Output Streams in Java"
date: 2023-10-01
tags: ["Java", "IO", "NIO"]
---

# Input/Output Streams in Java

-   [What is the difference between IO and NIO?](#what-is-the-difference-between-io-and-nio)
-   [What NIO features do you know?](#what-nio-features-do-you-know)
-   [What are _“channels”_?](#what-are-channels)
-   [What types of input/output streams exist?](#what-types-of-input-output-streams-exist)
-   [Name the main classes of input/output streams.](#name-the-main-classes-of-input-output-streams)
-   [In which packages are the classes for input/output streams located?](#in-which-packages-are-the-classes-for-input-output-streams-located)
-   [What subclasses of the `InputStream` class do you know, and what are they for?](#what-subclasses-of-the-inputstream-class-do-you-know-and-what-are-they-for)
-   [What is `PushbackInputStream` used for?](#what-is-pushbackinputstream-used-for)
-   [What is `SequenceInputStream` used for?](#what-is-sequenceinputstream-used-for)
-   [Which class allows reading data from an input byte stream in the format of primitive data types?](#which-class-allows-reading-data-from-an-input-byte-stream-in-the-format-of-primitive-data-types)
-   [What subclasses of the `OutputStream` class do you know, and what are they for?](#what-subclasses-of-the-outputstream-class-do-you-know-and-what-are-they-for)
-   [What subclasses of the `Reader` class do you know, and what are they for?](#what-subclasses-of-the-reader-class-do-you-know-and-what-are-they-for)
-   [What subclasses of the `Writer` class do you know, and what are they for?](#what-subclasses-of-the-writer-class-do-you-know-and-what-are-they-for)
-   [What is the difference between the `PrintWriter` and `PrintStream` classes?](#what-is-the-difference-between-the-printwriter-and-printstream-classes)
-   [What are the differences and similarities between `InputStream`, `OutputStream`, `Reader`, and `Writer`?](#what-are-the-differences-and-similarities-between-inputstream-outputstream-reader-and-writer)
-   [Which classes allow converting byte streams to character streams and vice versa?](#which-classes-allow-converting-byte-streams-to-character-streams-and-vice-versa)
-   [Which classes accelerate reading/writing by using a buffer?](#which-classes-accelerate-readingwriting-by-using-a-buffer)
-   [Which class is designed to work with file system elements?](#which-class-is-designed-to-work-with-file-system-elements)
-   [What methods of the `File` class do you know?](#what-methods-of-the-file-class-do-you-know)
-   [What do you know about the `FileFilter` interface?](#what-do-you-know-about-the-filefilter-interface)
-   [How to select all items in a specific directory by criteria (for example, with a specific extension)?](#how-to-select-all-items-in-a-specific-directory-by-criteria-for-example-with-a-specific-extension)
-   [What do you know about `RandomAccessFile`?](#what-do-you-know-about-randomaccessfile)
-   [What access modes does `RandomAccessFile` have?](#what-access-modes-does-randomaccessfile-have)
-   [Which classes support reading and writing streams in a compressed format?](#which-classes-support-reading-and-writing-streams-in-a-compressed-format)
-   [Is it possible to redirect standard input/output streams?](#is-it-possible-to-redirect-standard-inputoutput-streams)
-   [What character is the separator when specifying a path in the file system?](#what-character-is-the-separator-when-specifying-a-path-in-the-file-system)
-   [What is an _“absolute path”_ and a _“relative path”_?](#what-is-an-absolute-path-and-a-relative-path)
-   [What is a _“symbolic link”_?](#what-is-a-symbolic-link)

[Back to Table of Contents](#inputoutput-streams-in-java)

## What is the difference between IO and NIO?

-   Java IO (input-output) is stream-oriented, while Java NIO (new/non-blocking IO) is buffer-oriented. Stream-oriented input/output means reading/writing from/to a stream of one or more bytes at a time sequentially. This data is not cached anywhere, making it impossible to move freely forward or backward in the data stream. In Java NIO, data is first read into a buffer, allowing more flexibility when handling the data.
-   Input/output streams in Java IO are blocking. This means that when the `read()` or `write()` method of any class in the `java.io.*` package is called, it blocks until the data is read or written. The execution thread cannot do anything else at that moment. The non-blocking mode of Java NIO allows querying for read data from a channel and obtaining only what is currently available, or nothing at all if no data is available yet. Instead of remaining blocked until data becomes available for reading, the execution thread can engage in other tasks. This applies equally to non-blocking output as well. The execution thread can request to write some data to the channel without waiting for it to be fully written.
-   Java NIO includes selectors that allow one execution thread to monitor multiple input channels. This means you can register several channels with a selector and then use one execution thread to service channels that have data available for processing or to select the channels ready for writing.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What NIO features do you know?

-   **Channels and Selectors**: NIO supports various types of channels. A channel is an abstraction of lower-level file system objects (e.g., memory-mapped files and file locks), allowing data to be transmitted at higher speeds. Channels are non-blocking, which is why Java also provides tools like selectors, which allow selecting a ready channel for data transmission, and sockets, which serve as blocking tools.
-   **Buffers**: It uses buffering for all wrapper classes for primitives (except for Boolean). An abstract class, Buffer, has been introduced, providing operations like clear, flip, mark, etc. Its subclasses provide methods to get and set data.
-   **Character Encodings**: It introduces encoders and decoders for translating bytes and Unicode characters.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What are _“channels”_?

Channels are logical (not physical) portals, abstractions of lower-level file system objects (e.g., memory-mapped files and file locks) through which data input/output occurs, while buffers serve as sources or destinations for this transferred data. When organizing output, the data to be sent is placed into a buffer, which is then passed to a channel. When input occurs, data from the channel is placed into a provided buffer.

Channels resemble pipelines that efficiently transport data between byte buffers and the entities on the other side of the channels. Channels are gateways that allow access to operating system input/output services with minimal overhead, while buffers are internal endpoints of these gateways used for transferring and receiving data.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What types of input/output streams exist?

## Name the main classes of input/output streams.

There are two types of input/output streams:

-   **Byte Streams** - `java.io.InputStream`, `java.io.OutputStream`;
-   **Character Streams** - `java.io.Reader`, `java.io.Writer`.

[Back to Table of Contents](#inputoutput-streams-in-java)

## In which packages are the classes for input/output streams located?

`java.io`, `java.nio`. For working with streams of compressed data, classes from the `java.util.zip` package are used.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What subclasses of the `InputStream` class do you know, and what are they for?

-   `InputStream` - abstract class that describes an input stream;
-   `BufferedInputStream` - buffered input stream;
-   `ByteArrayInputStream` allows using a buffer in memory (byte array) as a source of data for the input stream;
-   `DataInputStream` - input stream for byte data, including methods for reading standard Java data types;
-   `FileInputStream` - input stream for reading information from a file;
-   `FilterInputStream` - abstract class providing an interface for decorator classes that add useful properties to existing streams;
-   `ObjectInputStream` - input stream for objects;
-   `StringBufferInputStream` turns a `String` into an `InputStream` data stream;
-   `PipedInputStream` implements the concept of an input channel;
-   `PushbackInputStream` - a variation of buffering that allows reading a byte and then returning it to the stream, enabling one to "peek" into the input stream and see what will come next without extracting the information.
-   `SequenceInputStream` is used for merging two or more `InputStream` instances into one.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What is `PushbackInputStream` used for?

A variation of buffering that allows reading a byte and then returning it to the stream. The `PushbackInputStream` class provides a mechanism to "peek" into the input stream and see what will come next without extracting information.

The class has an additional method `unread()`.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What is `SequenceInputStream` used for?

The `SequenceInputStream` class allows merging multiple instances of the `InputStream` class together. The constructor takes either a pair of `InputStream` objects or an `Enumeration` interface as arguments.

During operation, the class makes read requests from the first `InputStream` object until it reaches the end, and then switches to the second one. If an interface is used, the operation continues across all `InputStream` objects. Upon reaching the end, the associated stream is closed. Closing the stream created by the `SequenceInputStream` object results in the closure of all open streams.

[Back to Table of Contents](#inputoutput-streams-in-java)

## Which class allows reading data from an input byte stream in the format of primitive data types?

The `DataInputStream` class represents an input stream and is intended for reading primitive type data such as `int`, `double`, etc. Each primitive type has its own method for reading:

-   `boolean readBoolean()`: reads a one-byte boolean value from the stream
-   `byte readByte()`: reads 1 byte from the stream
-   `char readChar()`: reads a `char` value from the stream
-   `double readDouble()`: reads an 8-byte double value from the stream
-   `float readFloat()`: reads a 4-byte float value from the stream
-   `int readInt()`: reads an integer value from the stream
-   `long readLong()`: reads a long value from the stream
-   `short readShort()`: reads a short value from the stream
-   `String readUTF()`: reads a string in UTF-8 encoding from the stream

[Back to Table of Contents](#inputoutput-streams-in-java)

## What subclasses of the `OutputStream` class do you know, and what are they for?

-   `OutputStream` - an abstract class defining the byte output stream;
-   `BufferedOutputStream` - buffered output stream;
-   `ByteArrayOutputStream` - all data sent to this stream is placed in a preallocated buffer;
-   `DataOutputStream` - byte output stream, including methods for writing standard Java data types;
-   `FileOutputStream` - writes data to a file on physical media;
-   `FilterOutputStream` - abstract class providing an interface for decorator classes that add useful properties to existing streams;
-   `PrintStream` - includes the `print()` and `println()` methods;
-   `ObjectOutputStream` - output stream for writing objects;
-   `PipedOutputStream` implements the concept of an output channel.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What subclasses of the `Reader` class do you know, and what are they for?

-   `Reader` - abstract class describing character input;
-   `BufferedReader` - buffered character input stream;
-   `CharArrayReader` - input stream that reads from a character array;
-   `FileReader` - input stream reading from a file;
-   `FilterReader` - abstract class providing an interface for decorator classes;
-   `InputStreamReader` - input stream translating bytes into characters;
-   `LineNumberReader` - input stream counting lines;
-   `PipedReader` - input channel;
-   `PushbackReader` - input stream that allows returning characters back to the stream;
-   `StringReader` - input stream reading from a string.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What subclasses of the `Writer` class do you know, and what are they for?

-   `Writer` - abstract class describing character output;
-   `BufferedWriter` - buffered character output stream;
-   `CharArrayWriter` - output stream writing to a character array;
-   `FileWriter` - output stream writing to a file;
-   `FilterWriter` - abstract class providing an interface for decorator classes;
-   `OutputStreamWriter` - output stream translating characters into bytes;
-   `PipedWriter` - output channel;
-   `PrintWriter` - character output stream including the `print()` and `println()` methods;
-   `StringWriter` - output stream writing to a string.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What is the difference between the `PrintWriter` and `PrintStream` classes?

Primarily, the `PrintWriter` class employs a more advanced way of handling Unicode characters and a different output buffering mechanism: in `PrintStream`, the output buffer is flushed every time the `print()` or `println()` method is invoked, while in `PrintWriter`, you can optionally forgo automatic buffer flushing and do it explicitly using the `flush()` method.

Additionally, the methods in the `PrintWriter` class never throw exceptions. To check for errors, the `checkError()` method must be called explicitly.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What are the differences and similarities between `InputStream`, `OutputStream`, `Reader`, and `Writer`?

-   `InputStream` and its subclasses provide a collection for obtaining byte data from various sources;
-   `OutputStream` and its subclasses define a set of classes for byte output streams;
-   `Reader` and its subclasses define a stream for Unicode character input;
-   `Writer` and its subclasses define a stream for Unicode character output.

[Back to Table of Contents](#inputoutput-streams-in-java)

## Which classes allow converting byte streams to character streams and vice versa?

-   `OutputStreamWriter` is a "bridge" between the `OutputStream` class and the `Writer` class. Characters written to the stream are converted to bytes.
-   `InputStreamReader` serves as an analogous class for reading. It reads bytes from an `InputStream` and translates them into characters using methods from the `Reader` class.

[Back to Table of Contents](#inputoutput-streams-in-java)

## Which classes accelerate reading/writing by using a buffer?

-   `BufferedInputStream(InputStream in)`/`BufferedInputStream(InputStream in, int size)`,
-   `BufferedOutputStream(OutputStream out)`/`BufferedOutputStream(OutputStream out, int size)`,
-   `BufferedReader(Reader r)`/`BufferedReader(Reader in, int sz)`,
-   `BufferedWriter(Writer out)`/`BufferedWriter(Writer out, int sz)`

[Back to Table of Contents](#inputoutput-streams-in-java)

## Which class is designed to work with file system elements?

`File` works directly with files and directories. This class allows creating new elements and obtaining information about existing ones: size, access rights, creation date and time, and the path to the parent directory.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What methods of the `File` class do you know?

The most commonly used methods of the `File` class are:

-   `boolean createNewFile()`: attempts to create a new file;
-   `boolean delete()`: attempts to delete a directory or file;
-   `boolean mkdir()`: attempts to create a new directory;
-   `boolean renameTo(File dest)`: attempts to rename a file or directory;
-   `boolean exists()`: checks if a file or directory exists;
-   `String getAbsolutePath()`: returns the absolute path for the path passed in the object constructor;
-   `String getName()`: returns the short name of the file or directory;
-   `String getParent()`: returns the name of the parent directory;
-   `boolean isDirectory()`: returns `true` if the specified path is a directory;
-   `boolean isFile()`: returns `true` if the specified path is a file;
-   `boolean isHidden()`: returns `true` if the directory or file is hidden;
-   `long length()`: returns the size of the file in bytes;
-   `long lastModified()`: returns the time of the last modification to the file or directory;
-   `String[] list()`: returns an array of files and subdirectories in a specific directory;
-   `File[] listFiles()`: returns an array of files and subdirectories in a specific directory.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What do you know about the `FileFilter` interface?

The `FileFilter` interface is used to check whether a `File` object meets certain criteria. This interface contains a single method `boolean accept(File pathName)`. This method needs to be overridden and implemented. For example:

```java
public boolean accept(final File file) {
    return file.exists() && file.isDirectory();
}
```

[Back to Table of Contents](#inputoutput-streams-in-java)

## How to select all items in a specific directory by criteria (for example, with a specific extension)?

The `File.listFiles()` method returns an array of `File` objects contained in a directory. The method can accept a parameter of a class that implements `FileFilter`. This allows including only those items in the list for which the `accept` method returns `true` (criteria can include the length of the file name or its extension).

[Back to Table of Contents](#inputoutput-streams-in-java)

## What do you know about `RandomAccessFile`?

The `java.io.RandomAccessFile` class enables reading and writing data at random locations within a file. It is not part of the `InputStream` or `OutputStream` hierarchy. This is a completely separate class with its own (mostly _native_) methods. The reason for this is that `RandomAccessFile` behaves very differently from other input/output classes because it allows moving both forward and backward within a file.

`RandomAccessFile` has specific methods such as:

-   `getFilePointer()` to determine the current location in the file;
-   `seek()` for moving to a new position in the file;
-   `length()` to find out the size of the file;
-   `setLength()` for setting the size of the file;
-   `skipBytes()` to attempt to skip a specified number of bytes;
-   `getChannel()` for working with the unique file channel associated with a given file;
-   methods for performing both regular and formatted output from the file (`read()`, `readInt()`, `readLine()`, `readUTF()`, etc.);
-   methods for regular or formatted writing to a file with random access (`write()`, `writeBoolean()`, `writeByte()`, etc.).

It's worth noting that constructors for `RandomAccessFile` require a second argument indicating the desired access mode for the file - read-only (`"r"`), read and write (`"rw"`), or some other variations.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What access modes does `RandomAccessFile` have?

-   `"r"` opens the file for reading only. Invoking any data writing methods will result in an `IOException`.
-   `"rw"` opens the file for reading and writing. If the file does not exist yet, an attempt is made to create it.
-   `"rws"` opens the file for reading and writing similar to `"rw"` but requires the system to synchronously write changes to the physical storage whenever the content or metadata of the file is modified.
-   `"rwd"` opens the file for reading and writing similar to `"rws"` but requires synchronous writing to the physical storage only when the content of the file is modified. Changes to the metadata do not require synchronous writing.

[Back to Table of Contents](#inputoutput-streams-in-java)

## Which classes support reading and writing streams in a compressed format?

-   `DeflaterOutputStream` - compresses data in the deflate format.
-   `Deflater` - compresses data in ZLIB format.
-   `ZipOutputStream` - a subclass of `DeflaterOutputStream` for compressing data in ZIP format.
-   `GZIPOutputStream` - a subclass of `DeflaterOutputStream` for compressing data in GZIP format.
-   `InflaterInputStream` - decompresses data in the deflate format.
-   `Inflater` - decompresses data in ZLIB format.
-   `ZipInputStream` - a subclass of `InflaterInputStream` for decompressing data in ZIP format.
-   `GZIPInputStream` - a subclass of `InflaterInputStream` for decompressing data in GZIP format.

[Back to Table of Contents](#inputoutput-streams-in-java)

## Is it possible to redirect standard input/output streams?

The `System` class allows you to redirect standard input, output, and error output streams using a simple call to a static method:

-   `setIn(InputStream)` - for input;
-   `setOut(PrintStream)` - for output;
-   `setErr(PrintStream)` - for error output.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What character is the separator when specifying a path in the file system?

For various operating systems, the separator character differs. On Windows, it is `\`, and for Linux, it is `/`.

In Java, you can retrieve the separator for the current operating system by accessing the static field `File.separator`.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What is an _“absolute path”_ and a _“relative path”_?

**Absolute path** refers to a path that points to the same location in the file system, regardless of the current working directory or other circumstances. An absolute path always starts from the root directory.

**Relative path** represents a path relative to the current working directory of the user or the active application.

[Back to Table of Contents](#inputoutput-streams-in-java)

## What is a _“symbolic link”_?

A **symbolic link** (also "symlink") is a special file in the file system that, instead of containing user data, holds a path to a file that should be opened when attempting to access this link (file). The target of the link can be any object, such as another link, a file, a directory, or even a non-existent file (in the latter case, attempting to open it should yield a file not found message).

Symbolic links are used for more user-friendly organization of file structures on a computer, as they:

-   Allow a single file or directory to have multiple names and different attributes;
-   Are free from some of the constraints of hard links (the latter operate only within a single file system (a single partition) and cannot link to directories).

[Back to Table of Contents](#inputoutput-streams-in-java)

## Sources

-   [Quizful](http://www.quizful.net/post/java-nio-tutorial)
-   [HabrHabr](https://habrahabr.ru/post/235585/)
-   [Learn Programming Playfully](http://developer.alexanderklimov.ru/android/java/io.php)
-   [Metanit](http://metanit.com/java/tutorial/6.1.php)
-   [javastudy.ru](http://javastudy.ru/interview/input-output/)
-   [Bruce Eckel “Thinking in Java”](http://iais.kemsu.ru/odocs/java/Chapter11.html)

[Back to Interview Questions](README.md)
