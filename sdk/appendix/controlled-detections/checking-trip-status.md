# Checking Trip Status

In both [automatic](automatic-detections.md) and [controlled](controlled-trips-only.md) detection modes, you can check the SDK if a trip is ongoing at that moment.

{% tabs %}
{% tab title="iOS" %}
```swift
Sentiance.shared.isTripOngoing(ofType: .external)
```

The method takes a `SENTTripType` parameter to specify the type of trip you are interested in. You can pass `SDK` or `external`.
{% endtab %}

{% tab title="Android" %}
```kotlin
val isTripOngoing = sentiance.isTripOngoing(tripType)
```

The method takes a [`TripType`](../../api-reference/android/trip/triptype.md) parameter to specify the type of trip you are interested in. You can pass any one of `EXTERNAL_TRIP`, `SDK_TRIP`, and `ANY` to query the trip status.
{% endtab %}
{% endtabs %}

Trip types are classified as follows:

* External: a trip that has been started by your app.
* SDK: a trip that has been started by the SDK based on automatic detections.
