# Data Reference H-L

## Objects

* [HandheldCallingAnnotation](broken-reference)
* [HandlingWithoutCallingAnnotation](broken-reference)
* [HandsfreeCallingAnnotation](broken-reference)
* [LocationCluster](broken-reference)
* [LocationPlaceCandidate](broken-reference)

### HandheldCallingAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITransportBehaviorAnnotation

| Property | Type                            | Description                  | Nullable |
| -------- | ------------------------------- | ---------------------------- | -------- |
| type     | TransportBehaviorAnnotationType | 'HandheldCallingAnnotation'  | True     |
| start    | String                          |                              | True     |
| end      | String                          |                              | True     |
| duration | Int                             | Duration is in milliseconds. | True     |
| path     | BehaviorAnnotationPathWaypoint  |                              | True     |

### HandlingWithoutCallingAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITransportBehaviorAnnotation

| Property | Type                            | Description                        | Nullable |
| -------- | ------------------------------- | ---------------------------------- | -------- |
| type     | TransportBehaviorAnnotationType | 'HandlingWithoutCallingAnnotation' | True     |
| start    | String                          |                                    | True     |
| end      | String                          |                                    | True     |
| duration | Int                             | Duration is in milliseconds.       | True     |
| path     | BehaviorAnnotationPathWaypoint  |                                    | True     |

### HandsfreeCallingAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITransportBehaviorAnnotation

| Property | Type                            | Description                  | Nullable |
| -------- | ------------------------------- | ---------------------------- | -------- |
| type     | TransportBehaviorAnnotationType | 'HandsfreeCallingAnnotation' | True     |
| start    | String                          |                              | True     |
| end      | String                          |                              | True     |
| duration | Int                             | Duration is in milliseconds. | True     |
| path     | BehaviorAnnotationPathWaypoint  |                              | True     |

### IAggregatedAnomaly

**Kind**: INTERFACE

**Implemented by**: AggregatedDistanceAnomaly, AggregatedDurationAnomaly, DayCountAnomaly, OccurrenceCountAnomaly An anomaly that we have detected for a user over a period of time.

| Property  | Type              | Description                                                        | Nullable |
| --------- | ----------------- | ------------------------------------------------------------------ | -------- |
| period    | AnomalyTimePeriod | Aggregation period over which the data is calculated.              | True     |
| day\_part | DayPart           | Optional additional aggregation over which the data is calculated. | True     |

### IAnomaly

**Kind**: INTERFACE

**Implemented by**: DistanceAnomaly, AggregatedDistanceAnomaly, DurationAnomaly, AggregatedDurationAnomaly, DayCountAnomaly, OccurrenceCountAnomaly An anomaly that we have detected for a user.

| Property       | Type         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Nullable |
| -------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type           | AnomalyType  | 'IAnomaly'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| start          | String       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| end            | String       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| analysis\_type | AnalysisType | <p><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| anomaly        | Anomaly      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| sigma          | Float        | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| probability    | Float        | The larger the probability, the more anomaly. Value is between 0.0 and 1.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |

### IBranchEvent

**Kind**: INTERFACE

**Implemented by**: StationaryPrediction, TransportPrediction A single predicted event.

| Property    | Type               | Description                                   | Nullable |
| ----------- | ------------------ | --------------------------------------------- | -------- |
| start       | String             | Predicted start time of the event.            | True     |
| end         | String             | Predicted end time of the event.              | True     |
| probability | Float              | The probability of this prediction occurring. | True     |
| type        | TreePredictionType | 'IBranchEvent'                                | True     |

### IDayCountAnomaly

**Kind**: INTERFACE

**Implemented by**: DayCountAnomaly

| Property       | Type  | Description              | Nullable |
| -------------- | ----- | ------------------------ | -------- |
| observed\_days | Float | Observed amount of days. | True     |
| expected\_days | Float | Expected amount of days. | True     |

### IDistanceAnomaly

**Kind**: INTERFACE

**Implemented by**: DistanceAnomaly, AggregatedDistanceAnomaly

| Property           | Type  | Description                 | Nullable |
| ------------------ | ----- | --------------------------- | -------- |
| observed\_distance | Float | Observed distance in meter. | True     |
| expected\_distance | Float | Expected distance in meter. | True     |

### IDurationAnomaly

**Kind**: INTERFACE

**Implemented by**: DurationAnomaly, AggregatedDurationAnomaly

| Property           | Type  | Description                   | Nullable |
| ------------------ | ----- | ----------------------------- | -------- |
| observed\_duration | Float | Observed duration in seconds. | True     |
| expected\_duration | Float | Expected duration in seconds. | True     |

### IEvent

**Kind**: INTERFACE

