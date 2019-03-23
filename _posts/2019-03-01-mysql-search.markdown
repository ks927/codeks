---
layout: post
title:  "Implementing a Closest String Match in MySQL"
subtitle: "How to Utilize Navicat Functions"
date:   2019-03-01 20:40:45 -0500
categories: [MySql]
---

# Levenshtein

If you want your search feature to be more intuitive than comparing a query with the `LIKE` operator, the [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) string metric is what you are looking for. Simply put, it assigns a number to the amount of edits it takes to get from one word to another. This way, you can return an array of matches within however many edits you'd like, to provide a search that better understands typos and mispellings.

# Don't Try to Write It Yourself

If like me, you are using a MySQL database, there are numerous resources online with already written Levenshtein Distance functions. There is no reason to have to write one yourself, but if you're ambitious, I'm not stopping you. Here is a [link](http://www.artfulsoftware.com/infotree/qrytip.php?id=552) for the main and helper functions that I used. The trouble for me wasn't finding the solution; it was how to implement it in Navicat and call it from my codebase. Maybe I'm just dumb and it's common knowledge, but for some reason there is a dearth of information on the topic, so I hope to provide the details here. 

# Navicat

![navicat function]({{ site.url }}/assets/images/navicat_function.png "Invite Page"){:class="img-landscape"}

Within your Navicat database, there is a tab called **Functions**. You can either **right-click -> New Function** or **left-click** and use the **+ function** button underneath the objects tab to create your function. The above screenshot shows my function called `levenshtein`. Underneath the **Functions** tab there is a helper function `levenshtein_ratio` that references this function and converts the edit amount to a percentage. This is what I will be calling directly within my query.

The simplest part and what took the most time to figure out, was how to use one of these functions within a query. The `levenshtein_ratio` function takes 2 parameters - both strings. What I wanted was for 1 to be the search query from the user, and the other to be each name within the `User` table of my database. Again, maybe I'm not the sharpest tool in the shed, but I could find no examples of this and couldn't wrap my head around how to do it myself. But it really is as easy as placing it within the `SELECT` query as shown below. I found that a distance of 40 was a good threshold for similarity, but you can finagle with the exact number. 

![navicat query]({{ site.url }}/assets/images/navicat_query.png "Invite Page"){:class="img-landscape"}
