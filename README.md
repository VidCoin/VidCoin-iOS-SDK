VidCoin-iOS-SDK
===============
##Download and install

[Download the latest release (SDK + Documentation)](https://github.com/VidCoin/VidCoin-iOS-SDK/releases/download/v1.2.1/VidCoin-iOS-SDK.zip)

To update, simply remove the old versions of the .bundle and .framework from the project, and add the new bundle and framework files.

**Updating to v1.2.0 and later**

If you're updating from a SDK version prior to v1.2.0, make sure to add **CoreMedia.framework** to the target's linked libraries.

##Preview
![VidCoin Mobile Overlay](https://googledrive.com/host/0B6TMHf2nEKbFdFQxTjJJaGZUWm8 "VidCoin Mobile Overlay")

##Supported iOS versions

| SDK version  | iOS 6 | iOS 7 | iOS 8 |
| :-------------: | :-------------: | :-------------: | :-------------: |
| 1.2.1 *(latest)* | x | x | x |
| 1.2.0 | x | x | x |
| 1.1.2 | x | x |  |
| 1.1.1 | x | x |  |
| 1.1.0 | x | x |  |
| 1.0.0 | x | x |  |

##Changelog

###v1.2.0
*(Released on 24 Feb. 2015)*
- Updated for projects created with Xcode 6
- Visual improvements for the landing screen
- Better tracking, for better ad serving

**Important:**

If you're **updating from a SDK version prior to 1.2.0**, make sure to include **CoreMedia.framework** in the target's linked libraries.

###v1.2.0
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

###v1.1.2
*(Released on 08 Sep. 2014)*
- Optimized player for devices running iOS 6

###v1.1.1
*(Released on 31 Jul. 2014)*

- Better connectivity handling
- Improved localization
- More efficient video caching
- Optimized global memory footprint

###v1.1.0
*(Released on 04 Jul. 2014)*

- Whole new UI for an improved user experience
- Fixed video player when Airplay is active

###v1.0.0
*(Released on 06 Jun. 2014)*

- First public release

###v1.0.0-beta
*(Released on 26 May. 2014)*

- First beta release
