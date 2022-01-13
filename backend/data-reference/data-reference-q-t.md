# Data Reference Q-T

## Objects

* [SegmentDefinition](broken-reference)
* [SemanticTimeAggregate](broken-reference)
* [SemanticTimeAggregateValue](broken-reference)
* [Stationary](broken-reference)
* [StationaryFeedback](broken-reference)
* [StationaryIntervalPrediction](broken-reference)
* [StationaryLocation](broken-reference)
* [StationaryPrediction](broken-reference)
* [StationaryTimeAggregate](broken-reference)
* [TimeWindowTransportHeatmaps](broken-reference)
* [TimeWindowUserCarBehaviorFeatures](broken-reference)
* [TrajectoryWaypoint](broken-reference)
* [Transport](broken-reference)
* [TransportAddress](broken-reference)
* [TransportAddresses](broken-reference)
* [TransportFeedback](broken-reference)
* [TransportHeatmaps](broken-reference)
* [TransportIntervalPrediction](broken-reference)
* [TransportModeHeatmaps](broken-reference)
* [TransportPrediction](broken-reference)
* [TransportTimeAggregate](broken-reference)
* [TransportTrajectory](broken-reference)
* [Trip](broken-reference)
* [TripConnection](broken-reference)
* [TurnBehaviorAnnotation](broken-reference)

### SdkFlavor

**Kind**: ENUM

* **full**
* **offline\_driving**
* **realtime\_marketing**
* **offline\_segmentation**
* **triggered\_trips**

### SegmentDefinition

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single segment definition.

| Property       | Type    | Description                                                                                                                                               | Nullable |
| -------------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type           | String  | 'SegmentDefinition'                                                                                                                                       | True     |
| id             | String  | Identifier for this segment.                                                                                                                              | True     |
| version        | Int     | Version which will increase everytime minor changes or improvements happen to the calculation of this segment.                                            | True     |
| category       | String  | Category of this segment, if any.                                                                                                                         | True     |
| subcategory    | String  | Subcategory of this segment, if any.                                                                                                                      | True     |
| display\_name  | String  | A displayable name for this segment.                                                                                                                      | True     |
| description    | String  | A short description about this segment.                                                                                                                   | True     |
| deprecated     | Boolean | Flag that indicates if this segment will be removed in one of the following releases. Do not use segments that are marked deprecated for new development. | True     |
| deprecated\_at | String  | Date when the segment will be removed. Default null.                                                                                                      | True     |

### SegmentDefinitionStatus

**Kind**: ENUM

* **ACTIVE**: The current active version of segment definitions.
* **ALPHA**: The next version of segment definitions, these will become active in the next release. Identifies the release status of a segment definition.

### SegmentType

**Kind**: ENUM

* **GenericSegment**

### SemanticTime

**Kind**: ENUM

* **morning**
* **lunch**
* **afternoon**
* **evening**
* **night** The user semantic time.

### SemanticTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property  | Type                       | Description             | Nullable |
| --------- | -------------------------- | ----------------------- | -------- |
| type      | String                     | 'SemanticTimeAggregate' | True     |
| morning   | SemanticTimeAggregateValue |                         | True     |
| lunch     | SemanticTimeAggregateValue |                         | True     |
| afternoon | SemanticTimeAggregateValue |                         | True     |
| evening   | SemanticTimeAggregateValue |                         | True     |
| night     | SemanticTimeAggregateValue |                         | True     |

### SemanticTimeAggregateDaysEnum

**Kind**: ENUM

* **all\_days**: All days are used in the calculation of the aggregate.

### SemanticTimeAggregateValue

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property       | Type                          | Description                                                                                                           | Nullable |
| -------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------- |
| type           | String                        | 'SemanticTimeAggregateValue'                                                                                          | True     |
| semantic\_time | SemanticTime                  |                                                                                                                       | True     |
| days           | SemanticTimeAggregateDaysEnum |                                                                                                                       | True     |
| start          | String                        | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 | True     |
| end            | String                        | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00   | True     |

### Stationary

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IEvent

| Property            | Type               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Nullable |
| ------------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                | EventType          | 'Stationary'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | True     |
| event\_id           | String             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | False    |
| previous\_event\_id | String             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| next\_event\_id     | String             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| start               | String             | <p>The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| end                 | String             | <p>The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | True     |
| start\_ts           | BigInt             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| end\_ts             | BigInt             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| analysis\_type      | AnalysisType       | <p>How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| latitude            | Float              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| longitude           | Float              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| duration            | BigInt             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| address             | Address            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| location            | StationaryLocation |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| weather             | WeatherRange       | Weather data associated with this event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |

### StationaryFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IFeedback, IEventFeedback

