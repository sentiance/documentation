# Visit

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a visit to a particular venue.

## Visit API

|                            |                                                          |
| -------------------------- | -------------------------------------------------------- |
| long                       | [getDurationInSeconds](visit.md#getdurationinseconds) () |
| [DateTime](../datetime.md) | [getEndTime](visit.md#getendtime) ()                     |
| [DateTime](../datetime.md) | [getStartTime](visit.md#getstarttime) ()                 |



### `getDurationInSeconds()`

> ```java
> long getDurationInSeconds()
> ```
>
> Returns the duration of the visit, in seconds.

### `getEndTime()`

> ```java
> DateTime getEndTime()
> ```
>
> Returns the end time of the visit.

### `getStartTime()`

> ```java
> DateTime getStartTime()
> ```
>
> Returns the start time of the visit.
