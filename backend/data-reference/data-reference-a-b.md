# Data Reference A-B

## Objects

* [AccelerationBehaviorAnnotation](broken-reference)
* [AccessToken](broken-reference)
* [Account](broken-reference)
* [Address](broken-reference)
* [AggregatedDistanceAnomaly](broken-reference)
* [AggregatedDurationAnomaly](broken-reference)
* [AnomalyBehaviorAnnotation](broken-reference)
* [Application](broken-reference)
* [ApplicationActivity](broken-reference)
* [ApplicationActivityGroup](broken-reference)
* [ApplicationActivityGroupItem](broken-reference)
* [ApplicationsConnection](broken-reference)
* [BehaviorAnnotationPathWaypoint](broken-reference)
* [BoundaryBehaviorAnnotation](broken-reference)
* [Branch](broken-reference)

### AccelerationBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITransportBehaviorAnnotation

| Property     | Type                            | Description                                                                                                                                                                                  | Nullable |
| ------------ | ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type         | TransportBehaviorAnnotationType | 'AccelerationBehaviorAnnotation'                                                                                                                                                             | True     |
| start        | String                          |                                                                                                                                                                                              | True     |
| end          | String                          |                                                                                                                                                                                              | True     |
| duration     | Int                             | Duration is in milliseconds.                                                                                                                                                                 | True     |
| acceleration | AccelerationEnum                |                                                                                                                                                                                              | True     |
| path         | BehaviorAnnotationPathWaypoint  |                                                                                                                                                                                              | True     |
| magnitude    | Float                           | The longitudinal g-force you experience during accelerations and brakes, measured in (0.2\*m)/s². Doing a fast acceleration will result in a higher value compared to a slower acceleration. | True     |

### AccelerationEnum

**Kind**: ENUM

* **accelerate**
* **brake**
* **coast**

### AccessToken

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property    | Type   | Description                 | Nullable |
| ----------- | ------ | --------------------------- | -------- |
| type        | String | 'AccessToken'               | True     |
| token       | String | The access (bearer) token   | True     |
| expires\_at | String | When this token will expire | True     |

### Account

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property      | Type                   | Description                                   | Nullable |
| ------------- | ---------------------- | --------------------------------------------- | -------- |
| type          | String                 | 'Account'                                     | True     |
| id            | String                 |                                               | True     |
| display\_name | String                 |                                               | True     |
| created\_at   | String                 |                                               | True     |
| applications  | ApplicationsConnection | The applications that belong to this account. | True     |

### Address

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

An Address describes a reverse geocoded location.

| Property   | Type   | Description | Nullable |
| ---------- | ------ | ----------- | -------- |
| type       | String | 'Address'   | True     |
| country    | String |             | True     |
| city       | String |             | True     |
| city\_type | String |             | True     |

### AggregatedDistanceAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IAnomaly, IDistanceAnomaly, IAggregatedAnomaly, IStationaryAnomaly, ITransportAnomaly, IMomentAnomaly

| Property                  | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Nullable |
| ------------------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                      | AnomalyType           | 'AggregatedDistanceAnomaly'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| start                     | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| end                       | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| analysis\_type            | AnalysisType          | <p><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| anomaly                   | Anomaly               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| sigma                     | Float                 | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| probability               | Float                 | The larger the probability, the more anomaly. Value is between 0.0 and 1.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| observed\_distance        | Float                 | Observed distance in meter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| expected\_distance        | Float                 | Expected distance in meter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| period                    | AnomalyTimePeriod     | Aggregation period over which the data is calculated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | True     |
| day\_part                 | DayPart               | Optional additional aggregation over which the data is calculated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | True     |
| place\_category           | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| location\_significance    | LocationSignificance  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| transport\_mode           | TransportMode         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| transport\_mode\_category | TransportModeCategory |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| moment\_definition\_id    | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |

### AggregatedDurationAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IAnomaly, IDurationAnomaly, IAggregatedAnomaly, IStationaryAnomaly, ITransportAnomaly, IMomentAnomaly

| Property                  | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Nullable |
| ------------------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                      | AnomalyType           | 'AggregatedDurationAnomaly'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| start                     | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| end                       | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| analysis\_type            | AnalysisType          | <p><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| anomaly                   | Anomaly               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| sigma                     | Float                 | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| probability               | Float                 | The larger the probability, the more anomaly. Value is between 0.0 and 1.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| observed\_duration        | Float                 | Observed duration in seconds.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| expected\_duration        | Float                 | Expected duration in seconds.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| period                    | AnomalyTimePeriod     | Aggregation period over which the data is calculated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | True     |
| day\_part                 | DayPart               | Optional additional aggregation over which the data is calculated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | True     |
| place\_category           | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| location\_significance    | LocationSignificance  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| transport\_mode           | TransportMode         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| transport\_mode\_category | TransportModeCategory |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| moment\_definition\_id    | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |

### AnalysisType

**Kind**: ENUM

* **processed**: The most detailed processing with the highest latency. This processing also takes into account motion sensor data, does advanced timelining corrections.
* **indepth**: When data is analyzed with potentially more information available compared to the initial preliminary analysis. This type of processing also takes into account motion sensor data.
* **preliminary**: The initial realtime analysis of data with the lowest latency. The platform analyzes data in multiple stages, and updates values over time, how well the data is analyzed, can be identified by the analysis type.

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
* **commute\_duration**: This is an aggregation over the commute\_from\_home and commute\_from\_work moments, it includes small stationaries during commutes (such as stopping at the gas station).
* **commute\_transport\_mode\_category\_duration**
* **working\_duration**
* **dogwalk\_occurrence\_count**

### AnomalyBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITransportBehaviorAnnotation

