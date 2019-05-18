---
layout: post
title:  "How to Add Credit Card Scanner in React Native"
subtitle: "Using react-native-awesome-card-io to scan credit cards"
date:   2019-05-14 10:40:45 -0500
categories: [React Native]
---

# Install react-native-awesome-card-io NPM package

[react-native-awesome-card-io](https://github.com/Kerumen/react-native-awesome-card-io)

(1) npm install react-native-awesome-card-io --save

(2) react-native link react-native-awesome-card-io

# Build and Run Project

When I tried running the app at this point in XCode, I got a build error that looked like something like this - `build input file cannot be found ygfloatoptional cpp`.
Here is how I solved the issue.

(3) In XCode, right-click the Libraries folder

![XCode Libraries]({{ site.url }}/assets/images/scancard_xcode_rclick.png "Libraries"){:class="img-portrait"}


(4) Select `Add Files to APP_NAME`

(5) Select node_modules -> react-native-awesome-card-io -> ios -> RNCardIO.xcodeproj

(6) Target your project, and select Build Phases

![XCode Build Phases]({{ site.url }}/assets/images/scancard_xcode1.png "Build Phases"){:class="img-landscape"}

(7) Click the `+` at the bottom of the Link Binary with Libraries list

(8) Select libRNCardIO.a and click `Add`

(9) Restart your metro bundler and Build and Run your project

(10) $$$

# Implementing the CardIOModule

This part is self-explanatory from the [react-native-awesome-card-io docs](https://github.com/Kerumen/react-native-awesome-card-io). Here is the screenshot they provide of the CardIOModule that is supported by both iOS and Android.

![CardIO Module]({{ site.url }}/assets/images/scancard_cardio_module.png "CardIO Module"){:class="img-landscape"}




