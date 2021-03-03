# Vehicle Crash Detection

## App Integration

Follow the below steps to set up vehicle crash detection in you app.

### 1. Integrate the Sentiance SDK

If you haven't already integrated the Sentiance SDK, follow the steps in our [Getting Started](../sdk/getting-started/) guide to complete the integration. Once you have completed those steps, continue along with the steps documented below.

### 2. Check if Vehicle Crash Detection Is Supported

There are several reasons why vehicle crash detection may not be supported on the device. The two most common of these are:

* the feature is not enabled for your app;
* the device lacks the necessary sensors \(e.g. accelerometer\).

You can check to see whether vehicle crash detection is support on the device, as follows.

{% tabs %}
{% tab title="Android" %}
```java
Sentiance.getInstance(context).isVehicleCrashDetectionSupported(TripType.SDK_TRIP);
```
{% endtab %}

{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] isVehicleCrashDetectionSupported:SENTTripTypeSDK];
```
{% endtab %}
{% endtabs %}

As the Sentiance SDK supports both [automatic detections and manual trips](../sdk/appendix/controlled-detections/automatic-detections-with-forced-trips.md) \(i.e. explicitly starting and stopping a trip\), the availability of vehicle crash detection is also controlled at the level of the trip type. In the above example, we pass a trip type of `SDK_TRIP` or `SENTTripTypeSDK` to check if the feature is available for automatic trips. To check if it's available for manually started trips, pass `EXTERNAL_TRIP` or `SENTTripTypeExternal` instead.

### 3. Subscribe for Vehicle Crash Events

In order to be notified of vehicle crash events, you must set a listener that the SDK can invoke whenever it detects vehicle crashes.

{% tabs %}
{% tab title="Android" %}
```java
Sentiance.getInstance(context).setVehicleCrashListener(new VehicleCrashListener() {
    @Override
    public void onVehicleCrash(VehicleCrashEvent crashEvent) {
        // Handle the vehicle crash event
        
        long epochTimeMs = crashEvent.getTime();
        Location location = crashEvent.getLocation();
        Float speedAtImpact = crashEvent.getSpeedAtImpact();
        Float magnitude = crashEvent.getMagnitude();
        Float deltaV = crashEvent.getDeltaV();
        Integer confidence = crashEvent.getConfidence();
    }
});
```
{% endtab %}

{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] setVehicleCrashHandler:^(SENTVehicleCrashEvent *crashEvent) {
    // Handle the vehicle crash event
    
    NSDate *date = crashEvent.date;
    CLLocation *location = crashEvent.location;
    Float32 speedAtImpact = crashEvent.speedAtImpact;
    Float32 magnitude = crashEvent.magnitude;
    Float32 deltaV = crashEvent.deltaV;
    NSInteger confidence = crashEvent.confidence;
}];
```
{% endtab %}
{% endtabs %}

The crash event contains the time and location of the detected crash, in addition to a number of metrics to estimate the severity of the crash.

### 4. Test Your Integration

The final step is checking your integration, to make sure that your vehicle crash listener is properly set up to handle crash events. Add the following method call in your app to trigger a dummy crash event.

{% tabs %}
{% tab title="Android" %}
```java
Sentiance.getInstance(context).invokeDummyVehicleCrash();
```
{% endtab %}

