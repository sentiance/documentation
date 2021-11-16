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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'AccelerationBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| acceleration | [AccelerationEnum](data-reference-a-g.md#accelerationenum) |  | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | True |
| magnitude | Float | The longitudinal g-force you experience during accelerations and brakes, measured in (0.2*m)/s². Doing a fast acceleration will result in a higher value compared to a slower acceleration. | True |


### AccelerationEnum
**Kind**: ENUM

- **accelerate**
- **brake**
- **coast**

### AccessToken
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'AccessToken' | True |
| token | String | The access (bearer) token | True |
| expires_at | String | When this token will expire | True |


### Account
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Account' | True |
| id | String |  | True |
| display_name | String |  | True |
| created_at | String |  | True |
| applications | [ApplicationsConnection](data-reference-a-g.md#applicationsconnection) | The applications that belong to this account. | True |


### Address
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Address' | True |
| country | String |  | True |
| city | String |  | True |
| city_type | String |  | True |


### AggregatedDistanceAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDistanceAnomaly](data-reference-h-p.md#idistanceanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'AggregatedDistanceAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| observed_distance | Float | Observed distance in meter. | True |
| expected_distance | Float | Expected distance in meter. | True |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


### AggregatedDurationAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDurationAnomaly](data-reference-h-p.md#idurationanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'AggregatedDurationAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| observed_duration | Float | Observed duration in seconds. | True |
| expected_duration | Float | Expected duration in seconds. | True |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'AnomalyBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| anomaly | [BehaviorAnnotationAnomalyEnum](data-reference-a-g.md#behaviorannotationanomalyenum) |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-g.md#behaviorannotationpathwaypoint) |  | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Application' | True |
| id | String | The unique identifier for this application. | True |
| secret | String | The secret required when integrating the mobile SDK with this application ID. | True |
| name | String | The name of this application. For mobile apps it's the name how it's available in the AppStore/PlayStore. | True |
| description | String | A short description of this application. | True |
| logging | String | An optional override for the default debug logging behavior of the mobile SDKs. | True |
| flavor | String | An optional override for the default flavor configuration of the mobile SDKs. | True |
| project_code | String | An optional project code used to assign users from the demo applications to this application. | True |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00. | True |
| account_id | String | The developer account this application belongs to. | True |
| activity | [ApplicationActivity](data-reference-a-g.md#applicationactivity) | Activity information for this application, contains active users and no of installs | True |
| users | [UsersConnection](data-reference-q-z.md#usersconnection) | The users that belong to this application. | True |
| active_users | [UsersConnection](data-reference-q-z.md#usersconnection) | The users that belong to this application and have been active in the last 7 days. | True |
| trips | [TripConnection](data-reference-q-z.md#tripconnection) | Trips across all users recorded against this application. | True |


### ApplicationActivity
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the activity information

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivity' | True |
| active_users | [ApplicationActivityGroup](data-reference-a-g.md#applicationactivitygroup) | The active users for the application | True |
| installs | [ApplicationActivityGroup](data-reference-a-g.md#applicationactivitygroup) | The number of installs for the application | True |


### ApplicationActivityGroup
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the information for groups: ACTIVE_USERS, INSTALLS

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivityGroup' | True |
| daily | [ApplicationActivityGroupItem](data-reference-a-g.md#applicationactivitygroupitem) | The daily application activity data for type and group | True |
| monthly | [ApplicationActivityGroupItem](data-reference-a-g.md#applicationactivitygroupitem) | The monthly application activity data for the type and group | True |


### ApplicationActivityGroupItem
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the daily and monthly activity information

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivityGroupItem' | True |
| date | String | Date | True |
| count | Float | Count | True |


### ApplicationsConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the application nodes

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationsConnection' | True |
| slice | [Application](data-reference-a-g.md#application) | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. | True |
| paging | [Paging](data-reference-h-p.md#paging) |  | True |


### BehaviorAnnotationAnomalyEnum
**Kind**: ENUM

- **phone_handling**

### BehaviorAnnotationPathWaypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'BehaviorAnnotationPathWaypoint' | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| index | Int | <br><code>**Deprecation notice**</code><br>index is deprecated.<br>Obsolete | True |


### BigInt
**Kind**: SCALAR

The `BigInt` scalar type represents non-fractional signed whole numeric values. BigInt can represent values between -(2^53) + 1 and 2^53 - 1. 

### BoundaryBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-p.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-z.md#transportbehaviorannotationtype) | 'BoundaryBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| quality | [BoundaryBehaviorAnnotationQuality](data-reference-a-g.md#boundarybehaviorannotationquality) |  | True |


### BoundaryBehaviorAnnotationQuality
**Kind**: ENUM

- **valid**: Section of the transport where the event detection was successful.

### Branch
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A possible series of events predicted for the user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| id | String | Id of the branch unique among all the branches returned for the user at the given time. | True |
| probability | Float | Percentage probability of the events of this beam taking place. | True |
| events | [IBranchEvent](data-reference-h-p.md#ibranchevent) | The list of events predicted to occur. | True |


### CarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'CarBehaviorFeatures' | True |
| phone_handling | Int | Total time in milliseconds we detected phone handling by the user during this transport. Value will be -1 when the transport data was not sufficient. | True |
| distance_during_annotations | Int | Distance in meter during which the system had good quality sensor data available to observe transport behavior. Value will be -1 when the transport data was not sufficient. | True |


### CarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'CarBehaviorScores' | True |
| overall | Float | An aggregation of all scores where we had sufficient data. A low score in one of the scores will result in a lower overall score. <br><br><code>**Deprecation notice**</code><br>overall is deprecated.<br>Deprecated as it is computed based on the v1 scores. | True |
| smooth | Float | The smooth driving score measures how calm you drive. High accelerations and heavy braking result in a lower score, the use of coasting results in a higher score. The higher your score, the calmer you drive! When we do not have sufficient data the value will be -1.<br><br><code>**Deprecation notice**</code><br>smooth is deprecated.<br>Deprecated in favor of `smooth_v2`. | True |
| legal | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we do not have sufficient data the value will be -1.<br><br><code>**Deprecation notice**</code><br>legal is deprecated.<br>Deprecated in favor of `legal_v2`. | True |
| anticipative | Float | The anticipative driving score measures how well you anticipate traffic. A fast sequence of braking and accelerations in general traffic situations results in a lower score, the use of coasting results in a higher score. The higher your score, the more anticipative you drive! When we do not have sufficient data the value will be -1.<br><br><code>**Deprecation notice**</code><br>anticipative is deprecated.<br>Deprecated in favor of `anticipative_v2`. | True |
| focus | Float | The proportion of time (percentage) the user is focused while driving, being focused means: not using the phone, which is detected through phone handling. | True |
| mounted | Float | The proportion of time (percentage) the phone is mounted while driving. | True |
| hard_accel | Float | Measures how often you accelerate hard. Every hard acceleration will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. | True |
| hard_brake | Float | Measures how often you need to brake hard. Every hard brake will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. | True |
| hard_events | Float | This is a combination of hard_accel and hard_brake score. The hard brakes and accelerations are also normalized by the total number of events. When we do not have sufficient data this value will be -1. | True |
| legal_v2 | Float | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! When we do not have sufficient data the value will be -1. | True |
| hard_turn | Float | Measures how often you turn hard. Every hard turn will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. | True |
| smooth_v2 | Float | The smooth driving score measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, the difference with smooth score v1 is that turns are also taken in account. | True |
| anticipative_v2 | Float | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The higher your score, the more anticipative you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, this new version has a more accurate detection of brakes in turns. | True |
| handheld_calling | Float | A score based on how much time you spent using your phone and calling (1 means good behavior). | True |
| handheld_calling_duration | Int | Total time in seconds the user was calling while holding the phone during the transport. | True |
| handsfree_calling | Float | A score based on how much time you spent calling without holding your phone (1 means good behavior). | True |
| handsfree_calling_duration | Int | Total time in seconds the user was calling handsfree during the transport. | True |
| handling_without_calling | Float | A score based on how much time you spent holding your phone without calling (assume typing, texting etc.) | True |
| handling_without_calling_duration | Int | Total time in seconds the user held the phone without calling (assume typing, texting etc.) during the transport. | True |
| attention | Float | A combined score of handheld_calling, handsfree_calling and handling_without_calling. | True |


### CityMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment)
An occurrence of a City moment that we have detected for a user. 

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'CityMoment' | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | True |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | True |
| city_name | String | The name of the city this moment applies to. | True |


### CommuteTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-p.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-p.md#iuserattribute)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-q-z.md#userattributetype) | 'CommuteTimeAggregate' | True |
| period | [TimePeriod](data-reference-q-z.md#timeperiod) |  | True |
| transport_duration | Float |  | True |
| mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |


### ControlUser
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](data-reference-h-p.md#iuser)
A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-q-z.md#usertype) | 'ControlUser' | True |
| email | String | The email address that is optionally linked to provide access to the https://developers.sentiance.com and others. | True |
| account_roles | [UserAccountRole](data-reference-q-z.md#useraccountrole) | The accounts this user has elevated permissions to. | True |
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


### CountryMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment)
An occurrence of a Country moment that we have detected for a user. 

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'CountryMoment' | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | True |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | True |
| country_name | String | The name of the country this moment applies to. | True |


### Crash
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An occurrence of a Crash that we have detected for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| max_magnitude | Int | Peak magnitude in m/s^2 multiplied by 100 (e.g. a value of 150 is actually 1.5 m/s^2). | True |
| timestamp | String | The time the crash happened, in ISO8601 format. Value can change and become more accurate over time. Example: 2015-05-28T14:37:14.839+00:00 | False |
| confidence | Int | (0-100) confidence level that the crash is a true positive. | True |
| speed_at_impact | Int | Estimated speed in which the vehicle was travelling before the impact in m/s multiplied by a 100 (e.g., a value of 750 is actually 7.50 m/s. | True |
| delta_v | Int | Estimated change in velocity at impact in m/s multiplied by a 100. This is estimated from the acceleration signal. | True |
| waypoint | [Waypoint](data-reference-q-z.md#waypoint) | To be filled | True |
| on_device_ml_model | [OndeviceMLModel](data-reference-h-p.md#ondevicemlmodel) | Name of the models that were used to detect the crash. Mainly used as internal reference. | True |


### CrashFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-p.md#ifeedback)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-a-g.md#feedbacktype) | 'CrashFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |
| crash_feedback | [CrashFeedbackFeedback](data-reference-a-g.md#crashfeedbackfeedback) |  | True |
| crash | [Crash](data-reference-a-g.md#crash) | The Crash this feedback refers to. | True |


### CrashFeedbackConfirmation
**Kind**: ENUM

- **NoCrash**: No crash
- **LowImpactNoAssistance**: Low impact crash and no assistance required.
- **LowImpactVehicleTowed**: Low impact crash but the vehicle had to be towed.
- **HighImpactEmergencyAssistance**: High impact crash that required ambulance/police assistance.

### CrashFeedbackFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| feedback_type_of_crash | [CrashFeedbackType](data-reference-a-g.md#crashfeedbacktype) | This field represents feedback about the type of the crash. | True |
| feedback_airbag_deployed | Boolean | This field represents feedback to confirm if the airbag was deployed during the crash. | True |
| feedback_car_driveable | Boolean | This field represents feedback to confirm if the vehicle was driveable after the crash. | True |
| feedback_confirmation | [CrashFeedbackConfirmation](data-reference-a-g.md#crashfeedbackconfirmation) | This field represents feedback to confirm if a crash happened. | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| id | String | The ID of the event in the Sentiance system. This is unique across all custom events | True |
| created_at | String | The time this event was created ISO8601. | True |
| created_at_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| type | String | 'CustomEvent' | True |
| start | String | The time this event started, ISO8601. | True |
| end | String | The time this event ended, ISO8601. Value can be null when it is a one time event. | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| source | [CustomEventSources](data-reference-a-g.md#customeventsources) | Where the event originates. | True |
| event_id | String |  | True |
| latitude | Float | Latitude value of the event. | True |
| longitude | Float | Longitude value of the event. | True |
| values | [JSON](data-reference-h-p.md#json) | JSON string of key,value pairs submitted during event creation. | True |


### CustomEventSources
**Kind**: ENUM

- **SDK**: Event was generated in the SDK.
- **ENCLOSING_APP**: The enclosing application was generating the event through the SDK.
- **CUSTOMER**: The event was sent by the Customer.
Where the custome event originates at.

### DayCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDayCountAnomaly](data-reference-h-p.md#idaycountanomaly), [IAggregatedAnomaly](data-reference-h-p.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DayCountAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| period | [AnomalyTimePeriod](data-reference-a-g.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-a-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |
| observed_days | Float | Observed amount of days. | True |
| expected_days | Float | Expected amount of days. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'DeviceInfo' | True |
| os | [OperatingSystem](data-reference-h-p.md#operatingsystem) | The operating system this device is running. | True |
| os_version | String | The version of the operating system this device is running. | True |


### DistanceAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDistanceAnomaly](data-reference-h-p.md#idistanceanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DistanceAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| observed_distance | Float | Observed distance in meter. | True |
| expected_distance | Float | Expected distance in meter. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


### DurationAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-p.md#ianomaly), [IDurationAnomaly](data-reference-h-p.md#idurationanomaly), [IStationaryAnomaly](data-reference-h-p.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-p.md#itransportanomaly), [IMomentAnomaly](data-reference-h-p.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-g.md#anomalytype) | 'DurationAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-g.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| observed_duration | Float | Observed duration in seconds. | True |
| expected_duration | Float | Expected duration in seconds. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-p.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-z.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-z.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


### EventFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected type is correct. | True |
| place_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected place is correct. | True |
| place_feedback | [LocationPlaceCandidate](data-reference-h-p.md#locationplacecandidate) | The place candidate that was selected by the user as a better match, if any. | True |
| significance_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | If the user thinks the detected location significance is correct. | True |
| significance_feedback | [LocationSignificance](data-reference-h-p.md#locationsignificance) | The location significance that was selected by the user as a better match, if any. | True |
| mode_assessment | [FeedbackAssessment](data-reference-a-g.md#feedbackassessment) | What the user thinks about the transport mode. | True |
| mode_feedback | [TransportMode](data-reference-q-z.md#transportmode) | The transport mode that was selected by the user as a better match, if any. | True |
| occupant_role_feedback | [TransportOccupantRole](data-reference-q-z.md#transportoccupantrole) | The occupant role that was selected by the user as a better match, if any. | True |


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

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'FloatAttribute' | True |
| value | Float |  | True |


### GenericMoment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IMoment](data-reference-h-p.md#imoment)
An occurrence of a moment that we have detected for a user. 

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [MomentType](data-reference-h-p.md#momenttype) | 'GenericMoment' | True |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| start_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| end_ts | [BigInt](data-reference-a-g.md#bigint) |  | True |
| analysis_type | [AnalysisType](data-reference-a-g.md#analysistype) | How well this moment is analyzed by the platform, this value will update over time.<br>Possible values:<br>preliminary, indepth, processed.<br><br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. | True |
| moment_definition | [MomentDefinition](data-reference-h-p.md#momentdefinition) | The MomentDefinition this moment relates to. | True |


### GenericSegment
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ISegment](data-reference-h-p.md#isegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [SegmentType](data-reference-q-z.md#segmenttype) | 'GenericSegment' | True |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. | True |
| explanation | String | Reasoning why this segment was assigned to this user from a third person point of view. | True |
| explanation_you | String | Reasoning why this segment was assigned to this from a second person point of view. | True |
| segment_definition | [SegmentDefinition](data-reference-q-z.md#segmentdefinition) | The SegmentDefinition this segment relates to. | True |
