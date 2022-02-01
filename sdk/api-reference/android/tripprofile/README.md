# TripProfile

Holds the list of [`TransportSegments`](transportsegment.md) detected by the SDK during a trip.

## TripProfile API

|  |  |
| :--- | :--- |
| List&lt;[TransportSegment](transportsegment.md)&gt; | [getTransportSegments](./#gettransportsegments) \(\) |
| String | [getTripid](./#gettripid) \(\) |



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

