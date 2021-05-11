# Data Reference Q-Z

## Objects

* [SegmentDefinition](data-reference-q-z.md#segmentdefinition)
* [SemanticTimeAggregate](data-reference-q-z.md#semantictimeaggregate)
* [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue)
* [Stationary](data-reference-q-z.md#stationary)
* [StationaryFeedback](data-reference-q-z.md#stationaryfeedback)
* [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction)
* [StationaryLocation](data-reference-q-z.md#stationarylocation)
* [StationaryPrediction](data-reference-q-z.md#stationaryprediction)
* [StationaryTimeAggregate](data-reference-q-z.md#stationarytimeaggregate)
* [TimeWindowTransportHeatmaps](data-reference-q-z.md#timewindowtransportheatmaps)
* [TimeWindowUserCarBehaviorFeatures](data-reference-q-z.md#timewindowusercarbehaviorfeatures)
* [TrajectoryWaypoint](data-reference-q-z.md#trajectorywaypoint)
* [Transport](data-reference-q-z.md#transport)
* [TransportFeedback](data-reference-q-z.md#transportfeedback)
* [TransportHeatmaps](data-reference-q-z.md#transportheatmaps)
* [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
* [TransportModeHeatmaps](data-reference-q-z.md#transportmodeheatmaps)
* [TransportPrediction](data-reference-q-z.md#transportprediction)
* [TransportTimeAggregate](data-reference-q-z.md#transporttimeaggregate)
* [TransportTrajectory](data-reference-q-z.md#transporttrajectory)
* [Trip](data-reference-q-z.md#trip)
* [TripConnection](data-reference-q-z.md#tripconnection)
* [TurnBehaviorAnnotation](data-reference-q-z.md#turnbehaviorannotation)
* [User](data-reference-q-z.md#user)
* [UserAccountRole](data-reference-q-z.md#useraccountrole)
* [UserCarBehavior](data-reference-q-z.md#usercarbehavior)
* [UserCarBehaviorFeatures](data-reference-q-z.md#usercarbehaviorfeatures)
* [UserCarBehaviorScores](data-reference-q-z.md#usercarbehaviorscores)
* [UserHealth](data-reference-q-z.md#userhealth)
* [UserHealthScores](data-reference-q-z.md#userhealthscores)
* [UserSdkSettings](data-reference-q-z.md#usersdksettings)
* [UserSemanticTime](data-reference-q-z.md#usersemantictime)
* [UserTimeAggregatedScores](data-reference-q-z.md#usertimeaggregatedscores)
* [UsersConnection](data-reference-q-z.md#usersconnection)
* [Waypoint](data-reference-q-z.md#waypoint)
* [Weather](data-reference-q-z.md#weather)
* [WeatherRange](data-reference-q-z.md#weatherrange)
* [WeightedLocation](data-reference-q-z.md#weightedlocation)
* [WorkingTimeAggregate](data-reference-q-z.md#workingtimeaggregate)
* [ZoneCarBehaviorScores](data-reference-q-z.md#zonecarbehaviorscores)

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

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SegmentDefinition' |
| id | String | Identifier for this segment. |
| version | Int | Version which will increase everytime minor changes or improvements happen to the calculation of this segment. |
| category | String | Category of this segment, if any. |
| subcategory | String | Subcategory of this segment, if any. |
| display\_name | String | A displayable name for this segment. |
| description | String | A short description about this segment. |
| deprecated | Boolean | Flag that indicates if this segment will be removed in one of the following releases. Do not use segments that are marked deprecated for new development. |
| deprecated\_at | String | Date when the segment will be removed. Default null. |

### SegmentDefinitionStatus

**Kind**: ENUM

* **ACTIVE**: The current active version of segment definitions.
* **ALPHA**: The next version of segment definitions, these will become active in the next release.

  Identifies the release status of a segment definition.

### SegmentType

**Kind**: ENUM

* **GenericSegment**

### SemanticTime

**Kind**: ENUM

* **morning**
* **lunch**
* **afternoon**
* **evening**
* **night**

  The user semantic time.

### SemanticTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregate' |
| morning | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  |
| lunch | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  |
| afternoon | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  |
| evening | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  |
| night | [SemanticTimeAggregateValue](data-reference-q-z.md#semantictimeaggregatevalue) |  |

### SemanticTimeAggregateDaysEnum

**Kind**: ENUM

* **all\_days**: All days are used in the calculation of the aggregate.

### SemanticTimeAggregateValue

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregateValue' |
| semantic\_time | [SemanticTime](data-reference-q-z.md#semantictime) |  |
| days | [SemanticTimeAggregateDaysEnum](data-reference-q-z.md#semantictimeaggregatedaysenum) |  |
| start | String | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |
| end | String | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |

### Stationary

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Stationary' |
| previous\_event\_id | String |  |
| next\_event\_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| start\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. |
| latitude | Float |  |
| longitude | Float |  |
| duration | [BigInt](data-reference-a-g.md#bigint) |  |
| address | [Address](data-reference-a-g.md#address) |  |
| location | [StationaryLocation](data-reference-q-z.md#stationarylocation) |  |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. |

### StationaryFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IEventFeedback](data-reference-h-p.md#ieventfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'StationaryFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection\_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| event\_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  |
| stationary | [Stationary](data-reference-q-z.md#stationary) | The Stationary this feedback refers to. |

### StationaryIntervalPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-p.md#iprediction), [IEventPrediction](data-reference-h-p.md#ieventprediction), [IIntervalPrediction](data-reference-h-p.md#iintervalprediction)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'StationaryIntervalPrediction' |
| probability | Float |  |
| event\_type | [EventType](data-reference-a-g.md#eventtype) |  |
| start\_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  |
| location | [StationaryLocation](data-reference-q-z.md#stationarylocation) |  |

### StationaryLocation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Holds more information about a stationary location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StationaryLocation' |
| significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) | What this location means for the user, or the frequency it's being visited. |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  |
| place\_candidates | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  |

### StationaryPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-p.md#ibranchevent)

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'StationaryPrediction' |
| location\_type | String |  |
| significance | String |  |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  |

### StationaryTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'StationaryTimeAggregate' |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  |
| duration | Float |  |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |

### TimePeriod

**Kind**: ENUM

* **week**

### TimeWindowTransportHeatmaps

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TimeWindowTransportHeatmaps' |
| car | [TransportModeHeatmaps](data-reference-q-z.md#transportmodeheatmaps) |  |

### TimeWindowUserCarBehaviorFeatures

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TimeWindowUserCarBehaviorFeatures' |
| phone\_handling | Float | The average number of milliseconds this user is using his phone per hour in transport, during this time window. |
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
| road\_type | String |  |
| speed\_v2 | Float | The average speed between this waypoint and the next waypoint, in km/h. The difference with speed is that it has an improved estimation algorithm. |
| speed\_v2\_confidence | Float | This field gives confidence for our speed estimation based on the actual sampling rate of the waypoints and if there are multi-speed zones in the road segments between 2 actual waypoints. Values can range from 1.00-0.50. 1.00 will be assigned for those GPS waypoint with instantaneous speed.  0.95 will be assigned for those GPS waypoint with no instantaneous speed.  0.5 will be assigned for the augmented waypoints with the least confidence which includes those segments with more than 5 minutes between the real waypoints and where the average speed is within the \(combined\) speed limits of the trip but we still report speeding. |
| distance | Float | The distance in meter between the current waypoint and the next waypoint. |
| speed\_limit | Float | Speed limit \(in km/h\) measured at this point in the trajectory as provided by our mapping data partners. |

### Transport

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Transport' |
| previous\_event\_id | String |  |
| next\_event\_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| start\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. |
| session\_ids | [String](data-reference-q-z.md#string) | A list of sessionIDs from the SDK that can be used to correlate data in sensor-offloads. |
| mode | [TransportMode](data-reference-q-z.md#transportmode) | The transport mode that was identified for this transport. |
| distance | Int | Distance is in meters. |
| occupant\_role | [TransportOccupantRole](data-reference-q-z.md#transportoccupantrole) |  |
| waypoints | [Waypoint](data-reference-q-z.md#waypoint) |  |
| trajectory | [TransportTrajectory](data-reference-q-z.md#transporttrajectory) |  |
| behavior\_scores | [TransportBehaviorScores](data-reference-q-z.md#transportbehaviorscores) |  |
| behavior\_annotations | [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation) |  |
| behavior\_features | [TransportBehaviorFeatures](data-reference-q-z.md#transportbehaviorfeatures) |  |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. |

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

**Possible types**: [CarBehaviorFeatures](data-reference-a-g.md#carbehaviorfeatures)

### TransportBehaviorScores

**Kind**: UNION

**Possible types**: [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) The transport behavior scores we have detected during a transport. These scores are only available when the full trip is processed.

### TransportFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IEventFeedback](data-reference-h-p.md#ieventfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'TransportFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection\_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| event\_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  |
| transport | [Transport](data-reference-q-z.md#transport) | The Transport this feedback refers to. |

### TransportHeatmaps

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Historically aggregated transport heatmaps.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportHeatmaps' |
| l30d | [TimeWindowTransportHeatmaps](data-reference-q-z.md#timewindowtransportheatmaps) | Transport heatmaps that are calculated using the last . |

### TransportIntervalPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IPrediction](data-reference-h-p.md#iprediction), [IEventPrediction](data-reference-h-p.md#ieventprediction), [IIntervalPrediction](data-reference-h-p.md#iintervalprediction)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'TransportIntervalPrediction' |
| probability | Float |  |
| event\_type | [EventType](data-reference-a-g.md#eventtype) |  |
| start\_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  |
| mode | [TransportMode](data-reference-q-z.md#transportmode) |  |

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
* **insufficient\_data**: When we don't have enough data to identify a transport mode.

  The transport modes the platform supports.

### TransportModeCategory

**Kind**: ENUM

* **unknown**
* **healthy**
* **unhealthy**

### TransportModeHeatmaps

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportModeHeatmaps' |
| passed | [WeightedLocation](data-reference-q-z.md#weightedlocation) | An aggregate heatmap based on the amounts of times you have passed the coordinates during transports. |

### TransportOccupantRole

**Kind**: ENUM

* **driver**
* **passenger**
* **unknown**

### TransportPrediction

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IBranchEvent](data-reference-h-p.md#ibranchevent)

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'TransportPrediction' |
| mode | String |  |

### TransportTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'TransportTimeAggregate' |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  |
| duration | Float |  |
| mode | [TransportMode](data-reference-q-z.md#transportmode) |  |

### TransportTrajectory

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportTrajectory' |
| waypoints | [TrajectoryWaypoint](data-reference-q-z.md#trajectorywaypoint) |  |
| encoded | String | An encoded list of trajectory waypoints, \[\[lat,lon\],\[lat,lon\]\]. More info on polyline decoding: [https://developers.google.com/maps/documentation/utilities/polylinealgorithm](https://developers.google.com/maps/documentation/utilities/polylinealgorithm) |

### TreePredictionType

**Kind**: ENUM

* **StationaryPrediction**: Prediction of a Stationary event.
* **TransportPrediction**: Prediction of a Transport event.

### Trip

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IEvent](data-reference-h-p.md#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'Trip' |
| previous\_event\_id | String |  |
| next\_event\_id | String |  |
| user\_id | String |  |
| start | String |  |
| end | String |  |
| start\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| mode | String | Car, tram, walking, etc. |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) | Type of processing applied on the trip. |
| behavior\_scores | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) |  |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) |  |

### TripConnection

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access trips across all users.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TripConnection' |
| slice | [Trip](data-reference-q-z.md#trip) | The individual trips. Provide the right paging parameters to slice your result set. |

### TurnBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'TurnBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| maneuver | [TurnBehaviorAnnotationManeuver](data-reference-q-z.md#turnbehaviorannotationmaneuver) |  |
| duration | Int | Duration is in milliseconds. |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  |
| magnitude | Float | The centripetal g-force you experience during turns, measured in \(0.2\*m\)/s². Taking a turn at 60km/h will result in a higher magnitude compared to the same turn at 30 km/h |

### TurnBehaviorAnnotationManeuver

**Kind**: ENUM

* **left\_turn**
* **right\_turn**
* **roundabout**
* **lane\_switch**

### User

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](data-reference-h-p.md#iuser) An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'User' |
| install\_id | String | The unique identifier for active install id. |
| external\_id | String | The external id that was linked to this person. |
| id | String | The unique identifier for this user. |
| can\_login | Boolean |  |
| created\_at | String | The time when this user was created, ISO8601. Example: 2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](data-reference-q-z.md#usersdksettings) |  |
| application\_id | String | The ID of the Application this user relates to. |
| application | [Application](data-reference-a-g.md#application) | The Application this user relates to. |
| custom\_event\_history | [CustomEvent](data-reference-a-g.md#customevent) | Custom Event History |
| event\_history | [IEvent](data-reference-h-p.md#ievent) | An unordered list of events we have detected for this user. |
| car\_behavior | [UserCarBehavior](data-reference-q-z.md#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
| aggregated\_driving\_scores | [UserTimeAggregatedScores](data-reference-q-z.md#usertimeaggregatedscores) |  |
| transport\_heatmaps | [TransportHeatmaps](data-reference-q-z.md#transportheatmaps) | The aggregated transport heatmaps calculated over time. |
| metadata | [JSON](data-reference-h-p.md#json) | All custom set metadata properties on this user. This is a JSON object with key-&gt;value pairs. |
| device | [DeviceInfo](data-reference-a-g.md#deviceinfo) | The last known active tracking device metadata |
| active\_moments | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. |
| moment\_history | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments we have detected for this user. |
| semantic\_time | [UserSemanticTime](data-reference-q-z.md#usersemantictime) | The user's semantic time averaged over time. |
| anomaly\_history | [IAnomaly](data-reference-h-p.md#ianomaly) |  |
| segments | [ISegment](data-reference-h-p.md#isegment) | An unordered list of segments that are detected for this user. |
| location\_clusters | [LocationCluster](data-reference-h-p.md#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations \(significance, point of interest, ...\) |
| location | [Waypoint](data-reference-q-z.md#waypoint) | The last known location we have for this user. |
| health | [UserHealth](data-reference-q-z.md#userhealth) | The historical health attributes. |
| attributes | [IUserAttribute](data-reference-h-p.md#iuserattribute) |  |
| predictions | [IPrediction](data-reference-h-p.md#iprediction) | Event/Moment predictions for this user |
| prediction\_tree | [PredictionTree](data-reference-h-p.md#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. |
| feedback\_history | [IFeedback](data-reference-h-p.md#ifeedback) | Feedback on this user |

### UserAccountRole

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserAccountRole' |
| user\_id | String |  |
| account\_id | String |  |
| role | String |  |
| account | [Account](data-reference-a-g.md#account) |  |

### UserAttributeType

**Kind**: ENUM

* **TransportTimeAggregate**
* **CommuteTimeAggregate**
* **StationaryTimeAggregate**
* **WorkingTimeAggregate**

### UserCarBehavior

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical car behavior profile for a user. Note that the user must have driven for at least 50 km during this period for the scores to be computed.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehavior' |
| scores | [UserCarBehaviorScores](data-reference-q-z.md#usercarbehaviorscores) |  |
| features | [UserCarBehaviorFeatures](data-reference-q-z.md#usercarbehaviorfeatures) |  |

### UserCarBehaviorFeatures

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehaviorFeatures' |
| l7d | [TimeWindowUserCarBehaviorFeatures](data-reference-q-z.md#timewindowusercarbehaviorfeatures) | Recent features based on the transports we have analyzed in the last 7 days of data. |
| past | [TimeWindowUserCarBehaviorFeatures](data-reference-q-z.md#timewindowusercarbehaviorfeatures) | Historical features based on all transports we have available, excluding the last 7 days of data. |

### UserCarBehaviorScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehaviorScores' |
| l7d | [ZoneCarBehaviorScores](data-reference-q-z.md#zonecarbehaviorscores) | Recent scores based on the transports we have analyzed in the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. |
| past | [ZoneCarBehaviorScores](data-reference-q-z.md#zonecarbehaviorscores) | Historical scores based on all transports we have analysed excluding the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. |

### UserHealth

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical health attributes.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserHealth' |
| scores | [UserHealthScores](data-reference-q-z.md#userhealthscores) |  |

### UserHealthScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

This scoring system is used to track an individuals health.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserHealthScores' |
| activity | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user health. It takes into account sport duration, walking/biking distance & walking/biking speed. A higher score means you are more active in regard to physical activity and exercise. |
| mobility | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user mobility, the higher the score, the more ability to pursue various activities in life. It combines the locations visited frequency, distance travelled and user action radius. It is independent of transport mode. |
| work\_social | [FloatAttribute](data-reference-a-g.md#floatattribute) | Score that measures a general overview of user's social activities. It is calculated considering two components: the social score and work score. It takes into account how much time the user spends in locations, as well as how many locations the user visits. It is a measure of the number user social relationships together with their duration. It doesn't count user's home and work location, but remote work locations are considered. The higher the score, the more and the longer social interactions the user has. |

### UserRole

**Kind**: ENUM

* **developer**
* **spectator**
* **basic**

  The roles a user can have, both on accounts and apps.

### UserSdkSettings

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

User overrides that are used by the SDK configuration. This is not the SDK configuration model.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserSdkSettings' |
| flavor | [SdkFlavor](data-reference-q-z.md#sdkflavor) | If null, app-wide settings or defaults are active. |
| killswitch\_action | String |  |
| debug\_logging | String | If null, app-wide settings or defaults are active. |

### UserSemanticTime

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserSemanticTime' |
| all\_days | [SemanticTimeAggregate](data-reference-q-z.md#semantictimeaggregate) | Historical semantic time averaged for all days over all data. |

### UserTimeAggregatedScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport scores by month, week, day.

| Property | Type | Description |
| :--- | :--- | :--- |
| all | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of all driving scores |
| month | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given month |
| week | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given week |
| day | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Aggregation of driving scores for a given day |

### UserType

**Kind**: ENUM

* **User**: An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.
* **ControlUser**: A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

### UsersConnection

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the user nodes

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UsersConnection' |
| slice | [IUser](data-reference-h-p.md#iuser) | The individual user nodes. Provide the right paging parameters to slice your response data. By default a slice holds 100 users, which you can increase to 1000. |
| paging | [Paging](data-reference-h-p.md#paging) |  |

### Waypoint

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Waypoint' |
| latitude | Float |  |
| longitude | Float |  |
| timestamp | String |  |
| accuracy | Int | The estimated horizontal accuracy of this location, radial, in meters. |
| speed | Float | The instantaneous speed of the device, measured in meters per second. A negative value indicates an invalid speed. |
| altitude | Float | The altitude, measured in meters. Positive values indicate altitudes above sea level. Negative values indicate altitudes below sea level. |

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
| start | [Weather](data-reference-q-z.md#weather) | Weather data at the start of this event. |
| end | [Weather](data-reference-q-z.md#weather) | Weather data at the end of this event. Could be the same as the start if the event was short-lived. |

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

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'WorkingTimeAggregate' |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  |
| duration | Float |  |
| whereabouts | [WorkingTimeWhereabouts](data-reference-q-z.md#workingtimewhereabouts) |  |

### WorkingTimeWhereabouts

**Kind**: ENUM

* **all\_locations**: When at either regular work or remote locations visited during working time, excluding transports.
* **at\_work**: When working at work moment has been active, excluding nothing.
* **remote**: When working remote moment has been active, including transports in between.

### ZoneCarBehaviorScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport behavior scores by road type

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ZoneCarBehaviorScores' |
| all | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on aggregated features across all zones. |
| total | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on the average of features per zone. |
| motorway | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in the motorway zones. |
| city | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in non-motorway city zones. |
| non\_city | [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores) | Scores based on features in non-motorway non-city zones. |

