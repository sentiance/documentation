# Moment

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a moment that was detected for the user.

## Moment API

|                                    |                                      |
| ---------------------------------- | ------------------------------------ |
| List<[Attribute](../attribute.md)> | [getAttributes](./#getattributes) () |
| [DateTime](../datetime.md)         | [getEndTime](./#getendtime) ()       |
| [DateTime](../datetime.md)         | [getStartTime](./#getstarttime) ()   |
| [MomentType](momenttype.md)        | [getType](./#gettype) ()             |



### `getAttributes()`

> ```java
> List<Attribute> getAttributes()
> ```
>
> Returns attributes pertaining to the moment.

### `getEndTime()`

> ```java
> DateTime getEndTime()
> ```
>
> Returns the end time of the moment, if it has ended. Otherwise, returns null.

### `getStartTime()`

> ```java
> DateTime getStartTime()
> ```
>
> Returns the start time of the moment.

### `getType()`

> ```java
> EventType getType()
> ```
>
> Returns the type of the moment.
