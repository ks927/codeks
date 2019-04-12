---
layout: post
title:  "What Your First Job will be Like Pt. 2"
subtitle: "Or What My First Job <i>is</i> Like"
date:   2019-04-06 10:40:45 -0500
categories: [Career]
---

# Developing for Production vs. Personal Projects

 One of the hardest obstacles to navigate in your first job is the difference between programming for fun and programming when something is at stake. When you develop a project for no one’s use but your own education, you can be as careless as you want. You create an application and each feature works as you imagine it should. Finished right? Maybe for your project, but for an application with thousands of users, countless edge cases, and money at stake, it is never so simple. My boss likes to tell me that I’m great at solving problems for the “happy circumstances”. Meaning I almost always find a solution and push code for the base case. Examples of this vary widely, so I will use an instance of dealing with external APIs. I recently completed a task that leveraged [Twilio](https://www.twilio.com/) to text users a verification code after sign up. I’d never done this before, so once I got Twilio to text my device, I smiled, rubbed my hands together, and declared victory. “There’s a small issue” as my boss would say, regardless of the size of said issue. What if Twilio is down and the request to their API fails? Our user never receives a message, never find outs why, and doesn’t complete the sign up. We don’t get their membership and we don’t get their money. Huge issue. Perhaps this example doesn’t stress the importance of what I’m trying to say, but my point is, when you start work for a company with more to lose than your own education, it is *vital* to think about and account for all edge cases. "Just getting it to work", while a good place to start, is never good enough to push live.

# Am I Going Too Fast?

“Better perfect than done” is another quote I’ve grown accustomed to hearing in the past half-year. I used to finish my tickets and make pull requests so quickly that my boss would be left slack-jawed and unprepared to give me more work. Only after realizing I’d been checking for no more than the “happy circumstances” did he bestow upon me this advice. It is better to ensure the code is perfect than it is the task done. You may be tempted to impress your employer with how efficiently you turn around tickets, but the team is no longer efficient if your co-workers have to clean up buggy, incomplete code. It is *always*, **always**, worth it to take another hour, another day, to read through and test every function or variable or behavior. If you really want to impress your peers, push code that needs little revision. This saves time for everyone, plain and simple. 

# Code Readability > Fancy Play

Speaking of plain and simple, you should always strive for the simplest and most readable solution. We all know most logic can be condensed with ternary operators and/or language specific functions. But quantity, in this case, and quality, are not inversely proportional. What’s more important is how quickly someone who’s never seen your code before can read it and understand what it’s doing. Even more essential is that this person can modify its functionality with little cognitive effort. You may think, "well isn't this point kind of subjective?" Yes, and no. If you're unsure the best way to convey confusing code, ask your superior!

# Ask Questions

As pointed out in the [previous post]({{ "/career/2019/03/15/your-first-job1.html" | absolute_url }}), programmers are not famous for their social skills. As a result, you may be intimidated or even embarrassed to ask questions about the task at-hand. Again - totally normal. I would consider this my greatest fault as a junior developer. I hate when people think I'm dumb, and I hate not being able to figure out things on my own. Who doesn't? But this is another place you need to be able to set ego aside and put things into perspective. Curious people ask questions. Smart people ask questions. The quickest way to learn, and the quickest way to complete a task is to ask questions. Just make sure you keep it specific and aren't asking for your hand to be held. Asking something general and vague like "how do I do this?" is an easy way to annoy your questionee. Instead, explain how you've already tried to solve it yourself, and what exactly it is you're not getting. "I've tried 'x' and 'y', but the data is structured 'like so'. I'm having trouble figuring out the most elegant solution here". This will show what your thought process was and that you were at least willing to try. It will also narrow down what needs explaining, thus saving everyone time. 

At first, you will probably need a lot of explanation on the new codebase, best practices, style, etc. The more tasks you complete and the more questions you ask, the more clearly you will be able to see the puzzle fitting together. The sooner you adapt a humble mindset, the sooner you will pick it up. So put ego aside and don't be embarrassed to ask!


