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
- [OndeviceMLModel](#ondevicemlmodel)
- [Paging](#paging)
- [PagingCursors](#pagingcursors)
- [PredictionInterval](#predictioninterval)
- [PredictionTree](#predictiontree)

### HandheldCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandheldCallingAnnotation' | False |
| start | String |  | False |
| end | String |  | False |
| duration | Int | Duration is in milliseconds. | False |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | False |


### HandlingWithoutCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandlingWithoutCallingAnnotation' | False |
| start | String |  | False |
| end | String |  | False |
| duration | Int | Duration is in milliseconds. | False |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | False |


### HandsfreeCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandsfreeCallingAnnotation' | False |
| start | String |  | False |
| end | String |  | False |
| duration | Int | Duration is in milliseconds. | False |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | False |


### IAggregatedAnomaly
**Kind**: INTERFACE

**Implemented by**: [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user over a period of time.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | False |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | False |


### IAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'IAnomaly' | False |
| start | String |  | False |
| end | String |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | False |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | False |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | False |


### IBranchEvent
**Kind**: INTERFACE

**Implemented by**: [StationaryPrediction](data-reference-q-z.md#stationaryprediction), [TransportPrediction](data-reference-q-z.md#transportprediction)
A single predicted event.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | False |
| end | String | Predicted end time of the event. | False |
| probability | Float | The probability of this prediction occurring. | False |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'IBranchEvent' | False |


### IDayCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [DayCountAnomaly](data-reference-a-g.md#daycountanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| observed_days | Float | Observed amount of days. | False |
| expected_days | Float | Expected amount of days. | False |


### IDistanceAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| observed_distance | Float | Observed distance in meter. | False |
| expected_distance | Float | Expected distance in meter. | False |


### IDurationAnomaly
**Kind**: INTERFACE

**Implemented by**: [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| observed_duration | Float | Observed duration in seconds. | False |
| expected_duration | Float | Expected duration in seconds. | False |


### IEvent
**Kind**: INTERFACE

**Implemented by**: [Trip](data-reference-q-z.md#trip), [Stationary](data-reference-q-z.md#stationary), [Transport](data-reference-q-z.md#transport)
An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'IEvent' | False |
| event_id | String |  | True |
| previous_event_id | String |  | False |
| next_event_id | String |  | False |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. | False |


### IEventFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-z.md#stationaryfeedback), [TransportFeedback](data-reference-q-z.md#transportfeedback)
An occurrence of event feedback submitted by a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| event_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  | False |


### IEventPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| event_type | [EventType](data-reference-a-g.md#eventtype) |  | False |


### IFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-z.md#stationaryfeedback), [TransportFeedback](data-reference-q-z.md#transportfeedback), [CrashFeedback](data-reference-a-g.md#crashfeedback), [MomentFeedback](data-reference-h-p.md#momentfeedback)
An occurrence of feedback submitted by a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'IFeedback' | False |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | True |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | False |
| created | String | Time when this feedback entry was created. | False |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | False |


### IIntervalPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
A prediction that has a start interval.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| start_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  | False |


### IMoment
**Kind**: INTERFACE

**Implemented by**: [GenericMoment](data-reference-a-g.md#genericmoment), [CityMoment](data-reference-a-g.md#citymoment), [CountryMoment](data-reference-a-g.md#countrymoment)
An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'IMoment' | False |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | False |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | False |


### IMomentAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| moment_definition_id | String |  | False |


### IMomentFeedback
**Kind**: INTERFACE

**Implemented by**: [MomentFeedback](data-reference-h-p.md#momentfeedback)
An occurrence of moment feedback submitted by a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| moment_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  | False |


### IOccurrenceCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| observed_occurrences | Float | Observed amount of occurrences. | False |
| expected_occurrences | Float | Expected amount of occurrences. | False |


### IPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
An occurance of a prediction that we have detected for a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'IPrediction' | False |
| probability | Float |  | False |


### ISegment
**Kind**: INTERFACE

**Implemented by**: [GenericSegment](data-reference-a-g.md#genericsegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [SegmentType](data-reference-q-z.md#segmenttype) | 'ISegment' | False |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. | False |
| segment_definition | [SegmentDefinition](data-reference-q-z.md#segmentdefinition) | The SegmentDefinition this segment relates to. | False |


### IStationaryAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |


### ITimeAggregateAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-a-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-z.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-z.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-q-z.md#workingtimeaggregate)
An attribute that aggregates by TimePeriod.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | False |


### ITransportAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |


### ITransportBehaviorAnnotation
**Kind**: INTERFACE

**Implemented by**: [BoundaryBehaviorAnnotation](data-reference-a-g.md#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](data-reference-a-g.md#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](data-reference-a-g.md#anomalybehaviorannotation), [TurnBehaviorAnnotation](data-reference-q-z.md#turnbehaviorannotation), [HandlingWithoutCallingAnnotation](data-reference-h-p.md#handlingwithoutcallingannotation), [HandsfreeCallingAnnotation](data-reference-h-p.md#handsfreecallingannotation), [HandheldCallingAnnotation](data-reference-h-p.md#handheldcallingannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' | False |
| start | String |  | False |
| end | String |  | False |


### IUser
**Kind**: INTERFACE

**Implemented by**: [User](data-reference-q-z.md#user), [ControlUser](data-reference-a-g.md#controluser)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'IUser' | False |
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


### IUserAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-a-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-z.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-z.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-q-z.md#workingtimeaggregate)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'IUserAttribute' | False |


### InputAddress
**Kind**: INPUT_OBJECT


### InputCrash
**Kind**: INPUT_OBJECT


### InputCrashFeedback
**Kind**: INPUT_OBJECT


### InputEventFeedback
**Kind**: INPUT_OBJECT


### InputLocationPlaceCandidate
**Kind**: INPUT_OBJECT


### InputMoment
**Kind**: INPUT_OBJECT


### InputMomentFeedback
**Kind**: INPUT_OBJECT


### InputOndeviceMLModel
**Kind**: INPUT_OBJECT

Name of the models that were used to detect the crash. Mainly used as internal reference.

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


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'LocationCluster' | False |
| last_visit | String |  | False |
| latitude | Float |  | False |
| longitude | Float |  | False |
| address | [Address](data-reference-a-g.md#address) |  | False |
| radius | Int |  | False |
| is_poi | Boolean |  | False |
| significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | False |


### LocationPlaceCandidate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A place selected from one of our data sources.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' | False |
| name | String | Name of the place. Can be null if no specific place can be assigned. | False |
| categories | [String](data-reference-q-z.md#string) | List of categories for this place, sorted by granularity. Categories might still be provided when name is null, for example when shopping in a shopping street, categories like shopping and retail can still exist.<br><br><code>**Deprecation notice**</code><br>categories is deprecated.<br>These are outdated. Please use `category_hierarchy` instead. | False |
| category_hierarchy | [String](data-reference-q-z.md#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` | False |
| probability | Float |  | False |
| latitude | Float |  | False |
| longitude | Float |  | False |
| provider | String |  | False |


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

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'MomentDefinition' | False |
| id | String | Identifier of this MomentDefinition. Possible values: working_at_work,working_remote,home,morning,lunch,afternoon,evening,night,commute_from_work,commute_from_home,business_trip,holiday,nearby_home,nearby_work,city_name,country,children_drop_off,sport_routine,shopping_routine,evening_entertainment,night_out,afternoon_drinks,evening_drinks,breakfast_out,lunch_out,dinner_out,about_to_working,about_to_commute_from_home,about_to_commute_from_work,about_to_children_drop_off,about_to_sport,about_to_shopping,nearby_poi | False |
| category | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic_time,travel,geography,location,about_to_routine | False |
| display_name | String | A displayable name for this MomentDefinition. | False |
| description | String | A short description about this MomentDefinition. | False |


### MomentFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IMomentFeedback](data-reference-h-p.md#imomentfeedback)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'MomentFeedback' | False |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | True |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | False |
| created | String | Time when this feedback entry was created. | False |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | False |
| moment_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  | False |
| moment | [IMoment](data-reference-h-p.md#imoment) | The Moment this feedback refers to. | False |


### MomentFeedbackFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| moment_definition_id_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks our detected moment is correct. | False |
| moment_definition_id_feedback | String | Correction by the user in case our detection was incorrect. | False |


### MomentType
**Kind**: ENUM

- **GenericMoment**
- **CityMoment**
- **CountryMoment**

### OccurrenceCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IOccurrenceCountAnomaly](data-reference-h-p.md#ioccurrencecountanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'OccurrenceCountAnomaly' | False |
| start | String |  | False |
| end | String |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | False |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | False |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | False |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | False |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | False |
| observed_occurrences | Float | Observed amount of occurrences. | False |
| expected_occurrences | Float | Expected amount of occurrences. | False |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |
| moment_definition_id | String |  | False |


### OndeviceMLModel
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Name of the models that were used to detect the crash. Mainly used as internal reference.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| version | String |  | False |
| name | String |  | False |
| flavor | String |  | False |


### OperatingSystem
**Kind**: ENUM

- **android**
- **ios**

### Paging
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging information that allows you to paginate through a large response list.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Paging' | False |
| cursors | [PagingCursors](data-reference-h-p.md#pagingcursors) | The offset cursors to use when paging through results. | False |


### PagingCursors
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging cursors that you use to paginate through a large response set.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'PagingCursors' | False |
| before | String | This is the cursor that points to the start of the page of data that has been returned. | False |
| after | String | This is the cursor that points to the end of the page of data that has been returned. | False |


### PredictionInterval
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| start | String |  | False |
| end | String |  | False |


### PredictionTree
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Multiple possible events that might occur for a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| is_updated | Boolean |  | False |
| probability | Float | Percentage probability of these events taking place.<br><br><code>**Deprecation notice**</code><br>probability is deprecated.<br>No longer relevant. | False |
| events | [IBranchEvent](data-reference-h-p.md#ibranchevent) | The list of events predicted to occur. | False |
| branches | [Branch](data-reference-a-g.md#branch) | <br><code>**Deprecation notice**</code><br>branches is deprecated.<br>Going forward only one prediction will be valid instead of multiple branching predictions. Please check the `events` field. | False |


### PredictionType
**Kind**: ENUM

- **StationaryIntervalPrediction**: Prediction of a Stationary event.
- **TransportIntervalPrediction**: Prediction of a Transport event.

