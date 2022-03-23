# Data Reference U-Z

## Objects
- [User](#user)
- [UserAccountRole](#useraccountrole)
- [UserCarBehavior](#usercarbehavior)
- [UserCarBehaviorFeatures](#usercarbehaviorfeatures)
- [UserCarBehaviorScores](#usercarbehaviorscores)
- [UserHealth](#userhealth)
- [UserHealthScores](#userhealthscores)
- [UserSdkSettings](#usersdksettings)
- [UserSemanticTime](#usersemantictime)
- [UserStepCount](#userstepcount)
- [UserStepCountDaily](#userstepcountdaily)
- [UserStepCountHourly](#userstepcounthourly)
- [UserTimeAggregatedScores](#usertimeaggregatedscores)
- [UsersConnection](#usersconnection)
- [Waypoint](#waypoint)
- [Weather](#weather)
- [WeatherRange](#weatherrange)
- [WeightedLocation](#weightedlocation)
- [WorkingTimeAggregate](#workingtimeaggregate)
- [ZoneCarBehaviorScores](#zonecarbehaviorscores)

### User
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IUser](data-reference-h-l.md#iuser)
An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserType](data-reference-u-z.md#usertype) | 'User' | True |
| install_id | String | The unique identifier for active install id. | True |
| external_id | String | The external id that was linked to this person. | True |
| id | String | The unique identifier for this user. | True |
| can_login | Boolean |  | True |
| created_at | String | The time when this user was created, ISO8601.<br>Example:<br>2015-05-28T14:37:14.839+00:00 | True |
| sdk | [UserSdkSettings](data-reference-u-z.md#usersdksettings) |  | True |
| application_id | String | The ID of the Application this user relates to. | True |
| application | [Application](data-reference-a-b.md#application) | The Application this user relates to. | True |
| custom_event_history | [CustomEvent](data-reference-c-g.md#customevent) | Custom Event History | True |
| event_history | [IEvent](data-reference-h-l.md#ievent) | An unordered list of events we have detected for this user. | True |
| car_behavior | [UserCarBehavior](data-reference-u-z.md#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. | True |
| aggregated_driving_scores | [UserTimeAggregatedScores](data-reference-u-z.md#usertimeaggregatedscores) |  | True |
| transport_heatmaps | [TransportHeatmaps](data-reference-q-t.md#transportheatmaps) | The aggregated transport heatmaps calculated over time.<br><br><code>**Deprecation notice**</code><br>transport_heatmaps is deprecated.<br>No longer used. | True |
| metadata | [JSON](data-reference-h-l.md#json) | All custom set metadata properties on this user. This is a JSON object with key->value pairs. | True |
| device | [DeviceInfo](data-reference-c-g.md#deviceinfo) | The last known active tracking device metadata | True |
| active_moments | [IMoment](data-reference-h-l.md#imoment) | An unordered list of moments that are ongoing from the point of view of the platform. | True |
| moment_history | [IMoment](data-reference-h-l.md#imoment) | An unordered list of moments we have detected for this user. | True |
| semantic_time | [UserSemanticTime](data-reference-u-z.md#usersemantictime) | The user's semantic time averaged over time. | True |
| anomaly_history | [IAnomaly](data-reference-h-l.md#ianomaly) | <br><code>**Deprecation notice**</code><br>anomaly_history is deprecated.<br>No longer relevant. | True |
| segments | [ISegment](data-reference-h-l.md#isegment) | An unordered list of segments that are detected for this user. | True |
| location_clusters | [LocationCluster](data-reference-h-l.md#locationcluster) | Locations this user has been stationary at and the features we have learned about those locations (significance, point of interest, ...) | True |
| location | [Waypoint](data-reference-u-z.md#waypoint) | The last known location we have for this user. | True |
| health | [UserHealth](data-reference-u-z.md#userhealth) | The historical health attributes. | True |
| attributes | [IUserAttribute](data-reference-h-l.md#iuserattribute) |  | True |
| predictions | [IPrediction](data-reference-h-l.md#iprediction) | Event/Moment predictions for this user<br><br><code>**Deprecation notice**</code><br>predictions is deprecated.<br>Please use `prediction_tree`. | True |
| prediction_tree | [PredictionTree](data-reference-m-p.md#predictiontree) | Multiple possible predictions of events that are about to take place next. They are ordered by the highest probability of each sequence of events taking place. | True |
| feedback | [IFeedback](data-reference-h-l.md#ifeedback) | Feedback on this user<br><br><code>**Deprecation notice**</code><br>feedback is deprecated.<br>Replaced by feedback_history | True |
| feedback_history | [IFeedback](data-reference-h-l.md#ifeedback) | Feedback on this user | True |
| step_count | [UserStepCount](data-reference-u-z.md#userstepcount) | Step count details of the given user on the given date range. This feature is currently in Beta, for additional information contact support@sentiance.com. | True |


### UserAccountRole
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserAccountRole' | True |
| user_id | String |  | True |
| account_id | String |  | True |
| role | String |  | True |
| account | [Account](data-reference-a-b.md#account) |  | True |


### UserAttributeType
**Kind**: ENUM

- **TransportTimeAggregate**
- **CommuteTimeAggregate**
- **StationaryTimeAggregate**
- **WorkingTimeAggregate**

### UserCarBehavior
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical car behavior profile for a user. Note that the user must have driven for at least 50 km during this period for the scores to be computed.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehavior' | True |
| scores | [UserCarBehaviorScores](data-reference-u-z.md#usercarbehaviorscores) |  | True |
| features | [UserCarBehaviorFeatures](data-reference-u-z.md#usercarbehaviorfeatures) |  | True |


### UserCarBehaviorFeatures
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehaviorFeatures' | True |
| l7d | [TimeWindowUserCarBehaviorFeatures](data-reference-q-t.md#timewindowusercarbehaviorfeatures) | Recent features based on the transports we have analyzed in the last 7 days of data. | True |
| past | [TimeWindowUserCarBehaviorFeatures](data-reference-q-t.md#timewindowusercarbehaviorfeatures) | Historical features based on all transports we have available, excluding the last 7 days of data. | True |


### UserCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserCarBehaviorScores' | True |
| l7d | [ZoneCarBehaviorScores](data-reference-u-z.md#zonecarbehaviorscores) | Recent scores based on the transports we have analyzed in the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed.<br><br><code>**Deprecation notice**</code><br>l7d is deprecated.<br>No longer supported. | True |
| past | [ZoneCarBehaviorScores](data-reference-u-z.md#zonecarbehaviorscores) | Historical scores based on all transports we have analysed excluding the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. | True |


### UserHealth
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical health attributes.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserHealth' | True |
| scores | [UserHealthScores](data-reference-u-z.md#userhealthscores) |  | True |


### UserHealthScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

This scoring system is used to track an individuals health.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserHealthScores' | True |
| activity | [FloatAttribute](data-reference-c-g.md#floatattribute) | Score that measures a general overview of user health. It takes into account sport duration, walking/biking distance & walking/biking speed. A higher score means you are more active in regard to physical activity and exercise. | True |
| mobility | [FloatAttribute](data-reference-c-g.md#floatattribute) | Score that measures a general overview of user mobility, the higher the score, the more ability to pursue various activities in life. It combines the locations visited frequency, distance travelled and user action radius. It is independent of transport mode. | True |
| work_social | [FloatAttribute](data-reference-c-g.md#floatattribute) | Score that measures a general overview of user's social activities. It is calculated considering two components: the social score and work score. It takes into account how much time the user spends in locations, as well as how many locations the user visits. It is a measure of the number user social relationships together with their duration. It doesn't count user's home and work location, but remote work locations are considered. The higher the score, the more and the longer social interactions the user has. | True |


### UserRole
**Kind**: ENUM

- **developer**
- **spectator**
- **basic**
The roles a user can have, both on accounts and apps.

### UserSdkSettings
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

User overrides that are used by the SDK configuration. This is not the SDK configuration model.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserSdkSettings' | True |
| flavor | [SdkFlavor](data-reference-q-t.md#sdkflavor) | If null, app-wide settings or defaults are active. | True |
| killswitch_action | String |  | True |
| debug_logging | String | If null, app-wide settings or defaults are active. | True |


### UserSemanticTime
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserSemanticTime' | True |
| all_days | [SemanticTimeAggregate](data-reference-q-t.md#semantictimeaggregate) | Historical semantic time averaged for all days over all data. | True |


### UserStepCount
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access information on step count by different groupings. Note that only daily step counts are currently supported.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserStepCount' | True |
| daily | [UserStepCountDaily](data-reference-u-z.md#userstepcountdaily) | The daily step count activity data | True |


### UserStepCountDaily
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Daily information for step count

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserStepCountDaily' | True |
| date | String | Date | True |
| count | Float | Count | True |
| hourly | [UserStepCountHourly](data-reference-u-z.md#userstepcounthourly) | Hourly step count information | True |


### UserStepCountHourly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Hourly information for step count

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UserStepCountHourly' | True |
| hour | Float | Hour | True |
| count | Float | Count | True |


### UserTimeAggregatedScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport scores by month, week, day.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| all | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Aggregation of all driving scores | True |
| month | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Aggregation of driving scores for a given month. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current month in UTC. | True |
| week | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Aggregation of driving scores for a given week. Enter date as YYYY-MM-DD. The day must always correspond to the Monday of the week you're trying to access. So for the third week of April, it will be 2019-04-15. The default value is the start of the current week in UTC. | True |
| day | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Aggregation of driving scores for a given day. Enter date as YYYY-MM-DD. It must correspond exactly to the date for which you want to access the aggregation. The default value is the current day in UTC. | True |
| quarter | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Aggregation of driving scores for a given quarter. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current quarter in UTC. Given date will be determine to derive the quarter, i.e 2021-09-27 belongs to quarter starting from 2021-07-01 | True |


### UserType
**Kind**: ENUM

- **User**: An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.
- **ControlUser**: A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

### UsersConnection
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the user nodes

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'UsersConnection' | True |
| slice | [IUser](data-reference-h-l.md#iuser) | The individual user nodes. Provide the right paging parameters to slice your response data. By default a slice holds 100 users, which you can increase to 1000. | True |
| paging | [Paging](data-reference-m-p.md#paging) |  | True |


### Waypoint
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Waypoint' | True |
| latitude | Float | Location fix latitude. | True |
| longitude | Float | Location fix longitude. | True |
| timestamp | String |  | True |
| accuracy | Int | The estimated horizontal accuracy of this location, radial, in meters. | True |
| speed | Float | The instantaneous speed of the device, measured in meters per second. A negative value indicates an invalid speed. | True |
| altitude | Float | The altitude, measured in meters. Positive values indicate altitudes above sea level. Negative values indicate altitudes below sea level. | True |


### Weather
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| summary | String |  | True |
| icon | String |  | True |
| precipIntensity | Float |  | True |
| precipProbability | Float |  | True |
| temperature | Float |  | True |
| apparentTemperature | Float |  | True |
| dewPoint | Float |  | True |
| humidity | Float |  | True |
| pressure | Float |  | True |
| windSpeed | Float |  | True |
| windGust | Float |  | True |
| windBearing | Float |  | True |
| cloudCover | Float |  | True |
| uvIndex | Float |  | True |
| visibility | Float |  | True |
| ozone | Float |  | True |


### WeatherRange
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | [Weather](data-reference-u-z.md#weather) | Weather data at the start of this event. | True |
| end | [Weather](data-reference-u-z.md#weather) | Weather data at the end of this event. Could be the same as the start if the event was short-lived. | True |


### WeightedLocation
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'WeightedLocation' | True |
| latitude | Float |  | True |
| longitude | Float |  | True |
| weight | Float |  | True |


### WorkingTimeAggregate
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [ITimeAggregateAttribute](data-reference-h-l.md#itimeaggregateattribute), [IUserAttribute](data-reference-h-l.md#iuserattribute)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [UserAttributeType](data-reference-u-z.md#userattributetype) | 'WorkingTimeAggregate' | True |
| period | [TimePeriod](data-reference-q-t.md#timeperiod) |  | True |
| duration | Float |  | True |
| whereabouts | [WorkingTimeWhereabouts](data-reference-u-z.md#workingtimewhereabouts) |  | True |


### WorkingTimeWhereabouts
**Kind**: ENUM

- **all_locations**: When at either regular work or remote locations visited during working time, excluding transports.
- **at_work**: When working at work moment has been active, excluding nothing.
- **remote**: When working remote moment has been active, including transports in between.

### ZoneCarBehaviorScores
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport behavior scores by road type

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'ZoneCarBehaviorScores' | True |
| all | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Scores based on aggregated features across all zones. | True |
| total | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Scores based on the average of features per zone. | True |
| motorway | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Scores based on features in the motorway zones. | True |
| city | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Scores based on features in non-motorway city zones. | True |
| non_city | [CarBehaviorScores](data-reference-c-g.md#carbehaviorscores) | Scores based on features in non-motorway non-city zones. | True |


