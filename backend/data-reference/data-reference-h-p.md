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

**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'HandheldCallingAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](#behaviorannotationpathwaypoint) |  |


### HandlingWithoutCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'HandlingWithoutCallingAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](#behaviorannotationpathwaypoint) |  |


### HandsfreeCallingAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'HandsfreeCallingAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](#behaviorannotationpathwaypoint) |  |


### IAggregatedAnomaly
**Kind**: INTERFACE

**Implemented by**: [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)
An anomaly that we have detected for a user over a period of time.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [AnomalyTimePeriod](#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](#daypart) | Optional additional aggregation over which the data is calculated. |


### IAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)
An anomaly that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'IAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |


### IBranchEvent
**Kind**: INTERFACE

**Implemented by**: [StationaryPrediction](#stationaryprediction), [TransportPrediction](#transportprediction)
A single predicted event.

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](#treepredictiontype) | 'IBranchEvent' |


### IDayCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [DayCountAnomaly](#daycountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_days | Float | Observed amount of days. |
| expected_days | Float | Expected amount of days. |


### IDistanceAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_distance | Float | Observed distance in meter. |
| expected_distance | Float | Expected distance in meter. |


### IDurationAnomaly
**Kind**: INTERFACE

**Implemented by**: [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_duration | Float | Observed duration in seconds. |
| expected_duration | Float | Expected duration in seconds. |


### IEvent
**Kind**: INTERFACE

**Implemented by**: [Trip](#trip), [Stationary](#stationary), [Transport](#transport)
An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](#eventtype) | 'IEvent' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| weather | [WeatherRange](#weatherrange) | Weather data associated with this event. |


### IEventFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](#stationaryfeedback), [TransportFeedback](#transportfeedback)
An occurrence of event feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event_feedback | [EventFeedback](#eventfeedback) |  |


### IEventPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](#stationaryintervalprediction), [TransportIntervalPrediction](#transportintervalprediction)
An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event_type | [EventType](#eventtype) |  |


### IFeedback
**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](#stationaryfeedback), [TransportFeedback](#transportfeedback), [MomentFeedback](#momentfeedback)
An occurrence of feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](#feedbacktype) | 'IFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |


### IIntervalPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](#stationaryintervalprediction), [TransportIntervalPrediction](#transportintervalprediction)
A prediction that has a start interval.

| Property | Type | Description |
| :--- | :--- | :--- |
| start_interval | [PredictionInterval](#predictioninterval) |  |


### IMoment
**Kind**: INTERFACE

**Implemented by**: [GenericMoment](#genericmoment), [CityMoment](#citymoment), [CountryMoment](#countrymoment)
An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'IMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |


### IMomentAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| moment_definition_id | String |  |


### IMomentFeedback
**Kind**: INTERFACE

**Implemented by**: [MomentFeedback](#momentfeedback)
An occurrence of moment feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| moment_feedback | [MomentFeedbackFeedback](#momentfeedbackfeedback) |  |


### IOccurrenceCountAnomaly
**Kind**: INTERFACE

**Implemented by**: [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_occurrences | Float | Observed amount of occurrences. |
| expected_occurrences | Float | Expected amount of occurrences. |


### IPrediction
**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](#stationaryintervalprediction), [TransportIntervalPrediction](#transportintervalprediction)
An occurance of a prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](#predictiontype) | 'IPrediction' |
| probability | Float |  |


### ISegment
**Kind**: INTERFACE

**Implemented by**: [GenericSegment](#genericsegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](#segmenttype) | 'ISegment' |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. |
| segment_definition | [SegmentDefinition](#segmentdefinition) | The SegmentDefinition this segment relates to. |


### IStationaryAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |


### ITimeAggregateAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](#commutetimeaggregate), [StationaryTimeAggregate](#stationarytimeaggregate), [TransportTimeAggregate](#transporttimeaggregate), [WorkingTimeAggregate](#workingtimeaggregate)
An attribute that aggregates by TimePeriod.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [TimePeriod](#timeperiod) |  |


### ITransportAnomaly
**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |


### ITransportBehaviorAnnotation
**Kind**: INTERFACE

**Implemented by**: [BoundaryBehaviorAnnotation](#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](#anomalybehaviorannotation), [TurnBehaviorAnnotation](#turnbehaviorannotation), [HandlingWithoutCallingAnnotation](#handlingwithoutcallingannotation), [HandsfreeCallingAnnotation](#handsfreecallingannotation), [HandheldCallingAnnotation](#handheldcallingannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' |
| start | String |  |
| end | String |  |


### IUser
**Kind**: INTERFACE

**Implemented by**: [User](#user), [ControlUser](#controluser)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](#usertype) | 'IUser' |
| id | String | The unique identifier for this user. |
| can_login | Boolean |  |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](#usersdksettings) |  |
| application_id | String | The ID of the Application this user relates to. |
| application | [Application](#application) | The Application this user relates to. |
| custom_event_history | [CustomEvent](#customevent) | Custom Event History |
| event_history | [IEvent](#ievent) | An unordered list of events we have detected for this user. |
| car_behavior | [UserCarBehavior](#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
| aggregated_driving_scores | [UserTimeAggregatedScores](#usertimeaggregatedscores) |  |
| transport_heatmaps | [TransportHeatmaps](#transportheatmaps) | The aggregated transport heatmaps calculated over time. |
| metadata | [JSON](#json) | All custom set metadata properties on this user. This is a JSON object with key->value pairs. |
| device | [DeviceInfo](#deviceinfo) | The last known active tracking device metadata |
| active_moments | [IMoment](#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. |
| moment_history | [IMoment](#imoment) | An unordered list of moments we have detected for this user. |
| semantic_time | [UserSemanticTime](#usersemantictime) | The user's semantic time averaged over time. |
| anomaly_history | [IAnomaly](#ianomaly) |  |
| segments | [ISegment](#isegment) | An unordered list of segments that are detected for this user. |
| location_clusters | [LocationCluster](#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...) |
| location | [Waypoint](#waypoint) | The last known location we have for this user. |
| health | [UserHealth](#userhealth) | The historical health attributes. |
| attributes | [IUserAttribute](#iuserattribute) |  |
| predictions | [IPrediction](#iprediction) | Event/Moment predictions for this user |
| prediction_tree | [PredictionTree](#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. |
| feedback_history | [IFeedback](#ifeedback) | Feedback on this user |


### IUserAttribute
**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](#commutetimeaggregate), [StationaryTimeAggregate](#stationarytimeaggregate), [TransportTimeAggregate](#transporttimeaggregate), [WorkingTimeAggregate](#workingtimeaggregate)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](#userattributetype) | 'IUserAttribute' |


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
| address | [Address](#address) |  |
| radius | Int |  |
| is_poi | Boolean |  |
| significance | [LocationSignificance](#locationsignificance) |  |
| place | [LocationPlaceCandidate](#locationplacecandidate) |  |


### LocationPlaceCandidate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A place selected from one of our data sources.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' |
| name | String | Name of the place. Can be null if no specific place can be assigned. |
| category_hierarchy | [String](#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` |
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

**Implements**: [IFeedback](#ifeedback), [IMomentFeedback](#imomentfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](#feedbacktype) | 'MomentFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| moment_feedback | [MomentFeedbackFeedback](#momentfeedbackfeedback) |  |
| moment | [IMoment](#imoment) | The Moment this feedback refers to. |


### MomentFeedbackFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| moment_definition_id_assessment | [FeedbackAssessment](#feedbackassessment) | If the user thinks our detected moment is correct. |
| moment_definition_id_feedback | String | Correction by the user in case our detection was incorrect. |


### MomentType
**Kind**: ENUM

- **GenericMoment**
- **CityMoment**
- **CountryMoment**

### OccurrenceCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](#ianomaly), [IOccurrenceCountAnomaly](#ioccurrencecountanomaly), [IAggregatedAnomaly](#iaggregatedanomaly), [IStationaryAnomaly](#istationaryanomaly), [ITransportAnomaly](#itransportanomaly), [IMomentAnomaly](#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'OccurrenceCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](#daypart) | Optional additional aggregation over which the data is calculated. |
| observed_occurrences | Float | Observed amount of occurrences. |
| expected_occurrences | Float | Expected amount of occurrences. |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |
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
| cursors | [PagingCursors](#pagingcursors) | The offset cursors to use when paging through results. |


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
| events | [IBranchEvent](#ibranchevent) | The list of events predicted to occur. |


### PredictionType
**Kind**: ENUM

- **StationaryIntervalPrediction**: Prediction of a Stationary event.
- **TransportIntervalPrediction**: Prediction of a Transport event.

