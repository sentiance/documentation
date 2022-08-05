# Check the Location Permissions

To get current location permission status, use the `sdkStatus` property.

{% tabs %}
{% tab title="iOS" %}
```swift
let sdkStatus = Sentiance.shared.sdkStatus

if (sdkStatus.locationPermission == .always) {
    // We are good!
} else {
    // Background location permission not granted.
}

if (sdkStatus.isPreciseLocationAuthorizationGranted) {
    // We are good!
} else {
    // Precise location permission not granted.
}
```
{% endtab %}

{% tab title="Android" %}
```kotlin
val sdkStatus = Sentiance.getInstance(context).sdkStatus

if (sdkStatus.locationPermission == SdkStatus.LocationPermission.ALWAYS) {
    // We are good!
} else {
    // Background location permission not granted.
}

if (sdkStatus.isPreciseLocationPermGranted) {
    // We are good!
} else {
    // Precise location permission not granted.
}
```
{% endtab %}
{% endtabs %}

In the above example, `sdkStatus` returns an SDK status object ([iOS](../api-reference/ios/sentsdkstatus.md) / [Android](../api-reference/android/sdkstatus/)) which has properties for the location permission and precision.

{% hint style="info" %}
The user must grant the background location access permission in order for SDK detections to work. This is presented as the "**always**" option on iOS, and the "**allow all the time**" option on Android 10+ devices.

The user must also enable precise location accuracy.
{% endhint %}

To be notified of location permission changes, you can set up an SDK status listener on the SDK's config object as follows:&#x20;

{% tabs %}
{% tab title="iOS" %}
```swift
Sentiance.shared.setDidReceiveSdkStatusUpdateHandler { status in
    // Check the location permission and precision here.
}
```
{% endtab %}

{% tab title="Android" %}
```kotlin
Sentiance.getInstance(this).setSdkStatusUpdateListener { status -> 
    // Check the location permission and precision here.
}
```
{% endtab %}
{% endtabs %}