| Property         | Type          | Description                                                                        | Nullable |
| ---------------- | ------------- | ---------------------------------------------------------------------------------- | -------- |
| type             | FeedbackType  | 'StationaryFeedback'                                                               | True     |
| start            | String        | Start time the feedback relates to, sourced by the event, moment or user-provided. | False    |
| end              | String        | End time the feedback relates to, sourced by the event, moment or user-provided.   | True     |
| created          | String        | Time when this feedback entry was created.                                         | True     |
| projection\_time | String        | Time to provide when the feedback data was read from the API. ISO8601. Optional.   | True     |
| event\_feedback  | EventFeedback |                                                                                    | True     |
| stationary       | Stationary    | The Stationary this feedback refers to.                                            | True     |

### StationaryIntervalPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IPrediction, IEventPrediction, IIntervalPrediction

| Property        | Type               | Description                    | Nullable |
| --------------- | ------------------ | ------------------------------ | -------- |
| type            | PredictionType     | 'StationaryIntervalPrediction' | True     |
| probability     | Float              |                                | True     |
| event\_type     | EventType          |                                | True     |
| start\_interval | PredictionInterval |                                | True     |
| location        | StationaryLocation |                                | True     |

### StationaryLocation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Holds more information about a stationary location.

| Property          | Type                   | Description                                                                 | Nullable |
| ----------------- | ---------------------- | --------------------------------------------------------------------------- | -------- |
| type              | String                 | 'StationaryLocation'                                                        | True     |
| significance      | LocationSignificance   | What this location means for the user, or the frequency it's being visited. | True     |
| place             | LocationPlaceCandidate |                                                                             | True     |
| place\_candidates | LocationPlaceCandidate |                                                                             | True     |

### StationaryPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IBranchEvent

| Property       | Type                   | Description                                   | Nullable |
| -------------- | ---------------------- | --------------------------------------------- | -------- |
| start          | String                 | Predicted start time of the event.            | True     |
| end            | String                 | Predicted end time of the event.              | True     |
| probability    | Float                  | The probability of this prediction occurring. | True     |
| type           | TreePredictionType     | 'StationaryPrediction'                        | True     |
| location\_type | String                 |                                               | True     |
| significance   | String                 |                                               | True     |
| place          | LocationPlaceCandidate |                                               | True     |

### StationaryTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITimeAggregateAttribute, IUserAttribute

| Property               | Type                 | Description               | Nullable |
| ---------------------- | -------------------- | ------------------------- | -------- |
| type                   | UserAttributeType    | 'StationaryTimeAggregate' | True     |
| period                 | TimePeriod           |                           | True     |
| duration               | Float                |                           | True     |
| place\_category        | String               |                           | True     |
| location\_significance | LocationSignificance |                           | True     |

### TimePeriod

**Kind**: ENUM

* **week**

### TimeWindowTransportHeatmaps

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type                  | Description                   | Nullable |
| -------- | --------------------- | ----------------------------- | -------- |
| type     | String                | 'TimeWindowTransportHeatmaps' | True     |
| car      | TransportModeHeatmaps |                               | True     |

### TimeWindowUserCarBehaviorFeatures

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property        | Type   | Description                                                                                                     | Nullable |
| --------------- | ------ | --------------------------------------------------------------------------------------------------------------- | -------- |
| type            | String | 'TimeWindowUserCarBehaviorFeatures'                                                                             | True     |
| phone\_handling | Float  | The average number of milliseconds this user is using his phone per hour in transport, during this time window. | True     |
| distance        | Int    | Aggregated distance measured in meter for all car transports during this time window.                           | True     |

### TrajectoryWaypoint

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single waypoint in the augmented trajectory.

| Property              | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Nullable |
| --------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| type                  | String | 'TrajectoryWaypoint'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| latitude              | Float  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| longitude             | Float  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| timestamp             | String |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| road\_type            | String |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| speed                 | Float  | <p>The average speed between this waypoint and the next waypoint, in km/h.<br><br><strong><code>Deprecation notice</code></strong><br>speed is deprecated.<br>Deprecated in favor of <code>speed_v2</code>.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| speed\_v2             | Float  | The average speed between this waypoint and the next waypoint, in km/h. The difference with speed is that it has an improved estimation algorithm.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| speed\_v2\_confidence | Float  | <p>This field gives confidence for our speed estimation based on the actual sampling rate of the waypoints and if there are multi-speed zones in the road segments between 2 actual waypoints. Values can range from 1.00-0.50.<br>1.00 will be assigned for those GPS waypoint with instantaneous speed.<br><br>0.95 will be assigned for those GPS waypoint with no instantaneous speed.<br><br>0.5 will be assigned for the augmented waypoints with the least confidence which includes those segments with more than 5 minutes between the real waypoints and where the average speed is within the (combined) speed limits of the trip but we still report speeding.</p> | True     |
| distance              | Float  | The distance in meter between the current waypoint and the next waypoint.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| speed\_limit          | Float  | Speed limit (in km/h) measured at this point in the trajectory as provided by our mapping data partners.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | True     |

