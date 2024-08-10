---
title: "Basics of HTML"
date: 2023-10-01
tags: ["HTML", "web development", "coding"]
---

[Interview Questions](README.md)

# Basics of HTML

-   [What is _«HTML»_?](#what-is-html)
-   [What is _«XHTML»_?](#what-is-xhtml)
-   [What is `DOCTYPE` and why is it needed?](#what-is-doctype-and-why-is-it-needed)
-   [What is the purpose of the `<head>` tag?](#what-is-the-purpose-of-the-head-tag)
-   [What is the difference between `<div>` and `<span>`?](#what-is-the-difference-between-div-and-span)
-   [How are comments denoted in HTML?](#how-are-comments-denoted-in-html)
-   [How is the address of a document specified for linking?](#how-is-the-address-of-a-document-specified-for-linking)
-   [How to create a link to an email address?](#how-to-create-a-link-to-an-email-address)
-   [What is the purpose of the `<em>` tag?](#what-is-the-purpose-of-the-em-tag)
-   [What are the purposes of the `<ol>`, `<ul>`, `<li>` tags?](#what-are-the-purposes-of-the-ol-ul-li-tags)
-   [What are the purposes of the `<dl>`, `<dt>`, `<dd>` tags?](#what-are-the-purposes-of-the-dl-dt-dd-tags)
-   [What are the purposes of the `<tr>`, `<th>`, `<td>` tags?](#what-are-the-purposes-of-the-tr-th-td-tags)
-   [Is it mandatory to use the `alt` attribute in the `<img>` tag?](#is-it-mandatory-to-use-the-alt-attribute-in-the-img-tag)
-   [What is the best case for writing HTML code?](#what-is-the-best-case-for-writing-html-code)
-   [What is a "mnemonic (entity)"?](#what-is-a-mnemonic-entity)

## What is _«HTML»_?

**HTML**, HyperText Markup Language, is the standardized markup language for documents on the World Wide Web. Currently, the most recent version of this language is HTML5.

[Back to Table of Contents](#basics-of-html)

## What is _«XHTML»_?

**XHTML**, eXtensible HyperText Markup Language, is a more strict version of HTML that adheres to all XML constraints and is essentially an application of XML in the realm of hypertext markup.

[Back to Table of Contents](#basics-of-html)

## What is `DOCTYPE` and why is it needed?

The `<!DOCTYPE>` element specifies the type of the current document. This is necessary for the browser to understand which standard it should use to interpret the web page.

There are several types of `<!DOCTYPE>`, differing by the version of the language they are based on:

**HTML 4.01**

-   `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">`: strict syntax of HTML;

-   `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">`: transitional syntax of HTML;

-   `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN"
"http://www.w3.org/TR/html4/frameset.dtd">`: HTML with frames.

**HTML 5**

-   `<!DOCTYPE html>`: for all documents.

**XHTML 1.0**

-   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">`: strict syntax of XHTML;

-   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`: transitional syntax of XHTML;

-   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">`: XHTML with frames.

**XHTML 1.1**

-   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">`: for all documents.

[Back to Table of Contents](#basics-of-html)

## What is the purpose of the `<head>` tag?

The `<head>` tag is intended to hold other elements aimed at helping the browser manage the data. Within this container are _meta tags_, which are used to store information intended for browsers and search engines. For instance, search engines refer to meta tags for site descriptions, keywords, and other data.

The content of the `<head>` tag is not directly displayed on the web page, except for the `<title>` tag that sets the window title.

Inside the `<head>` container, the following elements may be included: `<base>`, `<basefont>`, `<bgsound>`, `<link>`, `<meta>`, `<script>`, `<style>`, `<title>`.

Syntax:

```html
<head>
    ...
</head>
```

Specific attributes:

-   `profile`: indicates the metadata profile address.

[Back to Table of Contents](#basics-of-html)

## What is the difference between `<div>` and `<span>`?

`<div>` is a block-level element, while `<span>` is an inline element. Therefore, `<div>` creates a block by placing its content on a new line, whereas `<span>` does not break lines, placing elements inline. Additionally, according to W3C guidelines, inline tags cannot contain block tags, so `<div>` is generally used for block markup, and `<span>` for snippets of text.

[Back to Table of Contents](#basics-of-html)

## How are comments denoted in HTML?

Comments in HTML code are denoted as follows: `<!-- comment -->`

Comments can be used anywhere on the page except within the `<title>` tag—they do not work there. Inside the `<style>` tag, HTML comments also do not work, as CSS code is commented differently.

[Back to Table of Contents](#basics-of-html)

## How is the address of a document specified for linking?

To create links to other documents, the `<a>` tag is used. Depending on the presence of the `name` or `href` attributes, the `<a>` tag either establishes a link or an anchor. An anchor refers to a bookmark within a page that can be set as a link target. When using a link that points to an anchor, the browser navigates to the bookmark within the web page.

Syntax:

-   `<a href="URL">...</a>`
-   `<a name="identifier">...</a>`

Specific attributes:

-   `accesskey`: activates the link using a key combination;
-   `coords`: sets the coordinates of the active area;
-   `download`: prompts to download the specified file;
-   `href`: specifies the address of the document to navigate to. Link addresses can be absolute or relative. Absolute addresses work everywhere, regardless of the site name or web page where the link is specified. Relative links, as the name suggests, are built relative to the current document or the root of the site;
-   `hreflang`: identifies the language of the text in the link;
-   `name`: sets the name of the anchor within the document;
-   `rel`: relationship between the linked and current documents;
-   `rev`: relationship between the current and linked documents;
-   `shape`: defines the shape of the active area for image links;
-   `tabindex`: determines the sequence of navigation between links when pressing the <kbd>Tab</kbd> key;
-   `target`: the name of the window or frame where the document will be loaded;
-   `title`: adds a tooltip to the link text;
-   `type`: specifies the MIME type of the document that the link refers to.

[Back to Table of Contents](#basics-of-html)

## How to create a link to an email address?

Creating a link to an email address is done similarly to creating a link to a web page, but instead of a URL, you use `mailto:"email address"`

```html
<a href="mailto:user@address.net">Email me!</a>
```

[Back to Table of Contents](#basics-of-html)

## What is the purpose of the `<em>` tag?

The `<em>` tag is used for emphasizing text. Browsers render such text in italics.

```html
<em>Text</em>
```

[Back to Table of Contents](#basics-of-html)

## What are the purposes of the `<ol>`, `<ul>`, `<li>` tags?

The `<ol>`, `<ul>`, and `<li>` tags are used for formatting lists.

-   `<ol>`: ordered list, where each list item starts with a number or letter and increments sequentially.
-   `<ul>`: unordered list, where each list item starts with a small symbol—a bullet.
-   `<li>`: individual list item. The outer `<ul>` or `<ol>` tag specifies the list type—unordered or ordered.

```html
<ol>
    Ordered List
    <li>first</li>
    <li>second</li>
    <li>third</li>
</ol>

<ul>
    Unordered List
    <li>first</li>
    <li>second</li>
    <li>third</li>
</ul>
```

[Back to Table of Contents](#basics-of-html)

## What are the purposes of the `<dl>`, `<dt>`, `<dd>` tags?

The `<dl>`, `<dt>`, and `<dd>` tags are used for creating a definition list.

Each such list starts with a `<dl>` container, which includes a `<dt>` tag for creating a term and a `<dd>` tag for defining that term. The closing `</dd>` tag is optional since the following tag indicates the end of the previous element. However, it is good style to close all tags.

```html
<dl>
    Definition List
    <dt>Term</dt>
    <dd>Definition</dd>
</dl>
```

[Back to Table of Contents](#basics-of-html)

## What are the purposes of the `<tr>`, `<th>`, `<td>` tags?

`<tr>`: serves as a container for creating a table row. Each cell within the row can be created using `<th>` or `<td>`.
`<th>`: used to create a cell for a table header.
`<td>`: used to create a cell within a table.

```html
<table>
    <tr>
        <th>Header</th>
    </tr>
    <tr>
        <td>Row</td>
    </tr>
</table>
```

[Back to Table of Contents](#basics-of-html)

## Is it mandatory to use the `alt` attribute in the `<img>` tag?

Yes, it is mandatory.

The `alt` attribute specifies alternative text for images. This text provides textual information about the image when images are not loaded in the browser. Since images are loaded after the browser has gathered information about them, the alternative text appears before the image loads. As the image loads, the text is replaced by the image.

```html
<img src="forest.jpg" alt="Forest" />
```

[Back to Table of Contents](#basics-of-html)

## What is the best case for writing HTML code?

It is recommended to write all HTML code in lowercase: this applies to element names, attribute names, attribute values (except for text/CDATAs), selectors, properties, and their values (except for text).

Not recommended:

```html
<a href="/">Home</a>
```

Recommended:

```html
<a href="/">Home</a>
```

[Back to Table of Contents](#basics-of-html)

## What is a "mnemonic (entity)"?

**A mnemonic (entity)** is a construction made from the `&` symbol followed by a letter (or numerical code) after it, intended to substitute characters that are prohibited for use in HTML in "visible form".

> &num; has the mnemonic `&num;`

[Back to Table of Contents](#basics-of-html)

# Sources

-   [htmlbook](http://htmlbook.ru/html/)
-   [Habr](https://habrahabr.ru/post/143452/)

[Interview Questions](README.md)