| Property | Type                            | Description                  | Nullable |
| -------- | ------------------------------- | ---------------------------- | -------- |
| type     | TransportBehaviorAnnotationType | 'AnomalyBehaviorAnnotation'  | True     |
| start    | String                          |                              | True     |
| end      | String                          |                              | True     |
| anomaly  | BehaviorAnnotationAnomalyEnum   |                              | True     |
| duration | Int                             | Duration is in milliseconds. | True     |
| path     | BehaviorAnnotationPathWaypoint  |                              | True     |

### AnomalyTimePeriod

**Kind**: ENUM

* **day**: Anomaly calculated on a daily basis.
* **week**: Anomaly calculated on a weekly basis.
* **month**: Anomaly calculated on a montly basis.
* **semantic\_day**: Anomaly calculated on the semantic day of the user.
* **weekend\_day**: Anomaly calculated on a daily basis, ex: each day of the weekend you are at home on average N hours, then if you are not home both days = 2 anomalies (one for saturday, one for sunday) will be available.

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

| Property      | Type                | Description                                                                                               | Nullable |
| ------------- | ------------------- | --------------------------------------------------------------------------------------------------------- | -------- |
| type          | String              | 'Application'                                                                                             | True     |
| id            | String              | The unique identifier for this application.                                                               | True     |
| secret        | String              | The secret required when integrating the mobile SDK with this application ID.                             | True     |
| name          | String              | The name of this application. For mobile apps it's the name how it's available in the AppStore/PlayStore. | True     |
| description   | String              | A short description of this application.                                                                  | True     |
| logging       | String              | An optional override for the default debug logging behavior of the mobile SDKs.                           | True     |
| flavor        | String              | An optional override for the default flavor configuration of the mobile SDKs.                             | True     |
| project\_code | String              | An optional project code used to assign users from the demo applications to this application.             | True     |
| created\_at   | String              | <p>The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00.</p>        | True     |
| account\_id   | String              | The developer account this application belongs to.                                                        | True     |
| activity      | ApplicationActivity | Activity information for this application, contains active users and no of installs                       | True     |
| users         | UsersConnection     | The users that belong to this application.                                                                | True     |
| active\_users | UsersConnection     | The users that belong to this application and have been active in the last 7 days.                        | True     |
| trips         | TripConnection      | Trips across all users recorded against this application.                                                 | True     |

### ApplicationActivity

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the activity information

| Property      | Type                     | Description                                | Nullable |
| ------------- | ------------------------ | ------------------------------------------ | -------- |
| type          | String                   | 'ApplicationActivity'                      | True     |
| active\_users | ApplicationActivityGroup | The active users for the application       | True     |
| installs      | ApplicationActivityGroup | The number of installs for the application | True     |

### ApplicationActivityGroup

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the information for groups: ACTIVE\_USERS, INSTALLS

| Property | Type                         | Description                                                  | Nullable |
| -------- | ---------------------------- | ------------------------------------------------------------ | -------- |
| type     | String                       | 'ApplicationActivityGroup'                                   | True     |
| daily    | ApplicationActivityGroupItem | The daily application activity data for type and group       | True     |
| monthly  | ApplicationActivityGroupItem | The monthly application activity data for the type and group | True     |

### ApplicationActivityGroupItem

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the daily and monthly activity information

| Property | Type   | Description                    | Nullable |
| -------- | ------ | ------------------------------ | -------- |
| type     | String | 'ApplicationActivityGroupItem' | True     |
| date     | String | Date                           | True     |
| count    | Float  | Count                          | True     |

### ApplicationsConnection

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the application nodes

| Property | Type        | Description                                                                                                                                         | Nullable |
| -------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type     | String      | 'ApplicationsConnection'                                                                                                                            | True     |
| slice    | Application | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. | True     |
| paging   | Paging      |                                                                                                                                                     | True     |

### BehaviorAnnotationAnomalyEnum

**Kind**: ENUM

* **phone\_handling**

### BehaviorAnnotationPathWaypoint

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property  | Type   | Description                                                                                     | Nullable |
| --------- | ------ | ----------------------------------------------------------------------------------------------- | -------- |
| type      | String | 'BehaviorAnnotationPathWaypoint'                                                                | True     |
| latitude  | Float  |                                                                                                 | True     |
| longitude | Float  |                                                                                                 | True     |
| index     | Int    | <p><br><strong><code>Deprecation notice</code></strong><br>index is deprecated.<br>Obsolete</p> | True     |

### BigInt

**Kind**: SCALAR

The `BigInt` scalar type represents non-fractional signed whole numeric values. BigInt can represent values between -(2^53) + 1 and 2^53 - 1.

### BoundaryBehaviorAnnotation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITransportBehaviorAnnotation

| Property | Type                              | Description                  | Nullable |
| -------- | --------------------------------- | ---------------------------- | -------- |
| type     | TransportBehaviorAnnotationType   | 'BoundaryBehaviorAnnotation' | True     |
| start    | String                            |                              | True     |
| end      | String                            |                              | True     |
| quality  | BoundaryBehaviorAnnotationQuality |                              | True     |

### BoundaryBehaviorAnnotationQuality

**Kind**: ENUM

* **valid**: Section of the transport where the event detection was successful.

### Branch

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A possible series of events predicted for the user.

| Property    | Type         | Description                                                                             | Nullable |
| ----------- | ------------ | --------------------------------------------------------------------------------------- | -------- |
| id          | String       | Id of the branch unique among all the branches returned for the user at the given time. | True     |
| probability | Float        | Percentage probability of the events of this beam taking place.                         | True     |
| events      | IBranchEvent | The list of events predicted to occur.                                                  | True     |
