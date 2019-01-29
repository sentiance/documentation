# Automatic Detections with Forced Trips

While in [automatic detection mode](automatic-detections.md), the SDK can be forced to start a trip. Doing so will prevent the SDK from detecting stationary moments and force it to continue collecting trip data until the trip is explicitly stopped \(e.g. when a user stops 15 minutes at a gas station, there won't be a stationary event for this generated in the timeline. Instead there will be idle transport events annotating this\).

Once the forced trip is stopped, the SDK will resume automatic detections.

## Starting a Trip

You can start a trip as follows:

{% tabs %}
{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] startTrip:metadata 
                          transportModeHint:SENTTransportModeUnknown
    success:^{
    }
    failure:^(SENTSDKStatus *status) {
}];
```

The `metadata` is an `NSDictionary` representing a map of string to string types. You can use it to attach any piece of information to this trip. The `transportModeHint` is a hint you can give the SDK about the type of transport the trip is \(e.g. car, bicycle, etc.\).

In case starting a trip fails, you can [check]() the `SENTSDKStatus` object to determine the reason. 
{% endtab %}

{% tab title="Android" %}
```java
startTrip(metadata, transportModeHint, new StartTripCallback() {
    @Override
    public void onSuccess () {
        // The trip was successfully started.
    }
    @Override
    public void onFailure (@Nullable SdkStatus sdkstatus) {
        // Something prevented the trip to start.
        // Check the status object for more details.
    }
});
```

The `metadata` is a map of string to string types. You can use it to attach any piece of information to this trip. The `transportModeHint` is a hint of type [`TransportMode`](../../api-reference/android/trip/transportmode.md) you can give the SDK about the type of transport the trip is \(e.g. car, bicycle, etc.\).

By passing a [`StartTripCallback`](../../api-reference/android/trip/starttripcallback.md) to the method, you will be notified when a trip is successfully started. If it fails, you can check the [`SdkStatus`](../../api-reference/android/sdkstatus/) object to determine the reason. 
{% endtab %}
{% endtabs %}

## Stopping a Trip

To stop a trip that you've started, call `stopTrip` as follows:

{% tabs %}
{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] stopTrip:^{
    // successfully stopped the trip
  } failure:^(SENTSDKStatus *status) {
    // stopping the trip failed
}];
```

If stopping the trip fails, you can [check]() the `SENTSDKStatus` to determine why. Note that if no trip was ongoing, `failure`  will be called as well.

To check if a trip is ongoing before calling `stopTrip`, see [this](checking-trip-status.md) guide.
{% endtab %}

{% tab title="Android" %}
```java
stopTrip(new StopTripCallback() {
    @Override
    public void onSuccess () {
    }
    @Override
    public void onFailure (@Nullable SdkStatus sdkstatus) {
    }
});
```

You can pass a [`StopTripCallback`](../../api-reference/android/trip/stoptripcallback.md) to this method to be notified when the trip is stopped. If stopping the trip fails, you can check the [`SdkStatus`](../../api-reference/android/sdkstatus/) to determine why. Note that if no trip was ongoing, the [`onFailure()`](../../api-reference/android/trip/stoptripcallback.md#onfailure) method will be called as well.

To check if a trip is ongoing before calling [`stopTrip()`](../../api-reference/android/sentiance.md#starttrip), see [this](checking-trip-status.md) guide.
{% endtab %}
{% endtabs %}



