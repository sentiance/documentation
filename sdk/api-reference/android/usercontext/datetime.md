# DateTime

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

A date-time with a time-zone in the ISO-8601 calendar system.

## DateTime API

|          |                                                                         |
| -------- | ----------------------------------------------------------------------- |
| long     | [getEpochTime](datetime.md#getepochtime) ()                             |
| String   | [getTimezoneId](datetime.md#gettimezoneid) ()                           |
| int      | [getTimezoneOffsetInMinutes](datetime.md#gettimezoneoffsetinminutes) () |
| Calendar | [toCalendar](datetime.md#tocalendar) ()                                 |



### `getEpochTime()`

> ```java
> long getEpochTime()
> ```
>
> Returns the epoch time.

### `getTimezoneId()`

> ```java
> String getTimezoneId()
> ```
>
> Returns the timezone ID. See java.util.TimeZone.

### `getTimezoneOffsetInMinutes()`

> ```java
> int getTimezoneOffsetInMinutes()
> ```
>
> Returns the timezone offset in minutes.

### `toCalendar()`

> ```java
> Calendar toCalendar()
> ```
>
> Returns a Calendar representation of this object.
