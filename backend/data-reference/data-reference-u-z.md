# Data Reference U-Z

## Objects

* [User](broken-reference)
* [UserAccountRole](broken-reference)
* [UserCarBehavior](broken-reference)
* [UserCarBehaviorFeatures](broken-reference)
* [UserCarBehaviorScores](broken-reference)
* [UserHealth](broken-reference)
* [UserHealthScores](broken-reference)
* [UserSdkSettings](broken-reference)
* [UserSemanticTime](broken-reference)
* [UserStepCount](broken-reference)
* [UserStepCountDaily](broken-reference)
* [UserStepCountHourly](broken-reference)
* [UserTimeAggregatedScores](broken-reference)
* [UsersConnection](broken-reference)
* [Waypoint](broken-reference)
* [Weather](broken-reference)
* [WeatherRange](broken-reference)
* [WeightedLocation](broken-reference)
* [WorkingTimeAggregate](broken-reference)
* [ZoneCarBehaviorScores](broken-reference)

### User

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IUser An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.

| Property                    | Type                     | Description                                                                                                                                                                     | Nullable |
| --------------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                        | UserType                 | 'User'                                                                                                                                                                          | True     |
| install\_id                 | String                   | The unique identifier for active install id.                                                                                                                                    | True     |
| external\_id                | String                   | The external id that was linked to this person.                                                                                                                                 | True     |
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

### UserAccountRole

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property    | Type    | Description       | Nullable |
| ----------- | ------- | ----------------- | -------- |
| type        | String  | 'UserAccountRole' | True     |
| user\_id    | String  |                   | True     |
| account\_id | String  |                   | True     |
| role        | String  |                   | True     |
| account     | Account |                   | True     |

### UserAttributeType

**Kind**: ENUM

* **TransportTimeAggregate**
* **CommuteTimeAggregate**
* **StationaryTimeAggregate**
* **WorkingTimeAggregate**

### UserCarBehavior

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical car behavior profile for a user. Note that the user must have driven for at least 50 km during this period for the scores to be computed.

| Property | Type                    | Description       | Nullable |
| -------- | ----------------------- | ----------------- | -------- |
| type     | String                  | 'UserCarBehavior' | True     |
| scores   | UserCarBehaviorScores   |                   | True     |
| features | UserCarBehaviorFeatures |                   | True     |

### UserCarBehaviorFeatures

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type                              | Description                                                                                       | Nullable |
| -------- | --------------------------------- | ------------------------------------------------------------------------------------------------- | -------- |
| type     | String                            | 'UserCarBehaviorFeatures'                                                                         | True     |
| l7d      | TimeWindowUserCarBehaviorFeatures | Recent features based on the transports we have analyzed in the last 7 days of data.              | True     |
| past     | TimeWindowUserCarBehaviorFeatures | Historical features based on all transports we have available, excluding the last 7 days of data. | True     |

### UserCarBehaviorScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type                  | Description                                                                                                                                                                                            | Nullable |
| -------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| type     | String                | 'UserCarBehaviorScores'                                                                                                                                                                                | True     |
| l7d      | ZoneCarBehaviorScores | Recent scores based on the transports we have analyzed in the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed.            | True     |
| past     | ZoneCarBehaviorScores | Historical scores based on all transports we have analysed excluding the last 7 days of data. Note that the user must have driven for at least 50 km during this period for the scores to be computed. | True     |

### UserHealth

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The historical health attributes.

| Property | Type             | Description  | Nullable |
| -------- | ---------------- | ------------ | -------- |
| type     | String           | 'UserHealth' | True     |
| scores   | UserHealthScores |              | True     |

### UserHealthScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

This scoring system is used to track an individuals health.

