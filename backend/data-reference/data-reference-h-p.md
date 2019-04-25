# Data Reference H-P

## Objects

* [LocationCluster](data-reference-h-p.md#locationcluster)
* [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate)
* [MomentDefinition](data-reference-h-p.md#momentdefinition)
* [MomentFeedback](data-reference-h-p.md#momentfeedback)
* [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback)
* [Mutation](data-reference-h-p.md#mutation)
* [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)
* [Paging](data-reference-h-p.md#paging)
* [PagingCursors](data-reference-h-p.md#pagingcursors)
* [PredictionInterval](data-reference-h-p.md#predictioninterval)
* [PredictionTree](data-reference-h-p.md#predictiontree)

### IAggregatedAnomaly

**Kind**: INTERFACE

**Implemented by**: [AggregatedDistanceAnomaly](data-reference-h-p.md#aggregateddistanceanomaly), [AggregatedDurationAnomaly](data-reference-h-p.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-h-p.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly) An anomaly that we have detected for a user over a period of time.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [AnomalyTimePeriod](data-reference-h-p.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference-h-p.md#daypart) | Optional additional aggregation over which the data is calculated. |

### IAnomaly

**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-h-p.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-h-p.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-h-p.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-h-p.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-h-p.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly) An anomaly that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-h-p.md#anomalytype) | 'IAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference-h-p.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-h-p.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |

### IBranchEvent

**Kind**: INTERFACE

**Implemented by**: [StationaryPrediction](data-reference-h-p.md#stationaryprediction), [TransportPrediction](data-reference-h-p.md#transportprediction) A single predicted event.

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](data-reference-h-p.md#treepredictiontype) | 'IBranchEvent' |

### IDayCountAnomaly

**Kind**: INTERFACE

**Implemented by**: [DayCountAnomaly](data-reference-h-p.md#daycountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_days | Float | Observed amount of days. |
| expected\_days | Float | Expected amount of days. |

### IDistanceAnomaly

**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-h-p.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-h-p.md#aggregateddistanceanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_distance | Float | Observed distance in meter. |
| expected\_distance | Float | Expected distance in meter. |

### IDurationAnomaly

**Kind**: INTERFACE

**Implemented by**: [DurationAnomaly](data-reference-h-p.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-h-p.md#aggregateddurationanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_duration | Float | Observed duration in seconds. |
| expected\_duration | Float | Expected duration in seconds. |

### IEvent

**Kind**: INTERFACE

**Implemented by**: [Trip](data-reference-h-p.md#trip), [Stationary](data-reference-h-p.md#stationary), [Transport](data-reference-h-p.md#transport) An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](data-reference-h-p.md#eventtype) | 'IEvent' |
| event\_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| start\_ts | [BigInt](data-reference-h-p.md#bigint) |  |
| end\_ts | [BigInt](data-reference-h-p.md#bigint) |  |
| analysis\_type | [AnalysisType](data-reference-h-p.md#analysistype) | How well this event is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. |
| weather | [WeatherRange](data-reference-h-p.md#weatherrange) | Weather data associated with this event. |

### IEventFeedback

**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-h-p.md#stationaryfeedback), [TransportFeedback](data-reference-h-p.md#transportfeedback) An occurrence of event feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event\_feedback | [EventFeedback](data-reference-h-p.md#eventfeedback) |  |

### IEventPrediction

**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-h-p.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-h-p.md#transportintervalprediction) An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event\_type | [EventType](data-reference-h-p.md#eventtype) |  |

### IFeedback

**Kind**: INTERFACE

**Implemented by**: [StationaryFeedback](data-reference-h-p.md#stationaryfeedback), [TransportFeedback](data-reference-h-p.md#transportfeedback), [MomentFeedback](data-reference-h-p.md#momentfeedback) An occurrence of feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference-h-p.md#feedbacktype) | 'IFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection\_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |

### IIntervalPrediction

**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-h-p.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-h-p.md#transportintervalprediction) A prediction that has a start interval.

| Property | Type | Description |
| :--- | :--- | :--- |
| start\_interval | [PredictionInterval](data-reference-h-p.md#predictioninterval) |  |

### IMoment

**Kind**: INTERFACE

**Implemented by**: [GenericMoment](data-reference-h-p.md#genericmoment), [CityMoment](data-reference-h-p.md#citymoment), [CountryMoment](data-reference-h-p.md#countrymoment) An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'IMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| start\_ts | [BigInt](data-reference-h-p.md#bigint) |  |
| end\_ts | [BigInt](data-reference-h-p.md#bigint) |  |
| analysis\_type | [AnalysisType](data-reference-h-p.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. |
| moment\_definition\_id | String | The ID of the MomentDefinition this moment relates to. |
| moment\_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. |

### IMomentAnomaly

**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-h-p.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-h-p.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-h-p.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-h-p.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-h-p.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| moment\_definition\_id | String |  |

### IMomentFeedback

**Kind**: INTERFACE

**Implemented by**: [MomentFeedback](data-reference-h-p.md#momentfeedback) An occurrence of moment feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| moment\_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  |

### IOccurrenceCountAnomaly

**Kind**: INTERFACE

**Implemented by**: [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_occurrences | Float | Observed amount of occurrences. |
| expected\_occurrences | Float | Expected amount of occurrences. |

### IPrediction

**Kind**: INTERFACE

**Implemented by**: [StationaryIntervalPrediction](data-reference-h-p.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference-h-p.md#transportintervalprediction) An occurance of a prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](data-reference-h-p.md#predictiontype) | 'IPrediction' |
| probability | Float |  |

### ISegment

**Kind**: INTERFACE

**Implemented by**: [GenericSegment](data-reference-h-p.md#genericsegment) An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](data-reference-h-p.md#segmenttype) | 'ISegment' |
| segment\_definition\_id | String | The ID of the SegmentDefinition this segment relates to. |
| segment\_definition | [SegmentDefinition](data-reference-h-p.md#segmentdefinition) | The SegmentDefinition this segment relates to. |

### IStationaryAnomaly

**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-h-p.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-h-p.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-h-p.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-h-p.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-h-p.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |

### ITimeAggregateAttribute

**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-h-p.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-h-p.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-h-p.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-h-p.md#workingtimeaggregate) An attribute that aggregates by TimePeriod.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [TimePeriod](data-reference-h-p.md#timeperiod) |  |

### ITransportAnomaly

**Kind**: INTERFACE

**Implemented by**: [DistanceAnomaly](data-reference-h-p.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference-h-p.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference-h-p.md#durationanomaly), [AggregatedDurationAnomaly](data-reference-h-p.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference-h-p.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference-h-p.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| transport\_mode | [TransportMode](data-reference-h-p.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference-h-p.md#transportmodecategory) |  |

### ITransportBehaviorAnnotation

**Kind**: INTERFACE

**Implemented by**: [BoundaryBehaviorAnnotation](data-reference-h-p.md#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](data-reference-h-p.md#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](data-reference-h-p.md#anomalybehaviorannotation), [TurnBehaviorAnnotation](data-reference-h-p.md#turnbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-h-p.md#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' |
| start | String |  |
| end | String |  |

### IUser

**Kind**: INTERFACE

**Implemented by**: [User](data-reference-h-p.md#user), [ControlUser](data-reference-h-p.md#controluser)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](data-reference-h-p.md#usertype) | 'IUser' |
| id | String | The unique identifier for this user. |
| can\_login | Boolean |  |
| created\_at | String | The time when this user was created, ISO8601. Example: 2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](data-reference-h-p.md#usersdksettings) |  |
| application\_id | String | The ID of the Application this user relates to. |
| application | [Application](data-reference-h-p.md#application) | The Application this user relates to. |
| custom\_event\_history | [CustomEvent](data-reference-h-p.md#customevent) | Custom Event History |
| event\_history | [IEvent](data-reference-h-p.md#ievent) | An unordered list of events we have detected for this user. |
| car\_behavior | [UserCarBehavior](data-reference-h-p.md#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
| aggregated\_driving\_scores | [UserTimeAggregatedScores](data-reference-h-p.md#usertimeaggregatedscores) |  |
| transport\_heatmaps | [TransportHeatmaps](data-reference-h-p.md#transportheatmaps) | The aggregated transport heatmaps calculated over time. |
| metadata | [JSON](data-reference-h-p.md#json) | All custom set metadata properties on this user. This is a JSON object with key-&gt;value pairs. |
| device | [DeviceInfo](data-reference-h-p.md#deviceinfo) | The last known active tracking device metadata |
| active\_moments | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. |
| moment\_history | [IMoment](data-reference-h-p.md#imoment) | An unordered list of moments we have detected for this user. |
| semantic\_time | [UserSemanticTime](data-reference-h-p.md#usersemantictime) | The user's semantic time averaged over time. |
| anomaly\_history | [IAnomaly](data-reference-h-p.md#ianomaly) |  |
| segments | [ISegment](data-reference-h-p.md#isegment) | An unordered list of segments that are detected for this user. |
| location\_clusters | [LocationCluster](data-reference-h-p.md#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations \(significance, point of interest, ...\) |
| location | [Waypoint](data-reference-h-p.md#waypoint) | The last known location we have for this user. |
| health | [UserHealth](data-reference-h-p.md#userhealth) | The historical health attributes. |
| attributes | [IUserAttribute](data-reference-h-p.md#iuserattribute) |  |
| predictions | [IPrediction](data-reference-h-p.md#iprediction) | Event/Moment predictions for this user |
| prediction\_tree | [PredictionTree](data-reference-h-p.md#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. |
| feedback\_history | [IFeedback](data-reference-h-p.md#ifeedback) | Feedback on this user |

### IUserAttribute

**Kind**: INTERFACE

**Implemented by**: [CommuteTimeAggregate](data-reference-h-p.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference-h-p.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference-h-p.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference-h-p.md#workingtimeaggregate)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-h-p.md#userattributetype) | 'IUserAttribute' |

### InputAddress

**Kind**: INPUT\_OBJECT

### InputEventFeedback

**Kind**: INPUT\_OBJECT

### InputLocationPlaceCandidate

**Kind**: INPUT\_OBJECT

### InputMoment

**Kind**: INPUT\_OBJECT

### InputMomentFeedback

**Kind**: INPUT\_OBJECT

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

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationCluster' |
| last\_visit | String |  |
| latitude | Float |  |
| longitude | Float |  |
| address | [Address](data-reference-h-p.md#address) |  |
| radius | Int |  |
| is\_poi | Boolean |  |
| significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| place | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) |  |

### LocationPlaceCandidate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A place selected from one of our data sources.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' |
| name | String | Name of the place. Can be null if no specific place can be assigned. |
| category\_hierarchy | [String](data-reference-h-p.md#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` |
| probability | Float |  |
| latitude | Float |  |
| longitude | Float |  |
| provider | String |  |

### LocationSignificance

**Kind**: ENUM

### MomentDefinition

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single moment definition.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'MomentDefinition' |
| id | String | Identifier of this MomentDefinition. Possible values: working\_at\_work,working\_remote,home,morning,lunch,afternoon,evening,night,commute\_from\_work,commute\_from\_home,business\_trip,holiday,nearby\_home,nearby\_work,city\_name,country,children\_drop\_off,sport\_routine,shopping\_routine,evening\_entertainment,night\_out,afternoon\_drinks,evening\_drinks,breakfast\_out,lunch\_out,dinner\_out,about\_to\_working,about\_to\_commute\_from\_home,about\_to\_commute\_from\_work,about\_to\_children\_drop\_off,about\_to\_sport,about\_to\_shopping,nearby\_poi |
| category | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic\_time,travel,geography,location,about\_to\_routine |
| display\_name | String | A displayable name for this MomentDefinition. |
| description | String | A short description about this MomentDefinition. |

### MomentFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback), [IMomentFeedback](data-reference-h-p.md#imomentfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference-h-p.md#feedbacktype) | 'MomentFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection\_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| moment\_feedback | [MomentFeedbackFeedback](data-reference-h-p.md#momentfeedbackfeedback) |  |
| moment | [IMoment](data-reference-h-p.md#imoment) | The Moment this feedback refers to. |

### MomentFeedbackFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| moment\_definition\_id\_assessment | [FeedbackAssessment](data-reference-h-p.md#feedbackassessment) | If the user thinks our detected moment is correct. |
| moment\_definition\_id\_feedback | String | Correction by the user in case our detection was incorrect. |

### MomentType

**Kind**: ENUM

### Mutation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Through mutations you can update data.

| Property | Type | Description |
| :--- | :--- | :--- |
| validateAccessTokens | [AccessToken](data-reference-h-p.md#accesstoken) | Validate access tokens. The valid tokens will be in the response. |
| createSubscription | [Subscription](data-reference-h-p.md#subscription) |  |
| deleteStreamDefinition | [StreamDefinition](data-reference-h-p.md#streamdefinition) | Allows one to delete a Stream Definition either because it was mistakenly created or because it has outlived its use. Trying to delete a non-existent Stream Definition will result in an error. |
| createStreamDefinition | [StreamDefinition](data-reference-h-p.md#streamdefinition) |  |
| createFeedback | [IFeedback](data-reference-h-p.md#ifeedback) |  |
| createUserRole | [UserAccountRole](data-reference-h-p.md#useraccountrole) |  |

### OccurrenceCountAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IOccurrenceCountAnomaly](data-reference-h-p.md#ioccurrencecountanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-h-p.md#anomalytype) | 'OccurrenceCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference-h-p.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-h-p.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](data-reference-h-p.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference-h-p.md#daypart) | Optional additional aggregation over which the data is calculated. |
| observed\_occurrences | Float | Observed amount of occurrences. |
| expected\_occurrences | Float | Expected amount of occurrences. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference-h-p.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference-h-p.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### OperatingSystem

**Kind**: ENUM

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
| is\_updated | Boolean |  |
| events | [IBranchEvent](data-reference-h-p.md#ibranchevent) | The list of events predicted to occur. |

### PredictionType

**Kind**: ENUM
