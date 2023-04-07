# On-Device Features

Sentiance offers a variety of features whose processing happens strictly offline on the device. These are the on-device features that are available via the Sentiance SDK.

{% hint style="success" %}
The features listed on this page must first be enabled by Sentiance for your app, before you can start using them. Please reach out to our support team to have a feature enabled.
{% endhint %}

{% hint style="info" %}
Some features that are listed here are released as [Early Access](feature-production-readiness.md). Please check out our [Production Readiness page](feature-production-readiness.md) to find out more.
{% endhint %}

### Vehicle Crash Detection

This feature offers the ability to detect vehicle crashes (collisions) in real time, during trips. Sentiance processes various sensor and location data in real time on the device, in order to detect crashes and notify your app.

Crash data includes information such as location, magnitude of the detected peak, and confidence.

You can learn more about this feature in our [Vehicle Crash Detection](../../guide/vehicle-crash-detection.md) page.

#### Activation for Android

For Android apps, in order to activate vehicle crash detection and receive crash data, you must add the _com.sentiance:sdk-crash-detection_ artifact as a dependency. You can then subscribe for vehicle crash events via the `CrashDetectionApi` class.

{% code title="app/build.gradle" %}
```groovy
dependencies {
    implementation(platform('com.sentiance:sdk-bom:<sentiance-version>'))
    implementation('com.sentiance:sdk-crash-detection')
    ...
}
```
{% endcode %}

#### Activation for iOS

For iOS apps, crash detection is included in the main SDK framework. No additional steps are needed to activate it.

#### Activation for React Native

For React Native apps, to activate and access crash detection, install the _@sentiance-react-native/crash-detection_ module.

### Transport Classification

The Sentiance SDK processes various sensor and location data in real-time, directly on the device, to segment a user's trips into the various transport methods used, such as walking, biking, vehicle. The SDK uses Sentiance's state of the art deep learning model to achieve this.

The classification results are exposed in the user's context information, part of the user's recent events.

#### Activation for Android

For Android apps, this feature is included after adding a dependency on the _com.sentiance:sdk-user-context or com.sentiance:sdk-lifestyle_ artifact.

#### Activation for iOS

For iOS apps, transport classification is included in the main SDK framework. No additional steps are needed to activate it.

#### Activation for React Native

For React Native apps, this feature is included after installing the _@sentiance-react-native/user-context_ module.

### User Current Context Information

A user's current context includes contextual information about the current state of the user. This includes things like:

* Recent transport and stationary events, with venue type information if available.
* The user's last known location.
* The user's home and work venues, if detected.
* The user's [segments](../../library/segments.md), if detected.

The population of this context information happens offline, on the device.

#### Activation for Android

For Android apps, in order to activate and access the user's current context information, you must add the _com.sentiance:sdk-user-context_ artifact as a dependency. By default, this artifact excludes segment detection. To activate segment detection, you can add a dependency to the _com.sentiance:sdk-lifestyle_ artifact instead, which will activate all lifestyle profiling features.

{% code title="app/build.gradle" %}
```groovy
dependencies {
    implementation(platform('com.sentiance:sdk-bom:<sentiance-version>'))
    implementation('com.sentiance:sdk-user-context')
    // or
    implementation('com.sentiance:sdk-lifestyle')
    ...
}
```
{% endcode %}

You can then subscribe for user context updates, or request the context directly, via the `UserContextApi` class.

#### Activation for iOS

For iOS apps, the user's current context information is available via the main SDK framework. No additional steps are needed to activate it.

#### Activation for React Native

For React Native apps, to activate and access the user's current context, install the _@sentiance-react-native/user-context_ module.

### Venue-Type Mapping, Home/Work Detection

The Sentiance SDK can enrich a user's stationary data with information about the significance of the stationary (i.e. home, work, or a point of interest), and type of venue (i.e. restaurant, fitness center, etc). This is possible with Sentiance's on-device, fully offline, venue type mapping feature.

The SDK uses venue data that is available for the entire globe, by downloading and storing it on the device on an as-needed basis. The data is divided into large geographic areas (town or city level), and is updated as the user navigates to different areas.

With the use of Sentiance's state of the art deep learning model for venue type mapping and home/work detection, the user's stationary data gets enriched, and refined as more data gets collected. Additionally, the user's semantic time gets determined

The venue information is exposed in the user's context, part of the user's recent stationary events, and as separate home and work venue properties. An additional property indicates the user's current semantic time.

#### Activation for Android

For Android apps, this feature is included after adding a dependency on the _com.sentiance:sdk-user-context_ artifact.

#### Activation for iOS

For iOS apps, this feature is included in the main SDK framework. No additional steps are needed to activate it.

#### Activation for React Native

For React Native apps, this feature is included after installing the _@sentiance-react-native/user-context_ module.

### Semantic Time

The Sentiance SDK can enrich a user's context by providing information about the user's current semantic time. Semantic time (e.g. morning, lunch, etc.) is personalized based on a user's timeline data, and becomes more accurate over time.

#### Activation for Android

For Android apps, this feature is included after adding a dependency on the _com.sentiance:sdk-user-context_ artifact.

#### Activation for iOS

For iOS apps, this feature is included in the main SDK framework. No additional steps are needed to activate it.

#### Activation for React Native

For React Native apps, this feature is included after installing the _@sentiance-react-native/user-context_ module.

### Segment Detection

The Sentiance SDK can enrich a user's context by assigning different segmentation profiles, e.g. heavy commuter, low/medium/high social activity, and more. This is possible with Sentiance's multi-platform decision engine which runs directly on the device. It consumes a user's timeline data, and in return produces segments that apply to the user.

#### Activation for Android

For Android apps, this feature is included after adding a dependency on the _com.sentiance:sdk-lifestyle_ artifact.

#### Activation for iOS

For iOS apps, this feature is included in the main SDK framework. No additional steps are needed to activate it.

#### Activation for React Native

For React Native apps, to activate this feature, add a dependency on the _com.sentiance:sdk-lifestyle_ artifact in your android app. For iOS apps, no additional steps are needed to activate it.

### Driving Insights

The Sentiance SDK can provide insights about the driving behaviour for vehicular transports. For example, for a given transport, scores can be computed for various safe driving attributes, such as attention, smooth and legal driving. These scores are based on a variety of detections that the SDK does during transports, such as harsh driving, phone usage, and call detection. These insights are made available via the Driving Insights API.

#### Activation for Android

For Android apps, this feature is included after adding a dependency on the _com.sentiance:sdk-driving-insights_ artifact.

#### Activation for iOS

For iOS apps, this feature is included in the main SDK framework. No additional steps are needed to activate it.

#### Activation for React Native

For React Native apps, this feature is included after installing the _@sentiance-react-native/driving-insights_ module.
