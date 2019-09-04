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
- [StreamDefinition](#streamdefinition)
- [Subscription](#subscription)
- [SubscriptionsConnection](#subscriptionsconnection)
- [TimeWindowTransportHeatmaps](#timewindowtransportheatmaps)
- [TimeWindowUserCarBehaviorFeatures](#timewindowusercarbehaviorfeatures)
- [TrajectoryWaypoint](#trajectorywaypoint)
- [Transport](#transport)
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

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SegmentDefinition' |
| id | String | Identifier for this segment. |
| version | Int | Version which will increase everytime minor changes or improvements happen to the calculation of this segment. |
| category | String | Category of this segment, if any. |
| subcategory | String | Subcategory of this segment, if any. |
| display_name | String | A displayable name for this segment. |
| description | String | A short description about this segment. |
| deprecated | Boolean | Flag that indicates if this segment will be removed in one of the following releases. Do not use segments that are marked deprecated for new development. |
| deprecated_at | String | Date when the segment will be removed. Default null. |


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


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregate' |
| morning | [SemanticTimeAggregateValue](/backend/data-reference/data-reference-q-z#semantictimeaggregatevalue) |  |
| lunch | [SemanticTimeAggregateValue](/backend/data-reference/data-reference-q-z#semantictimeaggregatevalue) |  |
| afternoon | [SemanticTimeAggregateValue](/backend/data-reference/data-reference-q-z#semantictimeaggregatevalue) |  |
| evening | [SemanticTimeAggregateValue](/backend/data-reference/data-reference-q-z#semantictimeaggregatevalue) |  |
| night | [SemanticTimeAggregateValue](/backend/data-reference/data-reference-q-z#semantictimeaggregatevalue) |  |


### SemanticTimeAggregateDaysEnum
**Kind**: ENUM

- **all_days**: All days are used in the calculation of the aggregate.

### SemanticTimeAggregateValue
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregateValue' |
| semantic_time | [SemanticTime](/backend/data-reference/data-reference-q-z#semantictime) |  |
| days | [SemanticTimeAggregateDaysEnum](/backend/data-reference/data-reference-q-z#semantictimeaggregatedaysenum) |  |
| start | String | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |
| end | String | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |


### Stationary
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](/backend/data-reference/data-reference-h-p#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](/backend/data-reference/data-reference-a-g#eventtype) | 'Stationary' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](/backend/data-reference/data-reference-a-g#bigint) |  |
| end_ts | [BigInt](/backend/data-reference/data-reference-a-g#bigint) |  |
| analysis_type | [AnalysisType](/backend/data-reference/data-reference-a-g#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| latitude | Float |  |
| longitude | Float |  |
| duration | [BigInt](/backend/data-reference/data-reference-a-g#bigint) |  |
| address | [Address](/backend/data-reference/data-reference-a-g#address) |  |
| location | [StationaryLocation](/backend/data-reference/data-reference-q-z#stationarylocation) |  |
| weather | [WeatherRange](/backend/data-reference/data-reference-q-z#weatherrange) | Weather data associated with this event. |


### StationaryFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](/backend/data-reference/data-reference-h-p#ifeedback), [IEventFeedback](/backend/data-reference/data-reference-h-p#ieventfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](/backend/data-reference/data-reference-a-g#feedbacktype) | 'StationaryFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| event_feedback | [EventFeedback](/backend/data-reference/data-reference-a-g#eventfeedback) |  |
| stationary | [Stationary](/backend/data-reference/data-reference-q-z#stationary) | The Stationary this feedback refers to. |


### StationaryIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](/backend/data-reference/data-reference-h-p#iprediction), [IEventPrediction](/backend/data-reference/data-reference-h-p#ieventprediction), [IIntervalPrediction](/backend/data-reference/data-reference-h-p#iintervalprediction)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](/backend/data-reference/data-reference-h-p#predictiontype) | 'StationaryIntervalPrediction' |
| probability | Float |  |
| event_type | [EventType](/backend/data-reference/data-reference-a-g#eventtype) |  |
| start_interval | [PredictionInterval](/backend/data-reference/data-reference-h-p#predictioninterval) |  |
| location | [StationaryLocation](/backend/data-reference/data-reference-q-z#stationarylocation) |  |


### StationaryLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Holds more information about a stationary location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StationaryLocation' |
| significance | [LocationSignificance](/backend/data-reference/data-reference-h-p#locationsignificance) | What this location means for the user, or the frequency it's being visited. |
| place | [LocationPlaceCandidate](/backend/data-reference/data-reference-h-p#locationplacecandidate) |  |
| place_candidates | [LocationPlaceCandidate](/backend/data-reference/data-reference-h-p#locationplacecandidate) |  |


### StationaryPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](/backend/data-reference/data-reference-h-p#ibranchevent)

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](/backend/data-reference/data-reference-q-z#treepredictiontype) | 'StationaryPrediction' |
| location_type | String |  |
| significance | String |  |
| place | [LocationPlaceCandidate](/backend/data-reference/data-reference-h-p#locationplacecandidate) |  |


### StationaryTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](/backend/data-reference/data-reference-h-p#itimeaggregateattribute), [IUserAttribute](/backend/data-reference/data-reference-h-p#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](/backend/data-reference/data-reference-q-z#userattributetype) | 'StationaryTimeAggregate' |
| period | [TimePeriod](/backend/data-reference/data-reference-q-z#timeperiod) |  |
| duration | Float |  |
| place_category | String |  |
| location_significance | [LocationSignificance](/backend/data-reference/data-reference-h-p#locationsignificance) |  |


### StreamDefinition
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Stream definition that can be activated/subscribed to with the Sentiance Firehose

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StreamDefinition' |
| id | String |  |
| name | String |  |
| projection | String | The GQL query that will be provided on every notification. |
| created_at | String |  |
| subscriptions | [SubscriptionsConnection](/backend/data-reference/data-reference-q-z#subscriptionsconnection) |  |


### StreamDefinitionConnectionType
**Kind**: ENUM

- **websockets**
- **sns**
Stream definition connection type.

### Subscription
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Subscription that can be activated to receive data from the Sentiance Firehose.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Subscription' |
| id | String |  |
| token | String |  |
| active | Boolean |  |
| connection_type | [StreamDefinitionConnectionType](/backend/data-reference/data-reference-q-z#streamdefinitionconnectiontype) |  |
| user_ids | [String](/backend/data-reference/data-reference-q-z#string) |  |
| created_at | String |  |


### SubscriptionsConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the stream subscriptions

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SubscriptionsConnection' |
| slice | [Subscription](/backend/data-reference/data-reference-q-z#subscription) | The individual subscriptions. Provide the right paging parameters to slice your result set. |


### TimePeriod
**Kind**: ENUM

- **week**

### TimeWindowTransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TimeWindowTransportHeatmaps' |
| car | [TransportModeHeatmaps](/backend/data-reference/data-reference-q-z#transportmodeheatmaps) |  |


### TimeWindowUserCarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TimeWindowUserCarBehaviorFeatures' |
| phone_handling | Float | The average number of milliseconds this user is using his phone per hour in transport, during this time window. |
| distance | Int | Aggregated distance measured in meter for all car transports during this time window. |


### TrajectoryWaypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single waypoint in the augmented trajectory.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TrajectoryWaypoint' |
| latitude | Float |  |
| longitude | Float |  |
| timestamp | String |  |
| road_type | String |  |
| speed | Float | The average speed between this waypoint and the next waypoint, in km/h. |
| speed_v2 | Float | The average speed between this waypoint and the next waypoint, in km/h. The difference with speed is that it has an improved estimation algorithm. |
| distance | Float | The distance in meter between the current waypoint and the next waypoint. |
| speed_limit | Float | Speed limit measured at this point in the trajectory. As is provided by our mapping data partners. |


### Transport
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](/backend/data-reference/data-reference-h-p#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](/backend/data-reference/data-reference-a-g#eventtype) | 'Transport' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](/backend/data-reference/data-reference-a-g#bigint) |  |
| end_ts | [BigInt](/backend/data-reference/data-reference-a-g#bigint) |  |
| analysis_type | [AnalysisType](/backend/data-reference/data-reference-a-g#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| mode | [TransportMode](/backend/data-reference/data-reference-q-z#transportmode) | The transport mode that was identified for this transport.  |
| distance | Int |  |
| occupant_role | [TransportOccupantRole](/backend/data-reference/data-reference-q-z#transportoccupantrole) |  |
| waypoints | [Waypoint](/backend/data-reference/data-reference-q-z#waypoint) |  |
| trajectory | [TransportTrajectory](/backend/data-reference/data-reference-q-z#transporttrajectory) |  |
| behavior_scores | [TransportBehaviorScores](/backend/data-reference/data-reference-q-z#transportbehaviorscores) |  |
| behavior_annotations | [ITransportBehaviorAnnotation](/backend/data-reference/data-reference-h-p#itransportbehaviorannotation) |  |
| behavior_features | [TransportBehaviorFeatures](/backend/data-reference/data-reference-q-z#transportbehaviorfeatures) |  |
| weather | [WeatherRange](/backend/data-reference/data-reference-q-z#weatherrange) | Weather data associated with this event. |


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

**Possible types**: [CarBehaviorFeatures](/backend/data-reference/data-reference-a-g#carbehaviorfeatures)

### TransportBehaviorScores
**Kind**: UNION

**Possible types**: [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores)
The transport behavior scores we have detected during a transport. These scores are only available when the full trip is processed.

### TransportFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](/backend/data-reference/data-reference-h-p#ifeedback), [IEventFeedback](/backend/data-reference/data-reference-h-p#ieventfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](/backend/data-reference/data-reference-a-g#feedbacktype) | 'TransportFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| event_feedback | [EventFeedback](/backend/data-reference/data-reference-a-g#eventfeedback) |  |
| transport | [Transport](/backend/data-reference/data-reference-q-z#transport) | The Transport this feedback refers to. |


### TransportHeatmaps
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Historically aggregated transport heatmaps.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportHeatmaps' |
| l30d | [TimeWindowTransportHeatmaps](/backend/data-reference/data-reference-q-z#timewindowtransportheatmaps) | Transport heatmaps that are calculated using the last . |


### TransportIntervalPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](/backend/data-reference/data-reference-h-p#iprediction), [IEventPrediction](/backend/data-reference/data-reference-h-p#ieventprediction), [IIntervalPrediction](/backend/data-reference/data-reference-h-p#iintervalprediction)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](/backend/data-reference/data-reference-h-p#predictiontype) | 'TransportIntervalPrediction' |
| probability | Float |  |
| event_type | [EventType](/backend/data-reference/data-reference-a-g#eventtype) |  |
| start_interval | [PredictionInterval](/backend/data-reference/data-reference-h-p#predictioninterval) |  |
| mode | [TransportMode](/backend/data-reference/data-reference-q-z#transportmode) |  |


### TransportMode
**Kind**: ENUM

- **car**: When we have identified a transport mode as car.
- **walking**: When we have identified a transport mode as walking.
- **biking**: When we have identified a transport mode as biking.
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


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportModeHeatmaps' |
| passed | [WeightedLocation](/backend/data-reference/data-reference-q-z#weightedlocation) | An aggregate heatmap based on the amounts of times you have passed the coordinates during transports. |


### TransportOccupantRole
**Kind**: ENUM

- **driver**
- **passenger**
- **unknown**

### TransportPrediction
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](/backend/data-reference/data-reference-h-p#ibranchevent)

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](/backend/data-reference/data-reference-q-z#treepredictiontype) | 'TransportPrediction' |
| mode | String |  |


### TransportTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](/backend/data-reference/data-reference-h-p#itimeaggregateattribute), [IUserAttribute](/backend/data-reference/data-reference-h-p#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](/backend/data-reference/data-reference-q-z#userattributetype) | 'TransportTimeAggregate' |
| period | [TimePeriod](/backend/data-reference/data-reference-q-z#timeperiod) |  |
| duration | Float |  |
| mode | [TransportMode](/backend/data-reference/data-reference-q-z#transportmode) |  |


### TransportTrajectory
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportTrajectory' |
| waypoints | [TrajectoryWaypoint](/backend/data-reference/data-reference-q-z#trajectorywaypoint) |  |
| encoded | String | An encoded list of trajectory waypoints, [[lat,lon],[lat,lon]]. More info on polyline decoding: https://developers.google.com/maps/documentation/utilities/polylinealgorithm |


### TreePredictionType
**Kind**: ENUM

- **StationaryPrediction**: Prediction of a Stationary event.
- **TransportPrediction**: Prediction of a Transport event.

### Trip
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](/backend/data-reference/data-reference-h-p#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](/backend/data-reference/data-reference-a-g#eventtype) | 'Trip' |
| user_id | String |  |
| start | String |  |
| end | String |  |
| start_ts | [BigInt](/backend/data-reference/data-reference-a-g#bigint) |  |
| end_ts | [BigInt](/backend/data-reference/data-reference-a-g#bigint) |  |
| mode | String | Car, tram, walking, etc. |
| analysis_type | [AnalysisType](/backend/data-reference/data-reference-a-g#analysistype) | Type of processing applied on the trip. |
| behavior_scores | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) |  |
| weather | [WeatherRange](/backend/data-reference/data-reference-q-z#weatherrange) |  |


### TripConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access trips across all users.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TripConnection' |
| slice | [Trip](/backend/data-reference/data-reference-q-z#trip) | The individual trips. Provide the right paging parameters to slice your result set. |


### TurnBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](/backend/data-reference/data-reference-h-p#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](/backend/data-reference/data-reference-q-z#transportbehaviorannotationtype) | 'TurnBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| maneuver | [TurnBehaviorAnnotationManeuver](/backend/data-reference/data-reference-q-z#turnbehaviorannotationmaneuver) |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](/backend/data-reference/data-reference-a-g#behaviorannotationpathwaypoint) |  |
| magnitude | Float | The centripetal g-force you experience during turns, measured in (0.2*m)/s². Taking a turn at 60km/h will result in a higher magnitude compared to the same turn at 30 km/h |


### TurnBehaviorAnnotationManeuver
**Kind**: ENUM

- **left_turn**
- **right_turn**
- **roundabout**
- **lane_switch**

### User
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](/backend/data-reference/data-reference-h-p#iuser)
An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](/backend/data-reference/data-reference-q-z#usertype) | 'User' |
| install_id | String | The unique identifier for active install id. |
| external_id | String | The external id that was linked to this person. |
| id | String | The unique identifier for this user. |
| can_login | Boolean |  |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](/backend/data-reference/data-reference-q-z#usersdksettings) |  |
| application_id | String | The ID of the Application this user relates to. |
| application | [Application](/backend/data-reference/data-reference-a-g#application) | The Application this user relates to. |
| custom_event_history | [CustomEvent](/backend/data-reference/data-reference-a-g#customevent) | Custom Event History |
| event_history | [IEvent](/backend/data-reference/data-reference-h-p#ievent) | An unordered list of events we have detected for this user. |
| car_behavior | [UserCarBehavior](/backend/data-reference/data-reference-q-z#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
| aggregated_driving_scores | [UserTimeAggregatedScores](/backend/data-reference/data-reference-q-z#usertimeaggregatedscores) |  |
| transport_heatmaps | [TransportHeatmaps](/backend/data-reference/data-reference-q-z#transportheatmaps) | The aggregated transport heatmaps calculated over time. |
| metadata | [JSON](/backend/data-reference/data-reference-h-p#json) | All custom set metadata properties on this user. This is a JSON object with key->value pairs. |
| device | [DeviceInfo](/backend/data-reference/data-reference-a-g#deviceinfo) | The last known active tracking device metadata |
| active_moments | [IMoment](/backend/data-reference/data-reference-h-p#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. |
| moment_history | [IMoment](/backend/data-reference/data-reference-h-p#imoment) | An unordered list of moments we have detected for this user. |
| semantic_time | [UserSemanticTime](/backend/data-reference/data-reference-q-z#usersemantictime) | The user's semantic time averaged over time. |
| anomaly_history | [IAnomaly](/backend/data-reference/data-reference-h-p#ianomaly) |  |
| segments | [ISegment](/backend/data-reference/data-reference-h-p#isegment) | An unordered list of segments that are detected for this user. |
| location_clusters | [LocationCluster](/backend/data-reference/data-reference-h-p#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...) |
| location | [Waypoint](/backend/data-reference/data-reference-q-z#waypoint) | The last known location we have for this user. |
| health | [UserHealth](/backend/data-reference/data-reference-q-z#userhealth) | The historical health attributes. |
| attributes | [IUserAttribute](/backend/data-reference/data-reference-h-p#iuserattribute) |  |
| predictions | [IPrediction](/backend/data-reference/data-reference-h-p#iprediction) | Event/Moment predictions for this user |
| prediction_tree | [PredictionTree](/backend/data-reference/data-reference-h-p#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. |
| feedback_history | [IFeedback](/backend/data-reference/data-reference-h-p#ifeedback) | Feedback on this user |


### UserAccountRole
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserAccountRole' |
| user_id | String |  |
| account_id | String |  |
| role | String |  |
| account | [Account](/backend/data-reference/data-reference-a-g#account) |  |


### UserAttributeType
**Kind**: ENUM

- **TransportTimeAggregate**
- **CommuteTimeAggregate**
- **StationaryTimeAggregate**
- **WorkingTimeAggregate**

### UserCarBehavior
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical car behavior profile for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehavior' |
| scores | [UserCarBehaviorScores](/backend/data-reference/data-reference-q-z#usercarbehaviorscores) |  |
| features | [UserCarBehaviorFeatures](/backend/data-reference/data-reference-q-z#usercarbehaviorfeatures) |  |


### UserCarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehaviorFeatures' |
| l7d | [TimeWindowUserCarBehaviorFeatures](/backend/data-reference/data-reference-q-z#timewindowusercarbehaviorfeatures) | Recent features based on the transports we have analyzed in the last 7 days of data. |
| past | [TimeWindowUserCarBehaviorFeatures](/backend/data-reference/data-reference-q-z#timewindowusercarbehaviorfeatures) | Historical features based on all transports we have available, excluding the last 7 days of data. |


### UserCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehaviorScores' |
| l7d | [ZoneCarBehaviorScores](/backend/data-reference/data-reference-q-z#zonecarbehaviorscores) | Recent scores based on the transports we have analyzed in the last 7 days of data. |
| past | [ZoneCarBehaviorScores](/backend/data-reference/data-reference-q-z#zonecarbehaviorscores) | Historical scores based on all transports we have analysed excluding the last 7 days of data. |


### UserHealth
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical health attributes.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserHealth' |
| scores | [UserHealthScores](/backend/data-reference/data-reference-q-z#userhealthscores) |  |


### UserHealthScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

This scoring system is used to track an individuals health.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserHealthScores' |
| activity | [FloatAttribute](/backend/data-reference/data-reference-a-g#floatattribute) | Score that measures a general overview of user health. It takes into account sport duration, walking/biking distance & walking/biking speed. A higher score means you are more active in regard to physical activity and exercise. |
| mobility | [FloatAttribute](/backend/data-reference/data-reference-a-g#floatattribute) | Score that measures a general overview of user mobility, the higher the score, the more ability to pursue various activities in life. It combines the locations visited frequency, distance travelled and user action radius. It is independent of transport mode. |
| work_social | [FloatAttribute](/backend/data-reference/data-reference-a-g#floatattribute) | Score that measures a general overview of user's social activities. It is calculated considering two components: the social score and work score. It takes into account how much time the user spends in locations, as well as how many locations the user visits. It is a measure of the number user social relationships together with their duration. It doesn't count user's home and work location, but remote work locations are considered. The higher the score, the more and the longer social interactions the user has. |


### UserRole
**Kind**: ENUM

- **developer**
- **spectator**
- **basic**
The roles a user can have, both on accounts and apps.

### UserSdkSettings
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

User overrides that are used by the SDK configuration. This is not the SDK configuration model.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserSdkSettings' |
| flavor | [SdkFlavor](/backend/data-reference/data-reference-q-z#sdkflavor) | If null, app-wide settings or defaults are active. |
| killswitch_action | String |  |
| debug_logging | String | If null, app-wide settings or defaults are active. |


### UserSemanticTime
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserSemanticTime' |
| all_days | [SemanticTimeAggregate](/backend/data-reference/data-reference-q-z#semantictimeaggregate) | Historical semantic time averaged for all days over all data. |


### UserTimeAggregatedScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport scores by month, week, day.

| Property | Type | Description |
| :--- | :--- | :--- |
| month | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) |  |
| week | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) |  |
| day | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) |  |


### UserType
**Kind**: ENUM

- **User**: An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.
- **ControlUser**: A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

### UsersConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the user nodes

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UsersConnection' |
| slice | [IUser](/backend/data-reference/data-reference-h-p#iuser) | The individual user nodes. Provide the right paging parameters to slice your response data. By default a slice holds 100 users, which you can increase to 1000. |
| paging | [Paging](/backend/data-reference/data-reference-h-p#paging) |  |


### Waypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Waypoint' |
| latitude | Float |  |
| longitude | Float |  |
| timestamp | String |  |
| accuracy | Int | The estimated horizontal accuracy of this location, radial, in meters. |


### Weather
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| summary | String |  |
| icon | String |  |
| precipIntensity | Float |  |
| precipProbability | Float |  |
| temperature | Float |  |
| apparentTemperature | Float |  |
| dewPoint | Float |  |
| humidity | Float |  |
| pressure | Float |  |
| windSpeed | Float |  |
| windGust | Float |  |
| windBearing | Float |  |
| cloudCover | Float |  |
| uvIndex | Float |  |
| visibility | Float |  |
| ozone | Float |  |


### WeatherRange
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| start | [Weather](/backend/data-reference/data-reference-q-z#weather) | Weather data at the start of this event. |
| end | [Weather](/backend/data-reference/data-reference-q-z#weather) | Weather data at the end of this event. Could be the same as the start if the event was short-lived. |


### WeightedLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'WeightedLocation' |
| latitude | Float |  |
| longitude | Float |  |
| weight | Float |  |


### WorkingTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](/backend/data-reference/data-reference-h-p#itimeaggregateattribute), [IUserAttribute](/backend/data-reference/data-reference-h-p#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](/backend/data-reference/data-reference-q-z#userattributetype) | 'WorkingTimeAggregate' |
| period | [TimePeriod](/backend/data-reference/data-reference-q-z#timeperiod) |  |
| duration | Float |  |
| whereabouts | [WorkingTimeWhereabouts](/backend/data-reference/data-reference-q-z#workingtimewhereabouts) |  |


### WorkingTimeWhereabouts
**Kind**: ENUM

- **all_locations**: When at either regular work or remote locations visited during working time, excluding transports.
- **at_work**: When working at work moment has been active, excluding nothing.
- **remote**: When working remote moment has been active, including transports in between.

### ZoneCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport behavior scores by road type

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ZoneCarBehaviorScores' |
| all | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) | Scores based on aggregated features across all zones. |
| total | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) | Scores based on the average of features per zone. |
| motorway | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) | Scores based on features in the motorway zones. |
| city | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) | Scores based on features in non-motorway city zones. |
| non_city | [CarBehaviorScores](/backend/data-reference/data-reference-a-g#carbehaviorscores) | Scores based on features in non-motorway non-city zones. |


