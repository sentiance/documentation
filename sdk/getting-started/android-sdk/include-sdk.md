# 1. Including the SDK

The latest version of the Sentiance SDK is **4.12.0**.

## Adding the Gradle Dependency

Add the Sentiance repository to your ****project \(top-level\) **build.gradle** file.

{% tabs %}
{% tab title="" %}
```groovy
allprojects {
  repositories {
    ...
    maven {
      url "http://repository.sentiance.com"
    }
  }
}
```
{% endtab %}
{% endtabs %}

In the **build.gradle** file of your app module, add the following line to the dependencies section.

{% tabs %}
{% tab title="" %}
```groovy
implementation ('com.sentiance:sdk:4.12.0@aar') { transitive = true }
```
{% endtab %}
{% endtabs %}

Your app should now build with the Sentiance SDK as a dependency.

## Native Optimization

The Sentiance SDK is also available in a native optimization flavor. This version is bundled with native libraries that resample accelerometer and gyroscope data at a specific frequency. Use this version only if explicitly asked to do so.

To include this version in your app, use the **-R** appended version of the SDK.

```groovy
implementation ('com.sentiance:sdk:4.12.0-R@aar') { transitive = true }
```

