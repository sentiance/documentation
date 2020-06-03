# SENTTripProcessingTripProfile

SENTTripProcessingTripProfile defines the profiling information about a trip that has finished. The profiling details are stored as a collection of SENTTripProcessingTransportSegment objects.

### tripId

The unique identifier associated with the trip

```objectivec
@property (nonatomic, readonly) NSString *tripId;
```

### transportSegments

The array of [SENTTripProcessingTransportSegment](transportsegment-1.md) objects detected during the trip

```objectivec
@property (nonatomic, strong) NSArray <SENTTripProcessingTransportSegment *> *transportSegments;
```

