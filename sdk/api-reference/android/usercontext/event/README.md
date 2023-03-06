# Event

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents an occurrence of an event that was detected for a user.

## Event API

|                            |                                                    |
| -------------------------- | -------------------------------------------------- |
| Long                       | [getDurationInSeconds](./#getdurationinseconds) () |
| [DateTime](../datetime.md) | [getEndTime](./#getendtime) ()                     |
| [EventType](eventtype.md)  | [getEventType](./#geteventtype) ()                 |
| [DateTime](../datetime.md) | [getStartTime](./#getstarttime) ()                 |
| boolean                    | [hasEnded](./#hasended) ()                         |



### `getDurationInSeconds()`

> ```java
> @Nullable Long getDurationInSeconds()
> ```
>
> Returns the duration of the event, in seconds, if it has ended. Otherwise returns null.

### `getEndTime()`

> ```java
> @Nullable DateTime getEndTime()
> ```
>
> Returns the end time of the event, if the event has ended. Otherwise, returns null.

### `getEventType()`

> ```java
> EventType getEventType()
> ```
>
> Returns the event type. Based on this type, you can cast an event to the corresponding event class (e.g. [TransportEvent](transportevent.md), [StationaryEvent](stationaryevent.md)) to access type specific properties.

### `getStartTime()`

> ```java
> DateTime getStartTime()
> ```
>
> Returns the start time of the event.

### `hasEnded()`

> ```java
> boolean hasEnded()
> ```
>
> Returns true if the event has ended.
