# Segment

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a segment that was detected for the user.

## Segment API

|                                    |                                      |
| ---------------------------------- | ------------------------------------ |
| List<[Attribute](../attribute.md)> | [getAttributes](./#getattributes) () |
| [DateTime](../datetime.md)         | [getEndTime](./#getendtime) ()       |
| [DateTime](../datetime.md)         | [getStartTime](./#getstarttime) ()   |
| [SegmentType](segmenttype.md)      | [getType](./#gettype) ()             |



### `getAttributes()`

> ```java
> List<Attribute> getAttributes()
> ```
>
> Returns attributes pertaining to the segment.

### `getEndTime()`

> ```java
> @Nullable DateTime getEndTime()
> ```
>
> Returns the end time of the segment, if it has ended. Otherwise, returns null.

### `getStartTime()`

> ```java
> DateTime getStartTime()
> ```
>
> Returns the start time of the segment.

### `getType()`

> ```java
> SegmentType getType()
> ```
>
> Returns the type of the segment.
