# SENTTripProcessingHardEvent

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v5.12.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

Hard events are acceleration events detected over a certain threshold of velocity.&#x20;

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
