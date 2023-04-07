# TransportEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a duration of the time when the user was in transport.

## TransportEvent API

{% hint style="info" %}
This class extends [Event](./). See [Event](./) for additional properties and methods.
{% endhint %}

### getDistanceInMeters`()`

> ```java
> @Nullable Integer getDistanceInMeters()
> ```
>
> Returns the distance travelled during the transport in meters. If distance cannot be computed then returns null.

### `getTransportMode()`

> ```java
> TransportMode getTransportMode()
> ```
>
> Returns the mode of transportation.

### getWaypoints`()`

> ```java
> List<Waypoint> getWaypoints()
> ```
>
> Returns the waypoints collected during the transport, as [Waypoint](../transportevent.md).
