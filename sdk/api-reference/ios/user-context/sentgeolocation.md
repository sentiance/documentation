# SENTGeolocation

```objectivec
@interface SENTGeolocation : NSObject <NSSecureCoding, NSCopying>

@property (nonatomic, assign) CLLocationDegrees latitude;
@property (nonatomic, assign) CLLocationDegrees longitude;
@property (nonatomic, assign) NSInteger accuracyInMeters;

- (instancetype)initWithLatitude:(CLLocationDegrees)latitude longitude:(CLLocationDegrees)longitude accuracy:(CLLocationAccuracy)accuracy;

- (BOOL)isEqualToGeolocation:(SENTGeolocation *)geolocation;

@end
```
