# React Native Background Geolocation Example

![Screenshot](/screenshot.png)

# Intro

This is an example app of [react-native-mauron85-background-geolocation](https://www.npmjs.com/package/react-native-mauron85-background-geolocation) component.

# Binary build

There is apk in [dist](/dist) folder.

# How to build

In cloned directory:

1. `npm install`

Also read [setup instructions](https://www.npmjs.com/package/react-native-mauron85-background-geolocation).

## Android

Check android lib versions:

 Google Play services >= 30
 Google Repository >= 28

Generate your SHA1 key to restrict usage to your app only (optional):

`keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android`

Go to Google API Console and select your project, or create one:

In Overview -> Google Maps API -> Google Maps Android API -> Check if it's enabled. Click button **Enable**!
Create a new key by clicking on Create credentials -> API Key -> Android Key, enter the name of the API key and your SHA1 key, generated before, and create it.

Add your Api key in  `android/app/src/main/AndroidManifest.xml`:

```xml
<application
  android:allowBackup="true"
  android:label="@string/app_name"
  android:icon="@mipmap/ic_launcher"
  android:theme="@style/AppTheme">
    <!-- You will only need to add this meta-data tag, but make sure it's a child of application -->
    <meta-data
      android:name="com.google.android.geo.API_KEY"
      android:value="{{Your Google maps API Key Here}}"/>
</application>
```

More info https://github.com/lelandrichardson/react-native-maps/blob/master/docs/installation.md

### Run in Simulator

`adb reverse tcp:8081 tcp:8081`

`react-native run-android` 

### Run on Device

```
$ cd android && ./gradlew installDebugAndroidTest
```

## iOS

in iOS Simulator:
Enable **Freeway Drive** in `Debug` ➜ `Location` menu.

### Run in Simulator

`react-native run-ios`


# Troubleshoot

## Android

Check `adb logcat` for errors. For example wrong API key:

```
E/Google Maps Android API(31792): Authorization failure.  Please see https://developers.google.com/maps/documentation/android-api/start for how to correctly set up the map.
E/Google Maps Android API(31792): In the Google Developer Console (https://console.developers.google.com)
E/Google Maps Android API(31792): Ensure that the "Google Maps Android API v2" is enabled.
E/Google Maps Android API(31792): Ensure that the following Android Key exists:
E/Google Maps Android API(31792): 	API Key: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA                                             
E/Google Maps Android API(31792): 	Android Application (<cert_fingerprint>;<package_name>): 00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00;com.rnbgexample
```
