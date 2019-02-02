---
layout: post
title:  "How to Access iOS NSUserDefaults with React Native"
date:   2019-02-01 20:40:45 -0500
categories: [React Native, iOS]
---

# Native Modules

Let's say you're re-writing your iOS application in React Native and pushing the update live in a few days. In order to keep users logged in, each codebase checks for a session stored in their individual local storage system. iOS uses NSUserDefaults and React Native uses AsyncStorage. However, when a user downloads the update, nothing is going to be stored in AsyncStorage. Thus, they will be forced to log back in - not an ideal user experience.

Fortunately, React Native has a built-in way to communicate with iOS/Android native code. I will start with iOS. Though intimidating at first, it is a fairly simple process. Here is what we will need:

- A bridge from iOS to connect to NSUserDefaults
- A way to access that bridge in React Native

Read the [Native Module Docs](https://facebook.github.io/react-native/docs/native-modules-ios) to skip this paragraph. In my example, my header file will be named UserToken, and it will import and extend the RCTBridgeModule to expose the class we need. 

    // UserToken.h
    #import <React/RCTBridgeModule.h>

    @interface UserToken : NSObject <RCTBridgeModule>
    
    - (void) getToken;
    
    @end

My implementation file will expose the class using `RCT_EXPORT_MODULE()` and the method I will be referencing using `RCT_REMAP_METHOD()`. This method will take the string supplied within React Native, and return a promise that will resolve with the value associated with that key from NSUserDefaults. `RCT_REMAP_METHOD()` will take four arguments:

- the name of the method
- the parameter supplied to that method, in our case the name of the token as stored in NSUserDefaults
- the resolver
- and the rejecter of the promise.

The method takes a string as a parameter, in case there are other tokens stored in iOS that the React Native app needs.

    // UserToken.m
    #import "UserToken.h"

    @implementation UserTokens

        RCT_EXPORT_MODULE();

        RCT_REMAP_METHOD(getToken,
                        tokenRequest: (NSString *)tokenRequest
                        resolver: (RCTPromiseResolveBlock)resolve
                        rejecter: (RCTPromiseRejectBlock)reject)
        {
        
            if (tokenRequest) {
                NSString *tokenResponse = [[NSUserDefaults standardUserDefaults] objectForKey:tokenRequest];

                resolve(tokenResponse);
            } else {
                NSError *error = @"error";
                reject(@"no_events", @"There were no events", error);
            }
        }

    @end

Now that the iOS code is exposed using the RCtBridgeModule, we can access it in the React Native codebase. It is as simple as importing the module.

    import { NativeModules } from 'react-native'
    const iosTokens = NativeModules.UserToken;

    function appUpdateSession() {
        if ( Platform.OS === 'ios' ) {
            return iosTokens.getToken('session_token').then((sessionToken) => {
                console.log(sessionToken)
            }
        }
    }

If your user is logged in on iOS, and downloads the app update to React Native, this code will log their session token that was stored in NSUserDefaults. You can use this value to prevent them from being logged out!








