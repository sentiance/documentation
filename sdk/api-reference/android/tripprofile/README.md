# TripProfile

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v4.21.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

Holds the list of [`TransportSegments`](transportsegment.md) detected by the SDK during a trip.

## TripProfile API

### `getTransportSegments()`

> ```java
> public List<TransportSegment> getTransportSegments()
> ```
>
> Returns a list of transport segments. See [`TransportSegment`](transportsegment.md).

### `getTripId()`

> ```java
> public String getTripId()
> ```
>
> Returns the id associated with this trip.
