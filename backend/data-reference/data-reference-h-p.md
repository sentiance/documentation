# Data Reference H-P
## Objects
- [HandheldCallingAnnotation](#handheldcallingannotation)
- [HandlingWithoutCallingAnnotation](#handlingwithoutcallingannotation)
- [HandsfreeCallingAnnotation](#handsfreecallingannotation)
- [LocationCluster](#locationcluster)
- [LocationPlaceCandidate](#locationplacecandidate)
- [MomentDefinition](#momentdefinition)
- [MomentFeedback](#momentfeedback)
- [MomentFeedbackFeedback](#momentfeedbackfeedback)
- [OccurrenceCountAnomaly](#occurrencecountanomaly)
- [Paging](#paging)
- [PagingCursors](#pagingcursors)
- [PredictionInterval](#predictioninterval)
- [PredictionTree](#predictiontree)

### HandheldCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandheldCallingAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  |


### HandlingWithoutCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandlingWithoutCallingAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  |


### HandsfreeCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandsfreeCallingAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  |


### IAggregatedAnomaly
**Kind**: INTERFACE

**Implemented by**: [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user over a period of time.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. |


### IAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'IAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |


### IBranchEvent
**Kind**: INTERFACE

**Implemented by**: [StationaryPrediction](data-reference-q-z.md#stationaryprediction), [TransportPrediction](data-reference-q-z.md#transportprediction)
A single predicted event.

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'IBranchEvent' |


### IDayCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [DayCountAnomaly](data-reference-a-g.md#daycountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_days | Float | Observed amount of days. |
| expected_days | Float | Expected amount of days. |


### IDistanceAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_distance | Float | Observed distance in meter. |
| expected_distance | Float | Expected distance in meter. |


### IDurationAnomaly
**Kind**: INTERFACE

**Implemented by**: [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_duration | Float | Observed duration in seconds. |
| expected_duration | Float | Expected duration in seconds. |


### IEvent
**Kind**: INTERFACE

**Implemented by**: [Trip](data-reference-q-z.md#trip), [Stationary](data-reference-q-z.md#stationary), [Transport](data-reference-q-z.md#transport)
An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'IEvent' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. |


### IEventFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-z.md#stationaryfeedback), [TransportFeedback](data-reference-q-z.md#transportfeedback)
An occurrence of event feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  |


### IEventPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event_type | [EventType](data-reference-a-g.md#eventtype) |  |


### IFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-z.md#stationaryfeedback), [TransportFeedback](data-reference-q-z.md#transportfeedback), [MomentFeedback](data-reference-h-p.md#momentfeedback)
An occurrence of feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'IFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |


### IIntervalPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
A prediction that has a start interval.

| Property | Type | Description |
| :--- | :--- | :--- |
| start_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  |


### IMoment
**Kind**: INTERFACE

**Implemented by**: [GenericMoment](data-reference-a-g.md#genericmoment), [CityMoment](data-reference-a-g.md#citymoment), [CountryMoment](data-reference-a-g.md#countrymoment)
An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'IMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. |


### IMomentAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| moment_definition_id | String |  |


### IMomentFeedback
**Kind**: INTERFACE

**Implemented by**: [MomentFeedback](data-reference-h-p.md#momentfeedback)
An occurrence of moment feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| moment_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  |


### IOccurrenceCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_occurrences | Float | Observed amount of occurrences. |
| expected_occurrences | Float | Expected amount of occurrences. |


### IPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
An occurance of a prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'IPrediction' |
| probability | Float |  |


### ISegment
**Kind**: INTERFACE

**Implemented by**: [GenericSegment](data-reference-a-g.md#genericsegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](data-reference-q-z.md#segmenttype) | 'ISegment' |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. |
| segment_definition | [SegmentDefinition](data-reference-q-z.md#segmentdefinition) | The SegmentDefinition this segment relates to. |


### IStationaryAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| place_category | String |  |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |


### ITimeAggregateAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-a-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-z.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-z.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-q-z.md#workingtimeaggregate)
An attribute that aggregates by TimePeriod.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  |


### ITransportAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |


### ITransportBehaviorAnnotation
**Kind**: INTERFACE

**Implemented by**: [BoundaryBehaviorAnnotation](data-reference-a-g.md#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](data-reference-a-g.md#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](data-reference-a-g.md#anomalybehaviorannotation), [TurnBehaviorAnnotation](data-reference-q-z.md#turnbehaviorannotation), [HandlingWithoutCallingAnnotation](data-reference-h-p.md#handlingwithoutcallingannotation), [HandsfreeCallingAnnotation](data-reference-h-p.md#handsfreecallingannotation), [HandheldCallingAnnotation](data-reference-h-p.md#handheldcallingannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' |
| start | String |  |
| end | String |  |


### IUser
**Kind**: INTERFACE

**Implemented by**: [User](data-reference-q-z.md#user), [ControlUser](data-reference-a-g.md#controluser)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'IUser' |
| id | String | The unique identifier for this user. |
| can_login | Boolean |  |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](data-reference-q-z.md#usersdksettings) |  |
| application_id | String | The ID of the Application this user relates to. |
| application | [Application](data-reference-a-g.md#application) | The Application this user relates to. |
| custom_event_history | [CustomEvent](data-reference-a-g.md#customevent) | Custom Event History |
| event_history | [IEvent](data-reference-h-p.md#ievent) | An unordered list of events we have detected for this user. |
| car_behavior | [UserCarBehavior](data-reference-q-z.md#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
| aggregated_driving_scores | [UserTimeAggregatedScores](data-reference-q-z.md#usertimeaggregatedscores) |  |
| transport_heatmaps | [TransportHeatmaps](data-reference-q-z.md#transportheatmaps) | The aggregated transport heatmaps calculated over time. |
| metadata | [JSON](data-reference-h-p.md#json) | All custom set metadata properties on this user. This is a JSON object with key->value pairs. |
| device | [DeviceInfo](data-reference-a-g.md#deviceinfo) | The last known active tracking device metadata |
| active_moments | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. |
| moment_history | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments we have detected for this user. |
| semantic_time | [UserSemanticTime](data-reference-q-z.md#usersemantictime) | The user's semantic time averaged over time. |
| anomaly_history | [IAnomaly](data-reference-h-p.md#ianomaly) |  |
| segments | [ISegment](data-reference-h-p.md#isegment) | An unordered list of segments that are detected for this user. |
| location_clusters | [LocationCluster](data-reference-h-p.md#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...) |
| location | [Waypoint](data-reference-q-z.md#waypoint) | The last known location we have for this user. |
| health | [UserHealth](data-reference-q-z.md#userhealth) | The historical health attributes. |
| attributes | [IUserAttribute](data-reference-h-p.md#iuserattribute) |  |
| predictions | [IPrediction](data-reference-h-p.md#iprediction) | Event/Moment predictions for this user |
| prediction_tree | [PredictionTree](data-reference-h-p.md#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. |
| feedback_history | [IFeedback](data-reference-h-p.md#ifeedback) | Feedback on this user |


### IUserAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-a-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-z.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-z.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-q-z.md#workingtimeaggregate)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'IUserAttribute' |


### InputAddress
**Kind**: INPUT_OBJECT


### InputEventFeedback
**Kind**: INPUT_OBJECT


### InputLocationPlaceCandidate
**Kind**: INPUT_OBJECT


### InputMoment
**Kind**: INPUT_OBJECT


### InputMomentFeedback
**Kind**: INPUT_OBJECT


### InputStationary
**Kind**: INPUT_OBJECT


### InputStationaryLocation
**Kind**: INPUT_OBJECT


### InputTrajectoryWaypoint
**Kind**: INPUT_OBJECT

A single waypoint in the augmented trajectory.

### InputTransport
**Kind**: INPUT_OBJECT


### InputTransportBehaviorFeatures
**Kind**: SCALAR


### InputTransportBehaviorScores
**Kind**: SCALAR


### InputTransportTrajectory
**Kind**: INPUT_OBJECT


### InputWaypoint
**Kind**: INPUT_OBJECT


### JSON
**Kind**: SCALAR

The `JSON` scalar type represents JSON values as specified by [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf).

### LocationCluster
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationCluster' |
| last_visit | String |  |
| latitude | Float |  |
| longitude | Float |  |
| address | [Address](data-reference-a-g.md#address) |  |
| radius | Int |  |
| is_poi | Boolean |  |
| significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  |


### LocationPlaceCandidate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A place selected from one of our data sources.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' |
| name | String | Name of the place. Can be null if no specific place can be assigned. |
| category_hierarchy | [String](data-reference-q-z.md#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` |
| probability | Float |  |
| latitude | Float |  |
| longitude | Float |  |
| provider | String |  |


### LocationSignificance
**Kind**: ENUM

- **home**: A location identified as one of the user's home locations.
- **work**: A location identified as one of the user's work locations.
- **regular**: Locations you regularly visit. Typical examples are places you regularly go shopping, your gym, a friend's place, ...
- **nonregular**: Default type for locations you don't often visit.
- **poi**: Points of interest that have not been classified as home/work previously.
- **new**: Only available a short time when you visit the location the first time.

### MomentDefinition
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single moment definition.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'MomentDefinition' |
| id | String | Identifier of this MomentDefinition. Possible values: working_at_work,working_remote,home,morning,lunch,afternoon,evening,night,commute_from_work,commute_from_home,business_trip,holiday,nearby_home,nearby_work,city_name,country,children_drop_off,sport_routine,shopping_routine,evening_entertainment,night_out,afternoon_drinks,evening_drinks,breakfast_out,lunch_out,dinner_out,about_to_working,about_to_commute_from_home,about_to_commute_from_work,about_to_children_drop_off,about_to_sport,about_to_shopping,nearby_poi |
| category | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic_time,travel,geography,location,about_to_routine |
| display_name | String | A displayable name for this MomentDefinition. |
| description | String | A short description about this MomentDefinition. |


### MomentFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IMomentFeedback](data-reference-h-p.md#imomentfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'MomentFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| moment_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  |
| moment | [IMoment](data-reference-h-p.md#imoment) | The Moment this feedback refers to. |


### MomentFeedbackFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| moment_definition_id_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks our detected moment is correct. |
| moment_definition_id_feedback | String | Correction by the user in case our detection was incorrect. |


### MomentType
**Kind**: ENUM

- **GenericMoment**
- **CityMoment**
- **CountryMoment**

### OccurrenceCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IOccurrenceCountAnomaly](data-reference-h-p.md#ioccurrencecountanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'OccurrenceCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. |
| observed_occurrences | Float | Observed amount of occurrences. |
| expected_occurrences | Float | Expected amount of occurrences. |
| place_category | String |  |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |
| moment_definition_id | String |  |


### OperatingSystem
**Kind**: ENUM

- **android**
- **ios**

### Paging
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging information that allows you to paginate through a large response list.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Paging' |
| cursors | [PagingCursors](data-reference-h-p.md#pagingcursors) | The offset cursors to use when paging through results. |


### PagingCursors
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging cursors that you use to paginate through a large response set.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'PagingCursors' |
| before | String | This is the cursor that points to the start of the page of data that has been returned. |
| after | String | This is the cursor that points to the end of the page of data that has been returned. |


### PredictionInterval
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| start | String |  |
| end | String |  |


### PredictionTree
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Multiple possible events that might occur for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| is_updated | Boolean |  |
| events | [IBranchEvent](data-reference-h-p.md#ibranchevent) | The list of events predicted to occur. |


### PredictionType
**Kind**: ENUM

- **StationaryIntervalPrediction**: Prediction of a Stationary event.
- **TransportIntervalPrediction**: Prediction of a Transport event.

