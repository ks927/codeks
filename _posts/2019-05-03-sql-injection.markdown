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

During a code review, my boss found an alarming pattern in my SQL queries. I was taking user input and directly <i>injecting</i> it into the database calls. Here is an example of what I mean:

Obviously I’ve heard of <strong>SQL injection</strong>, but being limited in database experience, I did not know what it actually was or how to avoid it. So my boss said to me, “what if a user makes a network request with the parameters…” and proceeded to write this in my test file: `Drop database internal;`. I got his jist, but before I could erase the line and make my changes, he wanted to show me what he was working on on his computer. I returned to my machine twenty minutes later with a head full of what he just showed me. I ran the test file, completely forgetting about his malicious example, and my database was history. 