### Transport

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IEvent

| Property              | Type                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Nullable |
| --------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                  | EventType                    | 'Transport'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| event\_id             | String                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | False    |
| previous\_event\_id   | String                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| next\_event\_id       | String                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| start                 | String                       | <p>The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| end                   | String                       | <p>The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | True     |
| start\_ts             | BigInt                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| end\_ts               | BigInt                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| analysis\_type        | AnalysisType                 | <p>How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| session\_ids          | String                       | A list of sessionIDs from the SDK that can be used to correlate data in sensor-offloads.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| mode                  | TransportMode                | The transport mode that was identified for this transport.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | True     |
| distance              | Int                          | Distance is in meters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | True     |
| occupant\_role        | TransportOccupantRole        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| waypoints             | Waypoint                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| trajectory            | TransportTrajectory          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| behavior\_scores      | TransportBehaviorScores      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| behavior\_annotations | ITransportBehaviorAnnotation |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| behavior\_features    | TransportBehaviorFeatures    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| addresses             | TransportAddresses           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| weather               | WeatherRange                 | Weather data associated with this event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |

### TransportAddress

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location. All the fields are retrieved from Open Street Map and all names are subject to whatever data has been provided in said map.

| Property   | Type   | Description        | Nullable |
| ---------- | ------ | ------------------ | -------- |
| type       | String | 'TransportAddress' | True     |
| street     | String |                    | True     |
| city       | String |                    | True     |
| city\_type | String |                    | True     |
| district   | String |                    | True     |
| region     | String |                    | True     |
| country    | String |                    | True     |

### TransportAddresses

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Details of the origin and destination locations of a Transport.

| Property    | Type             | Description | Nullable |
| ----------- | ---------------- | ----------- | -------- |
| origin      | TransportAddress |             | True     |
| destination | TransportAddress |             | True     |

### TransportBehaviorAnnotationType

**Kind**: ENUM

* **AccelerationBehaviorAnnotation**
* **BoundaryBehaviorAnnotation**
* **AnomalyBehaviorAnnotation**
* **TurnBehaviorAnnotation**
* **HandlingWithoutCallingAnnotation**
* **HandsfreeCallingAnnotation**
* **HandheldCallingAnnotation**

### TransportBehaviorFeatures

**Kind**: UNION

**Possible types**: CarBehaviorFeatures

### TransportBehaviorScores

**Kind**: UNION

**Possible types**: CarBehaviorScores The transport behavior scores we have detected during a transport. These scores are only available when the full trip is processed.

### TransportFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IFeedback, IEventFeedback

| Property         | Type          | Description                                                                        | Nullable |
| ---------------- | ------------- | ---------------------------------------------------------------------------------- | -------- |
| type             | FeedbackType  | 'TransportFeedback'                                                                | True     |
| start            | String        | Start time the feedback relates to, sourced by the event, moment or user-provided. | False    |
| end              | String        | End time the feedback relates to, sourced by the event, moment or user-provided.   | True     |
| created          | String        | Time when this feedback entry was created.                                         | True     |
| projection\_time | String        | Time to provide when the feedback data was read from the API. ISO8601. Optional.   | True     |
| event\_feedback  | EventFeedback |                                                                                    | True     |
| transport        | Transport     | The Transport this feedback refers to.                                             | True     |

### TransportHeatmaps

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Historically aggregated transport heatmaps.

| Property | Type                        | Description                                             | Nullable |
| -------- | --------------------------- | ------------------------------------------------------- | -------- |
| type     | String                      | 'TransportHeatmaps'                                     | True     |
| l30d     | TimeWindowTransportHeatmaps | Transport heatmaps that are calculated using the last . | True     |

### TransportIntervalPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IPrediction, IEventPrediction, IIntervalPrediction

| Property        | Type               | Description                   | Nullable |
| --------------- | ------------------ | ----------------------------- | -------- |
| type            | PredictionType     | 'TransportIntervalPrediction' | True     |
| probability     | Float              |                               | True     |
| event\_type     | EventType          |                               | True     |
| start\_interval | PredictionInterval |                               | True     |
| mode            | TransportMode      |                               | True     |

### TransportMode

**Kind**: ENUM

