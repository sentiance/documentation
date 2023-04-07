# SensorDataChunk

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a chunk of sensor data.

## SensorDataChunk API

### `getSize()`

> ```java
> int getSize()
> ```
>
> Returns the number of sensor samples in the chunk. All of x, y, z, and timestamp arrays will be of this size.

### `getTimestamps()`

> ```java
> long[] getTimestamps()
> ```
>
> Returns the timestamps in UTC epoch time.

### `getXValues()`

> ```java
> float[] getXValues()
> ```
>
> Returns the x-axis values.

### `getYValues()`

> ```java
> float[] getYValues()
> ```
>
> Returns the y-axis values.

### `getZValues()`

> ```java
> float[] getZValues()
> ```
>
> Returns the z-axis values.
