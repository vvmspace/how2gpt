---
title: "Basics of CSS"
date: 2023-10-01
tags: ["CSS", "web development", "frontend"]
---

# Basics of CSS

-   [What is _«CSS»_?](#what-is-css)
-   [How are comments denoted in CSS?](#how-are-comments-denoted-in-css)
-   [What is a _«selector»_?](#what-is-a-selector)
-   [List the main types of selectors.](#list-the-main-types-of-selectors)
-   [What is a pseudo-class?](#what-is-a-pseudo-class)
-   [What attribute selectors are there?](#what-attribute-selectors-are-there)
-   [What is the difference between `#my` and `.my`?](#what-is-the-difference-between-my-and-my)
-   [What is the difference between `margin` and `padding`?](#what-is-the-difference-between-margin-and-padding)
-   [What is the difference between the values `0` and `auto` in the `margin` property?](#what-is-the-difference-between-the-values-0-and-auto-in-the-margin-property)
-   [Which property sets the background color?](#which-property-sets-the-background-color)
-   [How to remove the underline from all links on the page?](#how-to-remove-the-underline-from-all-links-on-the-page)
-   [What is the `clear` property used for?](#what-is-the-clear-property-used-for)
-   [How to make text bold in all `<p>` elements?](#how-to-make-text-bold-in-all-p-elements)
-   [How to set the color red for all elements with the class `red`?](#how-to-set-the-color-red-for-all-elements-with-the-class-red)

## What is _«CSS»_?

**CSS, Cascading Style Sheets** - is a formal language for describing the visual appearance of a document written in a markup language, using it on elements of a web page to control their look and position.

The primary goal of developing CSS was to separate the description of the logical structure of a web page, which is done via HTML or other markup languages, from the description of the appearance of that web page, which is done via CSS.

[Back to Table of Contents](#basics-of-css)

## How are comments denoted in CSS?

To indicate that text is a comment, use the syntax `/* ... */`

[Back to Table of Contents](#basics-of-css)

## What is a _«selector»_?

A **selector** is a rule that selects elements in an HTML document to apply certain styles.

```css
p {
    text-align: center;
    font-size: 20px;
}
/* p is the selector, text-align and font-size are properties, and center and 20px are values. */
```

[Back to Table of Contents](#basics-of-css)

## List the main types of selectors.

-   **`*` selector** - selects all elements;
-   **element selector** - selects all elements in an HTML document with the specified tag (e.g., `div`);
-   **class selector** - selects all elements in an HTML document with the specified class (e.g., `.center`);
-   **id selector** - selects an element in an HTML document with the specified id (e.g., `#footer`);
-   **pseudo-class selectors** - selects all elements in an HTML document with the specified pseudo-class (e.g., `p:first-of-type`);
-   **attribute selectors** - selects elements based on a specified attribute or its value (e.g., `[href*="youtube"]`).

[Back to Table of Contents](#basics-of-css)

## What is a pseudo-class?

A pseudo-class defines a dynamic state of elements that changes as a result of user actions or corresponds to the current position in the document tree. Unlike a true class, a pseudo-class is not explicitly specified in HTML, but is specified in CSS using `:` directly after the selector.

The most well-known pseudo-classes are:

-   `:link` applies to unvisited links;
-   `:visited` applies to visited links;
-   `:hover` applies when the mouse cursor is over the element but does not activate it;
-   `:active` applies when the element is activated;
-   `:focus` applies to an element when it has focus;
-   `:first-child` applies to the first child element of a selector that is located in the document's element tree.

```css
a.snowman:link {
    color: blue;
}
a.snowman:visited {
    color: purple;
}
a.snowman:active {
    color: red;
}
a.snowman:hover {
    text-decoration: none;
    color: blue;
    background-color: yellow;
}
```

[Back to Table of Contents](#basics-of-css)

## What attribute selectors are there?

-   **`[attribute]`** - all elements that have the specified `attribute`;
-   **`[attribute=value]`** - all elements that have an `attribute` whose value is equal to `"value"`;
-   **`[attribute^=value]`** - all elements that have an `attribute` whose value starts with `value`;
-   **`[attribute|=value]`** - all elements that have an `attribute` whose value is equal to `value` or starts with `value` followed by `-` (i.e., `value-*`, where `value` must be followed by more content);
-   **`[attribute$=value]`** - all elements that have an `attribute` whose value ends with `value`;
-   **`[attribute*=value]`** - all elements that have an `attribute` whose value contains the substring `value`;
-   **`[attribute~=value]`** - all elements that have an `attribute` whose value contains `value` as one of the space-separated values.

[Back to Table of Contents](#basics-of-css)

## What is the difference between `#my` and `.my`?

`#my` is an id selector, while `.my` is a class selector.

[Back to Table of Contents](#basics-of-css)

## What is the difference between `margin` and `padding`?

`margin` is the outer spacing, while `padding` is the inner spacing.

[Back to Table of Contents](#basics-of-css)

## What is the difference between the values `0` and `auto` in the `margin` property?

In vertical margins, `auto` always means `0`. In horizontal margins, `auto` means `0` only when the `width` property is also `auto`.

[Back to Table of Contents](#basics-of-css)

## Which property sets the background color?

The background color is set with the `background-color` property.

[Back to Table of Contents](#basics-of-css)

## How to remove the underline from all links on the page?

```css
a {
    text-decoration: none;
}
```

[Back to Table of Contents](#basics-of-css)

## What is the `clear` property used for?

`clear` specifies which side of an element must not be adjacent to floating elements.

[Back to Table of Contents](#basics-of-css)

## How to make text bold in all `<p>` elements?

```css
p {
    font-weight: bold;
}
```

[Back to Table of Contents](#basics-of-css)

## How to set the color red for all elements with the class `red`?

```css
.red {
    color: red;
}
```

[Back to Table of Contents](#basics-of-css)

# Sources

-   [myway-blog.ru](http://myway-blog.ru/interview-frontend-web-programmer/)
-   [htmlbook.ru](http://stepbystep.htmlbook.ru/?id=43)
-   [itchief.ru](https://itchief.ru/lessons/html-and-css/css-selectors)

[Interview Questions](README.md)
