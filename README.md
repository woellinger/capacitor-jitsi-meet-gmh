# Jitsi Meet Capacitor Plugin for Ionic Apps

This Ionic Capacitor plugin is created to make video calls through the free, open-sourced Jitsi video platform (https://meet.jit.si) on iOS and Android.

## Compatibility to Capacitor Versions

<table>
  <thead>
    <tr>
      <th>Capacitor</th>
      <th>capacitor-jitsi-meet</th>
      <th>supported</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        v3
      </td>
      <td>
        >= 2.0.0
      </td>
      <td>
        current
      </td>
    </tr>
    <tr>
      <td>
        v2
      </td>
      <td>
        <= 1.5.14
      </td>
      <td>
        until Sept 30, 2021
      </td>
    </tr>
    <tr>
      <td>
        v1
      </td>
      <td>
        <= 1.3.6
      </td>
      <td>
        until June 30, 2020
      </td>
    </tr>
  </tbody>
</table>

Follow the [official Capacitor doc to upgrade to Capacitor 3](https://capacitorjs.com/docs/updating/3-0).

## iOS Compatible Versions

See the plugin [changelog](https://github.com/calvinckho/capacitor-jitsi-meet/blob/master/CHANGELOG.md) for plugin versions that are compatible to your local Xcode version.

## Embedding in web applications

This plugin does not currently support web implementation. We recommend using the Jitsi iFrame API (https://jitsi.github.io/handbook/docs/dev-guide/dev-guide-iframe) for full web implementation.

## Usage

1. npm install capacitor-jitsi-meet

2. use it as a [Capacitor Plugin](https://capacitorjs.com/docs/getting-started#adding-capacitor-to-your-app)

```javascript
// On Capacitor 3
import { Jitsi } from 'capacitor-jitsi-meet';

// On Capacitor 1 and 2
import { Plugins } from '@capacitor/core';
import 'capacitor-jitsi-meet';

const { Jitsi } = Plugins;
```

```javascript
const result = await Jitsi.joinConference({
    // required parameters
    roomName: 'room1', // room identifier for the conference
    url: 'https://meet.jit.si', // endpoint of the Jitsi Meet video bridge
    
    // optional parameters
    subject: string, // name of the video room
    displayName: string, // user's display name
    email: string, // user's email
    avatarURL: string, // user's avatar url
    startWithAudioMuted: true, // start with audio muted, default: false
    startWithVideoMuted: false, // start with video muted, default: false
    chatEnabled: false, // enable Chat feature, default: true
    inviteEnabled: false, // enable Invitation feature, default: true
    
    // advanced settings, optional
    token: string, // jwt authentication token
    featureFlags: { 'call-integration.enabled': true, 'live-streaming.enabled': false, 'android.screensharing.enabled': false }, // see list of featureFlags in the official Jitsi Meet SDK documentation
    configOverrides: { 'p2p.enabled': false }, // see list of config overrides in the official Jitsi Meet SDK documentation

   // advanced settings to be deprecated in 3.0. Use featureFlags and configOverrides instead
    callIntegrationEnabled: true, // enable call integration (CallKit on iOS, ConnectionService on Android), default: true
    liveStreamingEnabled: false, // enable live streaming feature, default: auto-detected
    recordingEnabled: false, // (experimental) enable recording feature, default: false, requires adding Dropbox APP_KEY to Info.plist and AndroidManifest.xml
    screenSharingEnabled: false, // enable screen sharing feature, default: false, iOS requires manually adding the Broadcast Upload Extension
});

window.addEventListener('onConferenceJoined', () => {
    // do things here
});
window.addEventListener('onConferenceLeft', () => {
    // do things here
});

```

3. Build the project

```
$ npm run build
```

4. Follow the deployment instructions for [Android](android/README.md) and [iOS](ios/README.md).

## Official Jitsi-Meet SDK Documentation

This plugin uses the Jitsi Meet SDK. See the [Jitsi Meet SDK documentation](https://jitsi.github.io/handbook/docs/dev-guide/dev-guide-mobile), and the lists of [feature flags](https://jitsi.github.io/handbook/docs/dev-guide/mobile-feature-flags) and [config overrides](https://github.com/jitsi/jitsi-meet/blob/e2731ce73e9221408d0f4d985affc91eb11fc214/config.js).

## Sample React App for Android

You can see a [React Demo App](https://github.com/calvinckho/react-capacitor-jitsi-meet-sample) which runs the Jitsi meeting on the Android device

## Feature Requests and Jitsi SDK Customizations

I appreciate those who use this plugin in their production apps and are funding this project as sponsors. Your sponsorship enables me to continue to maintain and roll out releases in a timely manner. Consider joining as a sponsor to get first-class support and consultation. For feature requests, create an issue with a label 'feature request'. I also offer paid consultation service to those needing to modify the Jitsi UI interface. To submit a request, create an issue and add the label 'sdk customization'.

## Acknowledgements

This plugin enables web and mobile apps to implement video conferencing feature for free. The Jitsi Meet mobile SDKs are actively maintained by Jitsi. Video bridges for multi-user video conferencing is powered by [Jitsi Meet](https://meet.jit.si), or you can run [your own video bridge](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-start).