**Implemented by**: Trip, Stationary, Transport An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property            | Type         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Nullable |
| ------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                | EventType    | 'IEvent'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| event\_id           | String       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | False    |
| previous\_event\_id | String       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| next\_event\_id     | String       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| start               | String       | <p>The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| end                 | String       | <p>The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | True     |
| start\_ts           | BigInt       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| end\_ts             | BigInt       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| analysis\_type      | AnalysisType | <p>How well this event is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| weather             | WeatherRange | Weather data associated with this event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |

### IEventFeedback

**Kind**: INTERFACE

**Implemented by**: StationaryFeedback, TransportFeedback An occurrence of event feedback submitted by a user.

| Property        | Type          | Description | Nullable |
| --------------- | ------------- | ----------- | -------- |
| event\_feedback | EventFeedback |             | True     |

### IEventPrediction

**Kind**: INTERFACE

**Implemented by**: StationaryIntervalPrediction, TransportIntervalPrediction An occurrence of an event prediction that we have detected for a user.

| Property    | Type      | Description | Nullable |
| ----------- | --------- | ----------- | -------- |
| event\_type | EventType |             | True     |

### IFeedback

**Kind**: INTERFACE

**Implemented by**: StationaryFeedback, TransportFeedback, CrashFeedback, MomentFeedback An occurrence of feedback submitted by a user.

| Property         | Type         | Description                                                                        | Nullable |
| ---------------- | ------------ | ---------------------------------------------------------------------------------- | -------- |
| type             | FeedbackType | 'IFeedback'                                                                        | True     |
| start            | String       | Start time the feedback relates to, sourced by the event, moment or user-provided. | False    |
| end              | String       | End time the feedback relates to, sourced by the event, moment or user-provided.   | True     |
| created          | String       | Time when this feedback entry was created.                                         | True     |
| projection\_time | String       | Time to provide when the feedback data was read from the API. ISO8601. Optional.   | True     |

### IIntervalPrediction

**Kind**: INTERFACE

**Implemented by**: StationaryIntervalPrediction, TransportIntervalPrediction A prediction that has a start interval.

| Property        | Type               | Description | Nullable |
| --------------- | ------------------ | ----------- | -------- |
| start\_interval | PredictionInterval |             | True     |

### IMoment

**Kind**: INTERFACE

**Implemented by**: GenericMoment, CityMoment, CountryMoment An occurrence of a MomentDefinition that we have detected for a user.

| Property               | Type             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Nullable |
| ---------------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                   | MomentType       | 'IMoment'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | True     |
| start                  | String           | <p>The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | True     |
| end                    | String           | <p>The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | True     |
| start\_ts              | BigInt           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | True     |
| end\_ts                | BigInt           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | True     |
| analysis\_type         | AnalysisType     | <p>How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| moment\_definition\_id | String           | The ID of the MomentDefinition this moment relates to.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | True     |
| moment\_definition     | MomentDefinition | The MomentDefinition this moment relates to.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | True     |

### IMomentAnomaly

**Kind**: INTERFACE

**Implemented by**: DistanceAnomaly, AggregatedDistanceAnomaly, DurationAnomaly, AggregatedDurationAnomaly, DayCountAnomaly, OccurrenceCountAnomaly

| Property               | Type   | Description | Nullable |
| ---------------------- | ------ | ----------- | -------- |
| moment\_definition\_id | String |             | True     |

### IMomentFeedback

**Kind**: INTERFACE

**Implemented by**: MomentFeedback An occurrence of moment feedback submitted by a user.

| Property         | Type                   | Description | Nullable |
| ---------------- | ---------------------- | ----------- | -------- |
| moment\_feedback | MomentFeedbackFeedback |             | True     |

### IOccurrenceCountAnomaly

**Kind**: INTERFACE

**Implemented by**: OccurrenceCountAnomaly

| Property              | Type  | Description                     | Nullable |
| --------------------- | ----- | ------------------------------- | -------- |
| observed\_occurrences | Float | Observed amount of occurrences. | True     |
| expected\_occurrences | Float | Expected amount of occurrences. | True     |

### IPrediction

**Kind**: INTERFACE

**Implemented by**: StationaryIntervalPrediction, TransportIntervalPrediction An occurance of a prediction that we have detected for a user.

| Property    | Type           | Description   | Nullable |
| ----------- | -------------- | ------------- | -------- |
| type        | PredictionType | 'IPrediction' | True     |
| probability | Float          |               | True     |

### ISegment

**Kind**: INTERFACE

**Implemented by**: GenericSegment An occurrence of a SegmentDefinition that we have detected for this user.

