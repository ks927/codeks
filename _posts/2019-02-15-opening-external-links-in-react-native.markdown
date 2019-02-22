---
layout: post
title:  "Opening External Apps from React Native"
subtitle: "How to Use React Native Linking"
date:   2019-02-15 20:40:45 -0500
categories: [React Native]
---

# How to Open SMS/Email/Twitter/Facebook from React Native Application

Most apps have a "Share on 'other app'" button these days. That button most likely opens another app on your device, and maybe even pre-populates an input with custom text for you. React Native, once again, makes adding this feature fairly straightforward and painless. Both for iOS and Android. Here is an example of a screen with multiple options, and the following is how to get those buttons to work to open their apps and fill in custom text for the user.

![invite page]({{ site.url }}/assets/images/invitepage.png "Invite Page"){:class="img-sm-landscape"}

![share buttons]({{ site.url }}/assets/images/share_buttons.png "Invite Page"){:class="img-landscape"}

# One Function to Rule Them All

If we set up each button to hit the same function, as I've done above, a simple switch statement will take care of all of our functionality. React Native's [Linking](https://facebook.github.io/react-native/docs/linking) API allows us to open external links from within our app. 

![share function]({{ site.url }}/assets/images/share_function3.png "Invite Page"){:class="img-landscape"}

When a user clicks **SMS**, our function needs to check whether he is using an iPhone or Android, due to slight variations in syntax. In *iOS*,  `'sms:number&body=' + YOUR_MESSAGE`, uses the & between parameters; while Android `'sms:number?body=' + YOUR_MESSAGE` uses the ?. In my case, I wanted to leave the number blank, so the user could fill in their contact with my message filling the body of the text. 

Oddly enough, both platforms **Email** syntax is the same, and both use the ?. Full disclosure, StackOverflow showed some variety regarding which syntax was supposed to work for which platform and took some fiddling to get mine to work. If my examples don't work for you, try mixing-and-matching the syntax.

When it behooves us to check whether our users have an app we want to open for them or not, the code gets *slightly* more complicated (but not really). In order to check for Facebook or Twitter, like in my code snippet, the Linking API provides the `Linking.canOpenUrl` function. Facebook uses 'fb://' while Twitter uses 'twitter://' to open their apps. If the user has an app available on their phone, the `canOpenUrl` will return `true`. Otherwise, we can provide a link to open the web apps.

My example provides the proper syntax for sharing a custom URL as your Facebook status and drafting a tweet with a custom message. 



