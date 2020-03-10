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

```text
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

Then, add the following SDK backup rules to your backup rules XML file \(location in the res/xml directory\):

```markup
<exclude domain="sharedpref" path="sentiance.xml"/>
<exclude domain="database" path="sentiance-payloads"/>
<exclude domain="database" path="sentiance-payloads.db"/>
<exclude domain="database" path="sentiance"/>
<exclude domain="database" path="sentiance.db"/>
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

**Solution:** The Sentiance SDK depends on several `com.android.support` libraries. Therefore, you must enable Jetifier to migrate the SDK's support dependencies to the AndroidX equivalent ones. To do so, add the following lines to your project's gradle.properties file:

{% code title="gradle.properties" %}
```groovy
android.useAndroidX=true
android.enableJetifier=true
```
{% endcode %}

## Permission revoked when adding the Sentiance SDK

**Problem:** When adding the Sentiance SDK to an app, the `WRITE_EXTERNAL_STORAGE` or `READ_PHONE_STATE` permission gets revoked or can no longer be acquired at runtime.

**Solution:** The Sentiance SDK adds these permissions to the app and specifies the `maxSdkVersion` attribute. To remove this attribute, add the `tools:remove="android:maxSdkVersion"` attribute to the permission in your app's manifest:

{% code title="AndroidManifest.xml" %}
```markup
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"
                 tools:remove="android:maxSdkVersion"/>
```
{% endcode %}