| Property                | Type              | Description                                              | Nullable |
| ----------------------- | ----------------- | -------------------------------------------------------- | -------- |
| type                    | SegmentType       | 'ISegment'                                               | True     |
| segment\_definition\_id | String            | The ID of the SegmentDefinition this segment relates to. | True     |
| segment\_definition     | SegmentDefinition | The SegmentDefinition this segment relates to.           | True     |

### IStationaryAnomaly

**Kind**: INTERFACE

**Implemented by**: DistanceAnomaly, AggregatedDistanceAnomaly, DurationAnomaly, AggregatedDurationAnomaly, DayCountAnomaly, OccurrenceCountAnomaly

| Property               | Type                 | Description | Nullable |
| ---------------------- | -------------------- | ----------- | -------- |
| place\_category        | String               |             | True     |
| location\_significance | LocationSignificance |             | True     |

### ITimeAggregateAttribute

**Kind**: INTERFACE

**Implemented by**: CommuteTimeAggregate, StationaryTimeAggregate, TransportTimeAggregate, WorkingTimeAggregate An attribute that aggregates by TimePeriod.

| Property | Type       | Description | Nullable |
| -------- | ---------- | ----------- | -------- |
| period   | TimePeriod |             | True     |

### ITransportAnomaly

**Kind**: INTERFACE

**Implemented by**: DistanceAnomaly, AggregatedDistanceAnomaly, DurationAnomaly, AggregatedDurationAnomaly, DayCountAnomaly, OccurrenceCountAnomaly

| Property                  | Type                  | Description | Nullable |
| ------------------------- | --------------------- | ----------- | -------- |
| transport\_mode           | TransportMode         |             | True     |
| transport\_mode\_category | TransportModeCategory |             | True     |

### ITransportBehaviorAnnotation

**Kind**: INTERFACE

**Implemented by**: BoundaryBehaviorAnnotation, AccelerationBehaviorAnnotation, AnomalyBehaviorAnnotation, TurnBehaviorAnnotation, HandlingWithoutCallingAnnotation, HandsfreeCallingAnnotation, HandheldCallingAnnotation

| Property | Type                            | Description                    | Nullable |
| -------- | ------------------------------- | ------------------------------ | -------- |
| type     | TransportBehaviorAnnotationType | 'ITransportBehaviorAnnotation' | True     |
| start    | String                          |                                | True     |
| end      | String                          |                                | True     |

### IUser

**Kind**: INTERFACE

**Implemented by**: User, ControlUser

| Property                    | Type                     | Description                                                                                                                                                                     | Nullable |
| --------------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                        | UserType                 | 'IUser'                                                                                                                                                                         | True     |
| id                          | String                   | The unique identifier for this user.                                                                                                                                            | True     |
| can\_login                  | Boolean                  |                                                                                                                                                                                 | True     |
| created\_at                 | String                   | <p>The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00</p>                                                                               | True     |
| sdk                         | UserSdkSettings          |                                                                                                                                                                                 | True     |
| application\_id             | String                   | The ID of the Application this user relates to.                                                                                                                                 | True     |
| application                 | Application              | The Application this user relates to.                                                                                                                                           | True     |
| custom\_event\_history      | CustomEvent              | Custom Event History                                                                                                                                                            | True     |
| event\_history              | IEvent                   | An unordered list of events we have detected for this user.                                                                                                                     | True     |
| car\_behavior               | UserCarBehavior          | The user car behavior aggregated over the last 9 weeks.                                                                                                                         | True     |
| aggregated\_driving\_scores | UserTimeAggregatedScores |                                                                                                                                                                                 | True     |
| transport\_heatmaps         | TransportHeatmaps        | <p>The aggregated transport heatmaps calculated over time.<br><br><strong><code>Deprecation notice</code></strong><br>transport_heatmaps is deprecated.<br>No longer used.</p>  | True     |
| metadata                    | JSON                     | All custom set metadata properties on this user. This is a JSON object with key->value pairs.                                                                                   | True     |
| device                      | DeviceInfo               | The last known active tracking device metadata                                                                                                                                  | True     |
| active\_moments             | IMoment                  | An unordered list of moments that are ongoing from the point of view of the platform.                                                                                           | True     |
| moment\_history             | IMoment                  | An unordered list of moments we have detected for this user.                                                                                                                    | True     |
| semantic\_time              | UserSemanticTime         | The user's semantic time averaged over time.                                                                                                                                    | True     |
| anomaly\_history            | IAnomaly                 | <p><br><strong><code>Deprecation notice</code></strong><br>anomaly_history is deprecated.<br>No longer relevant.</p>                                                            | True     |
| segments                    | ISegment                 | An unordered list of segments that are detected for this user.                                                                                                                  | True     |
| location\_clusters          | LocationCluster          | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...)                                        | True     |
| location                    | Waypoint                 | The last known location we have for this user.                                                                                                                                  | True     |
| health                      | UserHealth               | The historical health attributes.                                                                                                                                               | True     |
| attributes                  | IUserAttribute           |                                                                                                                                                                                 | True     |
| predictions                 | IPrediction              | <p>Event/Moment predictions for this user<br><br><strong><code>Deprecation notice</code></strong><br>predictions is deprecated.<br>Please use <code>prediction_tree</code>.</p> | True     |
| prediction\_tree            | PredictionTree           | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place.                 | True     |
| feedback                    | IFeedback                | <p>Feedback on this user<br><br><strong><code>Deprecation notice</code></strong><br>feedback is deprecated.<br>Replaced by feedback_history</p>                                 | True     |
| feedback\_history           | IFeedback                | Feedback on this user                                                                                                                                                           | True     |
| step\_count                 | UserStepCount            | Step count details of the given user on the given date range. This feature is currently in Beta, for additional information contact support@sentiance.com.                      | True     |

