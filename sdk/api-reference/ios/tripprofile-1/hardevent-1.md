# SENTTripProcessingHardEvent

Hard events are acceleration events detected over a certain threshold of velocity. 

### date

Returns the device date that the hard event has occurred.

```objectivec
@property (nonatomic, strong, readonly) NSDate *date;
```

### magnitude

Defines the acceleration velocity in m/s2.

```objectivec
@property (nonatomic, readonly) double magnitude;
```

