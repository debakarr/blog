---
title:  "Building a Restful API using JAX-RS"
date:   2017-09-27
comments: true
author: Debakar Roy
authorLink: https://github.com/debakarr
tags: ["RESTful", "API", "JAX-RS", "Java", "Tutorial", "Web Development"]
categories: ["Programming", "Web Development", "API"]
---





![](http://webstar.company/wp-content/uploads/2014/02/glassfish_logo1.png)

<hr><br />
This post will guide you through a series of steps you will need to create a Restful API for a simple book database using Jersey (an implementation of JAX-RS specification). The resultant API will be able to fetch all the books or book wih their specific ID, add a new book, update a book by its ID, remove a book from database and run queries to search for book(s) according to subject ID or title. Also, if the image is too small for you to see the details clearly, please do open it in a new tab. Also for the time being the codes are not commented properly. I will provide the full source code which is commented properly in coming future.

<hr><br />


[1. What are the tools needed?](#tools)

[2. Basic setup](#setup)

[3. Setting up Tomcat Server and Postman](#tomcatAndPostman)

[4. Structure](#structure)

[5. Book Model](#bookModel)

[6. Book Database](#database)

[7. Book Services](#bookServices)

[8. Book Resource](#bookResource)

[9. GET](#get)

[10. PUSH](#push)

[11. PUT](#put)

[12. DELETE](#delete)

[13. Query](#query)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[Get Book(s) by title](#title)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[Get Book(s) by subject ID](#subjectId)


<a name="tools"></a>
<h2> What are the tools needed? </h2>
First, we are going to use Eclipse IDE. You can download eclipse from [here](https://www.eclipse.org/downloads/eclipse-packages/). Download the one that says **Eclipse IDE for Java EE Developers**.

Another thing we are going to use is called Postman. Postman is an HTTP Request composer. It helps you test your API in a very efficient way. You can download Postman from [here](https://www.getpostman.com/apps).
<hr><br />
<a name="setup"></a>
<h2> Basic setup</h2>
First we need to create a **Maven Project**.
Go to **File->New->Maven Project->Next**
If you already have jersey archetype there then select it. If not you have to click on **Add Archetype...**.

Fill in the following data
<hr><br />
**Archetype Group Id**: org.glassfish.jersey.archetypes

**Archetype Artifact Id**: jersey-quickstart-webapp

**Archetype Version**: 2.16
<hr><br />
Then click **OK** and select  **jersey-quickstart-webapp** and click **Next**.

**Alternatively** you can add the following dependency after creating your Maven Project.

```
<!-- https://mvnrepository.com/artifact/org.glassfish.jersey.archetypes/jersey-quickstart-webapp -->
<dependency>
    <groupId>org.glassfish.jersey.archetypes</groupId>
    <artifactId>jersey-quickstart-webapp</artifactId>
    <version>2.16</version>
</dependency>
```

Now next you need to type your project detail. Mine is:

Group Id: org.debakar.bakadigest
Artifact Id: bookDatabase

This will create a package **org.debakar.bakadigest.bookDatabase** where your resource files are stored.

The very first thing you need to do is open up your project and double-click pom.xml. Now head to pom.xml tab and uncomment moxy dependency. This will let you produce JSON data. This is the same place where you can add jersey dependency after creating a Maven Project using maven archetype.

```
<dependency>
            <groupId>org.glassfish.jersey.media</groupId>
            <artifactId>jersey-media-moxy</artifactId>
</dependency>
```
<hr><br />
<a name="tomcatAndPostman"></a>
<h2> Setting up Tomcat Server and Postman</h2>
Now, as we are all done with eclipse setup part, for now, it’s time to get our server running up. For this, we will use Tomcat. Go to **Server** tab, and click on **No servers found. Click this link to create a server** and then select the tomcat version, under **Apache** that you have. [Here’s](https://tomcat.apache.org/download-90.cgi) a link for tomcat 9. And then click **Next**. Select the tomcat directory and click **Next**. Then add your project and click **Finish**.

And for Postman does need any particular step to install. You just need to install it basically as you install other application or add the chrome app available if you are using chrome.
<hr><br />
<a name="structure"></a>
<h2> Structure</h2>

Here’s the project structure:

![](https://goo.gl/4kznJW)

<hr><br />
<a name="bookModel"></a>
<h2> Book Model</h2>
This is model for every book, which is self-explanatory.

![](https://goo.gl/wvK8HF)
<hr><br />
<a name="database"></a>
<h2> Book Database</h2>
Basically, you need to connect to a database in this, but for the explanatory purpose we can create a map that maps each book according to their id.

![](https://goo.gl/Y4ZoiS)

**NOTE**: This is not a great way when you do it for business purpose.
<hr><br />
<a name="bookServices"></a>
<h2> Book Services</h2>
This includes all the services like add book, delete book  etc. Also I added 2 books in the constructor.

![](https://goo.gl/huAXcn)

<hr><br />
<a name="bookResource"></a>
<h2> Book Resource</h2>
This is the file which actually implements the API.

![](https://goo.gl/2YvoRN)
<hr><br />
<a name="get"></a>
<h2> GET</h2>
<h3> Getting all books:</h3>

![](https://goo.gl/WjpKkS)

<h3> Getting book by ID:</h3>
<h4> Getting book with ID ‘1’:</h4>

![](https://goo.gl/Yzgmj6)

<h4> Getting book with ID ‘2’:</h4>

![](https://goo.gl/4gs3d1)
<hr><br />
<a name="push"></a>
<h2> PUSH (Add book)</h2>

<h3> Adding a book in database (auto assigned ID '3')</h3>
![](https://goo.gl/bsR4D1)

<h3> Adding a book in database (auto assigned ID '4')</h3>
![](https://goo.gl/xCko6a)

<hr><br />
<a name="put"></a>
<h2> PUT (update book)</h2>
<h3> Updating book with ID '3'</h3>
![](https://goo.gl/WsVpVe)

<h3> If we do a GET request for book with ID '3', we will get the updated data</h3>
![](https://goo.gl/k2eGbo)
<hr><br />
<a name="delete"></a>
<h2> DELETE (remove book)</h2>
<h3> Removing the book with ID '3'</h3>
![](https://goo.gl/jHTKTS)

<h3> Display available book (book with ID '3' got deleted)</h3>
![](https://goo.gl/1qJ1pJ)
<hr><br />
<a name="query"></a>
<h2> Query</h2>
<a name="title"></a>
<h3> Get Book(s) by title (here we are searching for book(s) with 'algorithm' in its title)</h3>
![](https://goo.gl/7VYuUB)

<a name="subjectId"></a>
<h3> Get Book(s) by subject ID (here we are searching for book(s) with subject ID '1')</h3>
![](https://goo.gl/63xuS9)

<hr><br />
To know more about Jersey, head to [this documentation](https://jersey.github.io/documentation/latest/index.html). You can also follow [Koushik Kothagal](https://www.linkedin.com/in/koushiksrinivas) on his YouTube channel [Java Brains](https://www.youtube.com/user/koushks).