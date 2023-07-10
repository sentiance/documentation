# SensorDataChunk

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
