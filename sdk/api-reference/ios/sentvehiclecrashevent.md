# SENTVehicleCrashEvent

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Represents a vehicle crash event detected by the Sentiance SDK.

### date

Returns the date of the crash in the UTC

```text
@property (strong, nonatomic) NSDate *date;
```

### location

Returns the last known location prior to the crash.

```text
@property (strong, nonatomic) CLLocation *location;
```

### magnitude

Returns the magnitude of the crash event in m/s2.

```text
@property (assign) Float32 magnitude;
```

### deltaV

Returns the delta-v estimated over the peak duration, in m/s.

```text
@property (assign) Float32 deltaV;
```

### speedAtImpact

Returns the inferred speed at the moment of impact, in m/s.

```text
@property (assign) Float32 speedAtImpact;
```

### confidence

Returns a confidence value between 0 and 100.

```text
@property (assign) NSInteger confidence;
```

