# SENTTripProcessingTripProfile

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v5.12.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

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
