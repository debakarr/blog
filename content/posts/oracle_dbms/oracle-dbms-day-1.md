---
title:  "[Training] DBMS with Oracle Day 1"
date:   2017-07-18
comments: true
author: Debakar Roy
authorLink: https://github.com/debakarr
tags: ["Oracle", "DBMS", "Database", "SQL", "Tutorial", "Day 1"]
categories: ["Database Management", "Programming"]
resources:
- name: "day5.jpg"
  src: "http://i.imgur.com/bDVJGg3.png"
lightgallery: true
---


![](http://i.imgur.com/bDVJGg3.png)

<hr><br />

In this post, I am going to wrap up all the things I learned during my first class on 'DBMS with Oracle'. The training lecture is given by '**Rahul Sohal**', CTO & Resource Management Lead of [iandwe.in](https://secure.iandwe.in/). 



 **So first of all what is database?**  

A **database** is a collection of information kept an organized way, for the ease of retrieval. 

Facebook has its own database. Think about yesterday when you logged in your account and like all those posts, share certain stuff, commented on a picture. This all things are stored in a database and when you logged into your account today, all this information are retrieved from the database. 

<hr><br />

 **Now next we were taught about what is so called DBMS? ** 

As because we are Computer Science students we were familiar with the term. We have actually used **DBMS** like **mySQL** and **Microsoft Access**. So a DBMS stands for '**Database Management System**'. Basically it's a system software for creating as well as managing databases. So it provides a way by which a programmer/user can create, retrieve, update and manipulate the data in different ways. 

So we are going to learn **DBMS with Oracle**. As most of us have done mySQL, Rahul sir asked us the difference between mySQL and Oracle DBMS. I have not on Oracle DBMS before but I somewhat knew that Oracle DBMS is used fir more complex queries other the mySQL. In addition, it supports far more join then mySQL which only supports 61 join limit (These things I know as because I have used mySQL for managing database of my own website at some point, and I never have to use any complex queries). Then Rahul sir told us that Oracle is used for '**Enterprise Business Applications**' in big companies whereas mySQL is used by small companies as it is somewhat easier to use. 

<hr><br />

 **Next how data are processed between client and server? ** 

From client side, we send a request with the help of SQL(Structured Query Language). Then the server returns a tuple on the successful execution of SQL statement. The server is generally hosted on 127.0.0.1:8080. Here 127.0.0.1 is IP and is basically called localhost and 8080 is the port which can be changed during installation of the Oracle DBMS. 

<hr><br />

The data is generally organized as a **table** containing **rows** and **columns**. Here's a basic example:

| ROLL | NAME | 
| ------------- |:-------------:| 
| 1 | Rahul | 
| 2 | Baka | 
| 3 | Debakar | 

<br />

Here table contains Roll and Name which are attributes and each row contains one data. 
<hr><br />

If we need to display data for roll no. 1 then the query for that is:

```
SELECT * FROM STUDENT WHERE ROLL = 1;
```

<hr><br />
In Oracle  **SYSDBA** is administration privilege used to perform certain high-level administration operations such as granting privileges to other users, starting or shutting down databases and so on. 
<hr><br />
We used **Oracle 11g Express Edition** as Oracle DBMS. To be honest, the installation process is self-explanatory. After installation, to write up SQL queries we just need to go to start and search for something called 'SQL Plus'. This lets us write SQL queries on **CUI (Character User Interface)**. The first thing is to log in as SQLDBA. For that we have to type:



```
CONNECT / AS SYSDBA;
```

<hr><br />

To create a user we have to type:

```
CREATE USER <USERNAME> IDENTIFIED BY <PASSWORD>;
```

<hr><br />

Before jumping into creating the table we need to provide some **privilege** to the newly created user. This thing is quite new to me as in mySQL, we can directly create a table after creating and using one database. In Oracle, we have to assign privilege to the user using SYSDBA. The few common privilege can be assigned like this:



```
GRANT CONNECT TO <USERNAME>;
GRANT RESOURCE, DBA TO <USERNAME>;
GRANT CREATE SESSION TO <USERNAME>;
GRANT UNLIMITED TABLESPACE TO ;
```

<hr><br />

After this we can connect to our user like this:

```
CONNECT
Enter user-name: your_user_name 
Enter password: your_password
```

<hr><br />

Then we need to give privilege for the basic **DML(Data Manipulation Language)** commands. This can be done like this:

```
GRANT SELECT, INSERT, UPDATE, DELETE ON <TABLENAME> TO <USERNAME>
```

<hr><br />

But the above command only works after you created a table. This all privilege things are really something to consider in the difference between mySQL and Oracle. Up till now, I get one thing clear, that Oracle DBMS has much greater function than mySQL. 

<hr><br />
After this we created one table like this:

```
CREATE TABLE STUDENT(ROLL NUMBER, NAME VARCHAR2(30), DOB DATE) ;
```

<hr><br />

This takes us in a situation where we can talk about something called '**Data Redundancy**'. Rahul Sir told us that in the table we just created we can have as many numbers of the row as we want with same data. Which is nothing but a waste of space. Same data at different rows thus data which is not useful at all is cramming up all the spaces and hence it is called 'Data Redundancy'. He told us that it frequently happens when a beginner makes a form and due to some Internet issues we as a user end up submitting the form 10 times and our data is placed on the table 10 times causing 'Data Redundancy'. Up till now, I know all the things he was trying to explain and believe me I also know that he is going to tell us about constraints after this. Then he explained to us what is **Primary key, composite key and unique key**. 

<hr><br />

Then after all this, we were told about the **entities, relation, attributes and most important ER-Diagram** (Here ER Stands for **Entity Relationship**). To be honest it is not my first time hearing all this but I never bothered about drawing ER-Diagram before. 

<hr><br />

Then we were taught about the ER-Diagram in more depth. Few Diagrams we came to know about are as follows:

![](http://static3.creately.com/blog/wp-content/uploads/2012/03/ER-Diagram-Elements.jpeg)

<br />

![](https://image.slidesharecdn.com/topic-0304-131211014219-phpapp01/95/topic-03-04-entity-relationship-modelling-32-638.jpg?cb=1415320739)
###### NOTE: These pictures are taken from the internet. Yep I did a little bit of research. 
<hr><br />

Rahul sir have also given us some definitions on some of the basic terminologies. This includes **Entity, Relationship, Keys, Super keys, Candidate keys**. 

<hr><br />

Now we were shown Relationship in ER-Diagram, which somehow ends our Day-1 Training. We were given a problem of making a '**Employee Database**'. 
<hr><br />

Finally, as I have almost finished writing this blog and believe me, I am a beginner blogger. So writing up this blog took me a good amount of time. I ended up not doing any real stuff at home today. Still, I think I can make it up on tomorrow's class. I will also try to wrap up tomorrow's lecture in another upcoming blog post.