* **car**: When we have identified a transport mode as car.
* **walking**: When we have identified a transport mode as walking.
* **biking**: When we have identified a transport mode as biking.
* **escooter**: When we have identified a transport mode as escooter.
* **train**: When we have identified a transport mode as train.
* **bus**: When we have identified a transport mode as bus.
* **tram**: When we have identified a transport mode as tram.
* **subway**: When we have identified a transport mode as subway/underground/metro.
* **boat**: When we have identified a transport mode as boat.
* **ferry**: When we have identified a transport mode as ferry.
* **motorcycle**: When we have identified a transport mode as motorcycle.
* **flight**: When we have identified a transport mode as flight. This is currently only available for processed results.
* **running**: When we have identified a transport mode as running. This is currently only available for preliminary results.
* **idle**: When a transport is identified as idle behavior.
* **other**: When a transport is identified as other transport mode.
* **insufficient\_data**: When we don't have enough data to identify a transport mode. The transport modes the platform supports.

### TransportModeCategory

**Kind**: ENUM

* **unknown**
* **healthy**
* **unhealthy**

### TransportModeHeatmaps

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type             | Description                                                                                           | Nullable |
| -------- | ---------------- | ----------------------------------------------------------------------------------------------------- | -------- |
| type     | String           | 'TransportModeHeatmaps'                                                                               | True     |
| passed   | WeightedLocation | An aggregate heatmap based on the amounts of times you have passed the coordinates during transports. | True     |

### TransportOccupantRole

**Kind**: ENUM

* **driver**
* **passenger**
* **unknown**

### TransportPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IBranchEvent

| Property    | Type               | Description                                   | Nullable |
| ----------- | ------------------ | --------------------------------------------- | -------- |
| start       | String             | Predicted start time of the event.            | True     |
| end         | String             | Predicted end time of the event.              | True     |
| probability | Float              | The probability of this prediction occurring. | True     |
| type        | TreePredictionType | 'TransportPrediction'                         | True     |
| mode        | String             |                                               | True     |

### TransportTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITimeAggregateAttribute, IUserAttribute

| Property | Type              | Description              | Nullable |
| -------- | ----------------- | ------------------------ | -------- |
| type     | UserAttributeType | 'TransportTimeAggregate' | True     |
| period   | TimePeriod        |                          | True     |
| duration | Float             |                          | True     |
| mode     | TransportMode     |                          | True     |

### TransportTrajectory

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property  | Type               | Description                                                                                                                                                                     | Nullable |
| --------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type      | String             | 'TransportTrajectory'                                                                                                                                                           | True     |
| waypoints | TrajectoryWaypoint |                                                                                                                                                                                 | True     |
| encoded   | String             | An encoded list of trajectory waypoints, \[\[lat,lon],\[lat,lon]]. More info on polyline decoding: https://developers.google.com/maps/documentation/utilities/polylinealgorithm | True     |

### TreePredictionType

**Kind**: ENUM

* **StationaryPrediction**: Prediction of a Stationary event.
* **TransportPrediction**: Prediction of a Transport event.

### Trip

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IEvent

| Property            | Type              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Nullable |
| ------------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                | EventType         | 'Trip'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| event\_id           | String            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | False    |
| previous\_event\_id | String            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| next\_event\_id     | String            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| user\_id            | String            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| start               | String            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| end                 | String            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| start\_ts           | BigInt            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| end\_ts             | BigInt            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| mode                | String            | Car, tram, walking, etc.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| analysis\_type      | AnalysisType      | <p>Type of processing applied on the trip.<br><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| behavior\_scores    | CarBehaviorScores |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |
| weather             | WeatherRange      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | True     |

### TripConnection

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access trips across all users.

| Property | Type   | Description                                                                         | Nullable |
| -------- | ------ | ----------------------------------------------------------------------------------- | -------- |
| type     | String | 'TripConnection'                                                                    | True     |
| slice    | Trip   | The individual trips. Provide the right paging parameters to slice your result set. | True     |

### TurnBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITransportBehaviorAnnotation

| Property  | Type                            | Description                                                                                                                                                                  | Nullable |
| --------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type      | TransportBehaviorAnnotationType | 'TurnBehaviorAnnotation'                                                                                                                                                     | True     |
| start     | String                          |                                                                                                                                                                              | True     |
| end       | String                          |                                                                                                                                                                              | True     |
| maneuver  | TurnBehaviorAnnotationManeuver  |                                                                                                                                                                              | True     |
| duration  | Int                             | Duration is in milliseconds.                                                                                                                                                 | True     |
| path      | BehaviorAnnotationPathWaypoint  |                                                                                                                                                                              | True     |
| magnitude | Float                           | The centripetal g-force you experience during turns, measured in (0.2\*m)/s². Taking a turn at 60km/h will result in a higher magnitude compared to the same turn at 30 km/h | True     |

### TurnBehaviorAnnotationManeuver

**Kind**: ENUM

* **left\_turn**
* **right\_turn**
* **roundabout**
* **lane\_switch**
