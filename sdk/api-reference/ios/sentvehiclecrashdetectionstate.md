# SENTVehicleCrashDetectionState

The detection state of a vehicle crash.

| Name                                                           | Description                                                                            |
| -------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| SENTVehicleCrashDetectionStateNoCandidateDetected              | A crash candidate has not been detected                                                |
| SENTVehicleCrashDetectionStateCandidateDetected                | A crash candidate has been detected                                                    |
| SENTVehicleCrashDetectionStateDiscardedWeakImpact              | The crash candidate has been discarded due to weak impact                              |
| SENTVehicleCrashDetectionStateDiscardedNonVehicleTransportMode | The crash candidate has been discarded due to non-vehicular transport mode             |
| SENTVehicleCrashDetectionStateDiscardedPreImpactNoise          | The crash candidate has been discarded due to too much noise in the pre-impact signal  |
| SENTVehicleCrashDetectionStateDiscardedPreImpactNoise          | The crash candidate has been discarded due to low pre-impact speed                     |
| SENTVehicleCrashDetectionStateDiscardedPostImpactNoise         | The crash candidate has been discarded due to too much noise in the post-impact signal |
| SENTVehicleCrashDetectionStateDiscardedHighSpeedAfterImpact    | The crash candidate has been discarded due to high post-impact speed                   |
