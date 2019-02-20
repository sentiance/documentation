# 1. Including the SDK

## Adding Gradle Dependency

Add the Sentiance repository to your ****project \(top-level\) **build.gradle** file.

```groovy
buildscript {
    repositories {
    ...
    maven {
        url "http://repository.sentiance.com"
    }
}
```

In the **build.gradle** file of your app module, add the following line to the dependencies section.

```groovy
compile ('com.sentiance:sdk:4.5.1@aar') { transitive = true }
```

Your app should now build with the Sentiance SDK as a dependency.

## Native Optimization

The Sentiance SDK is also available in a native optimization flavor. This version is bundled with native libraries that resample accelerometer and gyroscope data at a specific frequency. Use this version only if explicitly asked to do so.

To include this version in your app, use the **-R** appended version of the SDK.

```groovy
compile ('com.sentiance:sdk:4.5.1-R@aar') { transitive = true }
```
