# Vidcoin iOS - QuickStart Guide

## Overview						
Vidcoin SDK enables you to broadcast videos in your apps in order to give users access to restricted content or to obtain virtual currency for free.
This document and the archive contain all the information you need in order to integrate our solution and start broadcasting videos. You’ll find an integration example inside unitypackage. You can also contact us directly at publishers@vidcoin.com.

## Account Settings						
An approved and valid publisher account is necessary in order to use the SDK. If you do not have an account, please sign up directly on https://manager.vidcoin.com.
This also grants you access to statistics and detailed reports in our Publishers Back-Office.

### App Creation
You can access App Creation in the “App” menu of your publisher area. The creation of an app generates an “App ID” which will be mandatory in order to use the Vidcoin SDK. 

### Placement Creation			
A Placement represents the zone in your app where the videos will be available for broadcasting. There are different settings available for any app Placement:
- Minimum Payout: corresponds to the minimum revenue that a video must generate in order to be offered to a user. We recommend you to set "No minimum payout" to get more videos. We will automatically give you the highest pricing.
- Test Mode: when “Test Mode” is activated, the Placement will always display videos for users, without any restrictions. Test mode placements do not generate any revenue.

#### Access Sponsoring		
An Access Sponsoring placement allows users to access a specific part of the app by watching a video. The user does not necessarily need to be logged in to your app in order to access videos. The process does not need a server-side callback and is only executed on the client-side.

#### Item Sponsoring					
An Item Sponsoring placement rewards the player with virtual currency. The user must therefore be logged in and have a specific and unique identifier. The validation of the transaction uses a secured server callback to credit the user.
The following settings can be defined for all Item Sponsoring placements:			
- Callback URL: URL that will be used to validate the transaction (please see “Set up of a server callback”)			
- Virtual Currency Name: name of your virtual currency			
- You can choose 2 types of rewards for the user:
    - Exchange rate: rate defining how much 1€ equals of your virtual currency. Please note that we recommend that you use a low exchange rate such that 1€ = 1000 of your virtual currency. This will prevent any problems of crediting users with small amounts of virtual currency.
    - Fixed reward: amount of virtual currency the user will be rewarded for 1 view.

## Setting up the framework in your app

### Step 1: Getting the framework
Download and open the zip file from Github : https://github.com/VidCoin/VidCoin-iOS-SDK

