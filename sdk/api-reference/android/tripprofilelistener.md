# TripProfileListener

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v4.21.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

This interface is used with [`setTripProfileListener(TripProfileListener)`](sentiance.md#settripprofilelistener).

## TripProfileListener API

### `onTripProfiled()`

> ```
> void onTripProfiled(TripProfile tripProfile)
> ```
>
> Called when a user completes a trip and the trip has been profiled. See [`TripProfile`](tripprofile/) for more details.

