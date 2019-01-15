# 1. Include SDK

The latest version of the Android SDK is **4.3.0.**

The latest version of the Android SDK with native optimizations is **4.3.0-R**.  
The native optimizations SDK has an additional overhead of 1.5MB application size.

### Adding Gradle dependency

Make sure the Sentiance repository is added to your **top-level build.gradle**

```text
repositories {
 maven {
  url "http://repository.sentiance.com"
 }
}
```

In the **build.gradle** file of your app module, add one of the following lines to the dependencies section.

```text
// Default SDK
compile ('com.sentiance:sdk:4.3.0@aar') {transitive = true}      
```

```text
// For native optimizations
compile ('com.sentiance:sdk:4.3.0-R@aar') {transitive = true} 
```

Your app should now build with the Sentiance SDK as a dependency.

Your development environment should now be properly set up to compile your app including the Sentiance SDK.

