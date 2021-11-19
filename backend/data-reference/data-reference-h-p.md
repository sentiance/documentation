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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandheldCallingAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | True |


### HandlingWithoutCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandlingWithoutCallingAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | True |


### HandsfreeCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'HandsfreeCallingAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | True |


### IAggregatedAnomaly
**Kind**: INTERFACE

**Implemented by**: [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user over a period of time.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |


### IAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'IAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |


### IBranchEvent
**Kind**: INTERFACE

**Implemented by**: [StationaryPrediction](data-reference-q-z.md#stationaryprediction), [TransportPrediction](data-reference-q-z.md#transportprediction)
A single predicted event.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | True |
| end | String | Predicted end time of the event. | True |
| probability | Float | The probability of this prediction occurring. | True |
| type | [TreePredictionType](data-reference-q-z.md#treepredictiontype) | 'IBranchEvent' | True |


### IDayCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [DayCountAnomaly](data-reference-a-g.md#daycountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_days | Float | Observed amount of days. | True |
| expected_days | Float | Expected amount of days. | True |


### IDistanceAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_distance | Float | Observed distance in meter. | True |
| expected_distance | Float | Expected distance in meter. | True |


### IDurationAnomaly
**Kind**: INTERFACE

**Implemented by**: [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_duration | Float | Observed duration in seconds. | True |
| expected_duration | Float | Expected duration in seconds. | True |


### IEvent
**Kind**: INTERFACE

**Implemented by**: [Trip](data-reference-q-z.md#trip), [Stationary](data-reference-q-z.md#stationary), [Transport](data-reference-q-z.md#transport)
An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-a-g.md#eventtype) | 'IEvent' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| weather | [WeatherRange](data-reference-q-z.md#weatherrange) | Weather data associated with this event. | True |


### IEventFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-z.md#stationaryfeedback), [TransportFeedback](data-reference-q-z.md#transportfeedback)
An occurrence of event feedback submitted by a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| event_feedback | [EventFeedback](data-reference-a-g.md#eventfeedback) |  | True |


### IEventPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| event_type | [EventType](data-reference-a-g.md#eventtype) |  | True |


### IFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-z.md#stationaryfeedback), [TransportFeedback](data-reference-q-z.md#transportfeedback), [CrashFeedback](data-reference-a-g.md#crashfeedback), [MomentFeedback](data-reference-h-p.md#momentfeedback)
An occurrence of feedback submitted by a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'IFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |


### IIntervalPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
A prediction that has a start interval.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  | True |


### IMoment
**Kind**: INTERFACE

**Implemented by**: [GenericMoment](data-reference-a-g.md#genericmoment), [CityMoment](data-reference-a-g.md#citymoment), [CountryMoment](data-reference-a-g.md#countrymoment)
An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'IMoment' | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | True |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | True |


### IMomentAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| moment_definition_id | String |  | True |


### IMomentFeedback
**Kind**: INTERFACE

**Implemented by**: [MomentFeedback](data-reference-h-p.md#momentfeedback)
An occurrence of moment feedback submitted by a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| moment_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  | True |


### IOccurrenceCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_occurrences | Float | Observed amount of occurrences. | True |
| expected_occurrences | Float | Expected amount of occurrences. | True |


### IPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-z.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-z.md#transportintervalprediction)
An occurance of a prediction that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'IPrediction' | True |
| probability | Float |  | True |


### ISegment
**Kind**: INTERFACE

**Implemented by**: [GenericSegment](data-reference-a-g.md#genericsegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [SegmentType](data-reference-q-z.md#segmenttype) | 'ISegment' | True |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. | True |
| segment_definition | [SegmentDefinition](data-reference-q-z.md#segmentdefinition) | The SegmentDefinition this segment relates to. | True |


### IStationaryAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |


### ITimeAggregateAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-a-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-z.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-z.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-q-z.md#workingtimeaggregate)
An attribute that aggregates by TimePeriod.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | True |


### ITransportAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-a-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-a-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-a-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |


### ITransportBehaviorAnnotation
**Kind**: INTERFACE

**Implemented by**: [BoundaryBehaviorAnnotation](data-reference-a-g.md#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](data-reference-a-g.md#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](data-reference-a-g.md#anomalybehaviorannotation), [TurnBehaviorAnnotation](data-reference-q-z.md#turnbehaviorannotation), [HandlingWithoutCallingAnnotation](data-reference-h-p.md#handlingwithoutcallingannotation), [HandsfreeCallingAnnotation](data-reference-h-p.md#handsfreecallingannotation), [HandheldCallingAnnotation](data-reference-h-p.md#handheldcallingannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |


### IUser
**Kind**: INTERFACE

**Implemented by**: [User](data-reference-q-z.md#user), [ControlUser](data-reference-a-g.md#controluser)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'IUser' | True |
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


### IUserAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-a-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-z.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-z.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-q-z.md#workingtimeaggregate)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'IUserAttribute' | True |


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


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'LocationCluster' | True |
| last_visit | String |  | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| address | [Address](data-reference-a-g.md#address) |  | True |
| radius | Int |  | True |
| is_poi | Boolean |  | True |
| significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  | True |


### LocationPlaceCandidate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A place selected from one of our data sources.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' | True |
| name | String | Name of the place. Can be null if no specific place can be assigned. | True |
| categories | [String](data-reference-q-z.md#string) | List of categories for this place, sorted by granularity. Categories might still be provided when name is null, for example when shopping in a shopping street, categories like shopping and retail can still exist.<br><br><code>**Deprecation notice**</code><br>categories is deprecated.<br>These are outdated. Please use `category_hierarchy` instead. | True |
| category_hierarchy | [String](data-reference-q-z.md#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` | True |
| probability | Float |  | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| provider | String |  | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'MomentDefinition' | True |
| id | String | Identifier of this MomentDefinition. Possible values: working_at_work,working_remote,home,morning,lunch,afternoon,evening,night,commute_from_work,commute_from_home,business_trip,holiday,nearby_home,nearby_work,city_name,country,children_drop_off,sport_routine,shopping_routine,evening_entertainment,night_out,afternoon_drinks,evening_drinks,breakfast_out,lunch_out,dinner_out,about_to_working,about_to_commute_from_home,about_to_commute_from_work,about_to_children_drop_off,about_to_sport,about_to_shopping,nearby_poi | True |
| category | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic_time,travel,geography,location,about_to_routine | True |
| display_name | String | A displayable name for this MomentDefinition. | True |
| description | String | A short description about this MomentDefinition. | True |


### MomentFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IMomentFeedback](data-reference-h-p.md#imomentfeedback)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'MomentFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |
| moment_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  | True |
| moment | [IMoment](data-reference-h-p.md#imoment) | The Moment this feedback refers to. | True |


### MomentFeedbackFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| moment_definition_id_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks our detected moment is correct. | True |
| moment_definition_id_feedback | String | Correction by the user in case our detection was incorrect. | True |


### MomentType
**Kind**: ENUM

- **GenericMoment**
- **CityMoment**
- **CountryMoment**

### OccurrenceCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IOccurrenceCountAnomaly](data-reference-h-p.md#ioccurrencecountanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'OccurrenceCountAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |
| observed_occurrences | Float | Observed amount of occurrences. | True |
| expected_occurrences | Float | Expected amount of occurrences. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


### OndeviceMLModel
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Name of the models that were used to detect the crash. Mainly used as internal reference.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| version | String |  | True |
| name | String |  | True |
| flavor | String |  | True |


### OperatingSystem
**Kind**: ENUM

- **android**
- **ios**

### Paging
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging information that allows you to paginate through a large response list.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Paging' | True |
| cursors | [PagingCursors](data-reference-h-p.md#pagingcursors) | The offset cursors to use when paging through results. | True |


### PagingCursors
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging cursors that you use to paginate through a large response set.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'PagingCursors' | True |
| before | String | This is the cursor that points to the start of the page of data that has been returned. | True |
| after | String | This is the cursor that points to the end of the page of data that has been returned. | True |


### PredictionInterval
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String |  | True |
| end | String |  | True |


### PredictionTree
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Multiple possible events that might occur for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| is_updated | Boolean |  | True |
| probability | Float | Percentage probability of these events taking place.<br><br><code>**Deprecation notice**</code><br>probability is deprecated.<br>No longer relevant. | True |
| events | [IBranchEvent](data-reference-h-p.md#ibranchevent) | The list of events predicted to occur. | True |
| branches | [Branch](data-reference-a-g.md#branch) | <br><code>**Deprecation notice**</code><br>branches is deprecated.<br>Going forward only one prediction will be valid instead of multiple branching predictions. Please check the `events` field. | True |


### PredictionType
**Kind**: ENUM

- **StationaryIntervalPrediction**: Prediction of a Stationary event.
- **TransportIntervalPrediction**: Prediction of a Transport event.

