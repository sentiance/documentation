# Data Reference

## Objects

* [AccelerationBehaviorAnnotation](data-reference.md#accelerationbehaviorannotation)
* [AccessToken](data-reference.md#accesstoken)
* [Account](data-reference.md#account)
* [Address](data-reference.md#address)
* [AggregatedDistanceAnomaly](data-reference.md#aggregateddistanceanomaly)
* [AggregatedDurationAnomaly](data-reference.md#aggregateddurationanomaly)
* [AnomalyBehaviorAnnotation](data-reference.md#anomalybehaviorannotation)
* [Application](data-reference.md#application)
* [ApplicationsConnection](data-reference.md#applicationsconnection)
* [BehaviorAnnotationPathWaypoint](data-reference.md#behaviorannotationpathwaypoint)
* [BoundaryBehaviorAnnotation](data-reference.md#boundarybehaviorannotation)
* [Branch](data-reference.md#branch)
* [CarBehaviorFeatures](data-reference.md#carbehaviorfeatures)
* [CarBehaviorScores](data-reference.md#carbehaviorscores)
* [CityMoment](data-reference.md#citymoment)
* [CommuteTimeAggregate](data-reference.md#commutetimeaggregate)
* [ControlUser](data-reference.md#controluser)
* [CountryMoment](data-reference.md#countrymoment)
* [CustomEvent](data-reference.md#customevent)
* [DayCountAnomaly](data-reference.md#daycountanomaly)
* [DeviceInfo](data-reference.md#deviceinfo)
* [DistanceAnomaly](data-reference.md#distanceanomaly)
* [DurationAnomaly](data-reference.md#durationanomaly)
* [EventFeedback](data-reference.md#eventfeedback)
* [FloatAttribute](data-reference.md#floatattribute)
* [GenericMoment](data-reference.md#genericmoment)
* [GenericSegment](data-reference.md#genericsegment)
* [LocationCluster](data-reference.md#locationcluster)
* [LocationPlaceCandidate](data-reference.md#locationplacecandidate)
* [MomentDefinition](data-reference.md#momentdefinition)
* [MomentFeedback](data-reference.md#momentfeedback)
* [MomentFeedbackFeedback](data-reference.md#momentfeedbackfeedback)
* [Mutation](data-reference.md#mutation)
* [OccurrenceCountAnomaly](data-reference.md#occurrencecountanomaly)
* [Paging](data-reference.md#paging)
* [PagingCursors](data-reference.md#pagingcursors)
* [PredictionInterval](data-reference.md#predictioninterval)
* [PredictionTree](data-reference.md#predictiontree)
* [SegmentDefinition](data-reference.md#segmentdefinition)
* [SemanticTimeAggregate](data-reference.md#semantictimeaggregate)
* [SemanticTimeAggregateValue](data-reference.md#semantictimeaggregatevalue)
* [Stationary](data-reference.md#stationary)
* [StationaryFeedback](data-reference.md#stationaryfeedback)
* [StationaryIntervalPrediction](data-reference.md#stationaryintervalprediction)
* [StationaryLocation](data-reference.md#stationarylocation)
* [StationaryPrediction](data-reference.md#stationaryprediction)
* [StationaryTimeAggregate](data-reference.md#stationarytimeaggregate)
* [StreamDefinition](data-reference.md#streamdefinition)
* [StreamDefinitionsConnection](data-reference.md#streamdefinitionsconnection)
* [Subscription](data-reference.md#subscription)
* [SubscriptionsConnection](data-reference.md#subscriptionsconnection)
* [TimeWindowTransportHeatmaps](data-reference.md#timewindowtransportheatmaps)
* [TimeWindowUserCarBehaviorFeatures](data-reference.md#timewindowusercarbehaviorfeatures)
* [TrajectoryWaypoint](data-reference.md#trajectorywaypoint)
* [Transport](data-reference.md#transport)
* [TransportFeedback](data-reference.md#transportfeedback)
* [TransportHeatmaps](data-reference.md#transportheatmaps)
* [TransportIntervalPrediction](data-reference.md#transportintervalprediction)
* [TransportModeHeatmaps](data-reference.md#transportmodeheatmaps)
* [TransportPrediction](data-reference.md#transportprediction)
* [TransportTimeAggregate](data-reference.md#transporttimeaggregate)
* [TransportTrajectory](data-reference.md#transporttrajectory)
* [Trip](data-reference.md#trip)
* [TripConnection](data-reference.md#tripconnection)
* [TurnBehaviorAnnotation](data-reference.md#turnbehaviorannotation)
* [User](data-reference.md#user)
* [UserAccountRole](data-reference.md#useraccountrole)
* [UserCarBehavior](data-reference.md#usercarbehavior)
* [UserCarBehaviorFeatures](data-reference.md#usercarbehaviorfeatures)
* [UserCarBehaviorScores](data-reference.md#usercarbehaviorscores)
* [UserHealth](data-reference.md#userhealth)
* [UserHealthScores](data-reference.md#userhealthscores)
* [UserSdkSettings](data-reference.md#usersdksettings)
* [UserSemanticTime](data-reference.md#usersemantictime)
* [UsersConnection](data-reference.md#usersconnection)
* [Waypoint](data-reference.md#waypoint)
* [Weather](data-reference.md#weather)
* [WeatherRange](data-reference.md#weatherrange)
* [WeightedLocation](data-reference.md#weightedlocation)
* [WorkingTimeAggregate](data-reference.md#workingtimeaggregate)
* [ZoneCarBehaviorScores](data-reference.md#zonecarbehaviorscores)

### AccelerationBehaviorAnnotation

**Kind**: OBJECT **Implements**: [ITransportBehaviorAnnotation](data-reference.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference.md#transportbehaviorannotationtype) | 'AccelerationBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| acceleration | [AccelerationEnum](data-reference.md#accelerationenum) |  |
| path | [BehaviorAnnotationPathWaypoint](data-reference.md#behaviorannotationpathwaypoint) |  |
| magnitude | Float | The longitudinal g-force you experience during accelerations and brakes, measured in \(0.2\*m\)/s². Doing a fast acceleration will result in a higher value compared to a slower acceleration. |

### AccelerationEnum

**Kind**: ENUM

### AccessToken

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'AccessToken' |
| token | String | The access \(bearer\) token |
| expires\_at | String | When this token will expire |

### Account

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Account' |
| id | String |  |
| display\_name | String |  |
| created\_at | String |  |
| applications | [ApplicationsConnection](data-reference.md#applicationsconnection) | The applications that belong to this account. |

### Address

**Kind**: OBJECT An Address describes a reverse geocoded location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Address' |
| country | String |  |
| city | String |  |
| city\_type | String |  |

### AggregatedDistanceAnomaly

**Kind**: OBJECT **Implements**: [IAnomaly](data-reference.md#ianomaly), [IDistanceAnomaly](data-reference.md#idistanceanomaly), [IAggregatedAnomaly](data-reference.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference.md#istationaryanomaly), [ITransportAnomaly](data-reference.md#itransportanomaly), [IMomentAnomaly](data-reference.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference.md#anomalytype) | 'AggregatedDistanceAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference.md#analysistype) |  |
| anomaly | [Anomaly](data-reference.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_distance | Float | Observed distance in meter. |
| expected\_distance | Float | Expected distance in meter. |
| period | [AnomalyTimePeriod](data-reference.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference.md#daypart) | Optional additional aggregation over which the data is calculated. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### AggregatedDurationAnomaly

**Kind**: OBJECT **Implements**: [IAnomaly](data-reference.md#ianomaly), [IDurationAnomaly](data-reference.md#idurationanomaly), [IAggregatedAnomaly](data-reference.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference.md#istationaryanomaly), [ITransportAnomaly](data-reference.md#itransportanomaly), [IMomentAnomaly](data-reference.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference.md#anomalytype) | 'AggregatedDurationAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference.md#analysistype) |  |
| anomaly | [Anomaly](data-reference.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_duration | Float | Observed duration in seconds. |
| expected\_duration | Float | Expected duration in seconds. |
| period | [AnomalyTimePeriod](data-reference.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference.md#daypart) | Optional additional aggregation over which the data is calculated. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### AnalysisType

**Kind**: ENUM The platform analyzes data in multiple stages, and updates values over time, how well the data is analyzed, can be identified by the analysis type.

### Anomaly

**Kind**: ENUM

### AnomalyBehaviorAnnotation

**Kind**: OBJECT **Implements**: [ITransportBehaviorAnnotation](data-reference.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference.md#transportbehaviorannotationtype) | 'AnomalyBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| anomaly | [BehaviorAnnotationAnomalyEnum](data-reference.md#behaviorannotationanomalyenum) |  |
| duration | Int |  |

### AnomalyTimePeriod

**Kind**: ENUM

### AnomalyType

**Kind**: ENUM

### Application

**Kind**: OBJECT An Application refers to an integration of the mobile SDK and pools together the users from this mobile app.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Application' |
| id | String | The unique identifier for this application. |
| secret | String | The secret required when integrating the mobile SDK with this application ID. |
| name | String | The name of this application. For mobile apps it's the name how it's available in the AppStore/PlayStore. |
| description | String | A short description of this application. |
| logging | String | An optional override for the default debug logging behavior of the mobile SDKs. |
| flavor | String | An optional override for the default flavor configuration of the mobile SDKs. |
| project\_code | String | An optional project code used to assign users from the demo applications to this application. |
| created\_at | String | The time when this user was created, ISO8601. |

Example: 2015-05-28T14:37:14.839+00:00. \| \| account\_id \| String \| The developer account this application belongs to. \| \| users \| [UsersConnection](data-reference.md#usersconnection) \| The users that belong to this application. \| \| active\_users \| [UsersConnection](data-reference.md#usersconnection) \| The users that belong to this application and have been active in the last 7 days. \| \| trips \| [TripConnection](data-reference.md#tripconnection) \| Trips across all users recorded against this application. \|

### ApplicationsConnection

**Kind**: OBJECT Access the application nodes

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ApplicationsConnection' |
| slice | [Application](data-reference.md#application) | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. |
| paging | [Paging](data-reference.md#paging) |  |

### BehaviorAnnotationAnomalyEnum

**Kind**: ENUM

### BehaviorAnnotationPathWaypoint

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'BehaviorAnnotationPathWaypoint' |
| latitude | Float |  |
| longitude | Float |  |
| index | Int |  |

### BigInt

**Kind**: SCALAR The `BigInt` scalar type represents non-fractional signed whole numeric values. BigInt can represent values between -\(2^53\) + 1 and 2^53 - 1.

### BoundaryBehaviorAnnotation

**Kind**: OBJECT **Implements**: [ITransportBehaviorAnnotation](data-reference.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference.md#transportbehaviorannotationtype) | 'BoundaryBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| quality | [BoundaryBehaviorAnnotationQuality](data-reference.md#boundarybehaviorannotationquality) |  |

### BoundaryBehaviorAnnotationQuality

**Kind**: ENUM

### Branch

**Kind**: OBJECT A possible series of events predicted for the user.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the branch unique among all the branches returned for the user at the given time. |
| probability | Float | Percentage probability of the events of this beam taking place. |
| events | [IBranchEvent](data-reference.md#ibranchevent) | The list of events predicted to occur. |

### CarBehaviorFeatures

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'CarBehaviorFeatures' |
| phone\_handling | Int | Total time in milliseconds we detected phone handling by the user during this transport. Value will be -1 when the transport data was not sufficient. |
| distance\_during\_annotations | Int | Distance in meter during which the system had good quality sensor data available to observe transport behavior. Value will be -1 when the transport data was not sufficient. |

### CarBehaviorScores

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'CarBehaviorScores' |
| overall | Float | An aggregation of all scores where we had sufficient data. A low score in one of the scores will result in a lower overall score. |
| smooth | Float | The smooth driving score measures how calm you drive. High accelerations and heavy braking result in a lower score, the use of coasting results in a higher score. The higher your score, the calmer you drive! When we did not have sufficient data value will be -1. |
| legal | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we did not have sufficient data value will be -1. |
| anticipative | Float | The anticipative driving score measures how well you anticipate traffic. A fast sequence of braking and accelerations in general traffic situations results in a lower score, the use of coasting results in a higher score. The higher your score, the more anticipative you drive! When we did not have sufficient data value will be -1. |
| focus | Float | The proportion of time \(percentage\) the user is focused while driving, being focused means: not using the phone, which is detected through phone handling. |
| mounted | Float | The proportion of time \(percentage\) the phone is mounted while driving. |
| hard\_accel | Float | Measures how often you accelerate hard. Every hard acceleration will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| hard\_brake | Float | Measures how often you need to brake hard. Every hard brake will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| hard\_events | Float | This is a combination of hard\_accel and hard\_brake score. The hard brakes and accelerations are also normalized by the total number of events. When we do not have sufficient data this value will be -1. |
| legal\_v2 | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we did not have sufficient data value will be -1. The difference with legal score is that this score has better speed estimation. |
| hard\_turn | Float | Measures how often you turn hard. Every hard turn will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| smooth\_v2 | Float | The smooth driving score measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. The use of coasting results in a higher score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! When we did not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, the difference with smooth score v1 is that turns are also taken in account. |
| anticipative\_v2 | Float | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The use of coasting results in a higher score. The higher your score, the more anticipative you drive! When we did not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, this new version has a more accurate detection of brakes in turns. |

### CityMoment

**Kind**: OBJECT **Implements**: [IMoment](data-reference.md#imoment) An occurrence of a City moment that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference.md#momenttype) | 'CityMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| end \| String \| The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 \| \| start\_ts \| [BigInt](data-reference.md#bigint) \| \| \| end\_ts \| [BigInt](data-reference.md#bigint) \| \| \| analysis\_type \| [AnalysisType](data-reference.md#analysistype) \| How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. \| \| moment\_definition\_id \| String \| The ID of the MomentDefinition this moment relates to. \| \| moment\_definition \| [MomentDefinition](data-reference.md#momentdefinition) \| The MomentDefinition this moment relates to. \| \| city\_name \| String \| The name of the city this moment applies to. \|

### CommuteTimeAggregate

**Kind**: OBJECT **Implements**: [ITimeAggregateAttribute](data-reference.md#itimeaggregateattribute), [IUserAttribute](data-reference.md#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference.md#userattributetype) | 'CommuteTimeAggregate' |
| period | [TimePeriod](data-reference.md#timeperiod) |  |
| transport\_duration | Float |  |
| mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |

### ControlUser

**Kind**: OBJECT **Implements**: [IUser](data-reference.md#iuser) A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](data-reference.md#usertype) | 'ControlUser' |
| email | String | The email address that is optionally linked to provide access to the [https://developers.sentiance.com](https://developers.sentiance.com) and others. |
| account\_roles | [UserAccountRole](data-reference.md#useraccountrole) | The accounts this user has elevated permissions to. |
| id | String | The unique identifier for this user. |
| can\_login | Boolean |  |
| created\_at | String | The time when this user was created, ISO8601. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| sdk \| [UserSdkSettings](data-reference.md#usersdksettings) \| \| \| application\_id \| String \| The ID of the Application this user relates to. \| \| application \| [Application](data-reference.md#application) \| The Application this user relates to. \| \| custom\_event\_history \| [CustomEvent](data-reference.md#customevent) \| Custom Event History \| \| event\_history \| [IEvent](data-reference.md#ievent) \| An unordered list of events we have detected for this user. \| \| car\_behavior \| [UserCarBehavior](data-reference.md#usercarbehavior) \| The user car behavior aggregated over the last 9 weeks. \| \| transport\_heatmaps \| [TransportHeatmaps](data-reference.md#transportheatmaps) \| The aggregated transport heatmaps calculated over time. \| \| metadata \| [JSON](data-reference.md#json) \| All custom set metadata properties on this user. This is a JSON object with key-&gt;value pairs. \| \| device \| [DeviceInfo](data-reference.md#deviceinfo) \| The last known active tracking device metadata \| \| active\_moments \| [IMoment](data-reference.md#imoment) \| An unordered list of moments that are ongoing from the point of view of the platform. \| \| moment\_history \| [IMoment](data-reference.md#imoment) \| An unordered list of moments we have detected for this user. \| \| semantic\_time \| [UserSemanticTime](data-reference.md#usersemantictime) \| The user's semantic time averaged over time. \| \| anomaly\_history \| [IAnomaly](data-reference.md#ianomaly) \| \| \| segments \| [ISegment](data-reference.md#isegment) \| An unordered list of segments that are detected for this user. \| \| location\_clusters \| [LocationCluster](data-reference.md#locationcluster) \| Locations this user has been stationary at and the features we have learned about those locations \(significance, point of interest, ...\) \| \| location \| [Waypoint](data-reference.md#waypoint) \| The last known location we have for this user. \| \| health \| [UserHealth](data-reference.md#userhealth) \| The historical health attributes. \| \| attributes \| [IUserAttribute](data-reference.md#iuserattribute) \| \| \| predictions \| [IPrediction](data-reference.md#iprediction) \| Event/Moment predictions for this user \| \| prediction\_tree \| [PredictionTree](data-reference.md#predictiontree) \| Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. \| \| feedback\_history \| [IFeedback](data-reference.md#ifeedback) \| Feedback on this user \|

### CountryMoment

**Kind**: OBJECT **Implements**: [IMoment](data-reference.md#imoment) An occurrence of a Country moment that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference.md#momenttype) | 'CountryMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| end \| String \| The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 \| \| start\_ts \| [BigInt](data-reference.md#bigint) \| \| \| end\_ts \| [BigInt](data-reference.md#bigint) \| \| \| analysis\_type \| [AnalysisType](data-reference.md#analysistype) \| How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. \| \| moment\_definition\_id \| String \| The ID of the MomentDefinition this moment relates to. \| \| moment\_definition \| [MomentDefinition](data-reference.md#momentdefinition) \| The MomentDefinition this moment relates to. \| \| country\_name \| String \| The name of the country this moment applies to. \|

### CustomEvent

**Kind**: OBJECT Custom Events.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the event in the Sentiance system. This is unique across all custom events |
| created\_at | String | The time this event was created ISO8601. |
| created\_at\_ts | [BigInt](data-reference.md#bigint) |  |
| type | String | 'CustomEvent' |
| start | String | The time this event started, ISO8601. |
| end | String | The time this event ended, ISO8601. Value can be null when it is a one time event. |
| start\_ts | [BigInt](data-reference.md#bigint) |  |
| end\_ts | [BigInt](data-reference.md#bigint) |  |
| source | [CustomEventSources](data-reference.md#customeventsources) | Where the event originates. |
| event\_id | String |  |
| latitude | Float | Latitude value of the event. |
| longitude | Float | Longitude value of the event. |
| values | [JSON](data-reference.md#json) | JSON string of key,value pairs submitted during event creation. |

### CustomEventSources

**Kind**: ENUM Where the custome event originates at.

### DayCountAnomaly

**Kind**: OBJECT **Implements**: [IAnomaly](data-reference.md#ianomaly), [IDayCountAnomaly](data-reference.md#idaycountanomaly), [IAggregatedAnomaly](data-reference.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference.md#istationaryanomaly), [ITransportAnomaly](data-reference.md#itransportanomaly), [IMomentAnomaly](data-reference.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference.md#anomalytype) | 'DayCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference.md#analysistype) |  |
| anomaly | [Anomaly](data-reference.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](data-reference.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference.md#daypart) | Optional additional aggregation over which the data is calculated. |
| observed\_days | Float | Observed amount of days. |
| expected\_days | Float | Expected amount of days. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### DayPart

**Kind**: ENUM Grouping of local time.

### DeviceInfo

**Kind**: OBJECT Tracking device metadata.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'DeviceInfo' |
| os | [OperatingSystem](data-reference.md#operatingsystem) | The operating system this device is running. |
| os\_version | String | The version of the operating system this device is running. |

### DistanceAnomaly

**Kind**: OBJECT **Implements**: [IAnomaly](data-reference.md#ianomaly), [IDistanceAnomaly](data-reference.md#idistanceanomaly), [IStationaryAnomaly](data-reference.md#istationaryanomaly), [ITransportAnomaly](data-reference.md#itransportanomaly), [IMomentAnomaly](data-reference.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference.md#anomalytype) | 'DistanceAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference.md#analysistype) |  |
| anomaly | [Anomaly](data-reference.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_distance | Float | Observed distance in meter. |
| expected\_distance | Float | Expected distance in meter. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### DurationAnomaly

**Kind**: OBJECT **Implements**: [IAnomaly](data-reference.md#ianomaly), [IDurationAnomaly](data-reference.md#idurationanomaly), [IStationaryAnomaly](data-reference.md#istationaryanomaly), [ITransportAnomaly](data-reference.md#itransportanomaly), [IMomentAnomaly](data-reference.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference.md#anomalytype) | 'DurationAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference.md#analysistype) |  |
| anomaly | [Anomaly](data-reference.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_duration | Float | Observed duration in seconds. |
| expected\_duration | Float | Expected duration in seconds. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### EventFeedback

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type\_assessment | [FeedbackAssessment](data-reference.md#feedbackassessment) | If the user thinks the detected type is correct. |
| place\_assessment | [FeedbackAssessment](data-reference.md#feedbackassessment) | If the user thinks the detected place is correct. |
| place\_feedback | [LocationPlaceCandidate](data-reference.md#locationplacecandidate) | The place candidate that was selected by the user as a better match, if any. |
| significance\_assessment | [FeedbackAssessment](data-reference.md#feedbackassessment) | If the user thinks the detected location significance is correct. |
| significance\_feedback | [LocationSignificance](data-reference.md#locationsignificance) | The location significance that was selected by the user as a better match, if any. |
| mode\_assessment | [FeedbackAssessment](data-reference.md#feedbackassessment) | What the user thinks about the transport mode. |
| mode\_feedback | [TransportMode](data-reference.md#transportmode) | The transport mode that was selected by the user as a better match, if any. |
| occupant\_role\_feedback | [TransportOccupantRole](data-reference.md#transportoccupantrole) | The occupant role that was selected by the user as a better match, if any. |

### EventType

**Kind**: ENUM

### FeedbackAssessment

**Kind**: ENUM

### FeedbackType

**Kind**: ENUM

### FloatAttribute

**Kind**: OBJECT A float attribute

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'FloatAttribute' |
| value | Float |  |

### GenericMoment

**Kind**: OBJECT **Implements**: [IMoment](data-reference.md#imoment) An occurrence of a moment that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference.md#momenttype) | 'GenericMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| end \| String \| The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 \| \| start\_ts \| [BigInt](data-reference.md#bigint) \| \| \| end\_ts \| [BigInt](data-reference.md#bigint) \| \| \| analysis\_type \| [AnalysisType](data-reference.md#analysistype) \| How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. \| \| moment\_definition\_id \| String \| The ID of the MomentDefinition this moment relates to. \| \| moment\_definition \| [MomentDefinition](data-reference.md#momentdefinition) \| The MomentDefinition this moment relates to. \|

### GenericSegment

**Kind**: OBJECT **Implements**: [ISegment](data-reference.md#isegment) An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](data-reference.md#segmenttype) | 'GenericSegment' |
| segment\_definition\_id | String | The ID of the SegmentDefinition this segment relates to. |
| explanation | String | Reasoning why this segment was assigned to this user from a third person point of view. |
| explanation\_you | String | Reasoning why this segment was assigned to this from a second person point of view. |
| segment\_definition | [SegmentDefinition](data-reference.md#segmentdefinition) | The SegmentDefinition this segment relates to. |

### IAggregatedAnomaly

**Kind**: INTERFACE **Implemented by**: [AggregatedDistanceAnomaly](data-reference.md#aggregateddistanceanomaly), [AggregatedDurationAnomaly](data-reference.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference.md#occurrencecountanomaly) An anomaly that we have detected for a user over a period of time.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [AnomalyTimePeriod](data-reference.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference.md#daypart) | Optional additional aggregation over which the data is calculated. |

### IAnomaly

**Kind**: INTERFACE **Implemented by**: [DistanceAnomaly](data-reference.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference.md#durationanomaly), [AggregatedDurationAnomaly](data-reference.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference.md#occurrencecountanomaly) An anomaly that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference.md#anomalytype) | 'IAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference.md#analysistype) |  |
| anomaly | [Anomaly](data-reference.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |

### IBranchEvent

**Kind**: INTERFACE **Implemented by**: [StationaryPrediction](data-reference.md#stationaryprediction), [TransportPrediction](data-reference.md#transportprediction) A single predicted event.

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](data-reference.md#treepredictiontype) | 'IBranchEvent' |

### IDayCountAnomaly

**Kind**: INTERFACE **Implemented by**: [DayCountAnomaly](data-reference.md#daycountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_days | Float | Observed amount of days. |
| expected\_days | Float | Expected amount of days. |

### IDistanceAnomaly

**Kind**: INTERFACE **Implemented by**: [DistanceAnomaly](data-reference.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference.md#aggregateddistanceanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_distance | Float | Observed distance in meter. |
| expected\_distance | Float | Expected distance in meter. |

### IDurationAnomaly

**Kind**: INTERFACE **Implemented by**: [DurationAnomaly](data-reference.md#durationanomaly), [AggregatedDurationAnomaly](data-reference.md#aggregateddurationanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_duration | Float | Observed duration in seconds. |
| expected\_duration | Float | Expected duration in seconds. |

### IEvent

**Kind**: INTERFACE **Implemented by**: [Trip](data-reference.md#trip), [Stationary](data-reference.md#stationary), [Transport](data-reference.md#transport) An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](data-reference.md#eventtype) | 'IEvent' |
| event\_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| end \| String \| The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 \| \| start\_ts \| [BigInt](data-reference.md#bigint) \| \| \| end\_ts \| [BigInt](data-reference.md#bigint) \| \| \| analysis\_type \| [AnalysisType](data-reference.md#analysistype) \| How well this event is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. \| \| weather \| [WeatherRange](data-reference.md#weatherrange) \| Weather data associated with this event. \|

### IEventFeedback

**Kind**: INTERFACE **Implemented by**: [StationaryFeedback](data-reference.md#stationaryfeedback), [TransportFeedback](data-reference.md#transportfeedback) An occurrence of event feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event\_feedback | [EventFeedback](data-reference.md#eventfeedback) |  |

### IEventPrediction

**Kind**: INTERFACE **Implemented by**: [StationaryIntervalPrediction](data-reference.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference.md#transportintervalprediction) An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event\_type | [EventType](data-reference.md#eventtype) |  |

### IFeedback

**Kind**: INTERFACE **Implemented by**: [StationaryFeedback](data-reference.md#stationaryfeedback), [TransportFeedback](data-reference.md#transportfeedback), [MomentFeedback](data-reference.md#momentfeedback) An occurrence of feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference.md#feedbacktype) | 'IFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection\_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |

### IIntervalPrediction

**Kind**: INTERFACE **Implemented by**: [StationaryIntervalPrediction](data-reference.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference.md#transportintervalprediction) A prediction that has a start interval.

| Property | Type | Description |
| :--- | :--- | :--- |
| start\_interval | [PredictionInterval](data-reference.md#predictioninterval) |  |

### IMoment

**Kind**: INTERFACE **Implemented by**: [GenericMoment](data-reference.md#genericmoment), [CityMoment](data-reference.md#citymoment), [CountryMoment](data-reference.md#countrymoment) An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference.md#momenttype) | 'IMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| end \| String \| The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 \| \| start\_ts \| [BigInt](data-reference.md#bigint) \| \| \| end\_ts \| [BigInt](data-reference.md#bigint) \| \| \| analysis\_type \| [AnalysisType](data-reference.md#analysistype) \| How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. \| \| moment\_definition\_id \| String \| The ID of the MomentDefinition this moment relates to. \| \| moment\_definition \| [MomentDefinition](data-reference.md#momentdefinition) \| The MomentDefinition this moment relates to. \|

### IMomentAnomaly

**Kind**: INTERFACE **Implemented by**: [DistanceAnomaly](data-reference.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference.md#durationanomaly), [AggregatedDurationAnomaly](data-reference.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| moment\_definition\_id | String |  |

### IMomentFeedback

**Kind**: INTERFACE **Implemented by**: [MomentFeedback](data-reference.md#momentfeedback) An occurrence of moment feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| moment\_feedback | [MomentFeedbackFeedback](data-reference.md#momentfeedbackfeedback) |  |

### IOccurrenceCountAnomaly

**Kind**: INTERFACE **Implemented by**: [OccurrenceCountAnomaly](data-reference.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed\_occurrences | Float | Observed amount of occurrences. |
| expected\_occurrences | Float | Expected amount of occurrences. |

### IPrediction

**Kind**: INTERFACE **Implemented by**: [StationaryIntervalPrediction](data-reference.md#stationaryintervalprediction), [TransportIntervalPrediction](data-reference.md#transportintervalprediction) An occurance of a prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](data-reference.md#predictiontype) | 'IPrediction' |
| probability | Float |  |

### ISegment

**Kind**: INTERFACE **Implemented by**: [GenericSegment](data-reference.md#genericsegment) An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](data-reference.md#segmenttype) | 'ISegment' |
| segment\_definition\_id | String | The ID of the SegmentDefinition this segment relates to. |
| segment\_definition | [SegmentDefinition](data-reference.md#segmentdefinition) | The SegmentDefinition this segment relates to. |

### IStationaryAnomaly

**Kind**: INTERFACE **Implemented by**: [DistanceAnomaly](data-reference.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference.md#durationanomaly), [AggregatedDurationAnomaly](data-reference.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |

### ITimeAggregateAttribute

**Kind**: INTERFACE **Implemented by**: [CommuteTimeAggregate](data-reference.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference.md#workingtimeaggregate) An attribute that aggregates by TimePeriod.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [TimePeriod](data-reference.md#timeperiod) |  |

### ITransportAnomaly

**Kind**: INTERFACE **Implemented by**: [DistanceAnomaly](data-reference.md#distanceanomaly), [AggregatedDistanceAnomaly](data-reference.md#aggregateddistanceanomaly), [DurationAnomaly](data-reference.md#durationanomaly), [AggregatedDurationAnomaly](data-reference.md#aggregateddurationanomaly), [DayCountAnomaly](data-reference.md#daycountanomaly), [OccurrenceCountAnomaly](data-reference.md#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| transport\_mode | [TransportMode](data-reference.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |

### ITransportBehaviorAnnotation

**Kind**: INTERFACE **Implemented by**: [BoundaryBehaviorAnnotation](data-reference.md#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](data-reference.md#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](data-reference.md#anomalybehaviorannotation), [TurnBehaviorAnnotation](data-reference.md#turnbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference.md#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' |
| start | String |  |
| end | String |  |

### IUser

**Kind**: INTERFACE **Implemented by**: [User](data-reference.md#user), [ControlUser](data-reference.md#controluser)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](data-reference.md#usertype) | 'IUser' |
| id | String | The unique identifier for this user. |
| can\_login | Boolean |  |
| created\_at | String | The time when this user was created, ISO8601. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| sdk \| [UserSdkSettings](data-reference.md#usersdksettings) \| \| \| application\_id \| String \| The ID of the Application this user relates to. \| \| application \| [Application](data-reference.md#application) \| The Application this user relates to. \| \| custom\_event\_history \| [CustomEvent](data-reference.md#customevent) \| Custom Event History \| \| event\_history \| [IEvent](data-reference.md#ievent) \| An unordered list of events we have detected for this user. \| \| car\_behavior \| [UserCarBehavior](data-reference.md#usercarbehavior) \| The user car behavior aggregated over the last 9 weeks. \| \| transport\_heatmaps \| [TransportHeatmaps](data-reference.md#transportheatmaps) \| The aggregated transport heatmaps calculated over time. \| \| metadata \| [JSON](data-reference.md#json) \| All custom set metadata properties on this user. This is a JSON object with key-&gt;value pairs. \| \| device \| [DeviceInfo](data-reference.md#deviceinfo) \| The last known active tracking device metadata \| \| active\_moments \| [IMoment](data-reference.md#imoment) \| An unordered list of moments that are ongoing from the point of view of the platform. \| \| moment\_history \| [IMoment](data-reference.md#imoment) \| An unordered list of moments we have detected for this user. \| \| semantic\_time \| [UserSemanticTime](data-reference.md#usersemantictime) \| The user's semantic time averaged over time. \| \| anomaly\_history \| [IAnomaly](data-reference.md#ianomaly) \| \| \| segments \| [ISegment](data-reference.md#isegment) \| An unordered list of segments that are detected for this user. \| \| location\_clusters \| [LocationCluster](data-reference.md#locationcluster) \| Locations this user has been stationary at and the features we have learned about those locations \(significance, point of interest, ...\) \| \| location \| [Waypoint](data-reference.md#waypoint) \| The last known location we have for this user. \| \| health \| [UserHealth](data-reference.md#userhealth) \| The historical health attributes. \| \| attributes \| [IUserAttribute](data-reference.md#iuserattribute) \| \| \| predictions \| [IPrediction](data-reference.md#iprediction) \| Event/Moment predictions for this user \| \| prediction\_tree \| [PredictionTree](data-reference.md#predictiontree) \| Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. \| \| feedback\_history \| [IFeedback](data-reference.md#ifeedback) \| Feedback on this user \|

### IUserAttribute

**Kind**: INTERFACE **Implemented by**: [CommuteTimeAggregate](data-reference.md#commutetimeaggregate), [StationaryTimeAggregate](data-reference.md#stationarytimeaggregate), [TransportTimeAggregate](data-reference.md#transporttimeaggregate), [WorkingTimeAggregate](data-reference.md#workingtimeaggregate)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference.md#userattributetype) | 'IUserAttribute' |

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

**Kind**: INPUT\_OBJECT A single waypoint in the augmented trajectory.

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

**Kind**: SCALAR The `JSON` scalar type represents JSON values as specified by [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf).

### LocationCluster

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationCluster' |
| last\_visit | String |  |
| latitude | Float |  |
| longitude | Float |  |
| address | [Address](data-reference.md#address) |  |
| radius | Int |  |
| is\_poi | Boolean |  |
| significance | [LocationSignificance](data-reference.md#locationsignificance) |  |
| place | [LocationPlaceCandidate](data-reference.md#locationplacecandidate) |  |

### LocationPlaceCandidate

**Kind**: OBJECT A place selected from one of our data sources.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' |
| name | String | Name of the place. Can be null if no specific place can be assigned. |
| category\_hierarchy | [String](data-reference.md#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` |
| probability | Float |  |
| latitude | Float |  |
| longitude | Float |  |
| provider | String |  |

### LocationSignificance

**Kind**: ENUM

### MomentDefinition

**Kind**: OBJECT A single moment definition.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'MomentDefinition' |
| id | String | Identifier of this MomentDefinition. Possible values: working\_at\_work,working\_remote,home,morning,lunch,afternoon,evening,night,commute\_from\_work,commute\_from\_home,business\_trip,holiday,nearby\_home,nearby\_work,city\_name,country,children\_drop\_off,sport\_routine,shopping\_routine,evening\_entertainment,night\_out,afternoon\_drinks,evening\_drinks,breakfast\_out,lunch\_out,dinner\_out,about\_to\_working,about\_to\_commute\_from\_home,about\_to\_commute\_from\_work,about\_to\_children\_drop\_off,about\_to\_sport,about\_to\_shopping,nearby\_poi |
| category | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic\_time,travel,geography,location,about\_to\_routine |
| display\_name | String | A displayable name for this MomentDefinition. |
| description | String | A short description about this MomentDefinition. |

### MomentFeedback

**Kind**: OBJECT **Implements**: [IFeedback](data-reference.md#ifeedback), [IMomentFeedback](data-reference.md#imomentfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference.md#feedbacktype) | 'MomentFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection\_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| moment\_feedback | [MomentFeedbackFeedback](data-reference.md#momentfeedbackfeedback) |  |
| moment | [IMoment](data-reference.md#imoment) | The Moment this feedback refers to. |

### MomentFeedbackFeedback

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| moment\_definition\_id\_assessment | [FeedbackAssessment](data-reference.md#feedbackassessment) | If the user thinks our detected moment is correct. |
| moment\_definition\_id\_feedback | String | Correction by the user in case our detection was incorrect. |

### MomentType

**Kind**: ENUM

### Mutation

**Kind**: OBJECT Through mutations you can update data.

| Property | Type | Description |
| :--- | :--- | :--- |
| validateAccessTokens | [AccessToken](data-reference.md#accesstoken) | Validate access tokens. The valid tokens will be in the response. |
| createSubscription | [Subscription](data-reference.md#subscription) |  |
| deleteStreamDefinition | [StreamDefinition](data-reference.md#streamdefinition) | Allows one to delete a Stream Definition either because it was mistakenly created or because it has outlived its use. Trying to delete a non-existent Stream Definition will result in an error. |
| createStreamDefinition | [StreamDefinition](data-reference.md#streamdefinition) |  |
| createFeedback | [IFeedback](data-reference.md#ifeedback) |  |
| createUserRole | [UserAccountRole](data-reference.md#useraccountrole) |  |

### OccurrenceCountAnomaly

**Kind**: OBJECT **Implements**: [IAnomaly](data-reference.md#ianomaly), [IOccurrenceCountAnomaly](data-reference.md#ioccurrencecountanomaly), [IAggregatedAnomaly](data-reference.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference.md#istationaryanomaly), [ITransportAnomaly](data-reference.md#itransportanomaly), [IMomentAnomaly](data-reference.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference.md#anomalytype) | 'OccurrenceCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference.md#analysistype) |  |
| anomaly | [Anomaly](data-reference.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](data-reference.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference.md#daypart) | Optional additional aggregation over which the data is calculated. |
| observed\_occurrences | Float | Observed amount of occurrences. |
| expected\_occurrences | Float | Expected amount of occurrences. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### OperatingSystem

**Kind**: ENUM

### Paging

**Kind**: OBJECT The paging information that allows you to paginate through a large response list.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Paging' |
| cursors | [PagingCursors](data-reference.md#pagingcursors) | The offset cursors to use when paging through results. |

### PagingCursors

**Kind**: OBJECT The paging cursors that you use to paginate through a large response set.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'PagingCursors' |
| before | String | This is the cursor that points to the start of the page of data that has been returned. |
| after | String | This is the cursor that points to the end of the page of data that has been returned. |

### PredictionInterval

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String |  |
| end | String |  |

### PredictionTree

**Kind**: OBJECT Multiple possible events that might occur for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| is\_updated | Boolean |  |
| probability | Float | Percentage probability of these events taking place. |
| events | [IBranchEvent](data-reference.md#ibranchevent) | The list of events predicted to occur. |

### PredictionType

**Kind**: ENUM

### SdkFlavor

**Kind**: ENUM

### SegmentDefinition

**Kind**: OBJECT A single segment definition.

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

**Kind**: ENUM Identifies the release status of a segment definition.

### SegmentType

**Kind**: ENUM

### SemanticTime

**Kind**: ENUM The user semantic time.

### SemanticTimeAggregate

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregate' |
| morning | [SemanticTimeAggregateValue](data-reference.md#semantictimeaggregatevalue) |  |
| lunch | [SemanticTimeAggregateValue](data-reference.md#semantictimeaggregatevalue) |  |
| afternoon | [SemanticTimeAggregateValue](data-reference.md#semantictimeaggregatevalue) |  |
| evening | [SemanticTimeAggregateValue](data-reference.md#semantictimeaggregatevalue) |  |
| night | [SemanticTimeAggregateValue](data-reference.md#semantictimeaggregatevalue) |  |

### SemanticTimeAggregateDaysEnum

**Kind**: ENUM

### SemanticTimeAggregateValue

**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregateValue' |
| semantic\_time | [SemanticTime](data-reference.md#semantictime) |  |
| days | [SemanticTimeAggregateDaysEnum](data-reference.md#semantictimeaggregatedaysenum) |  |
| start | String | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |
| end | String | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |

### Stationary

**Kind**: OBJECT **Implements**: [IEvent](data-reference.md#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](data-reference.md#eventtype) | 'Stationary' |
| event\_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. |

Example: 2015-05-28T14:37:14.839+00:00 \| \| end \| String \| The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 \| \| start\_ts \| [BigInt](data-reference.md#bigint) \| \| \| end\_ts \| [BigInt](data-reference.md#bigint) \| \| \| analysis\_type \| [AnalysisType](data-reference.md#analysistype) \| How well this event is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. \| \| latitude \| Float \| \| \| longitude \| Float \| \| \| duration \| [BigInt](data-reference.md#bigint) \| \| \| address \| [Address](data-reference.md#address) \| \| \| location \| [StationaryLocation](data-reference.md#stationarylocation) \| \| \| weather \| [WeatherRange](data-reference.md#weatherrange) \| Weather data associated with this event. \|

### StationaryFeedback

**Kind**: OBJECT **Implements**: [IFeedback](data-reference.md#ifeedback), [IEventFeedback](data-reference.md#ieventfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](data-reference.md#feedbacktype) | 'StationaryFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection\_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| event\_feedback | [EventFeedback](data-reference.md#eventfeedback) |  |
| stationary | [Stationary](data-reference.md#stationary) | The Stationary this feedback refers to. |

### StationaryIntervalPrediction

**Kind**: OBJECT **Implements**: [IPrediction](data-reference.md#iprediction), [IEventPrediction](data-reference.md#ieventprediction), [IIntervalPrediction](data-reference.md#iintervalprediction)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](data-reference.md#predictiontype) | 'StationaryIntervalPrediction' |
| probability | Float |  |
| event\_type | [EventType](data-reference.md#eventtype) |  |
| start\_interval | [PredictionInterval](data-reference.md#predictioninterval) |  |
| location | [StationaryLocation](data-reference.md#stationarylocation) |  |

### StationaryLocation

**Kind**: OBJECT Holds more information about a stationary location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StationaryLocation' |
| significance | [LocationSignificance](data-reference.md#locationsignificance) | What this location means for the user, or the frequency it's being visited. |
| place | [LocationPlaceCandidate](data-reference.md#locationplacecandidate) |  |
| place\_candidates | [LocationPlaceCandidate](data-reference.md#locationplacecandidate) |  |

### StationaryPrediction

**Kind**: OBJECT **Implements**: [IBranchEvent](data-reference.md#ibranchevent)

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](data-reference.md#treepredictiontype) | 'StationaryPrediction' |
| location\_type | String |  |

### StationaryTimeAggregate

**Kind**: OBJECT **Implements**: [ITimeAggregateAttribute](data-reference.md#itimeaggregateattribute), [IUserAttribute](data-reference.md#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference.md#userattributetype) | 'StationaryTimeAggregate' |
| period | [TimePeriod](data-reference.md#timeperiod) |  |
| duration | Float |  |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference.md#locationsignificance) |  |

### StreamDefinition

**Kind**: OBJECT Stream definition that can be activated/subscribed to with the Sentiance Firehose

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StreamDefinition' |
| id | String |  |
| name | String |  |
| projection | String | The GQL query that will be provided on every notification. |
| created\_at | String |  |
| subscriptions | [SubscriptionsConnection](data-reference.md#subscriptionsconnection) |  |

### StreamDefinitionConnectionType

**Kind**: ENUM Stream definition connection type.

### StreamDefinitionsConnection

**Kind**: OBJECT Access the stream definitions

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StreamDefinitionsConnection' |
| slice | [StreamDefinition](data-reference.md#streamdefinition) | The individual stream definitions. Provide the right paging parameters to slice your result set. |

### Subscription

**Kind**: OBJECT Subscription that can be activated to receive data from the Sentiance Firehose.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Subscription' |
| id | String |  |
| token | String |  |
| active | Boolean |  |
| connection\_type | [StreamDefinitionConnectionType](data-reference.md#streamdefinitionconnectiontype) |  |
| user\_ids | [String](data-reference.md#string) |  |
| created\_at | String |  |

### SubscriptionsConnection

**Kind**: OBJECT Access the stream subscriptions

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SubscriptionsConnection' |
| slice | [Subscription](data-reference.md#subscription) | The individual subscriptions. Provide the right paging parameters to slice your result set. |