| Property     | Type           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Nullable |
| ------------ | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type         | String         | 'UserHealthScores'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | True     |
| activity     | FloatAttribute | Score that measures a general overview of user health. It takes into account sport duration, walking/biking distance & walking/biking speed. A higher score means you are more active in regard to physical activity and exercise.                                                                                                                                                                                                                                                                                                 | True     |
| mobility     | FloatAttribute | Score that measures a general overview of user mobility, the higher the score, the more ability to pursue various activities in life. It combines the locations visited frequency, distance travelled and user action radius. It is independent of transport mode.                                                                                                                                                                                                                                                                 | True     |
| work\_social | FloatAttribute | Score that measures a general overview of user's social activities. It is calculated considering two components: the social score and work score. It takes into account how much time the user spends in locations, as well as how many locations the user visits. It is a measure of the number user social relationships together with their duration. It doesn't count user's home and work location, but remote work locations are considered. The higher the score, the more and the longer social interactions the user has. | True     |

### UserRole

**Kind**: ENUM

* **developer**
* **spectator**
* **basic** The roles a user can have, both on accounts and apps.

### UserSdkSettings

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

User overrides that are used by the SDK configuration. This is not the SDK configuration model.

| Property           | Type      | Description                                        | Nullable |
| ------------------ | --------- | -------------------------------------------------- | -------- |
| type               | String    | 'UserSdkSettings'                                  | True     |
| flavor             | SdkFlavor | If null, app-wide settings or defaults are active. | True     |
| killswitch\_action | String    |                                                    | True     |
| debug\_logging     | String    | If null, app-wide settings or defaults are active. | True     |

### UserSemanticTime

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property  | Type                  | Description                                                   | Nullable |
| --------- | --------------------- | ------------------------------------------------------------- | -------- |
| type      | String                | 'UserSemanticTime'                                            | True     |
| all\_days | SemanticTimeAggregate | Historical semantic time averaged for all days over all data. | True     |

### UserStepCount

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access information on step count by different groupings. Note that only daily step counts are currently supported.

| Property | Type               | Description                        | Nullable |
| -------- | ------------------ | ---------------------------------- | -------- |
| type     | String             | 'UserStepCount'                    | True     |
| daily    | UserStepCountDaily | The daily step count activity data | True     |

### UserStepCountDaily

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Daily information for step count

| Property | Type                | Description                   | Nullable |
| -------- | ------------------- | ----------------------------- | -------- |
| type     | String              | 'UserStepCountDaily'          | True     |
| date     | String              | Date                          | True     |
| count    | Float               | Count                         | True     |
| hourly   | UserStepCountHourly | Hourly step count information | True     |

### UserStepCountHourly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Hourly information for step count

| Property | Type   | Description           | Nullable |
| -------- | ------ | --------------------- | -------- |
| type     | String | 'UserStepCountHourly' | True     |
| hour     | Float  | Hour                  | True     |
| count    | Float  | Count                 | True     |

### UserTimeAggregatedScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport scores by month, week, day.

| Property | Type              | Description                                                                                                                                                                                                                                                                                                                                | Nullable |
| -------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| all      | CarBehaviorScores | Aggregation of all driving scores                                                                                                                                                                                                                                                                                                          | True     |
| month    | CarBehaviorScores | Aggregation of driving scores for a given month. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current month in UTC.                                                                                                                    | True     |
| week     | CarBehaviorScores | Aggregation of driving scores for a given week. Enter date as YYYY-MM-DD. The day must always correspond to the Monday of the week you're trying to access. So for the third week of April, it will be 2019-04-15. The default value is the start of the current week in UTC.                                                              | True     |
| day      | CarBehaviorScores | Aggregation of driving scores for a given day. Enter date as YYYY-MM-DD. It must correspond exactly to the date for which you want to access the aggregation. The default value is the current day in UTC.                                                                                                                                 | True     |
| quarter  | CarBehaviorScores | Aggregation of driving scores for a given quarter. Enter date as YYYY-MM-DD. The DD part must always be 01. Month must always be 0 padded. So 4 should be 04. The default value is the start of the current quarter in UTC. Given date will be determine to derive the quarter, i.e 2021-09-27 belongs to quarter starting from 2021-07-01 | True     |

### UserType

**Kind**: ENUM

* **User**: An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.
* **ControlUser**: A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

