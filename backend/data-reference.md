# Data Reference
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
- [LocationCluster](#locationcluster)
- [LocationPlaceCandidate](#locationplacecandidate)
- [MomentDefinition](#momentdefinition)
- [MomentFeedback](#momentfeedback)
- [MomentFeedbackFeedback](#momentfeedbackfeedback)
- [Mutation](#mutation)
- [OccurrenceCountAnomaly](#occurrencecountanomaly)
- [Paging](#paging)
- [PagingCursors](#pagingcursors)
- [PredictionInterval](#predictioninterval)
- [PredictionTree](#predictiontree)
- [SegmentDefinition](#segmentdefinition)
- [SemanticTimeAggregate](#semantictimeaggregate)
- [SemanticTimeAggregateValue](#semantictimeaggregatevalue)
- [Stationary](#stationary)
- [StationaryFeedback](#stationaryfeedback)
- [StationaryIntervalPrediction](#stationaryintervalprediction)
- [StationaryLocation](#stationarylocation)
- [StationaryPrediction](#stationaryprediction)
- [StationaryTimeAggregate](#stationarytimeaggregate)
- [StreamDefinition](#streamdefinition)
- [StreamDefinitionsConnection](#streamdefinitionsconnection)
- [Subscription](#subscription)
- [SubscriptionsConnection](#subscriptionsconnection)
- [TimeWindowTransportHeatmaps](#timewindowtransportheatmaps)
- [TimeWindowUserCarBehaviorFeatures](#timewindowusercarbehaviorfeatures)
- [TrajectoryWaypoint](#trajectorywaypoint)
- [Transport](#transport)
- [TransportFeedback](#transportfeedback)
- [TransportHeatmaps](#transportheatmaps)
- [TransportIntervalPrediction](#transportintervalprediction)
- [TransportModeHeatmaps](#transportmodeheatmaps)
- [TransportPrediction](#transportprediction)
- [TransportTimeAggregate](#transporttimeaggregate)
- [TransportTrajectory](#transporttrajectory)
- [Trip](#trip)
- [TripConnection](#tripconnection)
- [TurnBehaviorAnnotation](#turnbehaviorannotation)
- [User](#user)
- [UserAccountRole](#useraccountrole)
- [UserCarBehavior](#usercarbehavior)
- [UserCarBehaviorFeatures](#usercarbehaviorfeatures)
- [UserCarBehaviorScores](#usercarbehaviorscores)
- [UserHealth](#userhealth)
- [UserHealthScores](#userhealthscores)
- [UserSdkSettings](#usersdksettings)
- [UserSemanticTime](#usersemantictime)
- [UsersConnection](#usersconnection)
- [Waypoint](#waypoint)
- [Weather](#weather)
- [WeatherRange](#weatherrange)
- [WeightedLocation](#weightedlocation)
- [WorkingTimeAggregate](#workingtimeaggregate)
- [ZoneCarBehaviorScores](#zonecarbehaviorscores)

### AccelerationBehaviorAnnotation
**Kind**: OBJECT
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

### AccessToken
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'AccessToken' |
| token | String | The access (bearer) token |
| expires_at | String | When this token will expire |


### Account
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Account' |
| id | String |  |
| display_name | String |  |
| created_at | String |  |
| applications | [ApplicationsConnection](#applicationsconnection) | The applications that belong to this account. |


### Address
**Kind**: OBJECT
An Address describes a reverse geocoded location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Address' |
| country | String |  |
| city | String |  |
| city_type | String |  |


### AggregatedDistanceAnomaly
**Kind**: OBJECT
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
**Kind**: OBJECT
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
The platform analyzes data in multiple stages, and updates values over time, how well the data is analyzed, can be identified by the analysis type.

### Anomaly
**Kind**: ENUM

### AnomalyBehaviorAnnotation
**Kind**: OBJECT
**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'AnomalyBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| anomaly | [BehaviorAnnotationAnomalyEnum](#behaviorannotationanomalyenum) |  |
| duration | Int |  |


### AnomalyTimePeriod
**Kind**: ENUM

### AnomalyType
**Kind**: ENUM

### Application
**Kind**: OBJECT
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
| created_at | String | The time when this user was created, ISO8601.
Example:
2015-05-28T14:37:14.839+00:00. |
| account_id | String | The developer account this application belongs to. |
| users | [UsersConnection](#usersconnection) | The users that belong to this application. |
| active_users | [UsersConnection](#usersconnection) | The users that belong to this application and have been active in the last 7 days. |
| trips | [TripConnection](#tripconnection) | Trips across all users recorded against this application. |


### ApplicationsConnection
**Kind**: OBJECT
Access the application nodes

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ApplicationsConnection' |
| slice | [Application](#application) | The individual application nodes. Provide the right paging parameters to slice your response data. By default a slice holds up to 100 applications. |
| paging | [Paging](#paging) |  |


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
**Kind**: SCALAR
The `BigInt` scalar type represents non-fractional signed whole numeric values. BigInt can represent values between -(2^53) + 1 and 2^53 - 1. 

### BoundaryBehaviorAnnotation
**Kind**: OBJECT
**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'BoundaryBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| quality | [BoundaryBehaviorAnnotationQuality](#boundarybehaviorannotationquality) |  |


### BoundaryBehaviorAnnotationQuality
**Kind**: ENUM

### Branch
**Kind**: OBJECT
A possible series of events predicted for the user.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the branch unique among all the branches returned for the user at the given time. |
| probability | Float | Percentage probability of the events of this beam taking place. |
| events | [IBranchEvent](#ibranchevent) | The list of events predicted to occur. |


### CarBehaviorFeatures
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'CarBehaviorFeatures' |
| phone_handling | Int | Total time in milliseconds we detected phone handling by the user during this transport. Value will be -1 when the transport data was not sufficient. |
| distance_during_annotations | Int | Distance in meter during which the system had good quality sensor data available to observe transport behavior. Value will be -1 when the transport data was not sufficient. |


### CarBehaviorScores
**Kind**: OBJECT

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


### CityMoment
**Kind**: OBJECT
**Implements**: [IMoment](#imoment)
An occurrence of a City moment that we have detected for a user. 

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'CityMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.
Possible values:
preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |
| city_name | String | The name of the city this moment applies to. |


### CommuteTimeAggregate
**Kind**: OBJECT
**Implements**: [ITimeAggregateAttribute](#itimeaggregateattribute), [IUserAttribute](#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](#userattributetype) | 'CommuteTimeAggregate' |
| period | [TimePeriod](#timeperiod) |  |
| transport_duration | Float |  |
| mode_category | [TransportModeCategory](#transportmodecategory) |  |


### ControlUser
**Kind**: OBJECT
**Implements**: [IUser](#iuser)
A user that can authenticate using either password or token strategies, has an email address, might have access to dashboards, might have multiple roles, might manage multiple accounts and applications.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](#usertype) | 'ControlUser' |
| email | String | The email address that is optionally linked to provide access to the https://developers.sentiance.com and others. |
| account_roles | [UserAccountRole](#useraccountrole) | The accounts this user has elevated permissions to. |
| id | String | The unique identifier for this user. |
| can_login | Boolean |  |
| created_at | String | The time when this user was created, ISO8601.
Example:
2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](#usersdksettings) |  |
| application_id | String | The ID of the Application this user relates to. |
| application | [Application](#application) | The Application this user relates to. |
| custom_event_history | [CustomEvent](#customevent) | Custom Event History |
| event_history | [IEvent](#ievent) | An unordered list of events we have detected for this user. |
| car_behavior | [UserCarBehavior](#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
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
**Kind**: OBJECT
**Implements**: [IMoment](#imoment)
An occurrence of a Country moment that we have detected for a user. 

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'CountryMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.
Possible values:
preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |
| country_name | String | The name of the country this moment applies to. |


### CustomEvent
**Kind**: OBJECT
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
Where the custome event originates at.

### DayCountAnomaly
**Kind**: OBJECT
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
Grouping of local time.

### DeviceInfo
**Kind**: OBJECT
Tracking device metadata.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'DeviceInfo' |
| os | [OperatingSystem](#operatingsystem) | The operating system this device is running. |
| os_version | String | The version of the operating system this device is running. |


### DistanceAnomaly
**Kind**: OBJECT
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
**Kind**: OBJECT
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
**Kind**: OBJECT

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

### FeedbackAssessment
**Kind**: ENUM

### FeedbackType
**Kind**: ENUM

### FloatAttribute
**Kind**: OBJECT
A float attribute

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'FloatAttribute' |
| value | Float |  |


### GenericMoment
**Kind**: OBJECT
**Implements**: [IMoment](#imoment)
An occurrence of a moment that we have detected for a user. 

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'GenericMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.
Possible values:
preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |


### GenericSegment
**Kind**: OBJECT
**Implements**: [ISegment](#isegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](#segmenttype) | 'GenericSegment' |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. |
| explanation | String | Reasoning why this segment was assigned to this user from a third person point of view. |
| explanation_you | String | Reasoning why this segment was assigned to this from a second person point of view. |
| segment_definition | [SegmentDefinition](#segmentdefinition) | The SegmentDefinition this segment relates to. |


### IAggregatedAnomaly
**Kind**: INTERFACE
**Implemented by**: [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)
An anomaly that we have detected for a user over a period of time.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [AnomalyTimePeriod](#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](#daypart) | Optional additional aggregation over which the data is calculated. |


### IAnomaly
**Kind**: INTERFACE
**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)
An anomaly that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'IAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |


### IBranchEvent
**Kind**: INTERFACE
**Implemented by**: [StationaryPrediction](#stationaryprediction), [TransportPrediction](#transportprediction)
A single predicted event.

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](#treepredictiontype) | 'IBranchEvent' |


### IDayCountAnomaly
**Kind**: INTERFACE
**Implemented by**: [DayCountAnomaly](#daycountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_days | Float | Observed amount of days. |
| expected_days | Float | Expected amount of days. |


### IDistanceAnomaly
**Kind**: INTERFACE
**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_distance | Float | Observed distance in meter. |
| expected_distance | Float | Expected distance in meter. |


### IDurationAnomaly
**Kind**: INTERFACE
**Implemented by**: [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_duration | Float | Observed duration in seconds. |
| expected_duration | Float | Expected duration in seconds. |


### IEvent
**Kind**: INTERFACE
**Implemented by**: [Trip](#trip), [Stationary](#stationary), [Transport](#transport)
An occurrence of an event that we have detected for a user. This interface is implemented by the Stationary and Transport models.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](#eventtype) | 'IEvent' |
| event_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this event is analyzed by the platform, this value will update over time.
Possible values:
preliminary, indepth, processed. |
| weather | [WeatherRange](#weatherrange) | Weather data associated with this event. |


### IEventFeedback
**Kind**: INTERFACE
**Implemented by**: [StationaryFeedback](#stationaryfeedback), [TransportFeedback](#transportfeedback)
An occurrence of event feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event_feedback | [EventFeedback](#eventfeedback) |  |


### IEventPrediction
**Kind**: INTERFACE
**Implemented by**: [StationaryIntervalPrediction](#stationaryintervalprediction), [TransportIntervalPrediction](#transportintervalprediction)
An occurrence of an event prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| event_type | [EventType](#eventtype) |  |


### IFeedback
**Kind**: INTERFACE
**Implemented by**: [StationaryFeedback](#stationaryfeedback), [TransportFeedback](#transportfeedback), [MomentFeedback](#momentfeedback)
An occurrence of feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](#feedbacktype) | 'IFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |


### IIntervalPrediction
**Kind**: INTERFACE
**Implemented by**: [StationaryIntervalPrediction](#stationaryintervalprediction), [TransportIntervalPrediction](#transportintervalprediction)
A prediction that has a start interval.

| Property | Type | Description |
| :--- | :--- | :--- |
| start_interval | [PredictionInterval](#predictioninterval) |  |


### IMoment
**Kind**: INTERFACE
**Implemented by**: [GenericMoment](#genericmoment), [CityMoment](#citymoment), [CountryMoment](#countrymoment)
An occurrence of a MomentDefinition that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [MomentType](#momenttype) | 'IMoment' |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this moment is analyzed by the platform, this value will update over time.
Possible values:
preliminary, indepth, processed. |
| moment_definition_id | String | The ID of the MomentDefinition this moment relates to. |
| moment_definition | [MomentDefinition](#momentdefinition) | The MomentDefinition this moment relates to. |


### IMomentAnomaly
**Kind**: INTERFACE
**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| moment_definition_id | String |  |


### IMomentFeedback
**Kind**: INTERFACE
**Implemented by**: [MomentFeedback](#momentfeedback)
An occurrence of moment feedback submitted by a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| moment_feedback | [MomentFeedbackFeedback](#momentfeedbackfeedback) |  |


### IOccurrenceCountAnomaly
**Kind**: INTERFACE
**Implemented by**: [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| observed_occurrences | Float | Observed amount of occurrences. |
| expected_occurrences | Float | Expected amount of occurrences. |


### IPrediction
**Kind**: INTERFACE
**Implemented by**: [StationaryIntervalPrediction](#stationaryintervalprediction), [TransportIntervalPrediction](#transportintervalprediction)
An occurance of a prediction that we have detected for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](#predictiontype) | 'IPrediction' |
| probability | Float |  |


### ISegment
**Kind**: INTERFACE
**Implemented by**: [GenericSegment](#genericsegment)
An occurrence of a SegmentDefinition that we have detected for this user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [SegmentType](#segmenttype) | 'ISegment' |
| segment_definition_id | String | The ID of the SegmentDefinition this segment relates to. |
| segment_definition | [SegmentDefinition](#segmentdefinition) | The SegmentDefinition this segment relates to. |


### IStationaryAnomaly
**Kind**: INTERFACE
**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |


### ITimeAggregateAttribute
**Kind**: INTERFACE
**Implemented by**: [CommuteTimeAggregate](#commutetimeaggregate), [StationaryTimeAggregate](#stationarytimeaggregate), [TransportTimeAggregate](#transporttimeaggregate), [WorkingTimeAggregate](#workingtimeaggregate)
An attribute that aggregates by TimePeriod.

| Property | Type | Description |
| :--- | :--- | :--- |
| period | [TimePeriod](#timeperiod) |  |


### ITransportAnomaly
**Kind**: INTERFACE
**Implemented by**: [DistanceAnomaly](#distanceanomaly), [AggregatedDistanceAnomaly](#aggregateddistanceanomaly), [DurationAnomaly](#durationanomaly), [AggregatedDurationAnomaly](#aggregateddurationanomaly), [DayCountAnomaly](#daycountanomaly), [OccurrenceCountAnomaly](#occurrencecountanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |


### ITransportBehaviorAnnotation
**Kind**: INTERFACE
**Implemented by**: [BoundaryBehaviorAnnotation](#boundarybehaviorannotation), [AccelerationBehaviorAnnotation](#accelerationbehaviorannotation), [AnomalyBehaviorAnnotation](#anomalybehaviorannotation), [TurnBehaviorAnnotation](#turnbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'ITransportBehaviorAnnotation' |
| start | String |  |
| end | String |  |


### IUser
**Kind**: INTERFACE
**Implemented by**: [User](#user), [ControlUser](#controluser)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](#usertype) | 'IUser' |
| id | String | The unique identifier for this user. |
| can_login | Boolean |  |
| created_at | String | The time when this user was created, ISO8601.
Example:
2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](#usersdksettings) |  |
| application_id | String | The ID of the Application this user relates to. |
| application | [Application](#application) | The Application this user relates to. |
| custom_event_history | [CustomEvent](#customevent) | Custom Event History |
| event_history | [IEvent](#ievent) | An unordered list of events we have detected for this user. |
| car_behavior | [UserCarBehavior](#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
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


### IUserAttribute
**Kind**: INTERFACE
**Implemented by**: [CommuteTimeAggregate](#commutetimeaggregate), [StationaryTimeAggregate](#stationarytimeaggregate), [TransportTimeAggregate](#transporttimeaggregate), [WorkingTimeAggregate](#workingtimeaggregate)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](#userattributetype) | 'IUserAttribute' |


### InputAddress
**Kind**: INPUT_OBJECT

### InputEventFeedback
**Kind**: INPUT_OBJECT

### InputLocationPlaceCandidate
**Kind**: INPUT_OBJECT

### InputMoment
**Kind**: INPUT_OBJECT

### InputMomentFeedback
**Kind**: INPUT_OBJECT

### InputStationary
**Kind**: INPUT_OBJECT

### InputStationaryLocation
**Kind**: INPUT_OBJECT

### InputTrajectoryWaypoint
**Kind**: INPUT_OBJECT
A single waypoint in the augmented trajectory.

### InputTransport
**Kind**: INPUT_OBJECT

### InputTransportBehaviorFeatures
**Kind**: SCALAR

### InputTransportBehaviorScores
**Kind**: SCALAR

### InputTransportTrajectory
**Kind**: INPUT_OBJECT

### InputWaypoint
**Kind**: INPUT_OBJECT

### JSON
**Kind**: SCALAR
The `JSON` scalar type represents JSON values as specified by [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf).

### LocationCluster
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationCluster' |
| last_visit | String |  |
| latitude | Float |  |
| longitude | Float |  |
| address | [Address](#address) |  |
| radius | Int |  |
| is_poi | Boolean |  |
| significance | [LocationSignificance](#locationsignificance) |  |
| place | [LocationPlaceCandidate](#locationplacecandidate) |  |


### LocationPlaceCandidate
**Kind**: OBJECT
A place selected from one of our data sources.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'LocationPlaceCandidate' |
| name | String | Name of the place. Can be null if no specific place can be assigned. |
| category_hierarchy | [String](#string) | A list of venue categories in hierarchical order. The first item represents the broadest category, with each subsequent item representing a more specific one. For ex. `["shop","food","grocery","supermarket"]` |
| probability | Float |  |
| latitude | Float |  |
| longitude | Float |  |
| provider | String |  |


### LocationSignificance
**Kind**: ENUM

### MomentDefinition
**Kind**: OBJECT
A single moment definition.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'MomentDefinition' |
| id | String | Identifier of this MomentDefinition. Possible values: working_at_work,working_remote,home,morning,lunch,afternoon,evening,night,commute_from_work,commute_from_home,business_trip,holiday,nearby_home,nearby_work,city_name,country,children_drop_off,sport_routine,shopping_routine,evening_entertainment,night_out,afternoon_drinks,evening_drinks,breakfast_out,lunch_out,dinner_out,about_to_working,about_to_commute_from_home,about_to_commute_from_work,about_to_children_drop_off,about_to_sport,about_to_shopping,nearby_poi |
| category | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic_time,travel,geography,location,about_to_routine |
| display_name | String | A displayable name for this MomentDefinition. |
| description | String | A short description about this MomentDefinition. |


### MomentFeedback
**Kind**: OBJECT
**Implements**: [IFeedback](#ifeedback), [IMomentFeedback](#imomentfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](#feedbacktype) | 'MomentFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| moment_feedback | [MomentFeedbackFeedback](#momentfeedbackfeedback) |  |
| moment | [IMoment](#imoment) | The Moment this feedback refers to. |


### MomentFeedbackFeedback
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| moment_definition_id_assessment | [FeedbackAssessment](#feedbackassessment) | If the user thinks our detected moment is correct. |
| moment_definition_id_feedback | String | Correction by the user in case our detection was incorrect. |


### MomentType
**Kind**: ENUM

### Mutation
**Kind**: OBJECT
Through mutations you can update data.

| Property | Type | Description |
| :--- | :--- | :--- |
| validateAccessTokens | [AccessToken](#accesstoken) | Validate access tokens. The valid tokens will be in the response. |
| createSubscription | [Subscription](#subscription) |  |
| deleteStreamDefinition | [StreamDefinition](#streamdefinition) | Allows one to delete a Stream Definition either because it was mistakenly created or because it has outlived its use. Trying to delete a non-existent Stream Definition will result in an error. |
| createStreamDefinition | [StreamDefinition](#streamdefinition) |  |
| createFeedback | [IFeedback](#ifeedback) |  |
| createUserRole | [UserAccountRole](#useraccountrole) |  |


### OccurrenceCountAnomaly
**Kind**: OBJECT
**Implements**: [IAnomaly](#ianomaly), [IOccurrenceCountAnomaly](#ioccurrencecountanomaly), [IAggregatedAnomaly](#iaggregatedanomaly), [IStationaryAnomaly](#istationaryanomaly), [ITransportAnomaly](#itransportanomaly), [IMomentAnomaly](#imomentanomaly)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [AnomalyType](#anomalytype) | 'OccurrenceCountAnomaly' |
| start | String |  |
| end | String |  |
| analysis_type | [AnalysisType](#analysistype) |  |
| anomaly | [Anomaly](#anomaly) |  |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. |
| period | [AnomalyTimePeriod](#anomalytimeperiod) | Aggregation period over which the data is calculated. |
| day_part | [DayPart](#daypart) | Optional additional aggregation over which the data is calculated. |
| observed_occurrences | Float | Observed amount of occurrences. |
| expected_occurrences | Float | Expected amount of occurrences. |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |
| transport_mode | [TransportMode](#transportmode) |  |
| transport_mode_category | [TransportModeCategory](#transportmodecategory) |  |
| moment_definition_id | String |  |


### OperatingSystem
**Kind**: ENUM

### Paging
**Kind**: OBJECT
The paging information that allows you to paginate through a large response list.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Paging' |
| cursors | [PagingCursors](#pagingcursors) | The offset cursors to use when paging through results. |


### PagingCursors
**Kind**: OBJECT
The paging cursors that you use to paginate through a large response set.

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
**Kind**: OBJECT
Multiple possible events that might occur for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| is_updated | Boolean |  |
| probability | Float | Percentage probability of these events taking place. |
| events | [IBranchEvent](#ibranchevent) | The list of events predicted to occur. |


### PredictionType
**Kind**: ENUM

### SdkFlavor
**Kind**: ENUM

### SegmentDefinition
**Kind**: OBJECT
A single segment definition.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SegmentDefinition' |
| id | String | Identifier for this segment. |
| version | Int | Version which will increase everytime minor changes or improvements happen to the calculation of this segment. |
| category | String | Category of this segment, if any. |
| subcategory | String | Subcategory of this segment, if any. |
| display_name | String | A displayable name for this segment. |
| description | String | A short description about this segment. |
| deprecated | Boolean | Flag that indicates if this segment will be removed in one of the following releases. Do not use segments that are marked deprecated for new development. |
| deprecated_at | String | Date when the segment will be removed. Default null. |


### SegmentDefinitionStatus
**Kind**: ENUM
Identifies the release status of a segment definition.

### SegmentType
**Kind**: ENUM

### SemanticTime
**Kind**: ENUM
The user semantic time.

### SemanticTimeAggregate
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregate' |
| morning | [SemanticTimeAggregateValue](#semantictimeaggregatevalue) |  |
| lunch | [SemanticTimeAggregateValue](#semantictimeaggregatevalue) |  |
| afternoon | [SemanticTimeAggregateValue](#semantictimeaggregatevalue) |  |
| evening | [SemanticTimeAggregateValue](#semantictimeaggregatevalue) |  |
| night | [SemanticTimeAggregateValue](#semantictimeaggregatevalue) |  |


### SemanticTimeAggregateDaysEnum
**Kind**: ENUM

### SemanticTimeAggregateValue
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SemanticTimeAggregateValue' |
| semantic_time | [SemanticTime](#semantictime) |  |
| days | [SemanticTimeAggregateDaysEnum](#semantictimeaggregatedaysenum) |  |
| start | String | The average start time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |
| end | String | The average end time of the semantic time, in local time, ISO 8601 time format, second precision. Example: 15:34:00 |


### Stationary
**Kind**: OBJECT
**Implements**: [IEvent](#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](#eventtype) | 'Stationary' |
| event_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this event is analyzed by the platform, this value will update over time.
Possible values:
preliminary, indepth, processed. |
| latitude | Float |  |
| longitude | Float |  |
| duration | [BigInt](#bigint) |  |
| address | [Address](#address) |  |
| location | [StationaryLocation](#stationarylocation) |  |
| weather | [WeatherRange](#weatherrange) | Weather data associated with this event. |


### StationaryFeedback
**Kind**: OBJECT
**Implements**: [IFeedback](#ifeedback), [IEventFeedback](#ieventfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](#feedbacktype) | 'StationaryFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| event_feedback | [EventFeedback](#eventfeedback) |  |
| stationary | [Stationary](#stationary) | The Stationary this feedback refers to. |


### StationaryIntervalPrediction
**Kind**: OBJECT
**Implements**: [IPrediction](#iprediction), [IEventPrediction](#ieventprediction), [IIntervalPrediction](#iintervalprediction)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](#predictiontype) | 'StationaryIntervalPrediction' |
| probability | Float |  |
| event_type | [EventType](#eventtype) |  |
| start_interval | [PredictionInterval](#predictioninterval) |  |
| location | [StationaryLocation](#stationarylocation) |  |


### StationaryLocation
**Kind**: OBJECT
Holds more information about a stationary location.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StationaryLocation' |
| significance | [LocationSignificance](#locationsignificance) | What this location means for the user, or the frequency it's being visited. |
| place | [LocationPlaceCandidate](#locationplacecandidate) |  |
| place_candidates | [LocationPlaceCandidate](#locationplacecandidate) |  |


### StationaryPrediction
**Kind**: OBJECT
**Implements**: [IBranchEvent](#ibranchevent)

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](#treepredictiontype) | 'StationaryPrediction' |
| location_type | String |  |


### StationaryTimeAggregate
**Kind**: OBJECT
**Implements**: [ITimeAggregateAttribute](#itimeaggregateattribute), [IUserAttribute](#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](#userattributetype) | 'StationaryTimeAggregate' |
| period | [TimePeriod](#timeperiod) |  |
| duration | Float |  |
| place_category | String |  |
| location_significance | [LocationSignificance](#locationsignificance) |  |


### StreamDefinition
**Kind**: OBJECT
Stream definition that can be activated/subscribed to with the Sentiance Firehose

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StreamDefinition' |
| id | String |  |
| name | String |  |
| projection | String | The GQL query that will be provided on every notification. |
| created_at | String |  |
| subscriptions | [SubscriptionsConnection](#subscriptionsconnection) |  |


### StreamDefinitionConnectionType
**Kind**: ENUM
Stream definition connection type.

### StreamDefinitionsConnection
**Kind**: OBJECT
Access the stream definitions

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'StreamDefinitionsConnection' |
| slice | [StreamDefinition](#streamdefinition) | The individual stream definitions. Provide the right paging parameters to slice your result set. |


### Subscription
**Kind**: OBJECT
Subscription that can be activated to receive data from the Sentiance Firehose.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Subscription' |
| id | String |  |
| token | String |  |
| active | Boolean |  |
| connection_type | [StreamDefinitionConnectionType](#streamdefinitionconnectiontype) |  |
| user_ids | [String](#string) |  |
| created_at | String |  |


### SubscriptionsConnection
**Kind**: OBJECT
Access the stream subscriptions

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'SubscriptionsConnection' |
| slice | [Subscription](#subscription) | The individual subscriptions. Provide the right paging parameters to slice your result set. |


### TimePeriod
**Kind**: ENUM

### TimeWindowTransportHeatmaps
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TimeWindowTransportHeatmaps' |
| car | [TransportModeHeatmaps](#transportmodeheatmaps) |  |


### TimeWindowUserCarBehaviorFeatures
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TimeWindowUserCarBehaviorFeatures' |
| phone_handling | Float | The average number of milliseconds this user is using his phone per hour in transport, during this time window. |
| distance | Int | Aggregated distance measured in meter for all car transports during this time window. |


### TrajectoryWaypoint
**Kind**: OBJECT
A single waypoint in the augmented trajectory.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TrajectoryWaypoint' |
| latitude | Float |  |
| longitude | Float |  |
| timestamp | String |  |
| road_type | String |  |
| speed | Float | The average speed between this waypoint and the next waypoint, in km/h. |
| speed_v2 | Float | The average speed between this waypoint and the next waypoint, in km/h. The difference with speed is that it has an improved estimation algorithm. |
| distance | Float | The distance in meter between the current waypoint and the next waypoint. |
| speed_limit | Float | Speed limit measured at this point in the trajectory. As is provided by our mapping data partners. |


### Transport
**Kind**: OBJECT
**Implements**: [IEvent](#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](#eventtype) | 'Transport' |
| event_id | String |  |
| start | String | The time this moment started, ISO8601. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| end | String | The time this moment ended, ISO8601. Value can be null. Value can change and become more accurate over time.
Example:
2015-05-28T14:37:14.839+00:00 |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| analysis_type | [AnalysisType](#analysistype) | How well this event is analyzed by the platform, this value will update over time.
Possible values:
preliminary, indepth, processed. |
| mode | [TransportMode](#transportmode) | The transport mode that was identified for this transport.  |
| distance | Int |  |
| occupant_role | [TransportOccupantRole](#transportoccupantrole) |  |
| waypoints | [Waypoint](#waypoint) |  |
| trajectory | [TransportTrajectory](#transporttrajectory) |  |
| behavior_scores | [TransportBehaviorScores](#transportbehaviorscores) |  |
| behavior_annotations | [ITransportBehaviorAnnotation](#itransportbehaviorannotation) |  |
| behavior_features | [TransportBehaviorFeatures](#transportbehaviorfeatures) |  |
| weather | [WeatherRange](#weatherrange) | Weather data associated with this event. |


### TransportBehaviorAnnotationType
**Kind**: ENUM

### TransportBehaviorFeatures
**Kind**: UNION
**Possible types**: [CarBehaviorFeatures](#carbehaviorfeatures)

### TransportBehaviorScores
**Kind**: UNION
**Possible types**: [CarBehaviorScores](#carbehaviorscores)
The transport behavior scores we have detected during a transport. These scores are only available when the full trip is processed.

### TransportFeedback
**Kind**: OBJECT
**Implements**: [IFeedback](#ifeedback), [IEventFeedback](#ieventfeedback)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [FeedbackType](#feedbacktype) | 'TransportFeedback' |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. |
| created | String | Time when this feedback entry was created. |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. |
| event_feedback | [EventFeedback](#eventfeedback) |  |
| transport | [Transport](#transport) | The Transport this feedback refers to. |


### TransportHeatmaps
**Kind**: OBJECT
Historically aggregated transport heatmaps.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportHeatmaps' |
| l30d | [TimeWindowTransportHeatmaps](#timewindowtransportheatmaps) | Transport heatmaps that are calculated using the last . |


### TransportIntervalPrediction
**Kind**: OBJECT
**Implements**: [IPrediction](#iprediction), [IEventPrediction](#ieventprediction), [IIntervalPrediction](#iintervalprediction)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [PredictionType](#predictiontype) | 'TransportIntervalPrediction' |
| probability | Float |  |
| event_type | [EventType](#eventtype) |  |
| start_interval | [PredictionInterval](#predictioninterval) |  |
| mode | [TransportMode](#transportmode) |  |


### TransportMode
**Kind**: ENUM
The transport modes the platform supports.

### TransportModeCategory
**Kind**: ENUM

### TransportModeHeatmaps
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportModeHeatmaps' |
| passed | [WeightedLocation](#weightedlocation) | An aggregate heatmap based on the amounts of times you have passed the coordinates during transports. |


### TransportOccupantRole
**Kind**: ENUM

### TransportPrediction
**Kind**: OBJECT
**Implements**: [IBranchEvent](#ibranchevent)

| Property | Type | Description |
| :--- | :--- | :--- |
| start | String | Predicted start time of the event. |
| end | String | Predicted end time of the event. |
| probability | Float | The probability of this prediction occurring. |
| type | [TreePredictionType](#treepredictiontype) | 'TransportPrediction' |
| mode | String |  |


### TransportTimeAggregate
**Kind**: OBJECT
**Implements**: [ITimeAggregateAttribute](#itimeaggregateattribute), [IUserAttribute](#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](#userattributetype) | 'TransportTimeAggregate' |
| period | [TimePeriod](#timeperiod) |  |
| duration | Float |  |
| mode | [TransportMode](#transportmode) |  |


### TransportTrajectory
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TransportTrajectory' |
| waypoints | [TrajectoryWaypoint](#trajectorywaypoint) |  |
| encoded | String | An encoded list of trajectory waypoints, [[lat,lon],[lat,lon]]. More info on polyline decoding: https://developers.google.com/maps/documentation/utilities/polylinealgorithm |


### TreePredictionType
**Kind**: ENUM

### Trip
**Kind**: OBJECT
**Implements**: [IEvent](#ievent)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [EventType](#eventtype) | 'Trip' |
| event_id | String |  |
| user_id | String |  |
| start | String |  |
| end | String |  |
| start_ts | [BigInt](#bigint) |  |
| end_ts | [BigInt](#bigint) |  |
| mode | String | Car, tram, walking, etc. |
| analysis_type | [AnalysisType](#analysistype) | Type of processing applied on the trip. |
| behavior_scores | [CarBehaviorScores](#carbehaviorscores) |  |
| weather | [WeatherRange](#weatherrange) |  |


### TripConnection
**Kind**: OBJECT
Access trips across all users.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'TripConnection' |
| slice | [Trip](#trip) | The individual trips. Provide the right paging parameters to slice your result set. |


### TurnBehaviorAnnotation
**Kind**: OBJECT
**Implements**: [ITransportBehaviorAnnotation](#itransportbehaviorannotation)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [TransportBehaviorAnnotationType](#transportbehaviorannotationtype) | 'TurnBehaviorAnnotation' |
| start | String |  |
| end | String |  |
| maneuver | [TurnBehaviorAnnotationManeuver](#turnbehaviorannotationmaneuver) |  |
| duration | Int |  |
| path | [BehaviorAnnotationPathWaypoint](#behaviorannotationpathwaypoint) |  |
| magnitude | Float | The centripetal g-force you experience during turns, measured in (0.2*m)/s². Taking a turn at 60km/h will result in a higher magnitude compared to the same turn at 30 km/h |


### TurnBehaviorAnnotationManeuver
**Kind**: ENUM

### User
**Kind**: OBJECT
**Implements**: [IUser](#iuser)
An anonymous SDK user that authenticates using the token strategy, can push data and can query only it's own data.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserType](#usertype) | 'User' |
| install_id | String | The unique identifier for active install id. |
| external_id | String | The external id that was linked to this person. |
| id | String | The unique identifier for this user. |
| can_login | Boolean |  |
| created_at | String | The time when this user was created, ISO8601.
Example:
2015-05-28T14:37:14.839+00:00 |
| sdk | [UserSdkSettings](#usersdksettings) |  |
| application_id | String | The ID of the Application this user relates to. |
| application | [Application](#application) | The Application this user relates to. |
| custom_event_history | [CustomEvent](#customevent) | Custom Event History |
| event_history | [IEvent](#ievent) | An unordered list of events we have detected for this user. |
| car_behavior | [UserCarBehavior](#usercarbehavior) | The user car behavior aggregated over the last 9 weeks. |
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


### UserAccountRole
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserAccountRole' |
| user_id | String |  |
| account_id | String |  |
| role | String |  |
| account | [Account](#account) |  |


### UserAttributeType
**Kind**: ENUM

### UserCarBehavior
**Kind**: OBJECT
The historical car behavior profile for a user.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehavior' |
| scores | [UserCarBehaviorScores](#usercarbehaviorscores) |  |
| features | [UserCarBehaviorFeatures](#usercarbehaviorfeatures) |  |


### UserCarBehaviorFeatures
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehaviorFeatures' |
| l7d | [TimeWindowUserCarBehaviorFeatures](#timewindowusercarbehaviorfeatures) | Recent features based on the transports we have analyzed in the last 7 days of data. |
| past | [TimeWindowUserCarBehaviorFeatures](#timewindowusercarbehaviorfeatures) | Historical features based on all transports we have available, excluding the last 7 days of data. |


### UserCarBehaviorScores
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserCarBehaviorScores' |
| l7d | [ZoneCarBehaviorScores](#zonecarbehaviorscores) | Recent scores based on the transports we have analyzed in the last 7 days of data. |
| past | [ZoneCarBehaviorScores](#zonecarbehaviorscores) | Historical scores based on all transports we have analysed excluding the last 7 days of data. |


### UserHealth
**Kind**: OBJECT
The historical health attributes.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserHealth' |
| scores | [UserHealthScores](#userhealthscores) |  |


### UserHealthScores
**Kind**: OBJECT
This scoring system is used to track an individuals health.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserHealthScores' |
| activity | [FloatAttribute](#floatattribute) | Score that measures a general overview of user health. It takes into account sport duration, walking/biking distance & walking/biking speed. A higher score means you are more active in regard to physical activity and exercise. |
| mobility | [FloatAttribute](#floatattribute) | Score that measures a general overview of user mobility, the higher the score, the more ability to pursue various activities in life. It combines the locations visited frequency, distance travelled and user action radius. It is independent of transport mode. |
| work_social | [FloatAttribute](#floatattribute) | Score that measures a general overview of user's social activities. It is calculated considering two components: the social score and work score. It takes into account how much time the user spends in locations, as well as how many locations the user visits. It is a measure of the number user social relationships together with their duration. It doesn't count user's home and work location, but remote work locations are considered. The higher the score, the more and the longer social interactions the user has. |


### UserRole
**Kind**: ENUM
The roles a user can have, both on accounts and apps.

### UserSdkSettings
**Kind**: OBJECT
User overrides that are used by the SDK configuration. This is not the SDK configuration model.

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserSdkSettings' |
| flavor | [SdkFlavor](#sdkflavor) | If null, app-wide settings or defaults are active. |
| killswitch_action | String |  |
| debug_logging | String | If null, app-wide settings or defaults are active. |


### UserSemanticTime
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UserSemanticTime' |
| all_days | [SemanticTimeAggregate](#semantictimeaggregate) | Historical semantic time averaged for all days over all data. |


### UserType
**Kind**: ENUM

### UsersConnection
**Kind**: OBJECT
Access the user nodes

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'UsersConnection' |
| slice | [IUser](#iuser) | The individual user nodes. Provide the right paging parameters to slice your response data. By default a slice holds 100 users, which you can increase to 1000. |
| paging | [Paging](#paging) |  |


### Waypoint
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'Waypoint' |
| latitude | Float |  |
| longitude | Float |  |
| timestamp | String |  |
| accuracy | Int | The estimated horizontal accuracy of this location, radial, in meters. |


### Weather
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| summary | String |  |
| icon | String |  |
| precipIntensity | Float |  |
| precipProbability | Float |  |
| temperature | Float |  |
| apparentTemperature | Float |  |
| dewPoint | Float |  |
| humidity | Float |  |
| pressure | Float |  |
| windSpeed | Float |  |
| windGust | Float |  |
| windBearing | Float |  |
| cloudCover | Float |  |
| uvIndex | Float |  |
| visibility | Float |  |
| ozone | Float |  |


### WeatherRange
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| start | [Weather](#weather) | Weather data at the start of this event. |
| end | [Weather](#weather) | Weather data at the end of this event. Could be the same as the start if the event was short-lived. |


### WeightedLocation
**Kind**: OBJECT

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'WeightedLocation' |
| latitude | Float |  |
| longitude | Float |  |
| weight | Float |  |


### WorkingTimeAggregate
**Kind**: OBJECT
**Implements**: [ITimeAggregateAttribute](#itimeaggregateattribute), [IUserAttribute](#iuserattribute)

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [UserAttributeType](#userattributetype) | 'WorkingTimeAggregate' |
| period | [TimePeriod](#timeperiod) |  |
| duration | Float |  |
| whereabouts | [WorkingTimeWhereabouts](#workingtimewhereabouts) |  |


### WorkingTimeWhereabouts
**Kind**: ENUM

### ZoneCarBehaviorScores
**Kind**: OBJECT
Car transport behavior scores by road type

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | 'ZoneCarBehaviorScores' |
| all | [CarBehaviorScores](#carbehaviorscores) | Scores based on aggregated features across all zones. |
| total | [CarBehaviorScores](#carbehaviorscores) | Scores based on the average of features per zone. |
| motorway | [CarBehaviorScores](#carbehaviorscores) | Scores based on features in the motorway zones. |
| city | [CarBehaviorScores](#carbehaviorscores) | Scores based on features in non-motorway city zones. |
| non_city | [CarBehaviorScores](#carbehaviorscores) | Scores based on features in non-motorway non-city zones. |


