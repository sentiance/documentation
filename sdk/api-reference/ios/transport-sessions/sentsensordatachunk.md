# SENTSensorDataChunk

Represents a chunk of sensor data.

```objectivec
SWIFT_CLASS_NAMED("SensorDataChunk")
@interface SENTSensorDataChunk : NSObject
```

## SENTSensorDataChunk API

### `count`

> Returns the number of sensor samples in the chunk. All of x, y, z, and timestamp arrays will be of this size.
>
> ```objectivec
> @property (nonatomic, readonly) NSInteger count;
> ```

### `timestamps`

> Returns the timestamps in UTC epoch time.
>
> ```objectivec
> @property (nonatomic, readonly, copy) NSArray<NSNumber *> * _Nonnull timestamps;
> ```

### `xValues`

> Returns the x-axis values.
>
> ```objectivec
> @property (nonatomic, readonly, copy) NSArray<NSNumber *> * _Nonnull xValues;
> ```

### `yValues`

> Returns the y-axis values.
>
> ```objectivec
> @property (nonatomic, readonly, copy) NSArray<NSNumber *> * _Nonnull yValues;
> ```

### `zValues`

> Returns the z-axis values.
>
> ```objectivec
> @property (nonatomic, readonly, copy) NSArray<NSNumber *> * _Nonnull zValues;
> ```