### UsersConnection

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Access the user nodes

| Property | Type   | Description                                                                                                                                                     | Nullable |
| -------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type     | String | 'UsersConnection'                                                                                                                                               | True     |
| slice    | IUser  | The individual user nodes. Provide the right paging parameters to slice your response data. By default a slice holds 100 users, which you can increase to 1000. | True     |
| paging   | Paging |                                                                                                                                                                 | True     |

### Waypoint

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property  | Type   | Description                                                                                                                               | Nullable |
| --------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type      | String | 'Waypoint'                                                                                                                                | True     |
| latitude  | Float  | Location fix latitude.                                                                                                                    | True     |
| longitude | Float  | Location fix longitude.                                                                                                                   | True     |
| timestamp | String |                                                                                                                                           | True     |
| accuracy  | Int    | The estimated horizontal accuracy of this location, radial, in meters.                                                                    | True     |
| speed     | Float  | The instantaneous speed of the device, measured in meters per second. A negative value indicates an invalid speed.                        | True     |
| altitude  | Float  | The altitude, measured in meters. Positive values indicate altitudes above sea level. Negative values indicate altitudes below sea level. | True     |

### Weather

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property            | Type   | Description | Nullable |
| ------------------- | ------ | ----------- | -------- |
| summary             | String |             | True     |
| icon                | String |             | True     |
| precipIntensity     | Float  |             | True     |
| precipProbability   | Float  |             | True     |
| temperature         | Float  |             | True     |
| apparentTemperature | Float  |             | True     |
| dewPoint            | Float  |             | True     |
| humidity            | Float  |             | True     |
| pressure            | Float  |             | True     |
| windSpeed           | Float  |             | True     |
| windGust            | Float  |             | True     |
| windBearing         | Float  |             | True     |
| cloudCover          | Float  |             | True     |
| uvIndex             | Float  |             | True     |
| visibility          | Float  |             | True     |
| ozone               | Float  |             | True     |

### WeatherRange

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type    | Description                                                                                         | Nullable |
| -------- | ------- | --------------------------------------------------------------------------------------------------- | -------- |
| start    | Weather | Weather data at the start of this event.                                                            | True     |
| end      | Weather | Weather data at the end of this event. Could be the same as the start if the event was short-lived. | True     |

### WeightedLocation

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property  | Type   | Description        | Nullable |
| --------- | ------ | ------------------ | -------- |
| type      | String | 'WeightedLocation' | True     |
| latitude  | Float  |                    | True     |
| longitude | Float  |                    | True     |
| weight    | Float  |                    | True     |

### WorkingTimeAggregate

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: ITimeAggregateAttribute, IUserAttribute

| Property    | Type                   | Description            | Nullable |
| ----------- | ---------------------- | ---------------------- | -------- |
| type        | UserAttributeType      | 'WorkingTimeAggregate' | True     |
| period      | TimePeriod             |                        | True     |
| duration    | Float                  |                        | True     |
| whereabouts | WorkingTimeWhereabouts |                        | True     |

### WorkingTimeWhereabouts

**Kind**: ENUM

* **all\_locations**: When at either regular work or remote locations visited during working time, excluding transports.
* **at\_work**: When working at work moment has been active, excluding nothing.
* **remote**: When working remote moment has been active, including transports in between.

### ZoneCarBehaviorScores

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Car transport behavior scores by road type

| Property  | Type              | Description                                              | Nullable |
| --------- | ----------------- | -------------------------------------------------------- | -------- |
| type      | String            | 'ZoneCarBehaviorScores'                                  | True     |
| all       | CarBehaviorScores | Scores based on aggregated features across all zones.    | True     |
| total     | CarBehaviorScores | Scores based on the average of features per zone.        | True     |
| motorway  | CarBehaviorScores | Scores based on features in the motorway zones.          | True     |
| city      | CarBehaviorScores | Scores based on features in non-motorway city zones.     | True     |
| non\_city | CarBehaviorScores | Scores based on features in non-motorway non-city zones. | True     |
