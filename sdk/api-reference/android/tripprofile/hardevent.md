# HardEvent

A HardEvent is any unusual and/or rigorous force that is applied to the device and detected by the SDK.

## HardEvent API

|  |  |
| :--- | :--- |
| long | [getMagnitude](hardevent.md#getmagnitude) \(\) |
| long | [getTimestamp](hardevent.md#gettimestamp) \(\) |



### `getMagnitude()`

> ```java
> public long getMagnitude()
> ```
>
> Returns the magnitude of this hard event in m/s2.

### `getTimestamp()`

> ```java
> public long getTimestamp()
> ```
>
> Returns the UTC time of this hard event, in milliseconds since January 1, 1970.

