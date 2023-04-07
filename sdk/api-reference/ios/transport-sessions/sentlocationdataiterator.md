# SENTLocationDataIterator

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

An iterator that can be used to retrieve locations.

Iterating over the locations may be expensive, so avoid doing it directly on the main application thread.

```objectivec
SWIFT_CLASS_NAMED("LocationDataIterator")
@interface SENTLocationDataIterator : NSObject
```

## SENTLocationDataIterator API

### `next`

> Returns the location if available otherwise returns `nil`.
>
> ```objectivec
> - (CLLocation * _Nullable)next;
> ```
>
> \
> Example code:
>
> ```objectivec
> SENTLocationDataIterator *locationDataIterator;
> CLLocation *location;
> while ((location = [locationDataIterator next]) != nil) {
>   // location object
> }
> ```
