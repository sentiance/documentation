# Segment

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a segment that was detected for the user.

## Segment API

### `getAttributes()`

> ```java
> List<Attribute> getAttributes()
> ```
>
> Returns attributes pertaining to the segment.

### `getCategory()`

> ```java
> SegmentCategory getCategory()
> ```
>
> Returns the [category](segmentcategory.md) of the segment.

### `getEndTime()`

> ```java
> @Nullable DateTime getEndTime()
> ```
>
> Returns the end time of the segment, if it has ended. Otherwise, returns null.

### `getSegmentId()`

> ```java
> int getSegmentId()
> ```
>
> Returns the unique ID of this segment.

### `getStartTime()`

> ```java
> DateTime getStartTime()
> ```
>
> Returns the start time of the segment.

### `getSubcategory()`

> ```java
> SegmentSubcategory getSubcategory()
> ```
>
> Returns the [subcategory](segmentsubcategory.md) of the segment.

### `getType()`

> ```java
> SegmentType getType()
> ```
>
> Returns the [type](segmenttype.md) of the segment.
