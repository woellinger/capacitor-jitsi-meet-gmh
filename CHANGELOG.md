# Capacitor Plugin Changelog

Each version of the capacitor plugin uses a specific Jitsi SDK version. In iOS deployment, the SDK version is important because later SDKs compiled using the latest Xcode would not work if your local Xcode is older. So for iOS deployment, make sure you check your Xcode version and install the corresponding plugin version.  

See Jitsi-meet SDK [changelog](https://github.com/jitsi/jitsi-meet-release-notes/blob/master/CHANGELOG-MOBILE-SDKS.md)

# 2.2.1 (2022-03-11)

- bug fix: onConferenceJoined and onConferenceLeft not firing
- bug fix: iOS leaveConference() not working

# 2.2.0 (2022-03-04)

## Breaking Changes

The newly introduced featureFlags param provides a lot of flexibility to the developers, as the developers can now directly control ALL featureFlags settings supported by the SDKs, and no longer need to map the plugin params to the SDK featureFlags params, as we have done before.

- with this increased flexibility, the following plugin params will be deprecated in our 3.0 version. Their default values will be reset to following the SDK default values in this current plugin release.
  - callIntegrationEnabled (plugin default true -> SDK default true)
  - liveStreamingEnabled (plugin default false -> 4.1.0 SDK default auto-detected)
  - recordingEnabled (plugin default false -> 4.1.0 Android SDK true, 4.1.0 iOS SDK false)
  - screenSharingEnabled (plugin default false -> 4.1.0 Android SDK true, 4.1.0 iOS SDK false)

Going forward, for a stable production build, my recommendation is to add the following featureFlags params in your syntax:
```
featureFlags: {
'recording.enabled': false, // disable as it requires Dropbox integration
'live-streaming.enabled': false, // 'Sign in with Google' button not yet functional
'android.screensharing.enabled': false // experimental feature, not fully production ready
},
```
- adds the subject, featureFlags, and configOverrides params

# 2.1.3 (2022-02-09)

## Breaking Changes
- adds the following optional parameters with their default values. Those defaulted to false must be manually set to true in order to enable them.
  - recordEnabled (default: false)
  - liveStreamingEnabled (default: auto-detected)
  - screenSharingEnabled (android only, default: false)

- fixes liveStreamingEnabled bug in 2.1.2

## iOS

- uses Jitsi SDK 4.1.0.
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-4.1.0)

## Android

- uses Jitsi SDK 4.1.0.
- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-4.1.0)

# 2.1.1 (2021-12-15)

## Android
- Capacitor 3 requires each Capacitor plugin to load settings from its own AndroidManifest.xml. This version provides correct settings in the manifest file which allows the Jitsi call to run in the background even if the user minimizes the app.

# 2.1.0 (2021-12-10)

## Breaking Changes
- the 4.0.0 mobile sdk introduces breakout rooms.
- Support for iOS 11 has been dropped.

## iOS

- uses Jitsi SDK 4.0.0.
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-4.0.0)

## Android

- uses Jitsi SDK 4.0.0.
- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-4.0.0)

# 2.0.0 (2021-10-14)

## Breaking Changes
- upgrades plugin for Capacitor 3. If you are currently using Capacitor 2, you need to upgrade your project to Capacitor 3 first before you can use this plugin.

## iOS

- uses Jitsi SDK 3.10.4
- built with Xcode 13.0
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.10.4)

## Android

- uses Jitsi SDK 3.10.2
- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.10.2)

# 1.5.15 (2021-09-13)

## iOS

- uses Jitsi SDK 3.8.1.
- built with Xcode 12.5
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.8.1)

## Android

- uses Jitsi SDK 3.8.0.
- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.8.0)

# 1.5.14 (2021-07-06)

- uses Jitsi SDK 3.6.0.

- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.6.0)
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.6.0)

## iOS

- built with Xcode 12.5

# 1.5.13 (2021-05-12)

- uses Jitsi SDK 3.5.0.

- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.5.0)
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.5.0)

## iOS

- built with Xcode 12.5

# 1.5.12 (2021-04-20)

## Android

- uses Jitsi SDK 3.4.0.

- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.4.0)

## iOS

- uses Jitsi SDK 3.4.1.
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.4.1)
- built with Xcode 12.4

# 1.5.10 (2021-04-14)

- uses Jitsi SDK 3.3.0.

- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.3.0)
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.3.0)

## iOS

- built with Xcode 12.4

# 1.5.9 (2021-03-16)

- uses Jitsi SDK 3.2.0.

- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.2.0)
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.2.0)

## Android

- adds leaveConference() method
- supports callIntegrationEnabled property in JoinConference()
- uses the new Listening for broadcasted events mechanism

## iOS

- adds leaveConference() method
- supports callIntegrationEnabled property in JoinConference()
- built with Xcode 12.4

# 1.5.8 (2021-02-08)

- uses Jitsi SDK 3.1.0.

- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-3.1.0)
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-3.1.0)

## iOS

- built with Xcode 12.2

# 1.5.7 (2021-01-17)

- add userInfo (displayName, email, avatarURL) parameters in iOS

# 1.5.6 (2021-01-08)

- add userInfo (displayName, email, avatarURL) parameters in Android

# 1.5.5 (2020-11-19)

- uses Jitsi SDK 2.11.0.

- [Android](https://github.com/jitsi/jitsi-meet/releases/tag/android-sdk-2.11.0)
- [iOS](https://github.com/jitsi/jitsi-meet/releases/tag/ios-sdk-2.11.0)

## iOS

- built with Xcode 12.2

# 1.5.4 (2020-09-18)

- uses Jitsi SDK 2.10.2

## iOS

- built with Xcode 12.0

# 1.4.3 (2020-09-15)

- uses Jitsi SDK 2.10.0

## iOS

- built with Xcode 11.4.1

# 1.3.13 (2020-03-25)

- uses Jitsi SDK 2.7.0

## iOS

- built with Xcode 11.3.1

