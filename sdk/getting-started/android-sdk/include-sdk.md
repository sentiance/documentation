# 2. Including the SDK

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

The latest version of the Sentiance SDK is **4.22.1**.

## Adding the Gradle Dependency

Add the Sentiance repository to your **** project (top-level) **build.gradle** file.

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
implementation ('com.sentiance:sdk:4.22.1@aar') { transitive = true }
```
{% endcode %}

Your app should now build with the Sentiance SDK as a dependency.
