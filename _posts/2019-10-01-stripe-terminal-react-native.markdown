---
layout: post
title:  "How to Integrate Stripe Terminal with React Native"
subtitle: "react-native-stripe-terminal and custom Android"
date:   2019-10-01 10:40:45 -0500
categories: [React Native, iOS, Android]
---

# Beginning with iOS

My company put me in charge of creating the feature that would connect our React Native app with a Stripe credit card swiper ([BBPOS Chipper 2X](https://stripe.com/docs/terminal/readers/bbpos-chipper2xbt)). As of this writing, [Stripe's Terminal Service's](https://stripe.com/docs/terminal) documentation only covers native mobile integration. So before I started, I was under the impression that I was going to invent the solutions for integrating both iOS and Android with React Native. About 4 weeks into my progress on iOS, I emailed Stripe support about a problem I was having that I just could not figure out. They forwarded me to this already built, brilliant library that had solved the iOS native modules problem - [react-native-stripe-terminal](https://github.com/theopolisme/react-native-stripe-terminal). Had I known this repo had Stripe's backing, I could have saved myself about a month of spinning my wheels, but in that time I was forced to learn Objective-C, and ultimately am thankful for not having used it sooner. 

Sometime I may write about the issue that had me stuck, because it is an interesting threading topic.  My boss and I collaborated with Stripe support for a few emails, before we ultimately figured out for them. Not until after we sent our solution did they direct us to the aforementioned library, which we learned had beat us to the fix.

# Onto Android

As of this writing, no Android integration has been accepted into the [react-native-stripe-terminal](https://github.com/theopolisme/react-native-stripe-terminal) repo, though there is a PR pending. My personal project was finished a day or two after that PR was made, so while I did borrow a few lines of code from it, the vast majority of what I wrote I created myself. I've had some but very limited Android experience, so this was another great opportunity to learn a new language and deep dive into Java.