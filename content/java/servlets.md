---
title: "Understanding Servlets, JSP, and JSTL for Interview Preparation"
date: 2023-10-15
tags: ["Servlets", "JSP", "JSTL", "Interview Questions"]
description: "An extensive guide on Servlets, JSP, and JSTL with common interview questions and answers."
languageCode: "en"
---

# Interview Questions: Servlets, JSP, and JSTL

## Table of Contents

-   [What is a _«servlet»_?](#what-is-a-servlet)
-   [What advantages do servlets have over CGI (Common Gateway Interface)?](#what-advantages-do-servlets-have-over-cgi)
-   [What is the structure of a web project?](#what-is-the-structure-of-a-web-project)
-   [What is a _«servlet container»_?](#what-is-a-servlet-container)
-   [Why are application servers needed if there are servlet containers?](#why-are-application-servers-needed-if-there-are-servlet-containers)
-   [How does a servlet container manage the servlet lifecycle?](#how-does-a-servlet-container-manage-the-servlet-lifecycle)
-   [What is a _«deployment descriptor»_?](#what-is-a-deployment-descriptor)
-   [What actions are required to create servlets?](#what-actions-are-required-to-create-servlets)
-   [When is it necessary to override the `service()` method?](#when-is-it-necessary-to-override-the-service-method)
-   [Is there a point in defining a constructor for a servlet? How should data be initialized?](#is-there-a-point-in-defining-a-constructor-for-a-servlet-how-should-data-be-initialized)
-   [Why is it necessary to override only the `init()` method without arguments?](#why-is-it-necessary-to-override-only-the-init-method-without-arguments)
-   [What are the most common tasks performed in the servlet container?](#what-are-the-most-common-tasks-performed-in-the-servlet-container)
-   [What can you tell me about _servlet filters_?](#what-can-you-tell-me-about-servlet-filters)
-   [Why are various _listeners_ used in servlets?](#why-are-various-listeners-used-in-servlets)
-   [When should servlet filters be used, and when should listeners be used?](#when-should-servlet-filters-be-used-and-when-should-listeners-be-used)
-   [How can a servlet be executed concurrently with the application startup?](#how-can-a-servlet-be-executed-concurrently-with-the-application-startup)
-   [How to handle exceptions thrown by another servlet?](#how-to-handle-exceptions-thrown-by-another-servlet)
-   [What is `ServletConfig`?](#what-is-servletconfig)
-   [What is `ServletContext`?](#what-is-servletcontext)
-   [What are the differences between `ServletContext` and `ServletConfig`?](#what-are-the-differences-between-servletcontext-and-servletconfig)
-   [What is the purpose of the `ServletResponse` interface?](#what-is-the-purpose-of-the-servletresponse-interface)
-   [What is the purpose of the `ServletRequest` interface?](#what-is-the-purpose-of-the-servletrequest-interface)
-   [What is a `Request Dispatcher`?](#what-is-a-request-dispatcher)
-   [How can one servlet call another servlet?](#how-can-one-servlet-call-another-servlet)
-   [What is the difference between `sendRedirect()` and `forward()`?](#what-is-the-difference-between-sendredirect-and-forward)
-   [What are servlet attributes used for, and how do they work?](#what-are-servlet-attributes-used-for-and-how-do-they-work)
-   [How can deadlock occur in a servlet?](#how-can-deadlock-occur-in-a-servlet)
-   [How to obtain the actual location of a servlet on the server?](#how-to-obtain-the-actual-location-of-a-servlet-on-the-server)
-   [How to retrieve information about the server from a servlet?](#how-to-retrieve-information-about-the-server-from-a-servlet)
-   [How to get a client's IP address on the server?](#how-to-get-a-clients-ip-address-on-the-server)
-   [What wrapper classes for servlets do you know?](#what-wrapper-classes-for-servlets-do-you-know)
-   [What are the differences between `GenericServlet` and `HttpServlet`?](#what-are-the-differences-between-genericservlet-and-httpservlet)
-   [Why is the `HttpServlet` class declared as abstract?](#why-is-the-httpservlet-class-declared-as-abstract)
-   [What main methods are present in the `HttpServlet` class?](#what-main-methods-are-present-in-the-httpservlet-class)
-   [Should you worry about multithreading safety when working with servlets?](#should-you-worry-about-multithreading-safety-when-working-with-servlets)
-   [Which HTTP method is not idempotent?](#which-http-method-is-not-idempotent)
-   [What methods are available for sending data from the client to the server?](#what-methods-are-available-for-sending-data-from-the-client-to-the-server)
-   [What is the difference between `GET` and `POST` methods?](#what-is-the-difference-between-get-and-post-methods)
-   [What is the difference between `PrintWriter` and `ServletOutputStream`?](#what-is-the-difference-between-printwriter-and-servletoutputstream)
-   [Can `PrintWriter` and `ServletOutputStream` be used in the same servlet?](#can-printwriter-and-servletoutputstream-be-used-in-the-same-servlet)
-   [Tell me about the `SingleThreadModel` interface.](#tell-me-about-the-singlethreadmodel-interface)
-   [What does _URL encoding_ mean? How do it in Java?](#what-does-url-encoding-mean-how-do-it-in-java)
-   [What different session management methods in servlets do you know?](#what-different-session-management-methods-in-servlets-do-you-know)
-   [What are _cookies_?](#what-are-cookies)
-   [What methods for working with cookies are provided in servlets?](#what-methods-for-working-with-cookies-are-provided-in-servlets)
-   [What is _URL Rewriting_?](#what-is-url-rewriting)
-   [What are the purposes and differences between the methods `encodeURL()` and `encodeRedirectURL()`?](#what-are-the-purposes-and-differences-between-the-methods-encodeurl-and-encoderedirecturl)
-   [What is a _«session»_?](#what-is-a-session)
-   [How to notify an object in a session that the session is invalid or has ended?](#how-to-notify-an-object-in-a-session-that-the-session-is-invalid-or-has-ended)
-   [What effective way exists to ensure that all servlets are available only to users with valid sessions?](#what-effective-way-exists-to-ensure-that-all-servlets-are-available-only-to-users-with-valid-sessions)
-   [How can we ensure _transport layer security_ for our web application?](#how-can-we-ensure-transport-layer-security-for-our-web-application)
-   [How to organize database connection and logging in a servlet?](#how-to-organize-database-connection-and-logging-in-a-servlet)
-   [What are the main features in the _Servlet 3_ specification?](#what-are-the-main-features-in-the-servlet-3-specification)
-   [What types of authentication are available to a servlet?](#what-types-of-authentication-are-available-to-a-servlet)
-   [What is _Java Server Pages (JSP)_?](#what-is-java-server-pages-jsp)
-   [What is the purpose of JSP?](#what-is-the-purpose-of-jsp)
-   [Describe how JSP pages are processed, from request to response.](#describe-how-jsp-pages-are-processed-from-request-to-response)
-   [Tell us about the stages (phases) of the JSP lifecycle.](#tell-us-about-the-stages-phases-of-the-jsp-lifecycle)
-   [Discuss the methods of the JSP lifecycle.](#discuss-the-methods-of-the-jsp-lifecycle)
-   [Which JSP lifecycle methods can be overridden?](#which-jsp-lifecycle-methods-can-be-overridden)
-   [How can direct access to a JSP page from the browser be prevented?](#how-can-direct-access-to-a-jsp-page-from-the-browser-be-prevented)
-   [What is the difference between _dynamic_ and _static_ content in JSP?](#what-is-the-difference-between-dynamic-and-static-content-in-jsp)
-   [How to comment code in JSP?](#how-to-comment-code-in-jsp)
-   [What are the main types of JSP tags?](#what-are-the-main-types-of-jsp-tags)
-   [What can you tell me about JSP actions (_Action tag_ and _JSP Action Elements_)?](#what-can-you-tell-me-about-jsp-actions-action-tag-and-jsp-action-elements)
-   [How to extend the functionality of JSP?](#how-to-extend-the-functionality-of-jsp)
-   [What do you know about writing custom JSP tags?](#what-do-you-know-about-writing-custom-jsp-tags)
-   [Provide an example of using custom tags.](#provide-an-example-of-using-custom-tags)
-   [How to create line breaks in HTML using JSP?](#how-to-create-line-breaks-in-html-using-jsp)
-   [Why is it unnecessary to configure standard JSP tags in `web.xml`?](#why-is-it-unnecessary-to-configure-standard-jsp-tags-in-webxml)
-   [How to handle errors on JSP pages?](#how-to-handle-errors-on-jsp-pages)
-   [How is error handling performed with JSTL?](#how-is-error-handling-performed-with-jstl)
-   [How is JSP configured in the deployment descriptor?](#how-is-jsp-configured-in-the-deployment-descriptor)
-   [Is it possible to use JavaScript on a JSP page?](#is-it-possible-to-use-javascript-on-a-jsp-page)
-   [Is a session object always created on a JSP page, and can its creation be disabled?](#is-a-session-object-always-created-on-a-jsp-page-and-can-its-creation-be-disabled)
-   [What is the difference between `JSPWriter` and servlet `PrintWriter`?](#what-is-the-difference-between-jspwriter-and-servlet-printwriter)
-   [Describe general practical principles of working with JSP.](#describe-general-practical-principles-of-working-with-jsp)

...

## What is a _«servlet»_?

A **servlet** is an interface whose implementation extends the capabilities of a server. Servlets interact with clients via the request-response mechanism. While servlets can cater to any request, they are primarily used to extend web servers.

The majority of classes and interfaces necessary for creating servlets are contained within the `javax.servlet` and `javax.servlet.http` packages.

The primary methods of a servlet include:

-   `public void init(ServletConfig config) throws ServletException`, which is invoked immediately after the servlet is loaded into memory;
-   `public ServletConfig getServletConfig()`, which returns a reference to the object that grants access to the servlet's configuration information;
-   `public String getServletInfo()`, returning a string with information about the servlet, such as its author and version;
-   `public void service(ServletRequest request, ServletResponse response) throws ServletException, java.io.IOException`, called to process each request;
-   `public void destroy()`, executed before the servlet is unloaded from memory.

The current specification – Servlet 3.1 is outlined in JSR-340 and was adopted in 2013.

## What advantages do servlets have over CGI (Common Gateway Interface)?

-   Servlets offer improved request processing performance and more efficient memory use thanks to multithreading (a new thread is created for each request, which is faster than creating a new object for each request as is the case in CGI).
-   Servlets are platform-independent. Therefore, a web application developed using servlets can run on any servlet container that complies with the standard and on any operating system.
-   The use of servlets enhances program reliability since the servlet container manages the lifecycle of servlets (thus taking care of potential memory leaks), security, and garbage collection.
-   Servlets are relatively easy to learn and maintain, allowing developers to concentrate solely on the application's business logic rather than the inner workings of web technologies.

## What is the structure of a web project?

The typical structure of a web project can include the following directories:

-   `src/main/java`: Application/library source files
-   `src/main/resources`: Resource files for the application/library
-   `src/main/filters`: Servlet filter files
-   `src/main/webapp`: Web application source files
-   `src/test/java`: Test source files
-   `src/test/resources`: Resource files for tests
-   `src/test/filters`: Tests for servlet filters
-   `src/it`: Integration tests
-   `src/assembly`: Assembly description
-   `src/site`: Site
-   `LICENSE.txt`: Project license
-   `NOTICE.txt`: Notes and definitions of dependency libraries
-   `README.txt`: Project description

## What is a _«servlet container»_?

A **servlet container** is a program that serves as a server managing the system support for servlets and handles their lifecycle according to the rules defined in the specifications. It can function as a standalone web server, serve as a page provider for another web server, or integrate with a Java EE application server.

The servlet container facilitates data exchange between the servlet and clients, taking on responsibilities like creating a runtime environment for executing the servlet, and identifying and authorizing clients, as well as organizing sessions for each of them.

Notable servlet container implementations include:

-   Apache Tomcat
-   Jetty
-   JBoss
-   WildFly
-   GlassFish
-   IBM WebSphere
-   Oracle WebLogic

## Conclusion: Key Concepts and Best Practices for Servlets, JSP, and JSTL

Servlets and JSP (JavaServer Pages) are fundamental technologies within Java EE, used to create dynamic web applications. Understanding how servlets work, how to manage their lifecycle, and how JSP integrates with servlets can significantly enhance web application development. Utilizing JSTL for managing XML data, internationalization, and conditionals can further streamline coding practices, making applications more robust and easier to maintain.

When preparing for interviews, focus on the lifecycle methods of servlets and JSP, the differences between servlets and JSP, and the advantages of using JSTL. SQL and database connectivity, error handling, and servlet filters are also vital areas to cover. A deep understanding of these concepts will not only help in interviews but will also be beneficial in practical applications of Java EE technologies.

By mastering servlets, JSP, and JSTL, developers can build powerful and efficient web applications that meet modern user demands.
