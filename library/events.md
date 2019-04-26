# Events

Situational events describe what a user is doing.

Events are derived from time, location and motion data.  
They are available as a timeseries of stationaries and transports with duration.

Is the user in transport? In a car? Or a train? Walking? What route?  
Is the user stationary? What store or business is at that location?  
Is the location a home or work location?  


### Stationary events

When a user is a few minutes stationary at a certain location, a stationary event will be available.

This stationary event is enriched with:

* The significance what this place means to the user based on historical data. Values: home, work, regular, nonregular, poi, new.
* Place/venue information like name and categories
* Basic address information like country, city and city\_type

#### Example

[Lookup the Stationary event in the data model reference](https://developers.sentiance.com/docs/data-model#Stationary)

```text
{
  "type": "Stationary",
  "start": "2017-02-22T08:34:50.785+01:00",
  "end": "2017-02-22T16:24:55.244+01:00",
  "analysis_type": "processed",
  "latitude": 51.19666,
  "longitude": 4.40816,
  "location": {
    "significance": "work",
    "place": {
      "name": "Sentiance HQ",
      "categories": [
        "office",
        "company"
      ]
    }
  },
  "address": {
    "country": "België - Belgique - Belgien",
    "city": "Antwerpen",
    "city_type": "city"
  }
}
```

### Transport events

When a user is not stationary at a location, the user is in Transport. For each of these transports a Transport event will be available.

Additional data derived from the sensor data: distance, transport mode, advanced map-matching is done to build an accurate trajectory and driving behavior analysis.

Transport modes: car, walking, biking, train, bus, tram, flight

Depending on SDK configuration, additional features are derived from the sensor data.   
Only available in full SDK configuration:

* behavior\_scores
* behavior\_features
* behavior\_annotations

#### Example

[Lookup the Transport event in the data model reference](https://developers.sentiance.com/docs/data-model#Transport)

```text
{
  "type": "Transport",
  "start": "2017-02-19T15:13:00+01:00",
  "end": "2017-02-19T17:05:00+01:00",
  "analysis_type": "processed",
  "mode": "car",
  "distance": 158773,
  "waypoints": [
    {
      "type": "Waypoint",
      "latitude": 52.35004,
      "longitude": 4.87475,
      "timestamp": "2017-02-19T15:13:31.968000+01:00",
      "accuracy": 25
    },
    ...
  ],
  "trajectory": {
    "type": "TransportTrajectory",
    "encoded": "quo~Hmaw\\ACW{... polyline encoding",
    "waypoints": [
      {
        "type": "TrajectoryWaypoint",
        "latitude": 52.35049,
        "longitude": 4.87463,
        "timestamp": "2017-02-19T15:13:29.967+01:00",
        "road_type": "tertiary",
        "speed": 0,
        "distance": 1.4,
        "speed_limit": 50
      },
      ...
    ]
  },
  "behavior_scores": {
    "type": "CarBehaviorScores",
    "overall": 0.67,
    "smooth": 0.91,
    "legal": 0.79,
    "anticipative": 0.3
  },
  "behavior_annotations": [
    {
      "type": "AccelerationBehaviorAnnotation",
      "start": "2017-02-19T15:43:32.161604+01:00",
      "end": "2017-02-19T15:43:38.851760+01:00",
      "duration": 6690,
      "acceleration": "accelerate",
      "magnitude": 0.096
    },
    {
      "type": "AccelerationBehaviorAnnotation",
      "start": "2017-02-19T15:50:42.146224+01:00",
      "end": "2017-02-19T15:50:55.042963+01:00",
      "duration": 12897,
      "acceleration": "brake",
      "magnitude": 0.261
    },
    ...
  ],
  "behavior_features": {
    "type": "CarBehaviorFeatures",
    "phone_handling": 70000,
    "distance_during_annotations": 27455
  }
}
```

