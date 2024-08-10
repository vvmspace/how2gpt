---
title: "Understanding XML: Key Concepts and Definitions"
date: "2023-10-05"
tags: ["XML", "DTD", "XSD", "XML parsing", "XML namespaces"]
description: "Learn the fundamentals of XML, including what XML, DTD, XSD, and namespaces are, and their importance in web development and data representation."
languageCode: "en-ca"
---

# XML

-   [What is _XML_?](#what-is-xml)
-   [What is _DTD_?](#what-is-dtd)
-   [How does _well-formed XML_ differ from _valid XML_?](#how-does-well-formed-xml-differ-from-valid-xml)
-   [What is a "_namespace_" in XML?](#what-is-a-namespace-in-xml)
-   [What is XSD? What are its advantages over XML DTD?](#what-is-xsd-what-are-its-advantages-over-xml-dtd)
-   [What types exist in XSD?](#what-types-exist-in-xsd)
-   [What methods of reading XML do you know? Describe the strengths and weaknesses of each method.](#what-methods-of-reading-xml-do-you-know-describe-the-strengths-and-weaknesses-of-each-method)
-   [When to use _DOM_ vs. _SAX_ or _StAX_ parsers?](#when-to-use-dom-vs-sax-or-stax-parsers)
-   [What methods of writing XML do you know?](#what-methods-of-writing-xml-do-you-know)
-   [What is _JAXP_?](#what-is-jaxp)
-   [What is _XSLT_?](#what-is-xslt)

## What is _XML_?

**XML, or eXtensible Markup Language**, is a markup language designed to encode documents in a format that is both human-readable and machine-readable. Its simple formal syntax makes it well-suited for creating and manipulating structured documents through software, while also being easy for humans to read and write.

XML is highly extensible, allowing developers to create markup tailored to their specific needs, constrained only by the syntax rules of the language.

[Back to Table of Contents](#xml)

## What is _DTD_?

**DTD, or Document Type Definition**, is a set of markup declarations that define a document type for an XML document. It establishes relationships between elements and attributes.

> For instance, a DTD for HTML specifies that the `DIV` tag must reside within the `BODY` tag, and can occur multiple times; the `TITLE` must be inside the `HEAD`, and can appear only once, while the `SCRIPT` tag can appear any number of times in both sections.

A DTD is typically described in the document itself with a declaration starting with `<!DOCTYPE ... >` or in a separate file.

[Back to Table of Contents](#xml)

## How does _well-formed XML_ differ from _valid XML_?

Based on the level of adherence to standards, a document may be classified as either "well-formed" or "valid".

The core characteristics of _well-formed XML_ stem from the formal descriptions within the standard:

-   The document must have exactly one root element that contains all other elements.
-   All open tags must be explicitly closed. While HTML allows omitting closing tags for many elements (such as `<p>`, `<body>`, `<li>`, `<td>`, and many others), XML does not permit this.
-   Self-closing tags (e.g., `<br>`) are specified as `<br/>`, though one could also write `<br></br>`.
-   Tag names are case-sensitive. For example, if you open a tag as `<SiteDescription>`, it must be closed with the same name, `</sitedescription>` is invalid.
-   Tags must not violate nesting rules.
-   All attribute values must be enclosed in double quotes (`"`).
-   The characters `<`, `>`, and `&` must be escaped as `&lt;`, `&gt;`, and `&amp;` respectively. Inside attributes, double quotes must also be escaped as `&quot;`.
-   All characters in the document must comply with the declared encoding.

A document is considered _valid_ if it is formed according to the syntax rules of the specified XML standard and matches the corresponding _DTD_.

**_Well-formed XML_ is syntactically correct (able to be parsed by a parser), while _valid XML_ is correct both syntactically and semantically (it adheres to the rules defined by a given DTD).**

[Back to Table of Contents](#xml)

## What is a "_namespace_" in XML?

**An XML namespace** is a collection of names used in XML documents to distinguish among elements and attributes. It is identifiable via a URI reference. Unlike traditional programming namespaces, XML namespaces have an internal structure and are not considered a set mathematically.

> Namespaces are declared using the XML attribute `xmlns`, where the value must be a _URI_ that uniquely identifies the namespace for each element.

All element names within a namespace must be unique.

Generally, an XML namespace does not require an associated DTD.

An XML document may contain element and attribute names from multiple XML vocabularies. Each vocabulary defines its own namespace, resolving name-clashing issues.

[Back to Table of Contents](#xml)

## What is XSD? What are its advantages over XML DTD?

**XSD, or XML Schema Definition**, is a language for defining the structure of an XML document. Specifically, XML Schema describes:

-   _Dictionary_ - element and attribute names;
-   _Content model_ - relationships between elements and attributes, along with the document's
-   _Structure_;
-   Used _data types_.

**Advantages of XSD over DTD** include the following:

-   Unlike DTD, XSD is XML-compliant and has its syntax. This difference can lead to various encoding and validation issues with XML documents.
-   With XSD, an XML parser can check not just the syntax of the XML document but also its structure, content model, and data types. DTD only recognizes one data type—string—so a document with unexpected textual content in a numeric field may still pass validation, as DTD cannot verify data types.

-   A single XML document cannot correspond to multiple DTDs. Consequently, it can only be validated by one DTD definition. XSD is extensible, enabling the addition of multiple schemas to address different tasks.

-   XSD has built-in documentation features that allow the creation of self-contained documents without the need for additional explanations.

[Back to Table of Contents](#xml)

## What types exist in XSD?

**Simple types** refer to definitions for values that may be used as content within an element or attribute. This data type cannot contain elements or have attributes.

```xml
<xsd:element name='price' type='xsd:decimal'/>
...
<price>45.50</price>
```

**Complex types** refer to definitions for elements that may contain attributes and other elements.

```xml
<xsd:element name='price'>
    <xsd:complexType base='xsd:decimal'>
        <xsd:attribute name='currency' type='xsd:string'/>
    </xsd:complexType>
</xsd:element>
...
<price currency='US'>45.50</price>
```

[Back to Table of Contents](#xml)

## What methods of reading XML do you know? Describe the strengths and weaknesses of each method.

**DOM (Document Object Model)** is an object-oriented method that reads XML while reconstructing it in memory as an object structure, representing the document as a set of tags—nodes. Each node can have an unlimited number of child nodes. Ultimately, this creates a tree structure.

> ➖ Low processing speed.

> ➖ High memory consumption.

> ➕ Simple to program.

> ➕ Works well if the XML contains multiple objects with references to one another; it can make two passes over the document: first to create objects without links and fill a "name-object" dictionary, then a second pass to restore those links.

> ➕ If there is an error in the XML, a partially constructed XML structure remains in memory, which will be automatically cleaned up.

> ➕ Suitable for both reading and writing.

**SAX (Simple API for XML)** is an event-driven method that reads XML and reacts to events (opening or closing tags, strings, attributes) by invoking application-provided event handlers. Unlike DOM, it does not store the document in memory.

> ➕ High processing speed.

> ➕ Low memory consumption.

> ➗ Fairly complex to program.

> ➖ If there are many interlinked objects in the XML, temporary storage of string references is required to convert them into pointers after the document is read.

> ➖ If there is an error in the XML, a partially constructed application domain structure remains in memory; the programmer must manage its cleanup.

> ➖ Suitable only for reading.

**StAX (Stream API for XML)** is a streaming method comprising two sets of APIs for processing XML that provide different levels of abstraction. The cursor-based API allows applications to interact with XML as a stream of tokens (or events); the application can check the parser's status and obtain information about the last parsed token before moving to the next. The second high-level API uses event iterators, letting applications process XML as a series of event objects related to XML structure components. It requires the application to identify the specific types of syntax-analyzed events and utilize the appropriate methods for retrieving relevant information.

> ➗ Retains the advantages of SAX over DOM.

> ➕ Not based on callbacks; applications do not have to manage the parser's emulated state as they do when using SAX.

> ➖ Suitable only for reading.

[Back to Table of Contents](#xml)

## When to use _DOM_ vs. _SAX_ or _StAX_ parsers?

DOM is the natural choice when the XML structure itself is the subject of interest, especially when modification of the document's structure is needed or if information from the document is used repeatedly.

For quick, one-time reads, SAX or StAX is optimal.

[Back to Table of Contents](#xml)

## What methods of writing XML do you know?

**Direct writing** entails writing XML tag by tag, attribute by attribute.

> ➕ High processing speed.

> ➕ Memory-efficient: does not create intermediate objects.

> ➖ Suitable only for writing.

**Writing via DOM (Document Object Model)** creates a complete XML structure before any writing occurs.

> ➖ Low processing speed.

> ➖ Non-optimal memory usage.

> ➕ Suitable for both writing and reading.

[Back to Table of Contents](#xml)

## What is _JAXP_?

**JAXP, or The Java API for XML Processing**, is a set of APIs designed to simplify XML data processing in Java applications. It includes implementations for DOM, SAX, and StAX parsers, supports XSLT, and enables work with DTD.

[Back to Table of Contents](#xml)

## What is _XSLT_?

**XSLT, or eXtensible Stylesheet Language Transformations**, is a language for transforming XML documents.

XSLT was developed for use in _XSL (eXtensible Stylesheet Language)_, the stylesheet language for XML. During XSL transformations, an XSLT processor reads the XML document and its corresponding XSLT stylesheets. Based on the instructions found in the stylesheets, the processor produces a new XML document or fragments thereof.

[Back to Table of Contents](#xml)

# Conclusion

XML is a powerful tool for defining structured data formats. Understanding the core concepts of XML, including DTDs, XSDs, and namespaces, is essential for developers working on data interchange and web applications.

If you want to gain a deeper understanding of XML structures and processing techniques, familiarizing yourself with best practices will help you leverage XML to its full potential. From XML parsing methods to writing techniques and processing APIs, each foundational element of XML plays a vital role in modern data handling.

By broadening your knowledge of XML, including how it is validated and transformed using XSLT, you can enhance the functionality and interoperability of your applications.

For more information on XML fundamentals, consider researching topics such as XML processing frameworks and the differences between various XML parsers. Embracing XML in your projects will empower you to create flexible and maintainable data structures.
