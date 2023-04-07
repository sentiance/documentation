# SENTVehicleCrashEvent

Represents a vehicle crash event detected by the Sentiance SDK.

### date

Returns the date of the crash in the UTC

```
@property (strong, nonatomic) NSDate *date;
```

### location

Returns the last known location prior to the crash.

```
@property (strong, nonatomic) CLLocation *location;
```

### magnitude

Returns the magnitude of the crash event in m/s2.

```
@property (assign) Float32 magnitude;
```

### deltaV

Returns the delta-v estimated over the peak duration, in m/s.

```
@property (assign) Float32 deltaV;
```

### speedAtImpact

Returns the inferred speed at the moment of impact, in m/s.

```
@property (assign) Float32 speedAtImpact;
```

### confidence

Returns a confidence value between 0 and 100.

```
@property (assign) NSInteger confidence;
```

### precedingLocations

Returns a list of recent locations that lead up to this crash. Locations are ordered from oldest to most recent.

```
@property (strong, nonatomic) NSArray<CLLocation *> *precedingLocations;
```