### Step 2: Adding the framework to the project
Navigate to *VidCoin-iOS-SDK-version/Framework/* and add the .framework and the .bundle to the project:

![Image1](http://www.googledrive.com/host/0Bwu-tkR-jL-5TERzMXJ3SUkwakk)

*Note: both are necessary for presenting videos. If you do not add the .bundle file, you may be able to build but your app will crash when trying to show an ad.*

#### Updating the framework
To update the framework in your project, simply remove the old versions of the .bundle and .framework from the project, and add the new bundle and framework files.

### Step 3: Linking required frameworks
Select your target in the project settings, then go to “Build Phases”.
Expand Link Binary With Library, and add the following frameworks to the list :
- MediaPlayer.framework
- AVFoundation.framework
- AdSupport.framework
- CoreTelephony.framework
- SystemConfiguration.framework
- CoreMedia.framework

### Recommended step: Disabling iOS 9’s ATS
With iOS 9, Apple introduced a new feature called App Transport Security (ATS), which is a default setting that prevents your app from making non-secure connections. With ATS, any app built against iOS 9 using XCode 7 will only allow HTTPS connections.
Starting with v1.3.0, Vidcoin’s iOS SDK is fully compatible with iOS 9, which mean you should not worry about any ad revenue drop from our service. Nevertheless, some of our partners will not be able to make the transition that easily. To ensure you get the best service possible from our product, we recommend you disable ATS in your project.

Apple provided a way to do so easily. Simply add the following lines to your project’s .plist file:

```xml
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
</dict>
```
Do note that this change only impacts apps built for iOS 9, and apps built for older iOS versions will not be affected.

### Step 4: Enabling device rotation and status bar management
*Note: although this step is optional, it greatly improves the user experience.*

#### Device rotation:
Your app may run in portrait or landscape only. Vidcoin’s framework was built for the best user experience possible. To do so, we handle device rotation, but we need your app to forward us device rotation information.

To do so, go to the app configuration, select your target, and in the Deployment Info section, make sure at least Portrait, Landscape Left and Landscape Right are ticked. Then, if you want to keep for example a portrait-only orientation for your app, you should implement the following methods in your UIViewControllers:

```objective-c
-(UIInterfaceOrientationMask)supportedInterfaceOrientations {
    return UIInterfaceOrientationMaskPortrait;
}

-(BOOL)shouldAutorotate {
    return NO;
}
```

#### Status bar management:
Again, we want to make sure we give your users the best experience possible. Our player looks great with the status bar hidden, but you may have chosen to keep it visible in your app. What you should do next is open your App-Info.plist file, and add the key View controller-based status bar appearance and set its value to YES:

![Image2](http://www.googledrive.com/host/0Bwu-tkR-jL-5X29Db202SVJna00)

That way, we will be able to hide the status bar when we present our player, and put it back if necessary before returning to your app.

### Step 5: Start the framework
It’s now time to start the framework. Start by importing the main header file VidCoin.h in your AppDelegate:

```objective-c
#import <VidCoin/VidCoin.h>
```

Next, the recommended way to start Vidcoin is place a call to `+startWithGameId` as soon as possible. For example, you can do as follows:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    
	// Your custom initialization
	
    [VidCoin startWithGameId:@"your-app-id"];
    
    return YES;
}
```

Vidcoin uses a custom protocol, named VidCoinDelegate to dialog with your app. To assign an object to be Vidcoin’s delegate, you can process in two different ways:

- Start the framework as above, and assign the delegate later. This lets you use an object not yet available as the delegate.

```objective-c
[VidCoin startWithGameId:@"your-app-id"];
[...]
[VidCoin setDelegate:self];
```

- Start the framework and assign the delegate at the same time:

```objective-c
[VidCoin startWithGameId:@"your-app-id" delegate:self];
```

In any case, make sure the object you assign as the delegate conforms to our `VidCoinDelegate` protocol in the header file of its class. For example, if you assign your `AppDelegate` as the framework’s delegate, here is what your `AppDelegate.h` file should look like:

```objective-c
@interface AppDelegate : UIResponder <UIApplicationDelegate, VidCoinDelegate>
```

Assigning a delegate to your Vidcoin instance is a simple way to get notified when there is a status update, or when a video is presented / dismissed. For more information on `VidCoinDelegate` and the available methods, please refer to the associated section of this document.

### Optional step: Enable logging
In addition to implementing the `VidCoinDelegate` protocol, you can enable extra logging by making a call to the following method:

```objective-c
[VidCoin setLoggingEnabled: YES];
```

**Important note : this will also make the device’s network activity indicator visible when a network connection is active.**

*Advice: set the verbose tag to false before releasing your app.*

### Step 6: Update the user information
It’s really important you send us as much information on your user as you can, so we can target the ads appropriately. The easy way to do this is the following:

```objective-c
[VidCoin updateUserDictionary: @{ kVCUserGameID     : @"UserName",
                                kVCUserBirthYear 	: @"1980",
                                kVCUserGenderKey	: kVCUserGenderMale }];
```

You can pass any of these 3 key-value pairs, all keys and values being String objects.


| Key  | Values | Description |
| :-------------: | :-------------: | :-------------: |
| kVCUserGameID | Any NSString object | This is the string you use to identify the user in your app. This will be used in case you implement a server callback. |
| kVCUserBirthYear | An NSString object like @”1980” or an NSNumber object like @1980 | The birth year of the user, in a NSString or NSNumber format. |
| kVCUserGenderKey | kVCUserGenderMale or kVCUserGenderFemale | A string to specify the user’s gender. Any other value will be ignored. |

### Step 7: Check if a video is available
You may want to know if a video is available for a given placement. For example, you shouldn’t display a button inviting the user to watch a video if there is none in cache. Calling the class method +videoIsAvailableForPlacement: is the way to go:

```objective-c
[VidCoin videoIsAvailableForPlacement:@"your-placement-code"];
```

This method will return a `BOOL`, equal to `YES` if a video is ready to be played for the placement you passed as parameter, and `NO` otherwise.

### Step 8: Play a video
You can present a video to the user by calling the following method:

```objective-c
[VidCoin playAdFromViewController:self forPlacement:@"your-placement-code" animated:YES];
```

`self` is a pointer to your app’s view controller in charge of presenting the video player. You can also choose whether you want the controller appearance to be animated or not. If a video is ready to be played for this placement, the player will appear and the video will start.

### Step 9: Using `VidCoinDelegate` (optional)
If you want to be notified of multiple things happening in the framework, you can set an object to be Vidcoin’s delegate (as seen in step 5). Your object can then implement some (or all) of  the following methods :

###### `-(void)vidcoinCampaignsUpdate;`

This method will be called regularly, whenever a change happens in the framework: if the list of available videos changes, if a new video is available for display, etc.

###### `-(void)vidcoinViewWillAppear;`

This method will be called just before the video player appears on screen. This is for example the perfect time to pause the audio of your app.

###### `-(void)vidcoinViewDidDisappearWithViewInformation:(NSDictionary*)viewInfo;`

This method is called right after the video player left the screen. You may now resume the app audio if you paused it in the previous delegate method. You can access basic information about the video that was just watched in the viewInfo dictionary passed as parameter. Here are the values you can access:

- `VCStatusCode statusCode = [[viewInfo objectForKey:@"statusCode"] integerValue];`
- `NSNumber *reward = [viewInfo objectForKey:@"reward"];`

The `statusCode` var can be compared to the integers `VCStatusCodeSuccess` (the video was watched correctly), `VCStatusCodeCancel` (the user canceled the video), and `VCStatusCodeError` (something went wrong, and the user couldn’t watch the video).

The `reward` informs you on the amount the user will be rewarded when the view is validated on the server-side.

###### `-(void)vidcoinDidValidateView:(NSDictionary *)viewInfo;`

This method is called when the server answers after the framework tried to validate the view. You can access the same information as the previous method, but in this case, the `status` value is either `VCStatusCodeSuccess` or `VCStatusCodeError`, depending on whether the server did validate the view or not. The value associated to the `reward` key now contains the amount of your in-app currency that was actually credited to the user on the server side.

*Note: that this method will always be called after the previous delegate method `vidcoinViewDidDisappearWithViewInformation:`.*

### Step 10: Submitting to the AppStore
When you submit your app for Apple’s approval, you will be asked if your app uses the Advertising Identifier. Vidcoin’s framework does use this identifier, in order to serve advertisements within your app:

![Image3](http://www.googledrive.com/host/0Bwu-tkR-jL-5MUZKZ1VvN2c1dlE)

## Advice for integration
The integration of the Vidcoin solution must not deteriorate the user experience.
Because of certain parameters and restrictions (country, number of videos already viewed...) there may not always be available videos.

A non-blocking integration consists in offering Vidcoin to the user as an alternate solution to the classical running of the app.

Here is an example :
- The user is presented a given view of the app
- A button “Please sign-in to access your content” is presented
- Make the view subscribe to Vidcoin’s events, and implement the method triggered by the event called `vidcoinCampaignsUpdate`
- In this method, if a call to Vidcoin’s method `videoIsAvailableForPlacement` returns true for the given placement code, a second button can be presented: “Watch a video to access your content”
- If the call returns false, the second button should not be made visible.

This type of integration avoids proposing a user to watch a video if none is available, and does not damage the user experience. You should not expect videos to be always available.

The sample app gives a good example of a recommended integration.

## Server-side callback (optional)
If you want to use a server-side callback to credit your users (Item Sponsoring placement), you can download our PHP SDK: https://github.com/VidCoin/VidCoin-PHP-SDK
