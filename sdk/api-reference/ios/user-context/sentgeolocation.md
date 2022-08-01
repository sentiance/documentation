# SENTGeolocation

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```objectivec
@interface SENTGeolocation : NSObject <NSSecureCoding, NSCopying>

@property (nonatomic, assign) CLLocationDegrees latitude;
@property (nonatomic, assign) CLLocationDegrees longitude;
@property (nonatomic, assign) NSInteger accuracyInMeters;

- (instancetype)initWithLatitude:(CLLocationDegrees)latitude longitude:(CLLocationDegrees)longitude accuracy:(CLLocationAccuracy)accuracy;

- (BOOL)isEqualToGeolocation:(SENTGeolocation *)geolocation;

@end
```
