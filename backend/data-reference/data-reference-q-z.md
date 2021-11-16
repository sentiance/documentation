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
| morning | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | True |
| lunch | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | True |
| afternoon | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | True |
| evening | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | True |
| night | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  | True |


### SemanticTimeAggregateDaysEnum
**Kind**: ENUM

- **all_days**: All days are used in the calculation of the aggregate.

### SemanticTimeAggregateValue
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregateValue' | True |
| semantic_time | [SemanticTime](data-reference-q-z.md#semantictime) |  | True |
| days | [SemanticTimeAggregateDaysEnum](data-reference-q-z.md#semantictimeaggregatedaysenum) |  | True |
| start | String | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 | True |
| end | String | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 | True |


### Stationary
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Stationary' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| duration | [BigInt](data-reference-a-g.md#bigint) |  | True |
| address | [Address](data-reference-a-g.md#address) |  | True |
| location | [StationaryLocation](data-reference-q-z.md#stationarylocation) |  | True |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. | True |


### StationaryFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IEventFeedback](data-reference-h-p.md#ieventfeedback)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'StationaryFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |
| event_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  | True |
| stationary | [Stationary](data-reference-q-z.md#stationary) | The Stationary this feedback refers to. | True |


### StationaryIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-p.md#iprediction), [IEventPrediction](data-reference-h-p.md#ieventprediction), [IIntervalPrediction](data-reference-h-p.md#iintervalprediction)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'StationaryIntervalPrediction' | True |
| probability | Float |  | True |
| event_type | [EventType](data-reference-a-g.md#eventtype) |  | True |
| start_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  | True |
| location | [StationaryLocation](data-reference-q-z.md#stationarylocation) |  | True |


### StationaryLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Holds more information about a stationary location.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'StationaryLocation' | True |
| significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) | What this location means for the user, or the frequency it's being visited. | True |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | True |
| place_candidates | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | True |


### StationaryPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-p.md#ibranchevent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | True |
| end | String | Predicted end time of the event. | True |
| probability | Float | The probability of this prediction occurring. | True |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'StationaryPrediction' | True |
| location_type | String |  | True |
| significance | String |  | True |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | True |


### StationaryTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'StationaryTimeAggregate' | True |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | True |
| duration | Float |  | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |


### TimePeriod
**Kind**: ENUM

- **week**

### TimeWindowTransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TimeWindowTransportHeatmaps' | True |
| car | [TransportModeHeatmaps](data-reference-q-z.md#transportmodeheatmaps) |  | True |


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

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Transport' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| session_ids | [String](data-reference-q-z.md#string) | A list of sessionIDs from the SDK that can be used to correlate data in sensor-offloads. | True |
| mode | [TransportMode](data-reference-q-z.md#transportmode) | The transport mode that was identified for this transport.  | True |
| distance | Int | Distance is in meters. | True |
| occupant_role | [TransportOccupantRole](data-reference-q-z.md#transportoccupantrole) |  | True |
| waypoints | [Waypoint](data-reference-q-z.md#waypoint) |  | True |
| trajectory | [TransportTrajectory](data-reference-q-z.md#transporttrajectory) |  | True |
| behavior_scores | [TransportBehaviorScores](data-reference-q-z.md#transportbehaviorscores) |  | True |
| behavior_annotations | [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation) |  | True |
| behavior_features | [TransportBehaviorFeatures](data-reference-q-z.md#transportbehaviorfeatures) |  | True |
| addresses | [TransportAddresses](data-reference-q-z.md#transportaddresses) |  | True |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. | True |


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
| origin | [TransportAddress](data-reference-q-z.md#transportaddress) |  | True |
| destination | [TransportAddress](data-reference-q-z.md#transportaddress) |  | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'TransportFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |
| event_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  | True |
| transport | [Transport](data-reference-q-z.md#transport) | The Transport this feedback refers to. | True |


### TransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Historically aggregated transport heatmaps.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportHeatmaps' | True |
| l30d | [TimeWindowTransportHeatmaps](data-reference-q-z.md#timewindowtransportheatmaps) | Transport heatmaps that are calculated using the last . | True |


### TransportIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-p.md#iprediction), [IEventPrediction](data-reference-h-p.md#ieventprediction), [IIntervalPrediction](data-reference-h-p.md#iintervalprediction)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'TransportIntervalPrediction' | True |
| probability | Float |  | True |
| event_type | [EventType](data-reference-a-g.md#eventtype) |  | True |
| start_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  | True |
| mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |


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
| passed | [WeightedLocation](data-reference-q-z.md#weightedlocation) | An aggregate heatmap based on the amounts of times you have passed the coordinates during transports. | True |


### TransportOccupantRole
**Kind**: ENUM

- **driver**
- **passenger**
- **unknown**

### TransportPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-p.md#ibranchevent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | True |
| end | String | Predicted end time of the event. | True |
| probability | Float | The probability of this prediction occurring. | True |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'TransportPrediction' | True |
| mode | String |  | True |


### TransportTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'TransportTimeAggregate' | True |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | True |
| duration | Float |  | True |
| mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |


### TransportTrajectory
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TransportTrajectory' | True |
| waypoints | [TrajectoryWaypoint](data-reference-q-z.md#trajectorywaypoint) |  | True |
| encoded | String | An encoded list of trajectory waypoints, [[lat,lon],[lat,lon]]. More info on polyline decoding: https://developers.google.com/maps/documentation/utilities/polylinealgorithm | True |


### TreePredictionType
**Kind**: ENUM

- **StationaryPrediction**: Prediction of a Stationary event.
- **TransportPrediction**: Prediction of a Transport event.

### Trip
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Trip' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| user_id | String |  | True |
| start | String |  | True |
| end | String |  | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| mode | String | Car, tram, walking, etc. | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | Type of processing applied on the trip.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| behavior_scores | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) |  | True |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) |  | True |


### TripConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access trips across all users.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'TripConnection' | True |
| slice | [Trip](data-reference-q-z.md#trip) | The individual trips. Provide the right paging parameters to slice your result set. | True |


### TurnBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'TurnBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| maneuver | [TurnBehaviorAnnotationManeuver](data-reference-q-z.md#turnbehaviorannotationmaneuver) |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | True |
| magnitude | Float | The centripetal g-force you experience during turns, measured in (0.2*m)/s². Taking a turn at 60km/h will result in a higher magnitude compared to the same turn at 30 km/h | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'User' | True |
| install_id | String | The unique identifier for active install id. | True |
| external_id | String | The external id that was linked to this person. | True |
| id | String | The unique identifier for this user. | True |
| can_login | Boolean |  | True |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| sdk | [UserSdkSettings](data-reference-q-z.md#usersdksettings) |  | True |
| application_id | String | The ID of the Application this user relates to. | True |
| application | [Application](data-reference-a-g.md#application) | The Application this user relates to. | True |
| custom_event_history | [CustomEvent](data-reference-a-g.md#customevent) | Custom Event History | True |
| event_history | [IEvent](data-reference-h-p.md#ievent) | An unordered list of events we have detected for this user. | True |
| car_behavior | [UserCarBehavior](data-reference-q-z.md#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. | True |
| aggregated_driving_scores | [UserTimeAggregatedScores](data-reference-q-z.md#usertimeaggregatedscores) |  | True |
| transport_heatmaps | [TransportHeatmaps](data-reference-q-z.md#transportheatmaps) | The aggregated transport heatmaps calculated over time.<br><br><code>**Deprecation notice**</code><br>transport_heatmaps is deprecated.<br>No longer used. | True |
| metadata | [JSON](data-reference-h-p.md#json) | All custom set metadata properties on this user. This is a JSON object with key->value pairs. | True |
| device | [DeviceInfo](data-reference-a-g.md#deviceinfo) | The last known active tracking device metadata | True |
| active_moments | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. | True |
| moment_history | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments we have detected for this user. | True |
| semantic_time | [UserSemanticTime](data-reference-q-z.md#usersemantictime) | The user's semantic time averaged over time. | True |
| anomaly_history | [IAnomaly](data-reference-h-p.md#ianomaly) | <br><code>**Deprecation notice**</code><br>anomaly_history is deprecated.<br>No longer relevant. | True |
| segments | [ISegment](data-reference-h-p.md#isegment) | An unordered list of segments that are detected for this user. | True |
| location_clusters | [LocationCluster](data-reference-h-p.md#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...) | True |
| location | [Waypoint](data-reference-q-z.md#waypoint) | The last known location we have for this user. | True |
| health | [UserHealth](data-reference-q-z.md#userhealth) | The historical health attributes. | True |
| attributes | [IUserAttribute](data-reference-h-p.md#iuserattribute) |  | True |
| predictions | [IPrediction](data-reference-h-p.md#iprediction) | Event/Moment predictions for this user<br><br><code>**Deprecation notice**</code><br>predictions is deprecated.<br>Please use `prediction_tree`. | True |
| prediction_tree | [PredictionTree](data-reference-h-p.md#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. | True |
| feedback | [IFeedback](data-reference-h-p.md#ifeedback) | Feedback on this user<br><br><code>**Deprecation notice**</code><br>feedback is deprecated.<br>Replaced by feedback_history | True |
| feedback_history | [IFeedback](data-reference-h-p.md#ifeedback) | Feedback on this user | True |


### UserAccountRole
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserAccountRole' | True |
| user_id | String |  | True |
| account_id | String |  | True |
| role | String |  | True |
| account | [Account](data-reference-a-g.md#account) |  | True |


### UserAttributeType
**Kind**: ENUM

- **TransportTimeAggregate**
- **CommuteTimeAggregate**
- **StationaryTimeAggregate**
- **WorkingTimeAggregate**

### UserCarBehavior
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical car behavior profile for a user. Note that the user must have driven for at least 50 km during this period for the scores to be computed.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehavior' | True |
| scores | [UserCarBehaviorScores](data-reference-q-z.md#usercarbehaviorscores) |  | True |
| features | [UserCarBehaviorFeatures](data-reference-q-z.md#usercarbehaviorfeatures) |  | True |


### UserCarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehaviorFeatures' | True |
| l7d | [TimeWindowUserCarBehaviorFeatures](data-reference-q-z.md#timewindowusercarbehaviorfeatures) | Recent features based on the transports we have analyzed in the last 7 days of data. | True |
| past | [TimeWindowUserCarBehaviorFeatures](data-reference-q-z.md#timewindowusercarbehaviorfeatures) | Historical features based on all transports we have available, excluding the last 7 days of data. | True |


### UserCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehaviorScores' | True |
| l7d | [ZoneCarBehaviorScores](data-reference-q-z.md#zonecarbehaviorscores) | Recent scores based on the transports we have analyzed in the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. | True |
| past | [ZoneCarBehaviorScores](data-reference-q-z.md#zonecarbehaviorscores) | Historical scores based on all transports we have analysed excluding the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. | True |


### UserHealth
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical health attributes.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserHealth' | True |
| scores | [UserHealthScores](data-reference-q-z.md#userhealthscores) |  | True |


### UserHealthScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

This scoring system is used to track an individuals health.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserHealthScores' | True |
| activity | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user health. It takes into account sport duration, walking/biking distance & walking/biking speed. A higher score means you are more active in regard to physical activity and exercise. | True |
| mobility | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user mobility, the higher the score, the more ability to pursue various activities in life. It combines the locations visited frequency, distance travelled and user action radius. It is independent of transport mode. | True |
| work_social | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user's social activities. It is calculated considering two components: the social score and work score. It takes into account how much time the user spends in locations, as well as how many locations the user visits. It is a measure of the number user social relationships together with their duration. It doesn't count user's home and work location, but remote work locations are considered. The higher the score, the more and the longer social interactions the user has. | True |


### UserRole
**Kind**: ENUM

- **developer**
- **spectator**
- **basic**
The roles a user can have, both on accounts and apps.

### UserSdkSettings
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

User overrides that are used by the SDK configuration. This is not the SDK configuration model.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserSdkSettings' | True |
| flavor | [SdkFlavor](data-reference-q-z.md#sdkflavor) | If null, app-wide settings or defaults are active. | True |
| killswitch_action | String |  | True |
| debug_logging | String | If null, app-wide settings or defaults are active. | True |


### UserSemanticTime
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserSemanticTime' | True |
| all_days | [SemanticTimeAggregate](data-reference-q-z.md#semantictimeaggregate) | Historical semantic time averaged for all days over all data. | True |


### UserTimeAggregatedScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport scores by month, week, day.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| all | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of all driving scores | True |
| month | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given month. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current month in UTC. | True |
| week | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given week. Enter date as YYYY-MM-DD. The day must always correspond to the Monday of the week you're trying to access. So for the third week of April, it will be 2019-04-15. The default value is the start of the current week in UTC. | True |
| day | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given day. Enter date as YYYY-MM-DD. It must correspond exactly to the date for which you want to access the aggregation. The default value is the current day in UTC. | True |
| quarter | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given quarter. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current quarter in UTC. Given date will be determine to derive the quarter, i.e 2021-09-27 belongs to quarter starting from 2021-07-01 | True |


### UserType
**Kind**: ENUM

- **User**: An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.
- **ControlUser**: A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

### UsersConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the user nodes

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UsersConnection' | True |
| slice | [IUser](data-reference-h-p.md#iuser) | The individual user nodes. Provide the right paging parameters to slice your response data. By default a slice holds 100 users, which you can increase to 1000. | True |
| paging | [Paging](data-reference-h-p.md#paging) |  | True |


### Waypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Waypoint' | True |
| latitude | Float | Location fix latitude. | True |
| longitude | Float | Location fix longitude. | True |
| timestamp | String |  | True |
| accuracy | Int | The estimated horizontal accuracy of this location, radial, in meters. | True |
| speed | Float | The instantaneous speed of the device, measured in meters per second. A negative value indicates an invalid speed. | True |
| altitude | Float | The altitude, measured in meters. Positive values indicate altitudes above sea level. Negative values indicate altitudes below sea level. | True |


### Weather
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| summary | String |  | True |
| icon | String |  | True |
| precipIntensity | Float |  | True |
| precipProbability | Float |  | True |
| temperature | Float |  | True |
| apparentTemperature | Float |  | True |
| dewPoint | Float |  | True |
| humidity | Float |  | True |
| pressure | Float |  | True |
| windSpeed | Float |  | True |
| windGust | Float |  | True |
| windBearing | Float |  | True |
| cloudCover | Float |  | True |
| uvIndex | Float |  | True |
| visibility | Float |  | True |
| ozone | Float |  | True |


### WeatherRange
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | [Weather](data-reference-q-z.md#weather) | Weather data at the start of this event. | True |
| end | [Weather](data-reference-q-z.md#weather) | Weather data at the end of this event. Could be the same as the start if the event was short-lived. | True |


### WeightedLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'WeightedLocation' | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| weight | Float |  | True |


### WorkingTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'WorkingTimeAggregate' | True |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | True |
| duration | Float |  | True |
| whereabouts | [WorkingTimeWhereabouts](data-reference-q-z.md#workingtimewhereabouts) |  | True |


### WorkingTimeWhereabouts
**Kind**: ENUM

- **all_locations**: When at either regular work or remote locations visited during working time, excluding transports.
- **at_work**: When working at work moment has been active, excluding nothing.
- **remote**: When working remote moment has been active, including transports in between.

### ZoneCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport behavior scores by road type

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ZoneCarBehaviorScores' | True |
| all | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on aggregated features across all zones. | True |
| total | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on the average of features per zone. | True |
| motorway | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in the motorway zones. | True |
| city | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in non-motorway city zones. | True |
| non_city | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in non-motorway non-city zones. | True |


