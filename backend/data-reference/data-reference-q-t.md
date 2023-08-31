# Data Reference Q-T

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Objects
- [SegmentDefinition](#segmentdefinition)
- [SemanticTimeAggregate](#semantictimeaggregate)
- [SemanticTimeAggregateValue](#semantictimeaggregatevalue)
- [Stationary](#stationary)
- [StationaryFeedback](#stationaryfeedback)
- [StationaryIntervalPrediction](#stationaryintervalprediction)
- [StationaryLocation](#stationarylocation)
- [StationaryPrediction](#stationaryprediction)
- [StationaryTimeAggregate](#stationarytimeaggregate)
- [TimeWindowTransportHeatmaps](#timewindowtransportheatmaps)
- [TimeWindowUserCarBehaviorFeatures](#timewindowusercarbehaviorfeatures)
- [TrajectoryWaypoint](#trajectorywaypoint)
- [Transport](#transport)
- [TransportAddress](#transportaddress)
- [TransportAddresses](#transportaddresses)
- [TransportFeedback](#transportfeedback)
- [TransportHeatmaps](#transportheatmaps)
- [TransportIntervalPrediction](#transportintervalprediction)
- [TransportModeHeatmaps](#transportmodeheatmaps)
- [TransportPrediction](#transportprediction)
- [TransportTimeAggregate](#transporttimeaggregate)
- [TransportTrajectory](#transporttrajectory)
- [Trip](#trip)
- [TripConnection](#tripconnection)
- [TurnBehaviorAnnotation](#turnbehaviorannotation)

### SdkFlavor
**Kind**: ENUM

- **full**
- **offline_driving**
- **realtime_marketing**
- **offline_segmentation**
- **triggered_trips**

### SegmentDefinition
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single segment definition.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'SegmentDefinition' | True |
| id | String | Identifier for this segment. | True |
| version | Int | Version which will increase everytime minor changes or improvements happen to the calculation of this segment. | True |
| category | String | Category of this segment, if any. | True |
| subcategory | String | Subcategory of this segment, if any. | True |
| display_name | String | A displayable name for this segment. | True |
| description | String | A short description about this segment. | True |
| deprecated | Boolean | Flag that indicates if this segment will be removed in one of the following releases. Do not use segments that are marked deprecated for new development. | True |
| deprecated_at | String | Date when the segment will be removed. Default null. | True |


### SegmentDefinitionStatus
**Kind**: ENUM

- **ACTIVE**: The current active version of segment definitions.
- **ALPHA**: The next version of segment definitions, these will become active in the next release.
Identifies the release status of a segment definition.

### SegmentType
**Kind**: ENUM

- **GenericSegment**

### SemanticTime
**Kind**: ENUM

- **morning**
- **lunch**
- **afternoon**
- **evening**
- **night**
The user semantic time.

### SemanticTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregate' | True |
| morning | [SemanticTimeAggregateValue](data-reference-q-t.md#semantictimeaggregatevalue) |  | True |
| lunch | [SemanticTimeAggregateValue](data-reference-q-t.md#semantictimeaggregatevalue) |  | True |
| afternoon | [SemanticTimeAggregateValue](data-reference-q-t.md#semantictimeaggregatevalue) |  | True |
| evening | [SemanticTimeAggregateValue](data-reference-q-t.md#semantictimeaggregatevalue) |  | True |
| night | [SemanticTimeAggregateValue](data-reference-q-t.md#semantictimeaggregatevalue) |  | True |


### SemanticTimeAggregateDaysEnum
**Kind**: ENUM

- **all_days**: All days are used in the calculation of the aggregate.

### SemanticTimeAggregateValue
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregateValue' | True |
| semantic_time | [SemanticTime](data-reference-q-t.md#semantictime) |  | True |
| days | [SemanticTimeAggregateDaysEnum](data-reference-q-t.md#semantictimeaggregatedaysenum) |  | True |
| start | String | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 | True |
| end | String | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 | True |


### Stationary
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-l.md#ievent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-c-g.md#eventtype) | 'Stationary' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| duration | [BigInt](data-reference-a-b.md#bigint) |  | True |
| address | [Address](data-reference-a-b.md#address) |  | True |
| location | [StationaryLocation](data-reference-q-t.md#stationarylocation) |  | True |
| weather | [WeatherRange](data-reference-u-z.md#weatherrange) | Weather data associated with this event. | True |


### StationaryFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-l.md#ifeedback), [IEventFeedback](data-reference-h-l.md#ieventfeedback)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-c-g.md#feedbacktype) | 'StationaryFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |
| event_feedback | [EventFeedback](data-reference-c-g.md#eventfeedback) |  | True |
| stationary | [Stationary](data-reference-q-t.md#stationary) | The Stationary this feedback refers to. | True |


### StationaryIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-l.md#iprediction), [IEventPrediction](data-reference-h-l.md#ieventprediction), [IIntervalPrediction](data-reference-h-l.md#iintervalprediction)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-m-p.md#predictiontype) | 'StationaryIntervalPrediction' | True |
| probability | Float |  | True |
| event_type | [EventType](data-reference-c-g.md#eventtype) |  | True |
| start_interval | [PredictionInterval](data-reference-m-p.md#predictioninterval) |  | True |
| location | [StationaryLocation](data-reference-q-t.md#stationarylocation) |  | True |


### StationaryLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Holds more information about a stationary location.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'StationaryLocation' | True |
| significance | [LocationSignificance](data-reference-h-l.md#locationsignificance) | What this location means for the user, or the frequency it's being visited. | True |
| place | [LocationPlaceCandidate](data-reference-h-l.md#locationplacecandidate) |  | True |
| place_candidates | [LocationPlaceCandidate](data-reference-h-l.md#locationplacecandidate) |  | True |


### StationaryPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-l.md#ibranchevent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | True |
| end | String | Predicted end time of the event. | True |
| probability | Float | The probability of this prediction occurring. | True |
| type | [TreePredictionType](data-reference-q-t.md#treepredictiontype) | 'StationaryPrediction' | True |
| location_type | String |  | True |
| significance | String |  | True |
| place | [LocationPlaceCandidate](data-reference-h-l.md#locationplacecandidate) |  | True |


### StationaryTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-l.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-l.md#iuserattribute)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-u-z.md#userattributetype) | 'StationaryTimeAggregate' | True |
| period | [TimePeriod](data-reference-q-t.md#timeperiod) |  | True |
| duration | Float |  | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-l.md#locationsignificance) |  | True |


### TimePeriod
**Kind**: ENUM

- **week**

### TimeWindowTransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TimeWindowTransportHeatmaps' | True |
| car | [TransportModeHeatmaps](data-reference-q-t.md#transportmodeheatmaps) |  | True |


### TimeWindowUserCarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TimeWindowUserCarBehaviorFeatures' | True |
| phone_handling | Float | The average number of milliseconds this user is using his phone per hour in transport, during this time window. | True |
| distance | Int | Aggregated distance measured in meter for all car transports during this time window. | True |


### TrajectoryWaypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single waypoint in the augmented trajectory.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TrajectoryWaypoint' | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| timestamp | String |  | True |
| road_type | String |  | True |
| speed | Float | The average speed between this waypoint and the next waypoint, in km/h.<br><br><code>**Deprecation notice**</code><br>speed is deprecated.<br>Deprecated in favor of `speed_v2`. | True |
| speed_v2 | Float | The average speed between this waypoint and the next waypoint, in km/h. The difference with speed is that it has an improved estimation algorithm. | True |
| speed_v2_confidence | Float | This field gives confidence for our speed estimation based on the actual sampling rate of the waypoints and if there are multi-speed zones in the road segments between 2 actual waypoints. Values can range from 1.00-0.50.<br>1.00 will be assigned for those GPS waypoint with instantaneous speed.<br><br>0.95 will be assigned for those GPS waypoint with no instantaneous speed.<br><br>0.5 will be assigned for the augmented waypoints with the least confidence which includes those segments with more than 5 minutes between the real waypoints and where the average speed is within the (combined) speed limits of the trip but we still report speeding. | True |
| distance | Float | The distance in meter between the current waypoint and the next waypoint. | True |
| speed_limit | Float | Speed limit (in km/h) measured at this point in the trajectory as provided by our mapping data partners. | True |


### Transport
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-l.md#ievent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-c-g.md#eventtype) | 'Transport' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| session_ids | [String](data-reference-q-t.md#string) | A list of sessionIDs from the SDK that can be used to correlate data in sensor-offloads. | True |
| mode | [TransportMode](data-reference-q-t.md#transportmode) | The transport mode that was identified for this transport.  | True |
| distance | Int | Distance is in meters. | True |
| occupant_role | [TransportOccupantRole](data-reference-q-t.md#transportoccupantrole) |  | True |
| waypoints | [Waypoint](data-reference-u-z.md#waypoint) |  | True |
| trajectory | [TransportTrajectory](data-reference-q-t.md#transporttrajectory) |  | True |
| behavior_scores | [TransportBehaviorScores](data-reference-q-t.md#transportbehaviorscores) |  | True |
| behavior_annotations | [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation) |  | True |
| behavior_features | [TransportBehaviorFeatures](data-reference-q-t.md#transportbehaviorfeatures) |  | True |
| addresses | [TransportAddresses](data-reference-q-t.md#transportaddresses) |  | True |
| weather | [WeatherRange](data-reference-u-z.md#weatherrange) | Weather data associated with this event. | True |


### TransportAddress
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location. All the fields are retrieved from Open Street Map and all names are subject to whatever data has been provided in said map.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportAddress' | True |
| street | String |  | True |
| city | String |  | True |
| city_type | String |  | True |
| district | String |  | True |
| region | String |  | True |
| country | String |  | True |


### TransportAddresses
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Details of the origin and destination locations of a Transport.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| origin | [TransportAddress](data-reference-q-t.md#transportaddress) |  | True |
| destination | [TransportAddress](data-reference-q-t.md#transportaddress) |  | True |


### TransportBehaviorAnnotationType
**Kind**: ENUM

- **AccelerationBehaviorAnnotation**
- **BoundaryBehaviorAnnotation**
- **AnomalyBehaviorAnnotation**
- **TurnBehaviorAnnotation**
- **HandlingWithoutCallingAnnotation**
- **HandsfreeCallingAnnotation**
- **HandheldCallingAnnotation**
- **CrashAnnotation**

### TransportBehaviorFeatures
**Kind**: UNION

**Possible types**: [CarBehaviorFeatures](data-reference-c-g.md#carbehaviorfeatures)

### TransportBehaviorScores
**Kind**: UNION

**Possible types**: [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores)
The transport behavior scores we have detected during a transport. These scores are only available when the full trip is processed.

### TransportFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-l.md#ifeedback), [IEventFeedback](data-reference-h-l.md#ieventfeedback)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-c-g.md#feedbacktype) | 'TransportFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |
| event_feedback | [EventFeedback](data-reference-c-g.md#eventfeedback) |  | True |
| transport | [Transport](data-reference-q-t.md#transport) | The Transport this feedback refers to. | True |


### TransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Historically aggregated transport heatmaps.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportHeatmaps' | True |
| l30d | [TimeWindowTransportHeatmaps](data-reference-q-t.md#timewindowtransportheatmaps) | Transport heatmaps that are calculated using the last . | True |


### TransportIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-l.md#iprediction), [IEventPrediction](data-reference-h-l.md#ieventprediction), [IIntervalPrediction](data-reference-h-l.md#iintervalprediction)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-m-p.md#predictiontype) | 'TransportIntervalPrediction' | True |
| probability | Float |  | True |
| event_type | [EventType](data-reference-c-g.md#eventtype) |  | True |
| start_interval | [PredictionInterval](data-reference-m-p.md#predictioninterval) |  | True |
| mode | [TransportMode](data-reference-q-t.md#transportmode) |  | True |


### TransportMode
**Kind**: ENUM

- **car**: When we have identified a transport mode as car.
- **walking**: When we have identified a transport mode as walking.
- **biking**: When we have identified a transport mode as biking.
- **escooter**: When we have identified a transport mode as escooter.
- **train**: When we have identified a transport mode as train.
- **bus**: When we have identified a transport mode as bus.
- **tram**: When we have identified a transport mode as tram.
- **subway**: When we have identified a transport mode as subway/underground/metro.
- **boat**: When we have identified a transport mode as boat.
- **ferry**: When we have identified a transport mode as ferry.
- **motorcycle**: When we have identified a transport mode as motorcycle.
- **flight**: When we have identified a transport mode as flight. This is currently only available for processed results.
- **running**: When we have identified a transport mode as running. This is currently only available for preliminary results.
- **idle**: When a transport is identified as idle behavior.
- **other**: When a transport is identified as other transport mode.
- **insufficient_data**: When we don't have enough data to identify a transport mode.
The transport modes the platform supports.

### TransportModeCategory
**Kind**: ENUM

- **unknown**
- **healthy**
- **unhealthy**

### TransportModeHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportModeHeatmaps' | True |
| passed | [WeightedLocation](data-reference-u-z.md#weightedlocation) | An aggregate heatmap based on the amounts of times you have passed the coordinates during transports. | True |


### TransportOccupantRole
**Kind**: ENUM

- **driver**
- **passenger**
- **unknown**

### TransportPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-l.md#ibranchevent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | True |
| end | String | Predicted end time of the event. | True |
| probability | Float | The probability of this prediction occurring. | True |
| type | [TreePredictionType](data-reference-q-t.md#treepredictiontype) | 'TransportPrediction' | True |
| mode | String |  | True |


### TransportTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-l.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-l.md#iuserattribute)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-u-z.md#userattributetype) | 'TransportTimeAggregate' | True |
| period | [TimePeriod](data-reference-q-t.md#timeperiod) |  | True |
| duration | Float |  | True |
| mode | [TransportMode](data-reference-q-t.md#transportmode) |  | True |


### TransportTrajectory
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportTrajectory' | True |
| waypoints | [TrajectoryWaypoint](data-reference-q-t.md#trajectorywaypoint) |  | True |
| encoded | String | An encoded list of trajectory waypoints, [[lat,lon],[lat,lon]]. More info on polyline decoding: https://developers.google.com/maps/documentation/utilities/polylinealgorithm | True |


### TreePredictionType
**Kind**: ENUM

- **StationaryPrediction**: Prediction of a Stationary event.
- **TransportPrediction**: Prediction of a Transport event.

### Trip
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-l.md#ievent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-c-g.md#eventtype) | 'Trip' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| user_id | String |  | True |
| start | String |  | True |
| end | String |  | True |
| start_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| mode | String | Car, tram, walking, etc. | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | Type of processing applied on the trip.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| behavior_scores | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) |  | True |
| weather | [WeatherRange](data-reference-u-z.md#weatherrange) |  | True |


### TripConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access trips across all users.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TripConnection' | True |
| slice | [Trip](data-reference-q-t.md#trip) | The individual trips. Provide the right paging parameters to slice your result set. | True |


### TurnBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'TurnBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| maneuver | [TurnBehaviorAnnotationManeuver](data-reference-q-t.md#turnbehaviorannotationmaneuver) |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-b.md#behaviorannotationpathwaypoint) |  | True |
| magnitude | Float | The centripetal g-force you experience during turns, measured in (0.2*m)/s². Taking a turn at 60km/h will result in a higher magnitude compared to the same turn at 30 km/h | True |


### TurnBehaviorAnnotationManeuver
**Kind**: ENUM

- **left_turn**
- **right_turn**
- **roundabout**
- **lane_switch**

