# SENTAccelerometerDataIterator

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

An iterator that can be used to retrieve chunks of accelerometer data.

Iterating over the data may be expensive, so avoid doing it directly on the main application thread.

```objectivec
SWIFT_CLASS_NAMED("AccelerometerDataIterator")
@interface SENTAccelerometerDataIterator : NSObject
```

## SENTAccelerometerDataIterator API

### `next`

> Returns the [SensorDataChunk](sentsensordatachunk.md) if available otherwise returns `nil`.
>
> ```objectivec
> - (SENTSensorDataChunk * _Nullable)next;
> ```
>
> \
> Example code:
>
> ```objectivec
> SENTAccelerometerDataIterator *accelerometerDataIterator;
> SENTSensorDataChunk *sensorDataChunk;
> while ((sensorDataChunk = [accelerometerDataIterator next]) != nil) {
>   // SENTSensorDataChunk object
> }
> ```
