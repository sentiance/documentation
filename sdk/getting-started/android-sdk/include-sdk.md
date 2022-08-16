# 1. Including the SDK

## Adding the Gradle Dependency

Add the Sentiance repository to your **** project (top-level) **build.gradle** file.

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

In the **build.gradle** file of your app module, add the following line to the dependencies section.

```groovy
implementation (platform('com.sentiance:sdk-bom:6.0.+'))
implementation ('com.sentiance:sdk')
```

Your app should now build with the Sentiance SDK as a dependency.
