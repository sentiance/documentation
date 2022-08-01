# Android

## java.lang.RuntimeException: Exception while creating class X

```java
com.example.myapp E/Sentiance: Failed to initialize the Sentiance SDK
    java.lang.RuntimeException: Exception while creating class d
       ...
     Caused by: java.lang.reflect.InvocationTargetException
       ...
     Caused by: java.lang.NoClassDefFoundError: Failed resolution of: Lcom/google/android/gms/location/LocationServices;
```

**Problem:** This error is likely due to the app using a different version of the play-services-\* libraries than the Sentiance SDK.

**Solution:**  Exclude the play-services-location library used by Sentiance and include a newer version.

**Note:** Make sure to include the explicit play-services-location dependency in the app module to avoid potential problems with various versions of the Android gradle plugin, e.g. in a react-native project.

```java
implementation ('com.sentiance:sdk:xxx@aar') { // xxx being the current version of the SDK that is used
    transitive = true
    exclude group: 'com.google.android.gms', module: 'play-services-location'
}
implementation 'com.google.android.gms:play-services-location:16.0.0'
```

## Version conflict or mismatch error

{% hint style="danger" %}
All com.android.support libraries must use the exact same version specification...
{% endhint %}

**Problem:** Our SDK has a dependency on the Google Play location services library, which itself has dependencies on various other support libraries. When your application has a dependency on a different version of a play services, support, or location library, it may result in version conflict.

**Solution:** Exclude the conflicting library from our SDK and include a higher version separately.

```groovy
// In this example, 'com.android.support' has a conflict.

implementation ('com.sentiance:sdk:4.4.0@aar') {
	transitive = true
	exclude group: 'com.android.support', module: 'support-v4'
}
```

## Manifest merger failed: Attribute fullBackupContent

```
Manifest merger failed : Attribute application@fullBackupContent value=(@xml/my_backup_rules.xml) from AndroidManifest.xml:10:9-45
        is also present at [com.sentiance:sdk:4.10.0] AndroidManifest.xml:26:9-54 value=(@xml/backup_rules).
        Suggestion: add 'tools:replace="android:fullBackupContent"' to <application> element at AndroidManifest.xml:5:5-21:19 to override.
```

**Problem:** If you have specified custom backup rules in your application's manifest using the `android:fullBackupContent` attribute, then you might run into an exception during the build. This is because our SDK sets its own rules in the library manifest, which causes the manifest merger to complain about the conflict.

**Solution:** Add the following attribute to your app's `<application>` tag so that the manifest merger picks your app's backup rules instead:

```markup
<manifest xmlns:tools="http://schemas.android.com/tools" ...>
   <application 
      ...
      tools:replace="android:fullBackupContent">
```

Then, add the following SDK backup rules to your backup rules XML file (location in the res/xml directory):

```markup
<full-backup-content>
    ...
    <exclude domain="sharedpref" path="sentiance.xml"/>
    <exclude domain="database" path="sentiance-payloads"/>
    <exclude domain="database" path="sentiance-payloads.db"/>
    <exclude domain="database" path="sentiance"/>
    <exclude domain="database" path="sentiance.db"/>
    <exclude domain="database" path="sentiance-timelines"/>
    <exclude domain="database" path="sentiance-timelines.db"/>
    <exclude domain="database" path="sentiance-tiles"/>
    <exclude domain="database" path="sentiance-tiles.db"/>
    <exclude domain="database" path="sentiance-zipped-tiles"/>
    <exclude domain="database" path="sentiance-zipped-tiles.db"/>
    <exclude domain="database" path="sentiance-segment"/>
    <exclude domain="database" path="sentiance-segment.db"/>
</full-backup-content>
```

## Build failure or runtime exception when using AndroidX

{% hint style="danger" %}
**Build-time Exception**

Error while merging dex archives

Error: Program type already present: android.support.v4.app.INotificationSideChannel
{% endhint %}

{% hint style="danger" %}
**Runtime Exception**

NoClassDefFoundError: Failed resolution of: Landroid/support/v4/util/ArrayMap
{% endhint %}

**Problem:** When using AndroidX support libraries or a Google Play Services library which depends on AndroidX libraries, you might run into the above build-time or runtime exception.

**Solution:** The Sentiance SDK (before v6.x) depends on several `com.android.support` libraries. Therefore, you must enable Jetifier to migrate the SDK's support dependencies to the AndroidX equivalent ones. To do so, add the following lines to your project's gradle.properties file:

{% code title="gradle.properties" %}
```groovy
android.useAndroidX=true
android.enableJetifier=true
```
{% endcode %}

## Permission revoked when adding the Sentiance SDK

**Problem:** When adding the Sentiance SDK (before v6.x) to an app, the `READ_PHONE_STATE` permission gets revoked or can no longer be acquired at runtime.

**Solution:** The Sentiance SDK adds this permission to the app and specifies the `maxSdkVersion` attribute. To remove this attribute, add the `tools:remove="android:maxSdkVersion"` attribute to the permission in your app's manifest:

{% code title="AndroidManifest.xml" %}
```markup
<uses-permission android:name="android.permission.READ_PHONE_STATE"
                 tools:remove="android:maxSdkVersion"/>
```
{% endcode %}

## Exclude native libraries for unsupported architectures

**Problem:** When adding the Sentiance SDK to your app, your final apk may include native libraries for architectures you do not intend to support, unnecessarily increasing the size of your app.

{% hint style="info" %}
This problem does not affect you if you are publishing your app as an Android App Bundle (aab). Google Play takes care of stripping unnecessary binaries from your final apk.
{% endhint %}

**Solution:** You can restrict the architectures that you want to support by adding `abiFilters` to your build config. Below is an example of how to restrict it to `armeabi-v7a` and `arm64-v8a` only, in your release builds.

{% code title="app/build.gradle" %}
```groovy
android {

  buildTypes {
    release {
       ndk {
         abiFilters = [ 'armeabi-v7a', 'arm64-v8a ' ]
       }
    }
  }
}
```
{% endcode %}

## Manifest merger failed: uses-sdk:minSdkVersion X cannot be smaller than version Y declared in library

**Problem:** Your app supports an Android version that is older than what the Sentiance SDK supports (Android 6). During compilation, you get an error saying the compiler failed to merge the manifest files.

**Solution:** You can use the **overrideLibrary** attribute to override the minSdkVersion defined in the conflicting Sentiance library, without changing the minimum supported Android version of your app. Here's an example on how to resolve the conflict with 3 different Sentiance libraries:

```markup
<manifest ...
    xmlns:tools="http://schemas.android.com/tools">
    
    <uses-sdk tools:overrideLibrary="com.sentiance.sdk, com.sentiance.sdk.crashdetection, ..."/>
```

When you initialize the SDK on an older Android version, initialization will gracefully fail with reason UNSUPPORTED\_OS\_VERSION.
