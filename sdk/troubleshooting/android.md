# Android

### java.lang.RuntimeException: Exception while creating class X

```java
com.sentiance.osdktest E/Sentiance: Failed to initialize the Sentiance SDK
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

