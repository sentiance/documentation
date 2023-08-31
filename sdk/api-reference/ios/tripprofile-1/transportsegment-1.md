# SENTTripProcessingTransportSegment

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v5.12.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

SENTTripProcessingTransportSegment is used to define a portion of the trip having the same characteristics.

### vehicleMode

Returns the vehicle mode detected for the transport segment

```objectivec
@property (nonatomic) SENTTripProcessingVehicleMode vehicleMode;
```

### startDate

Returns the start date of the transport segment

```objectivec
@property (nonatomic, strong) NSDate *startDate;
```

### endDate

Returns the end date of the transport segment

```objectivec
@property (nonatomic, strong) NSDate *endDate;
```

### distance

Returns the distance in meters travelled during the timeframe of the transport segment

```objectivec
@property (nonatomic) double distance;
```

### averageSpeed

Returns the average speed in m/s of the user during the timeframe of the transport segment

```objectivec
@property (nonatomic) double averageSpeed;
```

### topSpeed

Returns the maximum speed in m/s detected during the timeframe of the transport segment

```objectivec
@property (nonatomic) double topSpeed;
```

### speedingPercentage

Returns the percentage of the transport segment the user's speed has been over the speed limit

```objectivec
@property (nonatomic) int speedingPercentage;
```

### hardEvents

Returns the array of hard events detected during the timeframe of the transport segment

```objectivec
@property (nonatomic, strong) NSMutableArray<SENTTripProcessingHardEvent *> *hardEvents;
```

{% hint style="info" %}
The hard event detection must be explicitly enabled via [`[SENTConfig isHardEventDetectionEnabled:]`](../sentconfig-1.md#ishardeventdetectionenabled) before initializing the SDK.
{% endhint %}
