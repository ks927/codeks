---
layout: post
title:  "How to Add Offline Notice Banner in React Native App"
date:   2019-02-01 20:40:45 -0500
categories: [React Native]
---

# Offline Notice

![offline notice]({{ site.url }}/codeks/assets/images/offline_notice.png "Offline Notice"){:class="img"}

User experience-wise, it is always more convenient to display through the app when there is no internet connection. This way, users won't assume the app is broken and immediately call your customer support number - when the only problem is they've lost the internet. Aside from a couple tricks, adding this feature is super simple in React Native.

React Native comes with a [NetInfo](https://facebook.github.io/react-native/docs/netinfo) module that does all the heavy lifting for you. All you need to do is create the component, style it the way you want, and stick it in your top-level App.js class. I used [this post on Medium](https://medium.com/dailyjs/offline-notice-in-react-native-28a8d01e8cd0) as a guide, but made a few minor tweaks.

![offline component 1]({{ site.url }}/codeks/assets/images/offline_component1.png "Offline Component 1"){:class="img-landscape"}

First, It is important to instantiate your state variable to assume there is internet connection so that the banner doesn't flash on first load. Second, in componentDidMount, we call NetInfo's isConnected() function, to check the status of our internet connection. When this promise resolves, we do two things: 1. Call our handleConnectivityChange function so that this gets used on mount. 2. Set up an event listener for future connection changes and hook it up to this same function.

![offline component 2]({{ site.url }}/codeks/assets/images/offline_component2.png "Offline Component 2"){:class="img-landscape"}

This code is fairly self-explanatory. handleConnectivityChange is given a boolean argument for the connection status. Each time the connection changes, we set that boolean in state. If the status is false, then we return the Offline Notice Banner, else we just return null.

![offline component 3]({{ site.url }}/codeks/assets/images/offline_component3.png "Offline Component 3"){:class="img-landscape"}

The final piece to the puzzle is the slightly tricky one and takes place in App.js. Here is a hint: it has to do with z-index. In my case, I am returning a Navigator that displays what screen I'm on and handles all routing. I would think that the OfflineNotice component should be placed 'above' this Navigator, because it appears at the top of the screen. However, the order determines the z-index of the elements, or how they overlap. If I were to flip the order, the OfflineNotice would still be rendered, but it would be hidden *underneath* the Navigator. 

[z-index reference](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index)