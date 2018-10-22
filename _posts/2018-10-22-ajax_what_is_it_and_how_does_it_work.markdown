---
layout: post
title:      "AJAX: What is it and how does it work? "
date:       2018-10-22 22:59:36 +0000
permalink:  ajax_what_is_it_and_how_does_it_work
---


One of the biggest misconceptions about AJAX is that it is a programming language. AJAX is **not** a programming language, it is actually a set of development techniques used when building websites and web applications. 

### What does AJAX stand for? 
Asynchronous JavaScript and XML

### What does AJAX do?
The core function of AJAX is to update web content **a**synchronously. This means that the web browser does not need to reload the web page when only a portion of the content on the page needs to be changed. 

### How does AJAX work? 
**J**avascript and **X**ML (Extensible Markup Language) combine together to make asynchronous updating happen through the use of an XMLHttpRequest object. As a user visits a web page and an event occurs (user loads the page, clicks a button, etc.), JavaScript creates an XMLHttpRequest object, which transfers data in an XML format between the web browser and web server. Then, the XMLHttpRequest object sends a request to the web server and the server processes the request. The server creates a response and sends it back to the browser, which uses JavaScript to process the response. The updated content is then displayed on the screen.

In summary: 

**Browser**<br>
An event occurs in a web page (i.e. page is loaded, button is clicked, etc.).<br>
An XMLHttpRequest object is created by JavaScript.<br>
The XMLHttpRequest object sends a request to a web server.<br>

**Server**<br>
The server processes the request.<br>
The server sends a response back to the web page.<br>

**Browser**<br>
The response is read by JavaScript.<br>
Proper action (page update) is performed by JavaScript. 

### What is a popular example of AJAX? 
One of the most popular examples of AJAX is Google’s “Google Suggest” feature. This is the auto-complete feature that appears when you enter a search query into Google’s search bar. This example shows the magic of AJAX, as the content on the page changes without the need to manually refresh the page. 

#### Resources
[AJAX—What It Is, How It Works, and What It’s Used For](https://skillcrush.com/2018/04/26/what-is-ajax/) 
<br>
[AJAX Introduction](https://www.w3schools.com/xml/ajax_intro.asp) 
