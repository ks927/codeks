---
layout: post
title:  "What Your First Job will be Like Pt. 2"
subtitle: "Or What My First Job <i>is</i> Like"
date:   2019-03-28 10:40:45 -0500
categories: [Career]
---

# Developing for Production vs. Personal Projects
 One of the hardest obstacles to navigate in your first job is the difference between programming for fun and programming when something is at stake. When you develop a project for no one’s use but your own education, you can be as careless as you want. You create an application and each feature works as you imagine it should. Finished right? Maybe for your project, but for an application with thousands of users, countless edge cases, and money at stake, it is never so simple. My boss likes to tell me that I’m great at solving problems for the “happy circumstances”. Meaning I almost always find a solution and push code for the base case. Examples of this vary widely, so I will use an instance of dealing with external APIs. I recently completed a task that leveraged [Twilio](https://www.twilio.com/) to text users a verification code after sign up. I’d never done this before, so once I got Twilio to text my device, I smiled, rubbed my hands together, and declared victory. “There’s a small issue” as my boss would say, regardless of the size of said issue. What if Twilio is down and the request to their API fails? Our user never receives a message, never find outs why, and doesn’t complete the sign up. We don’t get their membership and we don’t get their money. Huge issue. Perhaps this example doesn’t stress the importance of what I’m trying to say, but my point is, when you start work for a company with more at stake than your own education, it is *vital* to think about and account for all edge cases. 

# Am I Going Too Fast?
“Better perfect than done” is another quote I’ve grown accustomed to hearing in the past half-year. I used to finish my tickets and make pull requests so quickly that my boss would be left slack-jawed and unprepared to give me more work. Only after realizing I’d been checking for no more than the “happy circumstances” did he bestow upon me this advice. It is better to ensure the code is perfect than it is the task done. You may be tempted to impress your employer with how efficiently you turn around tickets, but the team is no longer efficient if your co-workers have to clean up buggy, incomplete code. It is *always*, **always**, worth it to take another hour, another day, to read through and test every function or variable or behavior. If you really want to impress your peers, push code that needs little revision. This saves time for everyone, plain and simple. 

# Code Readability > Fancy Play
Speaking of plain and simple, you should always strive for the simplest and most readable solution. We all know most logic can be condensed with ternary operators and/or language specific functions. But quantity, in this case, and quality, are not inversely proportional. What’s more important is how quickly someone who’s never seen your code before can read it and understand what it’s doing. Even more essential is that this person can modify its functionality with little cognitive effort.