{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] invokeDummyVehicleCrashHandler];
```
{% endtab %}
{% endtabs %}

This should invoke a dummy crash event, passing it to the listener that you previously set. You can then test how your app handles the event at runtime.

## Crash Report

A crash report contains contextual information pertaining to a crash event. This includes information specific to the crash, such as time, location, speed, and sensor data. It can also contain user timeline information before, during, and after the crash event, as well as weather and traffic data. A single crash event can produce one or more aggregative crash reports. Each new crash report is generated asynchronously as soon as new information is available on the Sentiance platform or on external data sources. So, we recommend to look for the latest file for a given crash event. 

Crash reports are securely stored on Amazon S3. Reports will be generated in client-specific root folders with the following directory structure:
```
s3://sentiance-u1-offloads/<CLIENT_APP_NAME>/crash_reports/<APP_ID>/<UTC_DATE>/<REPORT_ID>-<UTC_TIMESTAMP>.json.gz
```
* CLIENT_APP_NAME: The name of the client app (e.g. journeys)
* APP_ID: The client app ID (e.g. 0000xxxxxxxxxxxxxxxxxxx)
* UTC_DATE: The date of the crash event in UTC timezone
* REPORT_ID: A unique identifier for a crash report, belonging to a single crash event
* UTC_TIMESTAMP: Unix timestamp (UTC) in milliseconds of when the report was generated

The procedure to access the crash report files in Amazon s3 is the same as that of offload files. Please refer [here](../backend/offloads#connecting-to-the-offloads-amazon-s-3).

A single crash report file may consist multiple report segments. Each report segment contains different information related to the crash event.

* CRASH EVENT: This segment contains the most basic information about a crash event and is usually generated first and as soon as possible after a crash event occurs (though this may change in the subsequent reports due to the asynchronous nature of the Sentiance platform).
* TRANSPORTS:This segment contains information about one or more transports directly related to the crash event. Transports may include information like total distance traveled, trip waypoints, road types traveled, driving scores, and driving events.
* TIMELINE: This segment contains information about the user’s timeline before, during, and after a crash event. This may include either stationaries (venues/locations where the user remained static) or other transports.
* WEATHER: This segment contains information about the weather at the time and location of the crash event.
* TRAFFIC: This segment contains information about traffic conditions (traffic incidents and the traffic flow) at the time and location of the crash event, as well as after the crash.

Here you can find sample data for each of those segments. 

{% tabs %}
{% tab title="CRASH EVENT" %}
```java
{
    "reportId": "xxxx556a-XXXX-41cd-xxxx-3930936a875f",
    "reportSegments": [
        "CRASH_EVENT"
    ],
    "reportTier": 3,
    "userId": "5f3256cab1xxxxxxxxxxxxxxx",
    "appId": "000000000xxxxxxxxxxxxxxx",
    "correlationId": "c7a1xxxx-xxxx-xxxx-xxxx-91xxxxb144aa",
    "sessionId": "D43DXXXX-xxxx-xxxx-xxxx-E54FCXXXX2EA",
    "processingTime": 1600439157581,
    "crashEvent": {
        "timestamp": 1599564413382,
        "waypoint": {
            "location": {
                "latitude": 53.08163,
                "longitude": 9.98515,
                "horizontalAccuracy": 65,
                "verticalAccuracy": 2,
                "elevation": 4,
                "provider": "GPS"
            },
            "timestamp": 1599564468547,
            "base": 0,
            "speed": -1.0,
            "direction": -1
        },
        "sensorData": {
            "type": "ACCELEROMETER",
            "baseTimestamp": 1599564399613,
            "baseOffsets": [
                0,
                40,
                80,
                ...
            ],
            "measurements": [
                [
                    -0.028,
                    -0.063,
                    0.036,
                    ...
                ],
                [
                    -0.294,
                    -0.337,
                    -0.373,
                    ...
                ],
                [
                    -0.812,
                    -0.83,
                    -1.083,
                    ...
                ]
            ]
        },
        "timezoneOffset": 120,
        "maxMagnitude": 100,
        "confidence": 75
    },
    "timelineEvents": [],
    "weatherData": [],
    "trafficIncidentData": [],
    "trafficFlow": [],
    "transportEventId": null,
    "significantTransportMode": null,
    "significantStationaryIds": null
}```
{% endtab %}

{% tab title="TRANSPORTS" %}
```java
{
  "reportId": "0a93556a-7602-41cd-ae30-3930936a875f",
  "reportSegments": [
    "CRASH_EVENT",
    "TRANSPORTS"
  ],
  "reportTier": 3,
  "userId": "5f3256cab1xxxxxxxxxxxxxxx",
  "appId": "000000000xxxxxxxxxxxxxxx",    
  "correlationId": "c7a1xxxx-xxxx-xxxx-xxxx-91xxxxb144aa",
  "sessionId": "D43DXXXX-xxxx-xxxx-xxxx-E54FCXXXX2EA",
  "processingTime": 1600439159843,
  "crashEvent": {...},
  "timelineEvents": [
    {
      "timelineEventType": "com.sentiance.offloads.crash_report_aggregator.aggregated_crash_reports.AggregatedCrashReport$TimelineEvent$Transport",
      "timelineEvent": {
        "mode": "car",
        "distance": 4401,
        "waypoints": [
          {
            "location": {
                "latitude": 53.08163,
                "longitude": 9.98515,
                "horizontalAccuracy": 65,
                "verticalAccuracy": 2,
                "elevation": 4,
                "provider": "GPS"
            },
            "timestamp": 1599558857770
          },
          ...
        ],
        "trajectory": [
          {
            "location": {
              "latitude": 53.08163,
              "longitude": 9.98515,
              "horizontalAccuracy": null,
              "verticalAccuracy": null,
              "elevation": null,
              "provider": null
            },
            "timestamp": 1599564108000,
            "roadType": "service",
            "speedV2": 0,
            "speedV2Confidence": 0.95,
            "speedLimit": 50,
            "distance": 50.1
          },
          ...
        ],
        "behaviorScores": {
          "overall": 0.45,
          "focus": 1,
          "mounted": 0,
          "hardAccel": 0.95,
          "hardBrake": 0.95,
          "hardEvents": 0.81,
          "legalV2": 0.03,
          "hardTurn": 0.6,
          "smooth_V2": 0.51,
          "anticipativeV2": 0.85,
          "handheldCalling": 1,
          "handheldCalling_duration": 0,
          "handsfreeCalling": 0.11,
          "handsfreeCalling_duration": 86,
          "handlingWithoutCalling": 1,
          "handlingWithoutCallingDuration": 0,
          "attention": 0.7
        },
        "behaviorAnnotations": [
          {
            "behaviorAnnotationType": "com.sentiance.offloads.crash_report_aggregator.aggregated_crash_reports.AggregatedCrashReport$TimelineEvent$Transport$BehaviorAnnotation$AccelerationBehaviorAnnotation",
            "behaviorAnnotation": {
              "duration": 7233,
              "accelerationType": "ACCELERATE",
              "magnitude": 0.129,
              "behaviorAnnotationType": "ACCELERATION",
              "startTs": 1599564109238,
              "endTs": 1599564116471
            }
          },
          ...
        ],
        "occupantRole": "driver",
        "timelineEventType": "TRANSPORT",
        "eventId": "52d0f5cxxxxxxxxxxx78ee4a6cedcc73bcad3xxxxxxxxxxxd8f63c",
        "startTs": 1599564108000,
        "endTs": 1599564379000,
        "analysisType": "INDEPTH"
      }
    }
  ],
  "weatherData": [],
  "trafficIncidentData": [],
  "trafficFlow": [],
  "transportEventId": "52xxxxxxxxxxx578ee4a6cedcxxxxxxxxxxx33f0a441fxxxxxxxxxxxf63c",
  "significantTransportMode": true,
  "significantStationaryIds": []
}```
{% endtab %}

{% tab title="TIMELINE" %}
```java
{
  "reportId": "0a93556a-7602-41cd-ae30-3930936a875f",
  "reportSegments": [
    "CRASH_EVENT",
    "TIMELINE"
  ],
  "reportTier": 3,
  "userId": "5f3256cab1xxxxxxxxxxxxxxx",
  "appId": "000000000xxxxxxxxxxxxxxx",
  "correlationId": "c7a1xxxx-xxxx-xxxx-xxxx-91xxxxb144aa",
  "sessionId": "D43DXXXX-xxxx-xxxx-xxxx-E54FCXXXX2EA",  
  "processingTime": 1600769125013,
  "crashEvent": {...},
  "timelineEvents": [
    {
      "timelineEventType": "com.sentiance.offloads.crash_report_aggregator.aggregated_crash_reports.AggregatedCrashReport$TimelineEvent$Stationary",
      "timelineEvent": {
            "location": {
                "latitude": 53.08163,
                "longitude": 9.98515,
                "horizontalAccuracy": 65,
                "verticalAccuracy": 2,
                "elevation": 4,
                "provider": "GPS"
            },
        "city": "Lokeren",
        "country": "België / Belgique / Belgien",
        "significance": "HOME",
        "place": {
          "name": null,
          "categoryHierarchy": [
            "residential"
          ],
          "probability": null
        },
        "placeCandidates": [...],
        "timelineEventType": "STATIONARY",
        "eventId": "1e9xxxxxxxxxxxcb72279xxxxxxxxxxxxxxxxxxxxxxxxxxc444c",
        "startTs": 1599493920000,
        "endTs": 1599558857000,
        "analysisType": "INDEPTH"
      }
    },
    ...
  ],
  "weatherData": null,
  "trafficIncidentData": null,
  "trafficFlow": null,
  "transportEventId": null,
  "significantTransportMode": null,
  "significantStationaryIds": []
}```
{% endtab %}

{% tab title="WEATHER" %}
```java
{
  "reportId": "0a93556a-7602-41cd-ae30-3930936a875f",
  "reportSegments": [
    "CRASH_EVENT",
    "WEATHER"
  ],
  "reportTier": 3,
  "userId": "5f3256cab1xxxxxxxxxxxxxxx",
  "appId": "000000000xxxxxxxxxxxxxxx",
  "correlationId": "c7a1xxxx-xxxx-xxxx-xxxx-91xxxxb144aa",
  "sessionId": "D43DXXXX-xxxx-xxxx-xxxx-E54FCXXXX2EA",
  "processingTime": 1600769125013,
  "crashEvent": {...},
  "timelineEvents": null,
  "weatherData": [
    {
      "requestTime": 1599564582681,
      "observationTime": 1599564540000,
      "temperature": 18,
      "feelsLike": 18,
      "descriptions": [
        "Overcast"
      ],
      "windSpeed": 13,
      "windDegree": 220,
      "windDirection": "SW",
      "pressure": 1027,
      "precipitation": 0,
      "humidity": 0.83,
      "cloudcover": 1,
      "uvIndex": 5,
      "visibility": 10,
      "isDay": true,
      "solarAzimuthAngle": null,
      "solarZenithAngle": null,
      "solarGlare": null
    },
    ...
  ],
  "trafficIncidentData": null,
  "trafficFlow": null,
  "transportEventId": null,
  "significantTransportMode": null,
  "significantStationaryIds": null
}```
{% endtab %}

{% tab title="TRAFFIC" %}
```java
{
  "reportId": "cbd23837-ee43-453d-b790-ad0dc6bde03f",
  "reportSegments": [
    "CRASH_EVENT",
    "TRAFFIC"
  ],
  "reportTier": 3,
  "userId": "5f3256cab1xxxxxxxxxxxxxxx",
  "appId": "000000000xxxxxxxxxxxxxxx",
  "correlationId": "c7a1xxxx-xxxx-xxxx-xxxx-91xxxxb144aa",
  "sessionId": "D43DXXXX-xxxx-xxxx-xxxx-E54FCXXXX2EA",
  "processingTime": 1600850025293,
  "crashEvent": {...},
  "timelineEvents": null,
  "weatherData": null,
  "trafficIncidentData": [
    {
      "trafficIncidents": [
        {
            "location": {
                "latitude": 59.08163,
                "longitude": 3.72515,
                "horizontalAccuracy": 65,
                "verticalAccuracy": 2,
                "elevation": 4,
                "provider": "GPS"
          },
          "incidentType": "ROAD_CLOSED",
          "delayMagnitude": "UNDEFINED",
          "description": "closed",
          "cause": null,
          "roadsAffected": null,
          "fromRoad": "Berkenstraat",
          "toRoad": "Kattestraat"
        },
        ...
      ],
      "requestTime": 1600506586818
    },
  ],
  "trafficFlow": [
    {
      "roadType": "LOCAL_IMPORTANT",
      "currentSpeed": 21,
      "freeFlowSpeed": 33,
      "confidence": 0.8199999928474426,
      "path": [
        {
          "latitude": 59.07537,
          "longitude": 3.72688,
          "horizontalAccuracy": null,
          "verticalAccuracy": null,
          "elevation": null,
          "provider": null
        },
        ...
      ],
      "roadClosure": null,
      "requestTime": 1600506586939
    },
    ...
  ],
  "transportEventId": null,
  "significantTransportMode": null,
  "significantStationaryIds": null
}```
{% endtab %}


{% endtabs %}

The data model of the fields in the above sample segments of the crash report are explained in the attached file. 

{% file src="../.gitbook/assets/data-model-crash-reports.xlsx" caption="data model - crash report" %}
