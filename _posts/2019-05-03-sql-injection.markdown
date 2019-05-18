---
layout: post
title:  "What is SQL Injection?"
subtitle: "How I Wiped my Database"
date:   2019-05-03 10:40:45 -0500
categories: [MySql]
---

# A Lesson Learned

![xkcd comic]({{ site.url }}/assets/images/sql_injection.png "XKCD Comic"){:class="img-landscape"}

I wiped a database today. Ironically, it was an accident following a lesson about SQL injection from my boss. I can think of safer, but less effective ways to retain this lesson. Regardless, it’s a mistake I will not make again, and luckily it was only my local database. Here’s how it happened:

During a code review, my boss found an alarming pattern in my SQL queries. I was taking user input and directly <i>injecting</i> it into the database calls. In PHP, that is placing the request values from the `$_POST` object in the `SELECT` queries without any validation. For example:

![id injection]({{ site.url }}/assets/images/sql_injection1.png "User query"){:class="img-landscape"}

Obviously I’ve heard of <strong>SQL injection</strong>, but being limited in database experience, I did not know what it actually was or how to avoid it. So my boss said to me, “what if a user makes a network request with the parameters…” and proceeded to write this in my test file: `Drop database internal;` (internal being the nanme of the db). I got his jist, but before I could erase the line and make my changes, he brought me to his computer to show me what he was working on. I returned to my machine twenty minutes later and ran the test file, completely forgetting about his example line, and my database was history. 

The way to avoid malicious injection using my screenshot above would be to validate and assign the user input to a variable, and then place it into the query. For example:

![var declaration]({{ site.url }}/assets/images/sql_injection_var.png "user_id declaration"){:class="img-landscape"}

Php's `intval()` function gets the integer value of a variable. Thus if someone tries to send `Drop database internal;` as the id, the php will fail before even getting to the SQL query. 
