# TransportSession

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a session that was recorded during a transport. A session includes information about the transport, such as its ID and mode, in addition to a reference to the sensor data that was used to determine the mode of transport (e.g. accelerometer, location).

## TransportSession API

### `getAccelerometerData()`

> ```java
> Iterator<SensorDataChunk> getAccelerometerData()
> ```
>
> Returns an iterator that can be used to retrieve chunks of accelerometer data pertaining to the session. See [`SensorDataChunk`](sensordatachunk.md).
>
> Iterating over the data may be expensive, so avoid doing it directly on the main application thread.

### `getEndDate()`

> ```java
> DateTime getEndDate()
> ```
>
> Returns the end [date](../usercontext/datetime.md) of the session.

### `getId()`

> ```java
> String getId()
> ```
>
> Returns the unique ID of this transport session.
>
> This ID is equal to the one obtained from other Sentiance APIs, where the same transport is represented. e.g. the ID of a [`TransportEvent`](../usercontext/event/transportevent.md) obtained from the User Context API.

### `getLocationData()`

> ```java
> Iterator<Location> getLocationData()
> ```
>
> Returns an iterator that can be used to retrieve locations pertaining to the session.
>
> Iterating over the locations may be expensive, so avoid doing it directly on the main application thread.

### `getStartDate()`

> ```java
> DateTime getStartDate()
> ```
>
> Returns the start [date](../usercontext/datetime.md) of the session.

### `getTransportMode()`

> ```java
> TransportMode getTransportMode()
> ```
>
> Returns the [transport mode](../usercontext/event/transportmode.md).
