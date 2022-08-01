# Automatic Detections with Forced Trips

While in [automatic detection mode](automatic-detections.md), the SDK can be forced to start a trip. Doing so will prevent the SDK from detecting stationary moments and force it to continue collecting trip data until the trip is explicitly stopped.

Once the forced trip is stopped, the SDK will resume automatic detections.

## Starting a Trip

You can start a trip as follows:

{% tabs %}
{% tab title="iOS" %}
```swift
Sentiance.shared.startTrip(metadata: metadata, transportModeHint: hint) { result, error in
}
```



The `metadata` is an `NSDictionary` representing a map of string to string types. You can use it to attach any piece of information to this trip. The `transportModeHint` is a hint you can give the SDK about the type of transport the trip is (e.g. car, bicycle, etc.).

In case starting a trip fails, you can check the error to determine the reason.&#x20;
{% endtab %}

{% tab title="Android" %}
```kotlin
sentiance.startTrip(metadata, transportModeHint)
    .addOnSuccessListener { startTripResult -> 
        // The trip was successfully started.
    }
    .addOnFailureListener { startTripError ->
        // Something prevented the trip to start.
        // Check the status object for more details.
    }
```

The `metadata` is a map of string to string types. You can use it to attach any piece of information to this trip. The `transportModeHint` is a hint of type [`TransportMode`](../../api-reference/android/trip/transportmode.md) you can give the SDK about the type of transport the trip is (e.g. car, bicycle, etc.).

You can add an [OnSuccessListener](../../api-reference/android/pendingoperation/onsuccesslistener.md) and [`OnFailureListener`](../../api-reference/android/pendingoperation/onfailurelistener.md) to the returned [`PendingOperation`](../../api-reference/android/pendingoperation/), you will be notified when a trip is successfully started. If it fails, you can check the [`StartTripError`](../../api-reference/android/starttriperror/) object to determine the reason.
{% endtab %}
{% endtabs %}

## Stopping a Trip

To stop a trip that you've started, call `stopTrip` as follows:

{% tabs %}
{% tab title="iOS" %}
```swift
Sentiance.shared.stopTrip { result, error in
}
```

If stopping the trip fails, you can check the error to determine why. To check if a trip is ongoing before calling `stopTrip`, see [this](checking-trip-status.md) guide.
{% endtab %}

{% tab title="Android" %}
```kotlin
sentiance.stopTrip()
    .addOnSuccessListener { stopTripResult -> }
    .addOnFailureListener { stopTripError -> }
```

You can add an [OnSuccessListener](../../api-reference/android/pendingoperation/onsuccesslistener.md) and [`OnFailureListener`](../../api-reference/android/pendingoperation/onfailurelistener.md) to  the returned [`PendingOperation`](../../api-reference/android/pendingoperation/), you will be notified when a trip is successfully started. If it fails, you can check the [`StopTripError`](../../api-reference/android/stoptriperror/) object to determine the reason.

To check if a trip is ongoing before calling [`stopTrip()`](../../api-reference/android/sentiance.md.md#stoptrip), see [this](checking-trip-status.md) guide.
{% endtab %}
{% endtabs %}

