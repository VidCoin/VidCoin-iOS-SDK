VidCoin-iOS-SDK
===============

## Download and install

[Download the latest release (SDK)](https://github.com/VidCoin/VidCoin-iOS-SDK/releases/latest)


## Preview
![VidCoin Mobile Overlay](https://d3rud9259azp35.cloudfront.net/preview/ios_player.png "VidCoin Mobile Overlay")

## Additional Informations

### Supported iOS versions
| SDK version  | iOS 6 | iOS 7 | iOS 8 | iOS 9 | iOS 10 | iOS 11| iOS 12
| :-------------: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: |:-------------: |
| 3.0.0 | - | - | - | x | x | x | x |
| 2.4.0 | - | - | - | x | x | x | x |
| 2.3.0 | - | - | - | x | x | x | x |
| 2.2.0 | - | - | - | x | x | x | x |
| 2.1.0 | - | - | - | x | x | x | x |
| 2.0.0 | - | - | - | x | x | x | x |
| 1.4.5 | - | x | x | x | x | x | |
| 1.4.5 | - | x | x | x | x | x | |
| 1.4.4 | - | x | x | x | x | x | |
| 1.4.3 | - | x | x | x | x | x | |
| 1.4.2 | - | x | x | x | x |  | |
| 1.4.1 | - | x | x | x | x |  | |
| 1.4.0 | - | x | x | x | x |  | |
| 1.3.5 | x | x | x | x |  |  | |
| 1.3.4 | x | x | x | x |  |  | |
| 1.3.3 | x | x | x | x |  |  | |
| 1.3.2 | x | x | x | x |  |  | |
| 1.3.1 | x | x | x | x |  |  | |
| 1.3.0 | x | x | x | x |  |  | |
| 1.2.4 | x | x | x |  |  |  | |
| 1.2.3 | x | x | x |  |  |  | |
| 1.2.2 | x | x | x |  |  |  | |
| 1.2.1 | x | x | x |  |  |  | |
| 1.2.0 | x | x | x |  |  |  | |
| 1.1.2 | x | x |  |  |  |  | |
| 1.1.1 | x | x |  |  |  |  | |
| 1.1.0 | x | x |  |  |  |  | |
| 1.0.0 | x | x |  |  |  |  | |

### Deprecations
Versions **1.2.0 and before** have been partly disabled. For the maximum compatibilty, make sure your app runs the latest version available.

## Changelog

### v3.0.0
*(Released on 09 April. 2019)*

VoodooAds SDK is a major version upgrade.
All classes are renamed or removed compared to the last SDK versions.

- Refactor SDK public interface
- New request Ad API
- New sync SDK API ( get SDK configuration , automatic app creation )
- New internal trackers API
- Secure the trackers request (JWT)
- Cache trackers to increase analytics sanity
- Update tracking keys
- New Log errors reporter
- Handle HTTP error code
- Request Timeout management
- Support Banner format
- Support Tablet/iPad assets
- Improved asset's cache
- Support Landscape Ads

### v2.4.0
*(Released on 08 April. 2019)*

- Add new placeholder to the attribution trackers
- Bug fixes 

### v2.3.0
*(Released on 28 Nov. 2018)*

- New creative supported: Playable ads
- Support Limited Ad Tracking
- Overall stabilization and improvements

### v2.2.0
*(Released on 6 Nov. 2018)*

- Improved SDK integration process
- Apps and placement codes are created automatically
- Overall stabilization and improvements

### v2.1.0
*(Released on 22 Oct. 2018)*

- New format
- Overall stabilization and improvements

### v2.0.0
*(Released on 09 Oct. 2018)*

- iOS 12
- New workflow
- Zone ID

### v1.4.5
*(Released on 02 Jan. 2018)*

- Users are now presented with the in-app version of the AppStore page of a product advertised if they interact with the ad (requires `StoreKit.framework` as optional linked library)

### v1.4.4
*(Released on 26 Oct. 2017)*

- Improved callback management
- Overall stabilization and improvements

### v1.4.3
*(Released on 22 Sep. 2017)*

- iOS 11 & iPhone X support

### v1.4.2
*(Released on 23 Mar. 2017)*

- Overall stabilization and improvements

### v1.4.1
*(Released on 23 Nov. 2016)*

- Improved player performance
- Overall stabilization and improvements

### v1.4.0
*(Released on 25 Oct. 2016)*

- New improved UI for better user experience, with vertical ads support, lighter memory impact and many other improvements
- Overall stabilization and improvements

### v1.3.5
*(Released on 28 Jul. 2016)*

- Improved player performance
- Better ad tracking, for better ad serving
- Overall stabilization and improvements

### v1.3.4
*(Released on 1 Jun. 2016)*

- Overall stabilization and improvements

### v1.3.3
*(Released on 11 Feb. 2016)*

- Overall stabilization and improvements

### v1.3.2
*(Released on 10 Nov. 2015)*

- Improved transitions
- Overall stabilization and improvements


### v1.3.1
*(Released on 24 Sep. 2015)*

- Support for iOS 9
- Improvements for Xcode 7 builds and AppStore submissions
- Overall stabilization  

### v1.3.0
*(Released on 17 Sep. 2015)*

- Support for iOS 9
- Overall stabilization and improvements  

### v1.2.4
*(Released on 25 Aug. 2015)*

- Overall stabilization and improvements

### v1.2.3
*(Released on 27 Jul. 2015)*

- Improved video quality handling fo better user experience
- Reduced memory footprint and improved low memory handling

### v1.2.2
*(Released on 12 May. 2015)*

- More efficient video caching
- Speed improvements
- Reduced memory footprint
- Better tracking for better ad serving

**Important:**

If you're **updating from a SDK version prior to 1.2.0**, make sure to include **CoreMedia.framework** in the target's linked libraries.

### v1.2.1
*(Released on 24 Feb. 2015)*

- Updated for projects created with Xcode 6
- Visual improvements for the landing screen
- Better tracking, for better ad serving

**Important:**

If you're **updating from a SDK version prior to 1.2.0**, make sure to include **CoreMedia.framework** in the target's linked libraries.

### v1.2.0
*(Released on 14 Nov. 2014)*

- Xcode 6, iOS 8 and iPhone 6 / 6 Plus support
- New player and landing UI
- New share button on the landing
- Links open in a WebView to keep the user in the app
- Reduced memory footprint
- Improved player performance
- Choose to enable or disable the animations when calling VidCoin's player
- Network activity indicator is now only visible if logging is enabled
- Improved network handling

**Important:**

If you're **updating from a previous SDK version**, make sure to include **CoreMedia.framework** in the target's linked libraries.

### v1.1.2
*(Released on 08 Sep. 2014)*

- Optimized player for devices running iOS 6

### v1.1.1
*(Released on 31 Jul. 2014)*

- Better connectivity handling
- Improved localization
- More efficient video caching
- Optimized global memory footprint

### v1.1.0
*(Released on 04 Jul. 2014)*

- Whole new UI for an improved user experience
- Fixed video player when Airplay is active

### v1.0.0
*(Released on 06 Jun. 2014)*

- First public release

### v1.0.0-beta
*(Released on 26 May. 2014)*

- First beta release
