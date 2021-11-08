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
- [ApplicationActivity](#applicationactivity)
- [ApplicationActivityGroup](#applicationactivitygroup)
- [ApplicationActivityGroupItem](#applicationactivitygroupitem)
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
- [Crash](#crash)
- [CrashFeedback](#crashfeedback)
- [CrashFeedbackFeedback](#crashfeedbackfeedback)
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

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'AccelerationBehaviorAnnotation' | False |
| start | String |  | False |
| end | String |  | False |
| duration | Int | Duration is in milliseconds. | False |
| acceleration | [AccelerationEnum](data-reference-a-g.md#accelerationenum) |  | False |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | False |
| magnitude | Float | The longitudinal g-force you experience during accelerations and brakes, measured in (0.2*m)/s². Doing a fast acceleration will result in a higher value compared to a slower acceleration. | False |


### AccelerationEnum
**Kind**: ENUM

- **accelerate**
- **brake**
- **coast**

### AccessToken
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'AccessToken' | False |
| token | String | The access (bearer) token | False |
| expires_at | String | When this token will expire | False |


### Account
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Account' | False |
| id | String |  | False |
| display_name | String |  | False |
| created_at | String |  | False |
| applications | [ApplicationsConnection](data-reference-a-g.md#applicationsconnection) | The applications that belong to this account. | False |


### Address
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Address' | False |
| country | String |  | False |
| city | String |  | False |
| city_type | String |  | False |


### AggregatedDistanceAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDistanceAnomaly](data-reference-h-p.md#idistanceanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'AggregatedDistanceAnomaly' | False |
| start | String |  | False |
| end | String |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | False |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | False |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | False |
| observed_distance | Float | Observed distance in meter. | False |
| expected_distance | Float | Expected distance in meter. | False |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | False |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | False |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |
| moment_definition_id | String |  | False |


### AggregatedDurationAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDurationAnomaly](data-reference-h-p.md#idurationanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'AggregatedDurationAnomaly' | False |
| start | String |  | False |
| end | String |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | False |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | False |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | False |
| observed_duration | Float | Observed duration in seconds. | False |
| expected_duration | Float | Expected duration in seconds. | False |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | False |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | False |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |
| moment_definition_id | String |  | False |


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

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'AnomalyBehaviorAnnotation' | False |
| start | String |  | False |
| end | String |  | False |
| anomaly | [BehaviorAnnotationAnomalyEnum](data-reference-a-g.md#behaviorannotationanomalyenum) |  | False |
| duration | Int | Duration is in milliseconds. | False |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | False |


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

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Application' | False |
| id | String | The unique identifier for this application. | False |
| secret | String | The secret required when integrating the mobile SDK with this application ID. | False |
| name | String | The name of this application. For mobile apps it's the name how it's available in the AppStore/PlayStore. | False |
| description | String | A short description of this application. | False |
| logging | String | An optional override for the default debug logging behavior of the mobile SDKs. | False |
| flavor | String | An optional override for the default flavor configuration of the mobile SDKs. | False |
| project_code | String | An optional project code used to assign users from the demo applications to this application. | False |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00. | False |
| account_id | String | The developer account this application belongs to. | False |
| activity | [ApplicationActivity](data-reference-a-g.md#applicationactivity) | Activity information for this application, contains active users and no of installs | False |
| users | [UsersConnection](data-reference-q-z.md#usersconnection) | The users that belong to this application. | False |
| active_users | [UsersConnection](data-reference-q-z.md#usersconnection) | The users that belong to this application and have been active in the last 7 days. | False |
| trips | [TripConnection](data-reference-q-z.md#tripconnection) | Trips across all users recorded against this application. | False |


### ApplicationActivity
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the activity information

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivity' | False |
| active_users | [ApplicationActivityGroup](data-reference-a-g.md#applicationactivitygroup) | The active users for the application | False |
| installs | [ApplicationActivityGroup](data-reference-a-g.md#applicationactivitygroup) | The number of installs for the application | False |


### ApplicationActivityGroup
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the information for groups: ACTIVE_USERS, INSTALLS

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivityGroup' | False |
| daily | [ApplicationActivityGroupItem](data-reference-a-g.md#applicationactivitygroupitem) | The daily application activity data for type and group | False |
| monthly | [ApplicationActivityGroupItem](data-reference-a-g.md#applicationactivitygroupitem) | The monthly application activity data for the type and group | False |


### ApplicationActivityGroupItem
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the daily and monthly activity information

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivityGroupItem' | False |
| date | String | Date | False |
| count | Float | Count | False |


### ApplicationsConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the application nodes

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationsConnection' | False |
| slice | [Application](data-reference-a-g.md#application) | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. | False |
| paging | [Paging](data-reference-h-p.md#paging) |  | False |


### BehaviorAnnotationAnomalyEnum
**Kind**: ENUM

- **phone_handling**

### BehaviorAnnotationPathWaypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'BehaviorAnnotationPathWaypoint' | False |
| latitude | Float |  | False |
| longitude | Float |  | False |
| index | Int | <br><code>**Deprecation notice**</code><br>index is deprecated.<br>Obsolete | False |


### BigInt
**Kind**: SCALAR

The `BigInt` scalar type represents non-fractional signed whole numeric values. BigInt can represent values between -(2^53) + 1 and 2^53 - 1. 

### BoundaryBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'BoundaryBehaviorAnnotation' | False |
| start | String |  | False |
| end | String |  | False |
| quality | [BoundaryBehaviorAnnotationQuality](data-reference-a-g.md#boundarybehaviorannotationquality) |  | False |


### BoundaryBehaviorAnnotationQuality
**Kind**: ENUM

- **valid**: Section of the transport where the event detection was successful.

### Branch
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A possible series of events predicted for the user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| id | String | Id of the branch unique among all the branches returned for the user at the given time. | False |
| probability | Float | Percentage probability of the events of this beam taking place. | False |
| events | [IBranchEvent](data-reference-h-p.md#ibranchevent) | The list of events predicted to occur. | False |


### CarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'CarBehaviorFeatures' | False |
| phone_handling | Int | Total time in milliseconds we detected phone handling by the user during this transport. Value will be -1 when the transport data was not sufficient. | False |
| distance_during_annotations | Int | Distance in meter during which the system had good quality sensor data available to observe transport behavior. Value will be -1 when the transport data was not sufficient. | False |


### CarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'CarBehaviorScores' | False |
| overall | Float | An aggregation of all scores where we had sufficient data. A low score in one of the scores will result in a lower overall score. <br><br><code>**Deprecation notice**</code><br>overall is deprecated.<br>Deprecated as it is computed based on the v1 scores. | False |
| smooth | Float | The smooth driving score measures how calm you drive. High accelerations and heavy braking result in a lower score, the use of coasting results in a higher score. The higher your score, the calmer you drive! When we do not have sufficient data the value will be -1.<br><br><code>**Deprecation notice**</code><br>smooth is deprecated.<br>Deprecated in favor of `smooth_v2`. | False |
| legal | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we do not have sufficient data the value will be -1.<br><br><code>**Deprecation notice**</code><br>legal is deprecated.<br>Deprecated in favor of `legal_v2`. | False |
| anticipative | Float | The anticipative driving score measures how well you anticipate traffic. A fast sequence of braking and accelerations in general traffic situations results in a lower score, the use of coasting results in a higher score. The higher your score, the more anticipative you drive! When we do not have sufficient data the value will be -1.<br><br><code>**Deprecation notice**</code><br>anticipative is deprecated.<br>Deprecated in favor of `anticipative_v2`. | False |
| focus | Float | The proportion of time (percentage) the user is focused while driving, being focused means: not using the phone, which is detected through phone handling. | False |
| mounted | Float | The proportion of time (percentage) the phone is mounted while driving. | False |
| hard_accel | Float | Measures how often you accelerate hard. Every hard acceleration will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. | False |
| hard_brake | Float | Measures how often you need to brake hard. Every hard brake will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. | False |
| hard_events | Float | This is a combination of hard_accel and hard_brake score. The hard brakes and accelerations are also normalized by the total number of events. When we do not have sufficient data this value will be -1. | False |
| legal_v2 | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we do not have sufficient data the value will be -1. | False |
| hard_turn | Float | Measures how often you turn hard. Every hard turn will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. | False |
| smooth_v2 | Float | The smooth driving score measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, the difference with smooth score v1 is that turns are also taken in account. | False |
| anticipative_v2 | Float | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The higher your score, the more anticipative you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, this new version has a more accurate detection of brakes in turns. | False |
| handheld_calling | Float | A score based on how much time you spent using your phone and calling (1 means good behavior). | False |
| handheld_calling_duration | Int | Total time in seconds the user was calling while holding the phone during the transport. | False |
| handsfree_calling | Float | A score based on how much time you spent calling without holding your phone (1 means good behavior). | False |
| handsfree_calling_duration | Int | Total time in seconds the user was calling handsfree during the transport. | False |
| handling_without_calling | Float | A score based on how much time you spent holding your phone without calling (assume typing, texting etc.) | False |
| handling_without_calling_duration | Int | Total time in seconds the user held the phone without calling (assume typing, texting etc.) during the transport. | False |
| attention | Float | A combined score of handheld_calling, handsfree_calling and handling_without_calling. | False |


### CityMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment)
An occurrence of a City moment that we have detected for a user. 

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'CityMoment' | False |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | False |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | False |
| city_name | String | The name of the city this moment applies to. | False |


### CommuteTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'CommuteTimeAggregate' | False |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | False |
| transport_duration | Float |  | False |
| mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |


### ControlUser
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](data-reference-h-p.md#iuser)
A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'ControlUser' | False |
| email | String | The email address that is optionally linked to provide access to the https://developers.sentiance.com and others. | False |
| account_roles | [UserAccountRole](data-reference-q-z.md#useraccountrole) | The accounts this user has elevated permissions to. | False |
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


### CountryMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment)
An occurrence of a Country moment that we have detected for a user. 

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'CountryMoment' | False |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | False |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | False |
| country_name | String | The name of the country this moment applies to. | False |


### Crash
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An occurrence of a Crash that we have detected for a user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| max_magnitude | Int | Peak magnitude in m/s^2 multiplied by 100 (e.g. a value of 150 is actually 1.5 m/s^2). | False |
| timestamp | String | The time the crash happened, in ISO8601 format. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 | True |
| confidence | Int | (0-100) confidence level that the crash is a true positive. | False |
| speed_at_impact | Int | Estimated speed in which the vehicle was travelling before the impact in m/s multiplied by a 100 (e.g., a value of 750 is actually 7.50 m/s. | False |
| delta_v | Int | Estimated change in velocity at impact in m/s multiplied by a 100. This is estimated from the acceleration signal. | False |
| waypoint | [Waypoint](data-reference-q-z.md#waypoint) | To be filled | False |
| on_device_ml_model | [OndeviceMLModel](data-reference-h-p.md#ondevicemlmodel) | Name of the models that were used to detect the crash. Mainly used as internal reference. | False |


### CrashFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'CrashFeedback' | False |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | True |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | False |
| created | String | Time when this feedback entry was created. | False |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | False |
| crash_feedback | [CrashFeedbackFeedback](data-reference-a-g.md#crashfeedbackfeedback) |  | False |
| crash | [Crash](data-reference-a-g.md#crash) | The Crash this feedback refers to. | False |


### CrashFeedbackConfirmation
**Kind**: ENUM

- **NoCrash**: No crash
- **LowImpactNoAssistance**: Low impact crash and no assistance required.
- **LowImpactVehicleTowed**: Low impact crash but the vehicle had to be towed.
- **HighImpactEmergencyAssistance**: High impact crash that required ambulance/police assistance.

### CrashFeedbackFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| feedback_type_of_crash | [CrashFeedbackType](data-reference-a-g.md#crashfeedbacktype) | This field represents feedback about the type of the crash. | False |
| feedback_airbag_deployed | Boolean | This field represents feedback to confirm if the airbag was deployed during the crash. | False |
| feedback_car_driveable | Boolean | This field represents feedback to confirm if the vehicle was driveable after the crash. | False |
| feedback_confirmation | [CrashFeedbackConfirmation](data-reference-a-g.md#crashfeedbackconfirmation) | This field represents feedback to confirm if a crash happened. | False |


### CrashFeedbackType
**Kind**: ENUM

- **CollisionWithAnimal**: Collision with animal
- **CollisionWithPedestrian**: Collision with pedestrian
- **CollisionWithNonMotorizedVehicle**: Collision with non-motorized vehicle
- **CollisionWithObject**: Collision with an object
- **CollisionWithVehicle**: Collision with a vehicle
- **WindshieldGlassDamaged**: Windshield/glass damaged
- **Others**: Others

### CustomEvent
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Custom Events.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| id | String | The ID of the event in the Sentiance system. This is unique across all custom events | False |
| created_at | String | The time this event was created ISO8601. | False |
| created_at_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| type | String | 'CustomEvent' | False |
| start | String | The time this event started, ISO8601. | False |
| end | String | The time this event ended, ISO8601. Value can be null when it is a one time event. | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| source | [CustomEventSources](data-reference-a-g.md#customeventsources) | Where the event originates. | False |
| event_id | String |  | False |
| latitude | Float | Latitude value of the event. | False |
| longitude | Float | Longitude value of the event. | False |
| values | [JSON](data-reference-h-p.md#json) | JSON string of key,value pairs submitted during event creation. | False |


### CustomEventSources
**Kind**: ENUM

- **SDK**: Event was generated in the SDK.
- **ENCLOSING_APP**: The enclosing application was generating the event through the SDK.
- **CUSTOMER**: The event was sent by the Customer.
Where the custome event originates at.

### DayCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDayCountAnomaly](data-reference-h-p.md#idaycountanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DayCountAnomaly' | False |
| start | String |  | False |
| end | String |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | False |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | False |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | False |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | False |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | False |
| observed_days | Float | Observed amount of days. | False |
| expected_days | Float | Expected amount of days. | False |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |
| moment_definition_id | String |  | False |


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

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'DeviceInfo' | False |
| os | [OperatingSystem](data-reference-h-p.md#operatingsystem) | The operating system this device is running. | False |
| os_version | String | The version of the operating system this device is running. | False |


### DistanceAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDistanceAnomaly](data-reference-h-p.md#idistanceanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DistanceAnomaly' | False |
| start | String |  | False |
| end | String |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | False |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | False |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | False |
| observed_distance | Float | Observed distance in meter. | False |
| expected_distance | Float | Expected distance in meter. | False |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |
| moment_definition_id | String |  | False |


### DurationAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDurationAnomaly](data-reference-h-p.md#idurationanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DurationAnomaly' | False |
| start | String |  | False |
| end | String |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | False |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | False |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | False |
| observed_duration | Float | Observed duration in seconds. | False |
| expected_duration | Float | Expected duration in seconds. | False |
| place_category | String |  | False |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | False |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | False |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | False |
| moment_definition_id | String |  | False |


### EventFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected type is correct. | False |
| place_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected place is correct. | False |
| place_feedback | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) | The place candidate that was selected by the user as a better match, if any. | False |
| significance_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected location significance is correct. | False |
| significance_feedback | [LocationSignificance](data-reference-h-p.md#locationsignificance) | The location significance that was selected by the user as a better match, if any. | False |
| mode_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | What the user thinks about the transport mode. | False |
| mode_feedback | [TransportMode](data-reference-q-z.md#transportmode) | The transport mode that was selected by the user as a better match, if any. | False |
| occupant_role_feedback | [TransportOccupantRole](data-reference-q-z.md#transportoccupantrole) | The occupant role that was selected by the user as a better match, if any. | False |


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
- **CrashFeedback**: Feedback on a detected crash.

### FloatAttribute
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A float attribute

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'FloatAttribute' | False |
| value | Float |  | False |


### GenericMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment)
An occurrence of a moment that we have detected for a user. 

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'GenericMoment' | False |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | False |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | False |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | False |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | False |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | False |


### GenericSegment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ISegment](data-reference-h-p.md#isegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description | Non-Nullable |
| :--- | :--- | :--- | :--- |
| type | [SegmentType](data-reference-q-z.md#segmenttype) | 'GenericSegment' | False |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. | False |
| explanation | String | Reasoning why this segment was assigned to this user from a third person point of view. | False |
| explanation_you | String | Reasoning why this segment was assigned to this from a second person point of view. | False |
| segment_definition | [SegmentDefinition](data-reference-q-z.md#segmentdefinition) | The SegmentDefinition this segment relates to. | False |


