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

**Solution:** You can use the **overrideLibrary** attribute to override the minSdkVersion defined in the conflicting Sentiance library, without changing the minimum supported Android version of your app. Here's an example on how to resolve the conflict with 2 different Sentiance libraries:

```markup
<manifest ...
    xmlns:tools="http://schemas.android.com/tools">
    
    <uses-sdk tools:overrideLibrary="com.sentiance.sdk, com.sentiance.sdk.crashdetection"/>
```

When you initialize the SDK on an older Android version, initialization will gracefully fail with reason UNSUPPORTED\_OS\_VERSION.

## Exceptions Related to Foregrounding an SDK Service&#x20;

**Problem:** You encounter an exception related to the SDK foreground service, where Android terminates the app due to the service not being foregrounded on time. The crash log includes a message similar to the following:

```
Fatal Exception: android.app.RemoteServiceException: Context.startForegroundService() 
    did not then call Service.startForeground(): ServiceRecord{xxxxxxx u0 
    com.example.app/com.sentiance.sdk.services.ForegroundService}

Fatal Exception: android.app.RemoteServiceException$ForegroundServiceDidNotStartInTimeException: 
    Context.startForegroundService() did not then call Service.startForeground(): 
    ServiceRecord{xxxxxxx u0 com.example.app/com.sentiance.sdk.services.ForegroundService}
```

On Android, starting a foreground service is a two-step process:

1. Request Android to start a foreground service;
2. After the service is created or started, foreground the service by calling [startForegroundMode](https://developer.android.com/reference/android/app/Service#startForeground\(int,%20android.app.Notification\)).

This exception happens because the Sentiance SDK requests Android to start a foreground service, but after starting, the service does not get foregrounded in time (i.e. step 2 does not happen). To understand why this happens, let's first understand how Android operates.

After receiving the service start request in step 1, Android creates an instance of the service, and starts counting down the time, to track the foregrounding of the service. It then tries to invoke [onCreate](https://developer.android.com/reference/android/app/Service#onCreate\(\)) and [onStartCommand](https://developer.android.com/reference/android/app/Service#onStartCommand\(android.content.Intent,%20int,%20int\)) on the service instance, **on the application's main thread**. Both methods present an opportunity for the Sentiance SDK to foreground the service, by calling startForegroundMode. However, **if the application's main thread is busy or blocked, Android will not get the chance to call these methods**. And when the countdown expires, Android considers it too late, and terminates the app.

**Solution:** The Sentiance SDK always foregrounds its service when onCreate is called. This is done unconditionally. Therefore, when this exception happens, the cause is due to Android not getting the chance to call the onCreate method. It's therefore important to identify what the application's main thread was doing at the time of the exception.

When Android terminates an app with this exception, it also generates an ANR (application not responding) log. This log contains a snapshot of the stack trace of all of the application's threads at the time of the exception. The stack trace can be used to identify the state of the main thread when the exception happened. You can find out more about how to capture this information in [this](https://medium.com/@yangweigbh/monitoring-app-termination-on-android-11-97d514a3f9) external blog post.

Here's an example of the main thread's stack trace. Some lines were omitted for brevity.

{% code lineNumbers="true" %}
```
"main" prio=5 tid=1 Waiting
  | group="main" sCount=1 ucsCount=0 flags=1 obj=0x7222d218 self=0x7691660010
  | sysTid=5542 nice=0 cgrp=default sched=0/0 handle=0x7845798500
  | state=S schedstat=( 449640551 123141372 731 ) utm=29 stm=15 core=2 HZ=100
  | stack=0x7ffd50e000-0x7ffd510000 stackSize=8188KB
  | held mutexes=
  at java.lang.Object.wait(Native method)
  - waiting on <0x003c6057> (a okhttp3.internal.http2.Http2Stream)
  at java.lang.Object.wait(Object.java:442)
  at java.lang.Object.wait(Object.java:568)
  at okhttp3.internal.http2.Http2Stream.waitForIo$okhttp(Http2Stream.kt:716)
  at okhttp3.internal.http2.Http2Stream.takeHeaders(Http2Stream.kt:140)
  - locked <0x003c6057> (a okhttp3.internal.http2.Http2Stream)
  at okhttp3.internal.http2.Http2ExchangeCodec.readResponseHeaders(Http2ExchangeCodec.kt:96)
  ...
  at android.os.Handler.handleCallback(Handler.java:938)
  at android.os.Handler.dispatchMessage(Handler.java:99)
  at android.os.Looper.loopOnce(Looper.java:226)
  at android.os.Looper.loop(Looper.java:313)
  at android.app.ActivityThread.main(ActivityThread.java:8751)
  at java.lang.reflect.Method.invoke(Native method)
  at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:571)
  at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:1135)
```
{% endcode %}

Here, we see an OkHttp request executing on the main thread, and waiting for a response. On line 8, we see the main thread waiting on an Http2Stream object. In this example, the main thread is blocked due to a network request, which should actually be offloaded to a background thread.

Once you obtain the ANR log corresponding to the exception in your app, look at the main thread and try to identify what it was doing, and whether it was blocked or executing a long operation. By fixing the issue and unblocking the main thread, the Sentiance SDK service issue will also be addressed.