### IUserAttribute

**Kind**: INTERFACE

**Implemented by**: CommuteTimeAggregate, StationaryTimeAggregate, TransportTimeAggregate, WorkingTimeAggregate

| Property | Type              | Description      | Nullable |
| -------- | ----------------- | ---------------- | -------- |
| type     | UserAttributeType | 'IUserAttribute' | True     |

### InputAddress

**Kind**: INPUT\_OBJECT

### InputCrash

**Kind**: INPUT\_OBJECT

### InputCrashFeedback

**Kind**: INPUT\_OBJECT

### InputEventFeedback

**Kind**: INPUT\_OBJECT

### InputLocationPlaceCandidate

**Kind**: INPUT\_OBJECT

### InputMoment

**Kind**: INPUT\_OBJECT

### InputMomentFeedback

**Kind**: INPUT\_OBJECT

### InputOndeviceMLModel

**Kind**: INPUT\_OBJECT

Name of the models that were used to detect the crash. Mainly used as internal reference.

### InputStationary

**Kind**: INPUT\_OBJECT

### InputStationaryLocation

**Kind**: INPUT\_OBJECT

### InputTrajectoryWaypoint

**Kind**: INPUT\_OBJECT

A single waypoint in the augmented trajectory.

### InputTransport

**Kind**: INPUT\_OBJECT

### InputTransportBehaviorFeatures

**Kind**: SCALAR

### InputTransportBehaviorScores

**Kind**: SCALAR

### InputTransportTrajectory

**Kind**: INPUT\_OBJECT

### InputWaypoint

**Kind**: INPUT\_OBJECT

### JSON

**Kind**: SCALAR

The `JSON` scalar type represents JSON values as specified by [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf).

### LocationCluster

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property     | Type                   | Description       | Nullable |
| ------------ | ---------------------- | ----------------- | -------- |
| type         | String                 | 'LocationCluster' | True     |
| last\_visit  | String                 |                   | True     |
| latitude     | Float                  |                   | True     |
| longitude    | Float                  |                   | True     |
| address      | Address                |                   | True     |
| radius       | Int                    |                   | True     |
| is\_poi      | Boolean                |                   | True     |
| significance | LocationSignificance   |                   | True     |
| place        | LocationPlaceCandidate |                   | True     |

### LocationPlaceCandidate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A place selected from one of our data sources.

| Property            | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                 | Nullable |
| ------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                | String | 'LocationPlaceCandidate'                                                                                                                                                                                                                                                                                                                                                                    | True     |
| name                | String | Name of the place. Can be null if no specific place can be assigned.                                                                                                                                                                                                                                                                                                                        | True     |
| categories          | String | <p>List of categories for this place, sorted by granularity. Categories might still be provided when name is null, for example when shopping in a shopping street, categories like shopping and retail can still exist.<br><br><strong><code>Deprecation notice</code></strong><br>categories is deprecated.<br>These are outdated. Please use <code>category_hierarchy</code> instead.</p> | True     |
| category\_hierarchy | String | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]`                                                                                                                                                                            | True     |
| probability         | Float  |                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| latitude            | Float  |                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| longitude           | Float  |                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| provider            | String |                                                                                                                                                                                                                                                                                                                                                                                             | True     |

### LocationSignificance

**Kind**: ENUM

* **home**: A location identified as one of the user's home locations.
* **work**: A location identified as one of the user's work locations.
* **regular**: Locations you regularly visit. Typical examples are places you regularly go shopping, your gym, a friend's place, ...
* **nonregular**: Default type for locations you don't often visit.
* **poi**: Points of interest that have not been classified as home/work previously.
* **new**: Only available a short time when you visit the location the first time.
