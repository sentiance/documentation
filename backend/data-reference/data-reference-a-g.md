# Data Reference A-G

## Objects

* [AccelerationBehaviorAnnotation](data-reference-a-g.md#accelerationbehaviorannotation)
* [AccessToken](data-reference-a-g.md#accesstoken)
* [Account](data-reference-a-g.md#account)
* [Address](data-reference-a-g.md#address)
* [AggregatedDistanceAnomaly](data-reference-a-g.md#aggregateddistanceanomaly)
* [AggregatedDurationAnomaly](data-reference-a-g.md#aggregateddurationanomaly)
* [AnomalyBehaviorAnnotation](data-reference-a-g.md#anomalybehaviorannotation)
* [Application](data-reference-a-g.md#application)
* [ApplicationActivity](data-reference-a-g.md#applicationactivity)
* [ApplicationActivityGroup](data-reference-a-g.md#applicationactivitygroup)
* [ApplicationActivityGroupItem](data-reference-a-g.md#applicationactivitygroupitem)
* [ApplicationsConnection](data-reference-a-g.md#applicationsconnection)
* [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint)
* [BoundaryBehaviorAnnotation](data-reference-a-g.md#boundarybehaviorannotation)
* [Branch](data-reference-a-g.md#branch)
* [CarBehaviorFeatures](data-reference-a-g.md#carbehaviorfeatures)
* [CarBehaviorScores](data-reference-a-g.md#carbehaviorscores)
* [CityMoment](data-reference-a-g.md#citymoment)
* [CommuteTimeAggregate](data-reference-a-g.md#commutetimeaggregate)
* [ControlUser](data-reference-a-g.md#controluser)
* [CountryMoment](data-reference-a-g.md#countrymoment)
* [CustomEvent](data-reference-a-g.md#customevent)
* [DayCountAnomaly](data-reference-a-g.md#daycountanomaly)
* [DeviceInfo](data-reference-a-g.md#deviceinfo)
* [DistanceAnomaly](data-reference-a-g.md#distanceanomaly)
* [DurationAnomaly](data-reference-a-g.md#durationanomaly)
* [EventFeedback](data-reference-a-g.md#eventfeedback)
* [FloatAttribute](data-reference-a-g.md#floatattribute)
* [GenericMoment](data-reference-a-g.md#genericmoment)
* [GenericSegment](data-reference-a-g.md#genericsegment)

### AccelerationBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'AccelerationBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int | Duration is in milliseconds. |
| acceleration | [AccelerationEnum](data-reference-a-g.md#accelerationenum) |  |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  |
| magnitude | Float | The longitudinal g-force you experience during accelerations and brakes, measured in \(0.2\*m\)/s². Doing a fast acceleration will result in a higher value compared to a slower acceleration. |

### AccelerationEnum

**Kind**: ENUM

* **accelerate**
* **brake**
* **coast**

### AccessToken

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'AccessToken' |
| token | String | The access \(bearer\) token |
| expires\_at | String | When this token will expire |

### Account

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Account' |
| id | String |  |
| display\_name | String |  |
| created\_at | String |  |
| applications | [ApplicationsConnection](data-reference-a-g.md#applicationsconnection) | The applications that belong to this account. |

### Address

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Address' |
| country | String |  |
| city | String |  |
| city\_type | String |  |

### AggregatedDistanceAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDistanceAnomaly](data-reference-h-p.md#idistanceanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'AggregatedDistanceAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_distance | Float | Observed distance in meter. |
| expected\_distance | Float | Expected distance in meter. |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference-q-z.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### AggregatedDurationAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDurationAnomaly](data-reference-h-p.md#idurationanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'AggregatedDurationAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_duration | Float | Observed duration in seconds. |
| expected\_duration | Float | Expected duration in seconds. |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference-q-z.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### AnalysisType

**Kind**: ENUM

* **processed**: The most detailed processing with the highest latency. This processing also takes into account motion sensor data, does advanced timelining corrections.
* **indepth**: When data is analyzed with potentially more information available compared to the initial preliminary analysis. This type of processing also takes into account motion sensor data.
* **preliminary**: The initial realtime analysis of data with the lowest latency.

  The platform analyzes data in multiple stages, and updates values over time, how well the data is analyzed, can be identified by the analysis type.

### Anomaly

**Kind**: ENUM

* **transport\_distance**
* **transport\_duration**
* **transport\_mode\_distance**
* **transport\_mode\_duration**
* **transport\_mode\_category\_distance**
* **transport\_mode\_category\_duration**
* **transport\_day\_part\_distance**
* **transport\_day\_part\_duration**
* **transport\_mode\_category\_occurrence\_count**
* **stationary\_location\_significance\_duration**
* **stationary\_location\_significance\_day\_part\_duration**
* **stationary\_place\_category\_day\_count**
* **stationary\_location\_significance\_day\_part\_day\_count**
* **stationary\_place\_category\_duration**
* **stationary\_place\_category\_occurrence\_count**
* **moment\_duration**
* **commute\_distance**
* **commute\_duration**: This is an aggregation over the commute\_from\_home and commute\_from\_work moments, it includes small stationaries during commutes \(such as stopping at the gas station\).
* **commute\_transport\_mode\_category\_duration**
* **working\_duration**
* **dogwalk\_occurrence\_count**

### AnomalyBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'AnomalyBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| anomaly | [BehaviorAnnotationAnomalyEnum](data-reference-a-g.md#behaviorannotationanomalyenum) |  |
| duration | Int | Duration is in milliseconds. |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  |

### AnomalyTimePeriod

**Kind**: ENUM

* **day**: Anomaly calculated on a daily basis.
* **week**: Anomaly calculated on a weekly basis.
* **month**: Anomaly calculated on a montly basis.
* **semantic\_day**: Anomaly calculated on the semantic day of the user.
* **weekend\_day**: Anomaly calculated on a daily basis, ex: each day of the weekend you are at home on average N hours, then if you are not home both days = 2 anomalies \(one for saturday, one for sunday\) will be available.

### AnomalyType

**Kind**: ENUM

* **DistanceAnomaly**
* **AggregatedDistanceAnomaly**
* **DurationAnomaly**
* **AggregatedDurationAnomaly**
* **DayCountAnomaly**
* **OccurrenceCountAnomaly**

### Application

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Application refers to an integration of the mobile SDK and pools together the users from this mobile app.

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
| created\_at | String | The time when this user was created, ISO8601. Example: 2015-05-28T14:37:14.839+00:00. |
| account\_id | String | The developer account this application belongs to. |
| activity | [ApplicationActivity](data-reference-a-g.md#applicationactivity) | Activity information for this application, contains active users and no of installs |
| users | [UsersConnection](data-reference-q-z.md#usersconnection) | The users that belong to this application. |
| active\_users | [UsersConnection](data-reference-q-z.md#usersconnection) | The users that belong to this application and have been active in the last 7 days. |
| trips | [TripConnection](data-reference-q-z.md#tripconnection) | Trips across all users recorded against this application. |

### ApplicationActivity

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the activity information

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ApplicationActivity' |
| active\_users | [ApplicationActivityGroup](data-reference-a-g.md#applicationactivitygroup) | The active users for the application |
| installs | [ApplicationActivityGroup](data-reference-a-g.md#applicationactivitygroup) | The number of installs for the application |

### ApplicationActivityGroup

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the information for groups: ACTIVE\_USERS, INSTALLS

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ApplicationActivityGroup' |
| daily | [ApplicationActivityGroupItem](data-reference-a-g.md#applicationactivitygroupitem) | The daily application activity data for type and group |
| monthly | [ApplicationActivityGroupItem](data-reference-a-g.md#applicationactivitygroupitem) | The monthly application activity data for the type and group |

### ApplicationActivityGroupItem

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the daily and monthly activity information

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ApplicationActivityGroupItem' |
| date | String | Date |
| count | Float | Count |

### ApplicationsConnection

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the application nodes

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ApplicationsConnection' |
| slice | [Application](data-reference-a-g.md#application) | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. |
| paging | [Paging](data-reference-h-p.md#paging) |  |

### BehaviorAnnotationAnomalyEnum

**Kind**: ENUM

* **phone\_handling**

### BehaviorAnnotationPathWaypoint

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'BehaviorAnnotationPathWaypoint' |
| latitude | Float |  |
| longitude | Float |  |

### BigInt

**Kind**: SCALAR

The `BigInt` scalar type represents non-fractional signed whole numeric values. BigInt can represent values between -\(2^53\) + 1 and 2^53 - 1.

### BoundaryBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'BoundaryBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| quality | [BoundaryBehaviorAnnotationQuality](data-reference-a-g.md#boundarybehaviorannotationquality) |  |

### BoundaryBehaviorAnnotationQuality

**Kind**: ENUM

* **valid**: Section of the transport where the event detection was successful.

### Branch

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A possible series of events predicted for the user.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the branch unique among all the branches returned for the user at the given time. |
| probability | Float | Percentage probability of the events of this beam taking place. |
| events | [IBranchEvent](data-reference-h-p.md#ibranchevent) | The list of events predicted to occur. |

### CarBehaviorFeatures

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'CarBehaviorFeatures' |
| phone\_handling | Int | Total time in milliseconds we detected phone handling by the user during this transport. Value will be -1 when the transport data was not sufficient. |
| distance\_during\_annotations | Int | Distance in meter during which the system had good quality sensor data available to observe transport behavior. Value will be -1 when the transport data was not sufficient. |

### CarBehaviorScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'CarBehaviorScores' |
| focus | Float | The proportion of time \(percentage\) the user is focused while driving, being focused means: not using the phone, which is detected through phone handling. |
| mounted | Float | The proportion of time \(percentage\) the phone is mounted while driving. |
| hard\_accel | Float | Measures how often you accelerate hard. Every hard acceleration will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| hard\_brake | Float | Measures how often you need to brake hard. Every hard brake will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| hard\_events | Float | This is a combination of hard\_accel and hard\_brake score. The hard brakes and accelerations are also normalized by the total number of events. When we do not have sufficient data this value will be -1. |
| legal\_v2 | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we do not have sufficient data the value will be -1. |
| hard\_turn | Float | Measures how often you turn hard. Every hard turn will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| smooth\_v2 | Float | The smooth driving score measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, the difference with smooth score v1 is that turns are also taken in account. |
| anticipative\_v2 | Float | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The higher your score, the more anticipative you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, this new version has a more accurate detection of brakes in turns. |
| handheld\_calling | Float | A score based on how much time you spent using your phone and calling \(1 means good behavior\). |
| handheld\_calling\_duration | Int | Total time in seconds the user was calling while holding the phone during the transport. |
| handsfree\_calling | Float | A score based on how much time you spent calling without holding your phone \(1 means good behavior\). |
| handsfree\_calling\_duration | Int | Total time in seconds the user was calling handsfree during the transport. |
| handling\_without\_calling | Float | A score based on how much time you spent holding your phone without calling \(assume typing, texting etc.\) |
| handling\_without\_calling\_duration | Int | Total time in seconds the user held the phone without calling \(assume typing, texting etc.\) during the transport. |
| attention | Float | A combined score of handheld\_calling, handsfree\_calling and handling\_without\_calling. |

### CityMoment

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment) An occurrence of a City moment that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'CityMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| start\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. |
| moment\_definition\_id | String | The ID of the MomentDefinition this moment relates to. |
| moment\_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. |
| city\_name | String | The name of the city this moment applies to. |

### CommuteTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'CommuteTimeAggregate' |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  |
| transport\_duration | Float |  |
| mode\_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |

### ControlUser

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](data-reference-h-p.md#iuser) A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'ControlUser' |
| email | String | The email address that is optionally linked to provide access to the [https://developers.sentiance.com](https://developers.sentiance.com) and others. |
| account\_roles | [UserAccountRole](data-reference-q-z.md#useraccountrole) | The accounts this user has elevated permissions to. |
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

### CountryMoment

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment) An occurrence of a Country moment that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'CountryMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| start\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. |
| moment\_definition\_id | String | The ID of the MomentDefinition this moment relates to. |
| moment\_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. |
| country\_name | String | The name of the country this moment applies to. |

### CustomEvent

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Custom Events.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the event in the Sentiance system. This is unique across all custom events |
| created\_at | String | The time this event was created ISO8601. |
| created\_at\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| type | String | 'CustomEvent' |
| start | String | The time this event started, ISO8601. |
| end | String | The time this event ended, ISO8601. Value can be null when it is a one time event. |
| start\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| source | [CustomEventSources](data-reference-a-g.md#customeventsources) | Where the event originates. |
| event\_id | String |  |
| latitude | Float | Latitude value of the event. |
| longitude | Float | Longitude value of the event. |
| values | [JSON](data-reference-h-p.md#json) | JSON string of key,value pairs submitted during event creation. |

### CustomEventSources

**Kind**: ENUM

* **SDK**: Event was generated in the SDK.
* **ENCLOSING\_APP**: The enclosing application was generating the event through the SDK.
* **CUSTOMER**: The event was sent by the Customer.

  Where the custome event originates at.

### DayCountAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDayCountAnomaly](data-reference-h-p.md#idaycountanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DayCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day\_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. |
| observed\_days | Float | Observed amount of days. |
| expected\_days | Float | Expected amount of days. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference-q-z.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### DayPart

**Kind**: ENUM

* **morning**: Local time between 06:00-10:00.
* **noon**: Local time between 10:00-14:00.
* **afternoon**: Local time between 14:00-17:00.
* **evening**: Local time between 17:00-24:00.
* **night**: Local time between 00:00-06:00.
* **business**: Business hours, local time between 08:00-18:00.
* **non\_business**: Non-business hours, local time excluding 08:00 - 18:00.

  Grouping of local time.

### DeviceInfo

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Tracking device metadata.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'DeviceInfo' |
| os | [OperatingSystem](data-reference-h-p.md#operatingsystem) | The operating system this device is running. |
| os\_version | String | The version of the operating system this device is running. |

### DistanceAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDistanceAnomaly](data-reference-h-p.md#idistanceanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DistanceAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_distance | Float | Observed distance in meter. |
| expected\_distance | Float | Expected distance in meter. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference-q-z.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### DurationAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDurationAnomaly](data-reference-h-p.md#idurationanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DurationAnomaly' |
| start | String |  |
| end | String |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) |  |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed\_duration | Float | Observed duration in seconds. |
| expected\_duration | Float | Expected duration in seconds. |
| place\_category | String |  |
| location\_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  |
| transport\_mode | [TransportMode](data-reference-q-z.md#transportmode) |  |
| transport\_mode\_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  |
| moment\_definition\_id | String |  |

### EventFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type | Description |
| :--- | :--- | :--- |
| type\_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected type is correct. |
| place\_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected place is correct. |
| place\_feedback | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) | The place candidate that was selected by the user as a better match, if any. |
| significance\_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected location significance is correct. |
| significance\_feedback | [LocationSignificance](data-reference-h-p.md#locationsignificance) | The location significance that was selected by the user as a better match, if any. |
| mode\_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | What the user thinks about the transport mode. |
| mode\_feedback | [TransportMode](data-reference-q-z.md#transportmode) | The transport mode that was selected by the user as a better match, if any. |
| occupant\_role\_feedback | [TransportOccupantRole](data-reference-q-z.md#transportoccupantrole) | The occupant role that was selected by the user as a better match, if any. |

### EventType

**Kind**: ENUM

* **Transport**
* **Stationary**

### FeedbackAssessment

**Kind**: ENUM

* **correct**: When the user confirms the detection is correct.
* **incorrect**: When the user finds the detection not correct.

### FeedbackType

**Kind**: ENUM

* **StationaryFeedback**: Feedback on a detected Stationary event.
* **TransportFeedback**: Feedback on a detected Transport event.
* **MomentFeedback**: Feedback on a detected moment.

### FloatAttribute

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A float attribute

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'FloatAttribute' |
| value | Float |  |

### GenericMoment

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment) An occurrence of a moment that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'GenericMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 |
| start\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| end\_ts | [BigInt](data-reference-a-g.md#bigint) |  |
| analysis\_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time. Possible values: preliminary, indepth, processed. |
| moment\_definition\_id | String | The ID of the MomentDefinition this moment relates to. |
| moment\_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. |

### GenericSegment

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ISegment](data-reference-h-p.md#isegment) An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](data-reference-q-z.md#segmenttype) | 'GenericSegment' |
| segment\_definition\_id | String | The ID of the SegmentDefinition this segment relates to. |
| explanation | String | Reasoning why this segment was assigned to this user from a third person point of view. |
| explanation\_you | String | Reasoning why this segment was assigned to this from a second person point of view. |
| segment\_definition | [SegmentDefinition](data-reference-q-z.md#segmentdefinition) | The SegmentDefinition this segment relates to. |

