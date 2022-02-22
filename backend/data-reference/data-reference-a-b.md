# Data Reference A-B
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

### AccelerationBehaviorAnnotation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'AccelerationBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| duration | Int | Duration is in milliseconds. | True |
| acceleration | [AccelerationEnum](data-reference-a-b.md#accelerationenum) |  | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-b.md#behaviorannotationpathwaypoint) |  | True |
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
| applications | [ApplicationsConnection](data-reference-a-b.md#applicationsconnection) | The applications that belong to this account. | True |


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

**Implements**: [IAnomaly](data-reference-h-l.md#ianomaly), [IDistanceAnomaly](data-reference-h-l.md#idistanceanomaly), [IAggregatedAnomaly](data-reference-h-l.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-l.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-l.md#itransportanomaly), [IMomentAnomaly](data-reference-h-l.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-b.md#anomalytype) | 'AggregatedDistanceAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-b.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| observed_distance | Float | Observed distance in meter. | True |
| expected_distance | Float | Expected distance in meter. | True |
| period | [AnomalyTimePeriod](data-reference-a-b.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-c-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-l.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-t.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-t.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


### AggregatedDurationAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-l.md#ianomaly), [IDurationAnomaly](data-reference-h-l.md#idurationanomaly), [IAggregatedAnomaly](data-reference-h-l.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-l.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-l.md#itransportanomaly), [IMomentAnomaly](data-reference-h-l.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-b.md#anomalytype) | 'AggregatedDurationAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-b.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| observed_duration | Float | Observed duration in seconds. | True |
| expected_duration | Float | Expected duration in seconds. | True |
| period | [AnomalyTimePeriod](data-reference-a-b.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-c-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-l.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-t.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-t.md#transportmodecategory) |  | True |
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

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'AnomalyBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| anomaly | [BehaviorAnnotationAnomalyEnum](data-reference-a-b.md#behaviorannotationanomalyenum) |  | True |
| duration | Int | Duration is in milliseconds. | True |
| path | [BehaviorAnnotationPathWaypoint](data-reference-a-b.md#behaviorannotationpathwaypoint) |  | True |


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
| activity | [ApplicationActivity](data-reference-a-b.md#applicationactivity) | Activity information for this application, contains active users and no of installs | True |
| users | [UsersConnection](data-reference-u-z.md#usersconnection) | The users that belong to this application. | True |
| active_users | [UsersConnection](data-reference-u-z.md#usersconnection) | The users that belong to this application and have been active in the last 7 days. | True |
| trips | [TripConnection](data-reference-q-t.md#tripconnection) | Trips across all users recorded against this application. | True |


### ApplicationActivity
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the activity information

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivity' | True |
| active_users | [ApplicationActivityGroup](data-reference-a-b.md#applicationactivitygroup) | The active users for the application | True |
| installs | [ApplicationActivityGroup](data-reference-a-b.md#applicationactivitygroup) | The number of installs for the application | True |


### ApplicationActivityGroup
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the information for groups: ACTIVE_USERS, INSTALLS

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ApplicationActivityGroup' | True |
| daily | [ApplicationActivityGroupItem](data-reference-a-b.md#applicationactivitygroupitem) | The daily application activity data for type and group | True |
| monthly | [ApplicationActivityGroupItem](data-reference-a-b.md#applicationactivitygroupitem) | The monthly application activity data for the type and group | True |


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
| slice | [Application](data-reference-a-b.md#application) | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. | True |
| paging | [Paging](data-reference-m-p.md#paging) |  | True |


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

**Implements**: [ITransportBehaviorAnnotation](data-reference-h-l.md#itransportbehaviorannotation)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](data-reference-q-t.md#transportbehaviorannotationtype) | 'BoundaryBehaviorAnnotation' | True |
| start | String |  | True |
| end | String |  | True |
| quality | [BoundaryBehaviorAnnotationQuality](data-reference-a-b.md#boundarybehaviorannotationquality) |  | True |


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
| events | [IBranchEvent](data-reference-h-l.md#ibranchevent) | The list of events predicted to occur. | True |


...