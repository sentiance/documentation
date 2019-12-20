# 1. Including the SDK

The latest version of the Sentiance SDK is **4.12.0**.

## Adding the Gradle Dependency

Add the Sentiance repository to your ****project \(top-level\) **build.gradle** file.

{% code title="" %}
```groovy
allprojects {
  repositories {
    ...
    maven {
      url "https://repository.sentiance.com"
    }
  }
}
```
{% endcode %}

In the **build.gradle** file of your app module, add the following line to the dependencies section.

{% code title="" %}
```groovy
implementation ('com.sentiance:sdk:4.12.0@aar') { transitive = true }
```
{% endcode %}

Your app should now build with the Sentiance SDK as a dependency.

## Native Optimization

The Sentiance SDK is also available in a native optimization flavor. This version is bundled with native libraries that resample accelerometer and gyroscope data at a specific frequency. Use this version only if explicitly asked to do so.

To include this version in your app, use the **-R** appended version of the SDK.

```groovy
implementation ('com.sentiance:sdk:4.12.0-R@aar') { transitive = true }
```

