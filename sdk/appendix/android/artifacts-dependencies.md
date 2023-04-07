---
description: >-
  This page lists the Sentiance Android SDK library artifacts with their
  corresponding dependencies.
---

# Artifacts & Dependencies

## Version 6.x

{% hint style="danger" %}
Sentiance artifacts that depend on each other share a common version number. This is denoted as **\<sentiance-version>** below. Mixing different versions for these artifacts is not supported. You can avoid version conflicts by making use of the SDK's bill of materials (com.sentiance:sdk-bom).
{% endhint %}

### com.sentiance:sdk-bom

This is the bill of materials artifact. You can add a platform dependency to this artifact to avoid version mismatches between different Sentiance artifacts.

{% code title="build.gradle" %}
```groovy
dependencies {
    implementation(platform('com.sentiance:sdk-bom:<sentiance-version>'))
    implementation('com.sentiance:sdk')
    implementation('com.sentiance:sdk-crash-detection')
    ...
}
```
{% endcode %}

### com.sentiance:sdk

This is the core library artifact which offers the main SDK functionality, such as user creation and detections.

#### Dependencies

```
com.google.android.gms:play-services-location:18.0.0
com.sentiance:sdk-breakpad:1.0.2
```

### com.sentiance:sdk-breakpad

This library artifact allows the Sentiance SDK to capture and collect information about native app crashes.

You do not need to manually add this artifact as a dependency in your app.

#### Dependencies

This artifact has no dependencies.

### com.sentiance:sdk-on-device-common

This library artifact provides internal SDK functionality that is common among Sentiance's on-device features.

You do not need to manually add this artifact as a dependency in your app.

#### Dependencies

```
org.tensorflow:tensorflow-lite:2.7.0
```

### com.sentiance:sdk-crash-detection

This library artifact adds vehicle crash detection functionality to the SDK, and makes the `CrashDetectionApi` available to your app.&#x20;

You must add this artifact as a dependency in your app if you want to enable crash detection.

#### Dependencies

```
com.sentiance:sdk-on-device-common:<sentiance-version>
```

### com.sentiance:sdk-event-timeline

This library artifact provides internal SDK functionality that is required for creating a user's event-timeline on the device. Other SDK features, such as user context information and segment detection, are built on top of this timeline data.

You do not need to manually add this artifact as a dependency in your app.

#### Dependencies

```
com.sentiance:sdk-on-device-common:<sentiance-version>
org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.5.30
```

### com.sentiance:sdk-venue-mapper

This library artifact provides internal SDK functionality that is required for enriching a user's event-timeline using venue information.

You do not need to manually add this artifact as a dependency in your app.

#### Dependencies

```
com.sentiance:sdk-event-timeline:<sentiance-version>
org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.5.30
org.jetbrains.kotlinx:kotlinx-datetime0.3.0:
org.jetbrains.kotlinx:kotlinx-serialization-core:1.3.0
org.jetbrains.kotlinx:kotlinx-serialization-json:1.3.0
```

### com.sentiance:sdk-user-context

This library artifact adds the user context SDK functionality, and makes the `UserContextApi` available to your app. The user's context includes information about the recent timeline events (e.g. transports and stationaries), home and work venues, and the user's segments (if enabled/available).

You must add this artifact as a dependency in your app if you want to access the user's context information. Alternatively, you can add the _sdk-lifestyle_ artifact to enable all lifestyle features, including the user's context.

#### Dependencies

```
com.sentiance:sdk-venue-mapper:<sentiance-version>
```

### com.sentiance:sdk-segments

This library artifact adds user segment detection functionality to the SDK. Segment data is added to the user's context information (if enabled).

This artifact must be added as a dependency in your app if you want to enable segment detection. However, the recommended approach is to add the _sdk-lifestyle_ artifact to enable all lifestyle features, including segment detection.

#### Dependencies

```
com.sentiance:sdk-event-timeline:<sentiance-version>
com.sentiance:sdk-venue-mapper:<sentiance-version>
com.sentiance:sdk-decision-engine:<sentiance-version>
```

### com.sentiance:sdk-decision-engine

This library artifact is required by _sdk-segments_ to do segment detection.

You do not need to manually add this artifact as a dependency in your app.

#### Dependencies

```
com.sentiance:sdk-event-timeline:<sentiance-version>
org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.5.30
org.jetbrains.kotlinx:kotlinx-datetime:0.2.1
org.jetbrains.kotlinx:kotlinx-serialization-core:1.2.1
org.jetbrains.kotlinx:kotlinx-serialization-json:1.2.1
co.touchlab:stately-common:1.10.0
co.touchlab:stately-concurrency:1.10.0
co.touchlab:kermit-jvm:1.0.0
```

### com.sentiance:sdk-lifestyle

This library artifact adds the full Sentiance lifestyle functionality that is available via the SDK. This includes user event timeline creation, user context information, and user segment detection.

You must add this artifact as a dependency in your app if you want to enable the full lifestyle functionality.

#### Dependencies

```
com.sentiance:sdk-user-context:<sentiance-version>
com.sentiance:sdk-segments:<sentiance-version>
```

### com.sentiance:sdk-driving-insights

This library artifact adds the driving insights SDK functionality, and makes the `DrivingInsightsApi` available to your app. The driving insights includes information about detected transports, such as scores for various safe driving attributes (e.g. smooth driving).

You must add this artifact as a dependency in your app if you want to access the driving insights information.

#### Dependencies

```
com.sentiance:sdk-event-timeline:<sentiance-version>
org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.5.30
```

## Version 4.x

```
com.google.android.gms:play-services-location:12.0.1
org.tensorflow:tensorflow-lite:2.7.0
```
