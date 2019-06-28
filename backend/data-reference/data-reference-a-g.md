# Data Reference A-G
## Objects
- [AccelerationBehaviorAnnotation](#accelerationbehaviorannotation)
- [AccessToken](#accesstoken)
- [Account](#account)
- [Address](#address)
- [AggregatedDistanceAnomaly](#aggregateddistanceanomaly)
- [AggregatedDurationAnomaly](#aggregateddurationanomaly)
- [AnomalyBehaviorAnnotation](#anomalybehaviorannotation)
- [Application](#application)
- [ApplicationsConnection](#applicationsconnection)
- [BehaviorAnnotationPathWaypoint](#behaviorannotationpathwaypoint)
- [BoundaryBehaviorAnnotation](#boundarybehaviorannotation)
- [Branch](#branch)
- [CarBehaviorFeatures](#carbehaviorfeatures)
- [CarBehaviorScores](#carbehaviorscores)
- [CityMoment](#citymoment)
- [CommuteTimeAggregate](#commutetimeaggregate)
- [ControlUser](#controluser)
- [CountryMoment](#countrymoment)
- [CustomEvent](#customevent)
- [DayCountAnomaly](#daycountanomaly)
- [DeviceInfo](#deviceinfo)
- [DistanceAnomaly](#distanceanomaly)
- [DurationAnomaly](#durationanomaly)
- [EventFeedback](#eventfeedback)
- [FloatAttribute](#floatattribute)
- [GenericMoment](#genericmoment)
- [GenericSegment](#genericsegment)

### AccelerationBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'AccelerationBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| duration | Int |  |
| acceleration | [AccelerationEnum](#accelerationenum) |  |
| path | [BehaviorAnnotationPathWaypoint](#behaviorannotationpathwaypoint) |  |
| magnitude | Float | The longitudinal g-force you experience during accelerations and brakes, measured in (0.2*m)/s². Doing a fast acceleration will result in a higher value compared to a slower acceleration. |


### AccelerationEnum
**Kind**: ENUM

- **accelerate**
- **brake**
- **coast**

### AccessToken
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'AccessToken' |
| token | String | The access (bearer) token |
| expires_at | String | When this token will expire |


### Account
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Account' |
| id | String |  |
| display_name | String |  |
| created_at | String |  |
| applications | [ApplicationsConnection](#applicationsconnection) | The applications that belong to this account. |


### Address
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Address' |
| country | String |  |
| city | String |  |
| city_type | String |  |


### AggregatedDistanceAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](#ianomaly), [IDistanceAnomaly](#idistanceanomaly), [IAggregatedAnomaly](#iaggregatedanomaly), [IStationaryAnomaly](#istationaryanomaly), [ITransportAnomaly](#itransportanomaly), [IMomentAnomaly](#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'AggregatedDistanceAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed_distance | Float | Observed distance in meter. |
| expected_distance | Float | Expected distance in meter. |
| period | [AnomalyTimePeriod](#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](#daypart) | Optional additional aggregation over which the data is calculated. |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |
| moment_definition_id | String |  |


### AggregatedDurationAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](#ianomaly), [IDurationAnomaly](#idurationanomaly), [IAggregatedAnomaly](#iaggregatedanomaly), [IStationaryAnomaly](#istationaryanomaly), [ITransportAnomaly](#itransportanomaly), [IMomentAnomaly](#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'AggregatedDurationAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed_duration | Float | Observed duration in seconds. |
| expected_duration | Float | Expected duration in seconds. |
| period | [AnomalyTimePeriod](#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](#daypart) | Optional additional aggregation over which the data is calculated. |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |
| moment_definition_id | String |  |


### AnalysisType
**Kind**: ENUM

- **processed**: The most detailed processing with the highest latency. This processing also takes into account motion sensor data, does advanced timelining corrections.
- **indepth**: When data is analyzed with potentially more information available compared to the initial preliminary analysis. This type of processing also takes into account motion sensor data.
- **preliminary**: The initial realtime analysis of data with the lowest latency.
The platform analyzes data in multiple stages, and updates values over time, how well the data is analyzed, can be identified by the analysis type.

### Anomaly
**Kind**: ENUM

- **transport_distance**
- **transport_duration**
- **transport_mode_distance**
- **transport_mode_duration**
- **transport_mode_category_distance**
- **transport_mode_category_duration**
- **transport_day_part_distance**
- **transport_day_part_duration**
- **transport_mode_category_occurrence_count**
- **stationary_location_significance_duration**
- **stationary_location_significance_day_part_duration**
- **stationary_place_category_day_count**
- **stationary_location_significance_day_part_day_count**
- **stationary_place_category_duration**
- **stationary_place_category_occurrence_count**
- **moment_duration**
- **commute_distance**
- **commute_duration**: This is an aggregation over the commute_from_home and commute_from_work moments, it includes small stationaries during commutes (such as stopping at the gas station).
- **commute_transport_mode_category_duration**
- **working_duration**
- **dogwalk_occurrence_count**

### AnomalyBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'AnomalyBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| anomaly | [BehaviorAnnotationAnomalyEnum](#behaviorannotationanomalyenum) |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](#behaviorannotationpathwaypoint) |  |


### AnomalyTimePeriod
**Kind**: ENUM

- **day**: Anomaly calculated on a daily basis.
- **week**: Anomaly calculated on a weekly basis.
- **month**: Anomaly calculated on a montly basis.
- **semantic_day**: Anomaly calculated on the semantic day of the user.
- **weekend_day**: Anomaly calculated on a daily basis, ex: each day of the weekend you are at home on average N hours, then if you are not home both days = 2 anomalies (one for saturday, one for sunday) will be available.

### AnomalyType
**Kind**: ENUM

- **DistanceAnomaly**
- **AggregatedDistanceAnomaly**
- **DurationAnomaly**
- **AggregatedDurationAnomaly**
- **DayCountAnomaly**
- **OccurrenceCountAnomaly**

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
| project_code | String | An optional project code used to assign users from the demo applications to this application. |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00. |
| account_id | String | The developer account this application belongs to. |
| users | [UsersConnection](#usersconnection) | The users that belong to this application. |
| active_users | [UsersConnection](#usersconnection) | The users that belong to this application and have been active in the last 7 days. |
| trips | [TripConnection](#tripconnection) | Trips across all users recorded against this application. |


### ApplicationsConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the application nodes

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ApplicationsConnection' |
| slice | [Application](#application) | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. |
| paging | [Paging](#paging) |  |


### BehaviorAnnotationAnomalyEnum
**Kind**: ENUM

- **phone_handling**

### BehaviorAnnotationPathWaypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'BehaviorAnnotationPathWaypoint' |
| latitude | Float |  |
| longitude | Float |  |


### BigInt
**Kind**: SCALAR

The `BigInt` scalar type represents non-fractional signed whole numeric values. BigInt can represent values between -(2^53) + 1 and 2^53 - 1. 

### BoundaryBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'BoundaryBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| quality | [BoundaryBehaviorAnnotationQuality](#boundarybehaviorannotationquality) |  |


### BoundaryBehaviorAnnotationQuality
**Kind**: ENUM

- **valid**: Section of the transport where the event detection was successful.

### Branch
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A possible series of events predicted for the user.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the branch unique among all the branches returned for the user at the given time. |
| probability | Float | Percentage probability of the events of this beam taking place. |
| events | [IBranchEvent](#ibranchevent) | The list of events predicted to occur. |


### CarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'CarBehaviorFeatures' |
| phone_handling | Int | Total time in milliseconds we detected phone handling by the user during this transport. Value will be -1 when the transport data was not sufficient. |
| distance_during_annotations | Int | Distance in meter during which the system had good quality sensor data available to observe transport behavior. Value will be -1 when the transport data was not sufficient. |


### CarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'CarBehaviorScores' |
| overall | Float | An aggregation of all scores where we had sufficient data. A low score in one of the scores will result in a lower overall score.  |
| smooth | Float | The smooth driving score measures how calm you drive. High accelerations and heavy braking result in a lower score, the use of coasting results in a higher score. The higher your score, the calmer you drive! When we did not have sufficient data value will be -1. |
| legal | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we did not have sufficient data value will be -1. |
| anticipative | Float | The anticipative driving score measures how well you anticipate traffic. A fast sequence of braking and accelerations in general traffic situations results in a lower score, the use of coasting results in a higher score. The higher your score, the more anticipative you drive! When we did not have sufficient data value will be -1. |
| focus | Float | The proportion of time (percentage) the user is focused while driving, being focused means: not using the phone, which is detected through phone handling. |
| mounted | Float | The proportion of time (percentage) the phone is mounted while driving. |
| hard_accel | Float | Measures how often you accelerate hard. Every hard acceleration will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| hard_brake | Float | Measures how often you need to brake hard. Every hard brake will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| hard_events | Float | This is a combination of hard_accel and hard_brake score. The hard brakes and accelerations are also normalized by the total number of events. When we do not have sufficient data this value will be -1. |
| legal_v2 | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we did not have sufficient data value will be -1. The difference with legal score is that this score has better speed estimation. |
| hard_turn | Float | Measures how often you turn hard. Every hard turn will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. |
| smooth_v2 | Float | The smooth driving score measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. The use of coasting results in a higher score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! When we did not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, the difference with smooth score v1 is that turns are also taken in account. |
| anticipative_v2 | Float | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The use of coasting results in a higher score. The higher your score, the more anticipative you drive! When we did not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, this new version has a more accurate detection of brakes in turns. |
| handheld_calling | Float | A score based on how much time you spent using your phone and calling (1 means good behavior). |
| handsfree_calling | Float | A score based on how much time you spent calling without holding your phone (1 means good behavior). |
| handling_without_calling | Float | A score based on how much time you spent holding your phone without calling (assume typing, texting etc.) |
| attention | Float | A combined score of handheld_calling, handsfree_calling and handling_without_calling. |


### CityMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](#imoment)
An occurrence of a City moment that we have detected for a user. 

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'CityMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |
| city_name | String | The name of the city this moment applies to. |


### CommuteTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](#itimeaggregateattribute), [IUserAttribute](#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](#userattributetype) | 'CommuteTimeAggregate' |
| period | [TimePeriod](#timeperiod) |  |
| transport_duration | Float |  |
| mode_category | [TransportModeCategory](#transportmodecategory) |  |


### ControlUser
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](#iuser)
A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](#usertype) | 'ControlUser' |
| email | String | The email address that is optionally linked to provide access to the https://developers.sentiance.com and others. |
| account_roles | [UserAccountRole](#useraccountrole) | The accounts this user has elevated permissions to. |
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


### CountryMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](#imoment)
An occurrence of a Country moment that we have detected for a user. 

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'CountryMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |
| country_name | String | The name of the country this moment applies to. |


### CustomEvent
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Custom Events.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the event in the Sentiance system. This is unique across all custom events |
| created_at | String | The time this event was created ISO8601. |
| created_at_ts | [BigInt](#bigint) |  |
| type | String | 'CustomEvent' |
| start | String | The time this event started, ISO8601. |
| end | String | The time this event ended, ISO8601. Value can be null when it is a one time event. |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| source | [CustomEventSources](#customeventsources) | Where the event originates. |
| event_id | String |  |
| latitude | Float | Latitude value of the event. |
| longitude | Float | Longitude value of the event. |
| values | [JSON](#json) | JSON string of key,value pairs submitted during event creation. |


### CustomEventSources
**Kind**: ENUM

- **SDK**: Event was generated in the SDK.
- **ENCLOSING_APP**: The enclosing application was generating the event through the SDK.
- **CUSTOMER**: The event was sent by the Customer.
Where the custome event originates at.

### DayCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](#ianomaly), [IDayCountAnomaly](#idaycountanomaly), [IAggregatedAnomaly](#iaggregatedanomaly), [IStationaryAnomaly](#istationaryanomaly), [ITransportAnomaly](#itransportanomaly), [IMomentAnomaly](#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'DayCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](#daypart) | Optional additional aggregation over which the data is calculated. |
| observed_days | Float | Observed amount of days. |
| expected_days | Float | Expected amount of days. |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |
| moment_definition_id | String |  |


### DayPart
**Kind**: ENUM

- **morning**: Local time between 06:00-10:00.
- **noon**: Local time between 10:00-14:00.
- **afternoon**: Local time between 14:00-17:00.
- **evening**: Local time between 17:00-24:00.
- **night**: Local time between 00:00-06:00.
- **business**: Business hours, local time between 08:00-18:00.
- **non_business**: Non-business hours, local time excluding 08:00 - 18:00.
Grouping of local time.

### DeviceInfo
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Tracking device metadata.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'DeviceInfo' |
| os | [OperatingSystem](#operatingsystem) | The operating system this device is running. |
| os_version | String | The version of the operating system this device is running. |


### DistanceAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](#ianomaly), [IDistanceAnomaly](#idistanceanomaly), [IStationaryAnomaly](#istationaryanomaly), [ITransportAnomaly](#itransportanomaly), [IMomentAnomaly](#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'DistanceAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed_distance | Float | Observed distance in meter. |
| expected_distance | Float | Expected distance in meter. |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |
| moment_definition_id | String |  |


### DurationAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](#ianomaly), [IDurationAnomaly](#idurationanomaly), [IStationaryAnomaly](#istationaryanomaly), [ITransportAnomaly](#itransportanomaly), [IMomentAnomaly](#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'DurationAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| observed_duration | Float | Observed duration in seconds. |
| expected_duration | Float | Expected duration in seconds. |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |
| moment_definition_id | String |  |


### EventFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description |
| :--- | :--- | :--- |
| type_assessment | [FeedbackAssessment](#feedbackassessment) | If the user thinks the detected type is correct. |
| place_assessment | [FeedbackAssessment](#feedbackassessment) | If the user thinks the detected place is correct. |
| place_feedback | [LocationPlaceCandidate](#locationplacecandidate) | The place candidate that was selected by the user as a better match, if any. |
| significance_assessment | [FeedbackAssessment](#feedbackassessment) | If the user thinks the detected location significance is correct. |
| significance_feedback | [LocationSignificance](#locationsignificance) | The location significance that was selected by the user as a better match, if any. |
| mode_assessment | [FeedbackAssessment](#feedbackassessment) | What the user thinks about the transport mode. |
| mode_feedback | [TransportMode](#transportmode) | The transport mode that was selected by the user as a better match, if any. |
| occupant_role_feedback | [TransportOccupantRole](#transportoccupantrole) | The occupant role that was selected by the user as a better match, if any. |


### EventType
**Kind**: ENUM

- **Transport**
- **Stationary**

### FeedbackAssessment
**Kind**: ENUM

- **correct**: When the user confirms the detection is correct.
- **incorrect**: When the user finds the detection not correct.

### FeedbackType
**Kind**: ENUM

- **StationaryFeedback**: Feedback on a detected Stationary event.
- **TransportFeedback**: Feedback on a detected Transport event.
- **MomentFeedback**: Feedback on a detected moment.

### FloatAttribute
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A float attribute

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'FloatAttribute' |
| value | Float |  |


### GenericMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](#imoment)
An occurrence of a moment that we have detected for a user. 

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'GenericMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |


### GenericSegment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ISegment](#isegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](#segmenttype) | 'GenericSegment' |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. |
| explanation | String | Reasoning why this segment was assigned to this user from a third person point of view. |
| explanation_you | String | Reasoning why this segment was assigned to this from a second person point of view. |
| segment_definition | [SegmentDefinition](#segmentdefinition) | The SegmentDefinition this segment relates to. |


