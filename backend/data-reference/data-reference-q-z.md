# Data Reference Q-Z
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
- [User](#user)
- [UserAccountRole](#useraccountrole)
- [UserCarBehavior](#usercarbehavior)
- [UserCarBehaviorFeatures](#usercarbehaviorfeatures)
- [UserCarBehaviorScores](#usercarbehaviorscores)
- [UserHealth](#userhealth)
- [UserHealthScores](#userhealthscores)
- [UserSdkSettings](#usersdksettings)
- [UserSemanticTime](#usersemantictime)
- [UserTimeAggregatedScores](#usertimeaggregatedscores)
- [UsersConnection](#usersconnection)
- [Waypoint](#waypoint)
- [Weather](#weather)
- [WeatherRange](#weatherrange)
- [WeightedLocation](#weightedlocation)
- [WorkingTimeAggregate](#workingtimeaggregate)
- [ZoneCarBehaviorScores](#zonecarbehaviorscores)

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

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'SegmentDefinition' | False |
| id | String | Identifier for this segment. | False |
| version | Int | Version which will increase everytime minor changes or improvements happen to the calculation of this segment. | False |
| category | String | Category of this segment, if any. | False |
| subcategory | String | Subcategory of this segment, if any. | False |
| display_name | String | A displayable name for this segment. | False |
| description | String | A short description about this segment. | False |
| deprecated | Boolean | Flag that indicates if this segment will be removed in one of the following releases. Do not use segments that are marked deprecated for new development. | False |
| deprecated_at | String | Date when the segment will be removed. Default null. | False |


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


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregate' | False |
| morning | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | False |
| lunch | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | False |
| afternoon | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | False |
| evening | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | False |
| night | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | False |


### SemanticTimeAggregateDaysEnum
**Kind**: ENUM

- **all_days**: All days are used in the calculation of the aggregate.

### SemanticTimeAggregateValue
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregateValue' | False |
| semantic_time | [SemanticTime](data-reference-q-z.md#semantictime) |  | False |
| days | [SemanticTimeAggregateDaysEnum](data-reference-q-z.md#semantictimeaggregatedaysenum) |  | False |
| start | String | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 | False |
| end | String | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 | False |


### Stationary
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Stationary' | False |
| event_id | String |  | True |
| previous_event_id | String |  | False |
| next_event_id | String |  | False |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| latitude | Float |  | False |
| longitude | Float |  | False |
| duration | [BigInt](data-reference-a-g.md#bigint) |  | False |
| address | [Address](data-reference-a-g.md#address) |  | False |
| location | [StationaryLocation](data-reference-q-z.md#stationarylocation) |  | False |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. | False |


### StationaryFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IEventFeedback](data-reference-h-p.md#ieventfeedback)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'StationaryFeedback' | False |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | True |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | False |
| created | String | Time when this feedback entry was created. | False |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | False |
| event_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  | False |
| stationary | [Stationary](data-reference-q-z.md#stationary) | The Stationary this feedback refers to. | False |


### StationaryIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-p.md#iprediction), [IEventPrediction](data-reference-h-p.md#ieventprediction), [IIntervalPrediction](data-reference-h-p.md#iintervalprediction)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'StationaryIntervalPrediction' | False |
| probability | Float |  | False |
| event_type | [EventType](data-reference-a-g.md#eventtype) |  | False |
| start_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  | False |
| location | [StationaryLocation](data-reference-q-z.md#stationarylocation) |  | False |


### StationaryLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Holds more information about a stationary location.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'StationaryLocation' | False |
| significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) | What this location means for the user, or the frequency it's being visited. | False |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | False |
| place_candidates | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | False |


### StationaryPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-p.md#ibranchevent)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | False |
| end | String | Predicted end time of the event. | False |
| probability | Float | The probability of this prediction occurring. | False |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'StationaryPrediction' | False |
| location_type | String |  | False |
| significance | String |  | False |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | False |


### StationaryTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'StationaryTimeAggregate' | False |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | False |
| duration | Float |  | False |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |


### TimePeriod
**Kind**: ENUM

- **week**

### TimeWindowTransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TimeWindowTransportHeatmaps' | False |
| car | [TransportModeHeatmaps](data-reference-q-z.md#transportmodeheatmaps) |  | False |


### TimeWindowUserCarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TimeWindowUserCarBehaviorFeatures' | False |
| phone_handling | Float | The average number of milliseconds this user is using his phone per hour in transport, during this time window. | False |
| distance | Int | Aggregated distance measured in meter for all car transports during this time window. | False |


### TrajectoryWaypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single waypoint in the augmented trajectory.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TrajectoryWaypoint' | False |
| latitude | Float |  | False |
| longitude | Float |  | False |
| timestamp | String |  | False |
| road_type | String |  | False |
| speed | Float | The average speed between this waypoint and the next waypoint, in km/h.<br><br><code>**Deprecation notice**</code><br>speed is deprecated.<br>Deprecated in favor of `speed_v2`. | False |
| speed_v2 | Float | The average speed between this waypoint and the next waypoint, in km/h. The difference with speed is that it has an improved estimation algorithm. | False |
| speed_v2_confidence | Float | This field gives confidence for our speed estimation based on the actual sampling rate of the waypoints and if there are multi-speed zones in the road segments between 2 actual waypoints. Values can range from 1.00-0.50.<br>1.00 will be assigned for those GPS waypoint with instantaneous speed.<br><br>0.95 will be assigned for those GPS waypoint with no instantaneous speed.<br><br>0.5 will be assigned for the augmented waypoints with the least confidence which includes those segments with more than 5 minutes between the real waypoints and where the average speed is within the (combined) speed limits of the trip but we still report speeding. | False |
| distance | Float | The distance in meter between the current waypoint and the next waypoint. | False |
| speed_limit | Float | Speed limit (in km/h) measured at this point in the trajectory as provided by our mapping data partners. | False |


### Transport
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Transport' | False |
| event_id | String |  | True |
| previous_event_id | String |  | False |
| next_event_id | String |  | False |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| session_ids | [String](data-reference-q-z.md#string) | A list of sessionIDs from the SDK that can be used to correlate data in sensor-offloads. | False |
| mode | [TransportMode](data-reference-q-z.md#transportmode) | The transport mode that was identified for this transport.  | False |
| distance | Int | Distance is in meters. | False |
| occupant_role | [TransportOccupantRole](data-reference-q-z.md#transportoccupantrole) |  | False |
| waypoints | [Waypoint](data-reference-q-z.md#waypoint) |  | False |
| trajectory | [TransportTrajectory](data-reference-q-z.md#transporttrajectory) |  | False |
| behavior_scores | [TransportBehaviorScores](data-reference-q-z.md#transportbehaviorscores) |  | False |
| behavior_annotations | [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation) |  | False |
| behavior_features | [TransportBehaviorFeatures](data-reference-q-z.md#transportbehaviorfeatures) |  | False |
| addresses | [TransportAddresses](data-reference-q-z.md#transportaddresses) |  | False |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. | False |


### TransportAddress
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location. All the fields are retrieved from Open Street Map and all names are subject to whatever data has been provided in said map.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportAddress' | False |
| street | String |  | False |
| city | String |  | False |
| city_type | String |  | False |
| district | String |  | False |
| region | String |  | False |
| country | String |  | False |


### TransportAddresses
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Details of the origin and destination locations of a Transport.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| origin | [TransportAddress](data-reference-q-z.md#transportaddress) |  | False |
| destination | [TransportAddress](data-reference-q-z.md#transportaddress) |  | False |


### TransportBehaviorAnnotationType
**Kind**: ENUM

- **AccelerationBehaviorAnnotation**
- **BoundaryBehaviorAnnotation**
- **AnomalyBehaviorAnnotation**
- **TurnBehaviorAnnotation**
- **HandlingWithoutCallingAnnotation**
- **HandsfreeCallingAnnotation**
- **HandheldCallingAnnotation**

### TransportBehaviorFeatures
**Kind**: UNION

**Possible types**: [CarBehaviorFeatures](data-reference-a-g.md#carbehaviorfeatures)

### TransportBehaviorScores
**Kind**: UNION

**Possible types**: [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores)
The transport behavior scores we have detected during a transport. These scores are only available when the full trip is processed.

### TransportFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IEventFeedback](data-reference-h-p.md#ieventfeedback)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'TransportFeedback' | False |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | True |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | False |
| created | String | Time when this feedback entry was created. | False |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | False |
| event_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  | False |
| transport | [Transport](data-reference-q-z.md#transport) | The Transport this feedback refers to. | False |


### TransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Historically aggregated transport heatmaps.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportHeatmaps' | False |
| l30d | [TimeWindowTransportHeatmaps](data-reference-q-z.md#timewindowtransportheatmaps) | Transport heatmaps that are calculated using the last . | False |


### TransportIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-p.md#iprediction), [IEventPrediction](data-reference-h-p.md#ieventprediction), [IIntervalPrediction](data-reference-h-p.md#iintervalprediction)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'TransportIntervalPrediction' | False |
| probability | Float |  | False |
| event_type | [EventType](data-reference-a-g.md#eventtype) |  | False |
| start_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  | False |
| mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |


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


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportModeHeatmaps' | False |
| passed | [WeightedLocation](data-reference-q-z.md#weightedlocation) | An aggregate heatmap based on the amounts of times you have passed the coordinates during transports. | False |


### TransportOccupantRole
**Kind**: ENUM

- **driver**
- **passenger**
- **unknown**

### TransportPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-p.md#ibranchevent)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | False |
| end | String | Predicted end time of the event. | False |
| probability | Float | The probability of this prediction occurring. | False |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'TransportPrediction' | False |
| mode | String |  | False |


### TransportTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'TransportTimeAggregate' | False |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | False |
| duration | Float |  | False |
| mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |


### TransportTrajectory
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportTrajectory' | False |
| waypoints | [TrajectoryWaypoint](data-reference-q-z.md#trajectorywaypoint) |  | False |
| encoded | String | An encoded list of trajectory waypoints, [[lat,lon],[lat,lon]]. More info on polyline decoding: https://developers.google.com/maps/documentation/utilities/polylinealgorithm | False |


### TreePredictionType
**Kind**: ENUM

- **StationaryPrediction**: Prediction of a Stationary event.
- **TransportPrediction**: Prediction of a Transport event.

### Trip
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Trip' | False |
| event_id | String |  | True |
| previous_event_id | String |  | False |
| next_event_id | String |  | False |
| user_id | String |  | False |
| start | String |  | False |
| end | String |  | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| mode | String | Car, tram, walking, etc. | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | Type of processing applied on the trip.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| behavior_scores | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) |  | False |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) |  | False |


### TripConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access trips across all users.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TripConnection' | False |
| slice | [Trip](data-reference-q-z.md#trip) | The individual trips. Provide the right paging parameters to slice your result set. | False |


### TurnBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'TurnBehaviorAnnotation' | False |
| start | String |  | False |
| end | String |  | False |
| maneuver | [TurnBehaviorAnnotationManeuver](data-reference-q-z.md#turnbehaviorannotationmaneuver) |  | False |
| duration | Int | Duration is in milliseconds. | False |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | False |
| magnitude | Float | The centripetal g-force you experience during turns, measured in (0.2*m)/s². Taking a turn at 60km/h will result in a higher magnitude compared to the same turn at 30 km/h | False |


### TurnBehaviorAnnotationManeuver
**Kind**: ENUM

- **left_turn**
- **right_turn**
- **roundabout**
- **lane_switch**

### User
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](data-reference-h-p.md#iuser)
An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'User' | False |
| install_id | String | The unique identifier for active install id. | False |
| external_id | String | The external id that was linked to this person. | False |
| id | String | The unique identifier for this user. | False |
| can_login | Boolean |  | False |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| sdk | [UserSdkSettings](data-reference-q-z.md#usersdksettings) |  | False |
| application_id | String | The ID of the Application this user relates to. | False |
| application | [Application](data-reference-a-g.md#application) | The Application this user relates to. | False |
| custom_event_history | [CustomEvent](data-reference-a-g.md#customevent) | Custom Event History | False |
| event_history | [IEvent](data-reference-h-p.md#ievent) | An unordered list of events we have detected for this user. | False |
| car_behavior | [UserCarBehavior](data-reference-q-z.md#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. | False |
| aggregated_driving_scores | [UserTimeAggregatedScores](data-reference-q-z.md#usertimeaggregatedscores) |  | False |
| transport_heatmaps | [TransportHeatmaps](data-reference-q-z.md#transportheatmaps) | The aggregated transport heatmaps calculated over time.<br><br><code>**Deprecation notice**</code><br>transport_heatmaps is deprecated.<br>No longer used. | False |
| metadata | [JSON](data-reference-h-p.md#json) | All custom set metadata properties on this user. This is a JSON object with key->value pairs. | False |
| device | [DeviceInfo](data-reference-a-g.md#deviceinfo) | The last known active tracking device metadata | False |
| active_moments | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. | False |
| moment_history | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments we have detected for this user. | False |
| semantic_time | [UserSemanticTime](data-reference-q-z.md#usersemantictime) | The user's semantic time averaged over time. | False |
| anomaly_history | [IAnomaly](data-reference-h-p.md#ianomaly) | <br><code>**Deprecation notice**</code><br>anomaly_history is deprecated.<br>No longer relevant. | False |
| segments | [ISegment](data-reference-h-p.md#isegment) | An unordered list of segments that are detected for this user. | False |
| location_clusters | [LocationCluster](data-reference-h-p.md#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...) | False |
| location | [Waypoint](data-reference-q-z.md#waypoint) | The last known location we have for this user. | False |
| health | [UserHealth](data-reference-q-z.md#userhealth) | The historical health attributes. | False |
| attributes | [IUserAttribute](data-reference-h-p.md#iuserattribute) |  | False |
| predictions | [IPrediction](data-reference-h-p.md#iprediction) | Event/Moment predictions for this user<br><br><code>**Deprecation notice**</code><br>predictions is deprecated.<br>Please use `prediction_tree`. | False |
| prediction_tree | [PredictionTree](data-reference-h-p.md#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. | False |
| feedback | [IFeedback](data-reference-h-p.md#ifeedback) | Feedback on this user<br><br><code>**Deprecation notice**</code><br>feedback is deprecated.<br>Replaced by feedback_history | False |
| feedback_history | [IFeedback](data-reference-h-p.md#ifeedback) | Feedback on this user | False |


### UserAccountRole
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserAccountRole' | False |
| user_id | String |  | False |
| account_id | String |  | False |
| role | String |  | False |
| account | [Account](data-reference-a-g.md#account) |  | False |


### UserAttributeType
**Kind**: ENUM

- **TransportTimeAggregate**
- **CommuteTimeAggregate**
- **StationaryTimeAggregate**
- **WorkingTimeAggregate**

### UserCarBehavior
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical car behavior profile for a user. Note that the user must have driven for at least 50 km during this period for the scores to be computed.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehavior' | False |
| scores | [UserCarBehaviorScores](data-reference-q-z.md#usercarbehaviorscores) |  | False |
| features | [UserCarBehaviorFeatures](data-reference-q-z.md#usercarbehaviorfeatures) |  | False |


### UserCarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehaviorFeatures' | False |
| l7d | [TimeWindowUserCarBehaviorFeatures](data-reference-q-z.md#timewindowusercarbehaviorfeatures) | Recent features based on the transports we have analyzed in the last 7 days of data. | False |
| past | [TimeWindowUserCarBehaviorFeatures](data-reference-q-z.md#timewindowusercarbehaviorfeatures) | Historical features based on all transports we have available, excluding the last 7 days of data. | False |


### UserCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehaviorScores' | False |
| l7d | [ZoneCarBehaviorScores](data-reference-q-z.md#zonecarbehaviorscores) | Recent scores based on the transports we have analyzed in the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. | False |
| past | [ZoneCarBehaviorScores](data-reference-q-z.md#zonecarbehaviorscores) | Historical scores based on all transports we have analysed excluding the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. | False |


### UserHealth
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical health attributes.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserHealth' | False |
| scores | [UserHealthScores](data-reference-q-z.md#userhealthscores) |  | False |


### UserHealthScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

This scoring system is used to track an individuals health.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserHealthScores' | False |
| activity | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user health. It takes into account sport duration, walking/biking distance & walking/biking speed. A higher score means you are more active in regard to physical activity and exercise. | False |
| mobility | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user mobility, the higher the score, the more ability to pursue various activities in life. It combines the locations visited frequency, distance travelled and user action radius. It is independent of transport mode. | False |
| work_social | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user's social activities. It is calculated considering two components: the social score and work score. It takes into account how much time the user spends in locations, as well as how many locations the user visits. It is a measure of the number user social relationships together with their duration. It doesn't count user's home and work location, but remote work locations are considered. The higher the score, the more and the longer social interactions the user has. | False |


### UserRole
**Kind**: ENUM

- **developer**
- **spectator**
- **basic**
The roles a user can have, both on accounts and apps.

### UserSdkSettings
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

User overrides that are used by the SDK configuration. This is not the SDK configuration model.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserSdkSettings' | False |
| flavor | [SdkFlavor](data-reference-q-z.md#sdkflavor) | If null, app-wide settings or defaults are active. | False |
| killswitch_action | String |  | False |
| debug_logging | String | If null, app-wide settings or defaults are active. | False |


### UserSemanticTime
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserSemanticTime' | False |
| all_days | [SemanticTimeAggregate](data-reference-q-z.md#semantictimeaggregate) | Historical semantic time averaged for all days over all data. | False |


### UserTimeAggregatedScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport scores by month, week, day.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| all | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of all driving scores | False |
| month | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given month. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current month in UTC. | False |
| week | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given week. Enter date as YYYY-MM-DD. The day must always correspond to the Monday of the week you're trying to access. So for the third week of April, it will be 2019-04-15. The default value is the start of the current week in UTC. | False |
| day | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given day. Enter date as YYYY-MM-DD. It must correspond exactly to the date for which you want to access the aggregation. The default value is the current day in UTC. | False |
| quarter | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given quarter. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current quarter in UTC. Given date will be determine to derive the quarter, i.e 2021-09-27 belongs to quarter starting from 2021-07-01 | False |


### UserType
**Kind**: ENUM

- **User**: An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.
- **ControlUser**: A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

### UsersConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the user nodes

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UsersConnection' | False |
| slice | [IUser](data-reference-h-p.md#iuser) | The individual user nodes. Provide the right paging parameters to slice your response data. By default a slice holds 100 users, which you can increase to 1000. | False |
| paging | [Paging](data-reference-h-p.md#paging) |  | False |


### Waypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Waypoint' | False |
| latitude | Float | Location fix latitude. | False |
| longitude | Float | Location fix longitude. | False |
| timestamp | String |  | False |
| accuracy | Int | The estimated horizontal accuracy of this location, radial, in meters. | False |
| speed | Float | The instantaneous speed of the device, measured in meters per second. A negative value indicates an invalid speed. | False |
| altitude | Float | The altitude, measured in meters. Positive values indicate altitudes above sea level. Negative values indicate altitudes below sea level. | False |


### Weather
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| summary | String |  | False |
| icon | String |  | False |
| precipIntensity | Float |  | False |
| precipProbability | Float |  | False |
| temperature | Float |  | False |
| apparentTemperature | Float |  | False |
| dewPoint | Float |  | False |
| humidity | Float |  | False |
| pressure | Float |  | False |
| windSpeed | Float |  | False |
| windGust | Float |  | False |
| windBearing | Float |  | False |
| cloudCover | Float |  | False |
| uvIndex | Float |  | False |
| visibility | Float |  | False |
| ozone | Float |  | False |


### WeatherRange
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| start | [Weather](data-reference-q-z.md#weather) | Weather data at the start of this event. | False |
| end | [Weather](data-reference-q-z.md#weather) | Weather data at the end of this event. Could be the same as the start if the event was short-lived. | False |


### WeightedLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'WeightedLocation' | False |
| latitude | Float |  | False |
| longitude | Float |  | False |
| weight | Float |  | False |


### WorkingTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'WorkingTimeAggregate' | False |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | False |
| duration | Float |  | False |
| whereabouts | [WorkingTimeWhereabouts](data-reference-q-z.md#workingtimewhereabouts) |  | False |


### WorkingTimeWhereabouts
**Kind**: ENUM

- **all_locations**: When at either regular work or remote locations visited during working time, excluding transports.
- **at_work**: When working at work moment has been active, excluding nothing.
- **remote**: When working remote moment has been active, including transports in between.

### ZoneCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport behavior scores by road type

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ZoneCarBehaviorScores' | False |
| all | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on aggregated features across all zones. | False |
| total | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on the average of features per zone. | False |
| motorway | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in the motorway zones. | False |
| city | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in non-motorway city zones. | False |
| non_city | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in non-motorway non-city zones. | False |


