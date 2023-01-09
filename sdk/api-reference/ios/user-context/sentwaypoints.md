# SENTWaypoints

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
@interface SENTWaypoint : NSObject <NSSecureCoding, NSCopying>
```

### accuracyInMeters

Returns the accuracy in degrees.

```objectivec
@property (nonatomic, assign, readonly) NSInteger accuracyInMeters;
```

### latitude

Returns the latitude in degrees.

```objectivec
@property (nonatomic, assign, readonly) CLLocationDegrees latitude;
```

### longitude

Returns the longitude in degrees.

```objectivec
@property (nonatomic, assign, readonly) CLLocationDegrees longitude;
```

### timestamp

Returns the UTC time of the waypoint, in seconds since epoch (January 1, 1970).

```objectivec
@property (nonatomic, assign, readonly) NSTimeInterval timestamp;
```

