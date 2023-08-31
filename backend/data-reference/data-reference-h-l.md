# Data Reference H-L

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Objects
- [HandheldCallingAnnotation](#handheldcallingannotation)
- [HandlingWithoutCallingAnnotation](#handlingwithoutcallingannotation)
- [HandsfreeCallingAnnotation](#handsfreecallingannotation)
- [LocationCluster](#locationcluster)
- [LocationPlaceCandidate](#locationplacecandidate)

### HandheldCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'HandheldCallingAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-b.md#behaviorannotationpathwaypoint) |  | True |


### HandlingWithoutCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'HandlingWithoutCallingAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-b.md#behaviorannotationpathwaypoint) |  | True |


### HandsfreeCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'HandsfreeCallingAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-b.md#behaviorannotationpathwaypoint) |  | True |


### IAggregatedAnomaly
**Kind**: INTERFACE

**Implemented by**: [AggregatedDistanceAnomaly](data-reference-a-b.md#aggregateddistanceanomaly), [AggregatedDurationAnomaly](data-reference-a-b.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-c-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-m-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user over a period of time.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| period | [AnomalyTimePeriod](data-reference-a-b.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-c-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |


### IAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-c-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-b.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-c-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-b.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-c-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-m-p.md#occurrencecountanomaly)
An anomaly that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-b.md#anomalytype) | 'IAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-b.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |


### IBranchEvent
**Kind**: INTERFACE

**Implemented by**: [StationaryPrediction](data-reference-q-t.md#stationaryprediction), [TransportPrediction](data-reference-q-t.md#transportprediction)
A single predicted event.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String | Predicted start time of the event. | True |
| end | String | Predicted end time of the event. | True |
| probability | Float | The probability of this prediction occurring. | True |
| type | [TreePredictionType](data-reference-q-t.md#treepredictiontype) | 'IBranchEvent' | True |


### IDayCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [DayCountAnomaly](data-reference-c-g.md#daycountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_days | Float | Observed amount of days. | True |
| expected_days | Float | Expected amount of days. | True |


### IDistanceAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-c-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-b.md#aggregateddistanceanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_distance | Float | Observed distance in meter. | True |
| expected_distance | Float | Expected distance in meter. | True |


### IDurationAnomaly
**Kind**: INTERFACE

**Implemented by**: [DurationAnomaly](data-reference-c-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-b.md#aggregateddurationanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_duration | Float | Observed duration in seconds. | True |
| expected_duration | Float | Expected duration in seconds. | True |


### IEvent
**Kind**: INTERFACE

**Implemented by**: [Trip](data-reference-q-t.md#trip), [Stationary](data-reference-q-t.md#stationary), [Transport](data-reference-q-t.md#transport)
An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [EventType](data-reference-c-g.md#eventtype) | 'IEvent' | True |
| event_id | String |  | False |
| previous_event_id | String |  | True |
| next_event_id | String |  | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| weather | [WeatherRange](data-reference-u-z.md#weatherrange) | Weather data associated with this event. | True |


### IEventFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-t.md#stationaryfeedback), [TransportFeedback](data-reference-q-t.md#transportfeedback)
An occurrence of event feedback submitted by a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| event_feedback | [EventFeedback](data-reference-c-g.md#eventfeedback) |  | True |


### IEventPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-t.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-t.md#transportintervalprediction)
An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| event_type | [EventType](data-reference-c-g.md#eventtype) |  | True |


### IFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-q-t.md#stationaryfeedback), [TransportFeedback](data-reference-q-t.md#transportfeedback), [CrashFeedback](data-reference-c-g.md#crashfeedback), [MomentFeedback](data-reference-m-p.md#momentfeedback)
An occurrence of feedback submitted by a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-c-g.md#feedbacktype) | 'IFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |


### IIntervalPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-t.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-t.md#transportintervalprediction)
A prediction that has a start interval.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start_interval | [PredictionInterval](data-reference-m-p.md#predictioninterval) |  | True |


### IMoment
**Kind**: INTERFACE

**Implemented by**: [GenericMoment](data-reference-c-g.md#genericmoment), [CityMoment](data-reference-c-g.md#citymoment), [CountryMoment](data-reference-c-g.md#countrymoment)
An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-m-p.md#momenttype) | 'IMoment' | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-b.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | True |
| moment_definition | [MomentDefinition](data-reference-m-p.md#momentdefinition) | The MomentDefinition this moment relates to. | True |


### IMomentAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-c-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-b.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-c-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-b.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-c-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-m-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| moment_definition_id | String |  | True |


### IMomentFeedback
**Kind**: INTERFACE

**Implemented by**: [MomentFeedback](data-reference-m-p.md#momentfeedback)
An occurrence of moment feedback submitted by a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| moment_feedback | [MomentFeedbackFeedback](data-reference-m-p.md#momentfeedbackfeedback) |  | True |


### IOccurrenceCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [OccurrenceCountAnomaly](data-reference-m-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| observed_occurrences | Float | Observed amount of occurrences. | True |
| expected_occurrences | Float | Expected amount of occurrences. | True |


### IPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-q-t.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-q-t.md#transportintervalprediction)
An occurance of a prediction that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [PredictionType](data-reference-m-p.md#predictiontype) | 'IPrediction' | True |
| probability | Float |  | True |


### ISegment
**Kind**: INTERFACE

**Implemented by**: [GenericSegment](data-reference-c-g.md#genericsegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [SegmentType](data-reference-q-t.md#segmenttype) | 'ISegment' | True |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. | True |
| segment_definition | [SegmentDefinition](data-reference-q-t.md#segmentdefinition) | The SegmentDefinition this segment relates to. | True |


### IStationaryAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-c-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-b.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-c-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-b.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-c-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-m-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-l.md#locationsignificance) |  | True |


### ITimeAggregateAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-c-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-t.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-t.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-u-z.md#workingtimeaggregate)
An attribute that aggregates by TimePeriod.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| period | [TimePeriod](data-reference-q-t.md#timeperiod) |  | True |


### ITransportAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-c-g.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-a-b.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-c-g.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-a-b.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-c-g.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-m-p.md#occurrencecountanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| transport_mode | [TransportMode](data-reference-q-t.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-t.md#transportmodecategory) |  | True |


### ITransportBehaviorAnnotation
**Kind**: INTERFACE

**Implemented by**: [BoundaryBehaviorAnnotation](data-reference-a-b.md#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](data-reference-a-b.md#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](data-reference-a-b.md#anomalybehaviorannotation), [TurnBehaviorAnnotation](data-reference-q-t.md#turnbehaviorannotation), [HandlingWithoutCallingAnnotation](data-reference-h-l.md#handlingwithoutcallingannotation), [HandsfreeCallingAnnotation](data-reference-h-l.md#handsfreecallingannotation), [HandheldCallingAnnotation](data-reference-h-l.md#handheldcallingannotation), [CrashAnnotation](data-reference-c-g.md#crashannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |


### IUser
**Kind**: INTERFACE

**Implemented by**: [User](data-reference-u-z.md#user), [ControlUser](data-reference-c-g.md#controluser)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-u-z.md#usertype) | 'IUser' | True |
| id | String | The unique identifier for this user. | True |
| can_login | Boolean |  | True |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| sdk | [UserSdkSettings](data-reference-u-z.md#usersdksettings) |  | True |
| application_id | String | The ID of the Application this user relates to. | True |
| application | [Application](data-reference-a-b.md#application) | The Application this user relates to. | True |
| custom_event_history | [CustomEvent](data-reference-c-g.md#customevent) | Custom Event History | True |
| event_history | [IEvent](data-reference-h-l.md#ievent) | An unordered list of events we have detected for this user. | True |
| car_behavior | [UserCarBehavior](data-reference-u-z.md#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. | True |
| aggregated_driving_scores | [UserTimeAggregatedScores](data-reference-u-z.md#usertimeaggregatedscores) |  | True |
| transport_heatmaps | [TransportHeatmaps](data-reference-q-t.md#transportheatmaps) | The aggregated transport heatmaps calculated over time.<br><br><code>**Deprecation notice**</code><br>transport_heatmaps is deprecated.<br>No longer used. | True |
| metadata | [JSON](data-reference-h-l.md#json) | All custom set metadata properties on this user. This is a JSON object with key->value pairs. | True |
| device | [DeviceInfo](data-reference-c-g.md#deviceinfo) | The last known active tracking device metadata | True |
| active_moments | [IMoment](data-reference-h-l.md#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. | True |
| moment_history | [IMoment](data-reference-h-l.md#imoment) | An unordered list of moments we have detected for this user. | True |
| semantic_time | [UserSemanticTime](data-reference-u-z.md#usersemantictime) | The user's semantic time averaged over time. | True |
| anomaly_history | [IAnomaly](data-reference-h-l.md#ianomaly) | <br><code>**Deprecation notice**</code><br>anomaly_history is deprecated.<br>No longer relevant. | True |
| segments | [ISegment](data-reference-h-l.md#isegment) | An unordered list of segments that are detected for this user. | True |
| location_clusters | [LocationCluster](data-reference-h-l.md#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...) | True |
| location | [Waypoint](data-reference-u-z.md#waypoint) | The last known location we have for this user. | True |
| health | [UserHealth](data-reference-u-z.md#userhealth) | The historical health attributes.<br><br><code>**Deprecation notice**</code><br>health is deprecated.<br>No longer supported | True |
| attributes | [IUserAttribute](data-reference-h-l.md#iuserattribute) | <br><code>**Deprecation notice**</code><br>attributes is deprecated.<br>No longer supported. | True |
| predictions | [IPrediction](data-reference-h-l.md#iprediction) | Event/Moment predictions for this user<br><br><code>**Deprecation notice**</code><br>predictions is deprecated.<br>Please use `prediction_tree`. | True |
| prediction_tree | [PredictionTree](data-reference-m-p.md#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. | True |
| feedback | [IFeedback](data-reference-h-l.md#ifeedback) | Feedback on this user<br><br><code>**Deprecation notice**</code><br>feedback is deprecated.<br>Replaced by feedback_history | True |
| feedback_history | [IFeedback](data-reference-h-l.md#ifeedback) | Feedback on this user | True |
| step_count | [UserStepCount](data-reference-u-z.md#userstepcount) | Step count details of the given user on the given date range. This feature is currently in Beta, for additional information contact support@sentiance.com. | True |


### IUserAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-c-g.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-q-t.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-q-t.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-u-z.md#workingtimeaggregate)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-u-z.md#userattributetype) | 'IUserAttribute' | True |


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
| address | [Address](data-reference-a-b.md#address) |  | True |
| radius | Int |  | True |
| is_poi | Boolean |  | True |
| significance | [LocationSignificance](data-reference-h-l.md#locationsignificance) |  | True |
| place | [LocationPlaceCandidate](data-reference-h-l.md#locationplacecandidate) |  | True |


### LocationPlaceCandidate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A place selected from one of our data sources.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' | True |
| name | String | Name of the place. Can be null if no specific place can be assigned. | True |
| categories | [String](data-reference-q-t.md#string) | List of categories for this place, sorted by granularity. Categories might still be provided when name is null, for example when shopping in a shopping street, categories like shopping and retail can still exist.<br><br><code>**Deprecation notice**</code><br>categories is deprecated.<br>These are outdated. Please use `category_hierarchy` instead. | True |
| category_hierarchy | [String](data-reference-q-t.md#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` | True |
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

