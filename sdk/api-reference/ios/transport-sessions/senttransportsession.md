# SENTTransportSession

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a session that was recorded during a transport. A session includes information about the transport, such as its ID and mode, in addition to a reference to the sensor data that was used to determine the mode of transport (e.g. accelerometer, location).

```objectivec
SWIFT_CLASS_NAMED("TransportSession")
@interface SENTTransportSession : NSObject
```

## SENTTransportSession API

### `accelerometerDataIterator`

> Returns an iterator that can be used to retrieve chunks of accelerometer data pertaining to the session. See [`SensorDataChunk`](sentsensordatachunk.md).
>
> Iterating over the data may be expensive, so avoid doing it directly on the main application thread.
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTAccelerometerDataIterator * _Nonnull accelerometerDataIterator;
> ```

### `endDate`

> Returns the end [date](../user-context/sentdate.md) of the session.
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTDate * _Nonnull endDate;@property (nonatomic, readonly) SENTTimelineTransportMode transportMode;
> ```

### `sessionId`

> Returns the unique ID of this transport session.
>
> This ID is equal to the one obtained from other Sentiance APIs, where the same transport is represented. e.g. the ID of a [`TransportEvent`](../user-context/senttimelineevent/senttransportevent.md) obtained from the User Context API.
>
> ```objectivec
> @property (nonatomic, readonly, copy) NSString * _Nonnull sessionId;
> ```

### `locationDataIterator`

> Returns an iterator that can be used to retrieve locations pertaining to the session.
>
> Iterating over the locations may be expensive, so avoid doing it directly on the main application thread.
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTLocationDataIterator * _Nonnull locationDataIterator;
> ```

### `startDate`

> Returns the start [date](../user-context/sentdate.md) of the session.
>
> ```objectivec
> @property (nonatomic, readonly, strong) SENTDate * _Nonnull startDate;
> ```

### `transportMode`

> Returns the [transport mode](../user-context/senttimelinetransportmode.md).
>
> ```objectivec
> @property (nonatomic, readonly) SENTTimelineTransportMode transportMode;
> ```
