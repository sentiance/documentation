# Data Reference M-P

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Objects
- [MomentDefinition](#momentdefinition)
- [MomentFeedback](#momentfeedback)
- [MomentFeedbackFeedback](#momentfeedbackfeedback)
- [OccurrenceCountAnomaly](#occurrencecountanomaly)
- [OndeviceMLModel](#ondevicemlmodel)
- [Paging](#paging)
- [PagingCursors](#pagingcursors)
- [PredictionInterval](#predictioninterval)
- [PredictionTree](#predictiontree)

### MomentDefinition
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single moment definition.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'MomentDefinition' | True |
| id | String | Identifier of this MomentDefinition. Possible values: working_at_work,working_remote,home,morning,lunch,afternoon,evening,night,commute_from_work,commute_from_home,business_trip,holiday,city_name,country,children_drop_off,sport_routine,shopping_routine,evening_entertainment,night_out,afternoon_drinks,evening_drinks,breakfast_out,lunch_out,dinner_out,about_to_working,about_to_commute_from_home,about_to_commute_from_work,about_to_children_drop_off,about_to_sport,about_to_shopping | True |
| category | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic_time,travel,location,about_to_routine | True |
| display_name | String | A displayable name for this MomentDefinition. | True |
| description | String | A short description about this MomentDefinition. | True |


### MomentFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IFeedback](data-reference-h-l.md#ifeedback), [IMomentFeedback](data-reference-h-l.md#imomentfeedback)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [FeedbackType](data-reference-c-g.md#feedbacktype) | 'MomentFeedback' | True |
| start | String | Start time the feedback relates to, sourced by the event, moment or user-provided. | False |
| end | String | End time the feedback relates to, sourced by the event, moment or user-provided. | True |
| created | String | Time when this feedback entry was created. | True |
| projection_time | String | Time to provide when the feedback data was read from the API. ISO8601. Optional. | True |
| moment_feedback | [MomentFeedbackFeedback](data-reference-m-p.md#momentfeedbackfeedback) |  | True |
| moment | [IMoment](data-reference-h-l.md#imoment) | The Moment this feedback refers to. | True |


### MomentFeedbackFeedback
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| moment_definition_id_assessment | [FeedbackAssessment](data-reference-c-g.md#feedbackassessment) | If the user thinks our detected moment is correct. | True |
| moment_definition_id_feedback | String | Correction by the user in case our detection was incorrect. | True |


### MomentType
**Kind**: ENUM

- **GenericMoment**
- **CityMoment**
- **CountryMoment**

### OccurrenceCountAnomaly
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: [IAnomaly](data-reference-h-l.md#ianomaly), [IOccurrenceCountAnomaly](data-reference-h-l.md#ioccurrencecountanomaly), [IAggregatedAnomaly](data-reference-h-l.md#iaggregatedanomaly), [IStationaryAnomaly](data-reference-h-l.md#istationaryanomaly), [ITransportAnomaly](data-reference-h-l.md#itransportanomaly), [IMomentAnomaly](data-reference-h-l.md#imomentanomaly)

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | [AnomalyType](data-reference-a-b.md#anomalytype) | 'OccurrenceCountAnomaly' | True |
| start | String |  | True |
| end | String |  | True |
| analysis_type | [AnalysisType](data-reference-a-b.md#analysistype) | <br><code>**Deprecation notice**</code><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field. | True |
| anomaly | [Anomaly](data-reference-a-b.md#anomaly) |  | True |
| sigma | Float | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low. | True |
| probability | Float | The larger the probability, the more anomaly. Value is between 0.0 and 1.0. | True |
| period | [AnomalyTimePeriod](data-reference-a-b.md#anomalytimeperiod) | Aggregation period over which the data is calculated. | True |
| day_part | [DayPart](data-reference-c-g.md#daypart) | Optional additional aggregation over which the data is calculated. | True |
| observed_occurrences | Float | Observed amount of occurrences. | True |
| expected_occurrences | Float | Expected amount of occurrences. | True |
| place_category | String |  | True |
| location_significance | [LocationSignificance](data-reference-h-l.md#locationsignificance) |  | True |
| transport_mode | [TransportMode](data-reference-q-t.md#transportmode) |  | True |
| transport_mode_category | [TransportModeCategory](data-reference-q-t.md#transportmodecategory) |  | True |
| moment_definition_id | String |  | True |


### OndeviceMLModel
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Name of the models that were used to detect the crash. Mainly used as internal reference.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| version | String |  | True |
| name | String |  | True |
| flavor | String |  | True |


### OperatingSystem
**Kind**: ENUM

- **android**
- **ios**

### OrderingEnum
**Kind**: ENUM

- **asc**
- **desc**

### Paging
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging information that allows you to paginate through a large response list.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'Paging' | True |
| cursors | [PagingCursors](data-reference-m-p.md#pagingcursors) | The offset cursors to use when paging through results. | True |


### PagingCursors
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging cursors that you use to paginate through a large response set.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| type | String | 'PagingCursors' | True |
| before | String | This is the cursor that points to the start of the page of data that has been returned. | True |
| after | String | This is the cursor that points to the end of the page of data that has been returned. | True |


### PredictionInterval
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)


| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| start | String |  | True |
| end | String |  | True |


### PredictionTree
**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Multiple possible events that might occur for a user.

| Property | Type | Description | Nullable |
| :--- | :--- | :--- | :--- |
| is_updated | Boolean |  | True |
| probability | Float | Percentage probability of these events taking place.<br><br><code>**Deprecation notice**</code><br>probability is deprecated.<br>No longer relevant. | True |
| events | [IBranchEvent](data-reference-h-l.md#ibranchevent) | The list of events predicted to occur. | True |
| branches | [Branch](data-reference-a-b.md#branch) | <br><code>**Deprecation notice**</code><br>branches is deprecated.<br>Going forward only one prediction will be valid instead of multiple branching predictions. Please check the `events` field. | True |


### PredictionType
**Kind**: ENUM

- **StationaryIntervalPrediction**: Prediction of a Stationary event.
- **TransportIntervalPrediction**: Prediction of a Transport event.

