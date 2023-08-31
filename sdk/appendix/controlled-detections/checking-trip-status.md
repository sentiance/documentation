# Checking Trip Status

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

During both [automatic](automatic-detections.md) and [controlled](controlled-trips-only.md) detection modes, you can check the SDK if a trip is ongoing at that moment.

{% tabs %}
{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] isTripOngoing: tripType];
```

The method takes a `SENTTripType` parameter to specify the type of trip you are interested in. You can pass `SENTTripTypeSDK` or `SENTTripTypeExternal`.
{% endtab %}

{% tab title="Android" %}
```java
boolean isTripOngoing = isTripOngoing(tripType);
```

The method takes a [`TripType`](../../api-reference/android/trip/triptype.md) parameter to specify the type of trip you are interested in. You can pass any one of `EXTERNAL_TRIP`, `SDK_TRIP`, and `ANY` to query the trip status.
{% endtab %}
{% endtabs %}

Trip types are classified as follows:

* External: a trip that has been started by your app.
* SDK: a trip that has been started by the SDK based on automatic detections.

