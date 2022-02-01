# Data Reference M-P

## Objects

* [MomentDefinition](broken-reference)
* [MomentFeedback](broken-reference)
* [MomentFeedbackFeedback](broken-reference)
* [OccurrenceCountAnomaly](broken-reference)
* [OndeviceMLModel](broken-reference)
* [Paging](broken-reference)
* [PagingCursors](broken-reference)
* [PredictionInterval](broken-reference)
* [PredictionTree](broken-reference)

### MomentDefinition

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

A single moment definition.

| Property      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Nullable |
| ------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| type          | String | 'MomentDefinition'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | True     |
| id            | String | Identifier of this MomentDefinition. Possible values: working\_at\_work,working\_remote,home,morning,lunch,afternoon,evening,night,commute\_from\_work,commute\_from\_home,business\_trip,holiday,nearby\_home,nearby\_work,city\_name,country,children\_drop\_off,sport\_routine,shopping\_routine,evening\_entertainment,night\_out,afternoon\_drinks,evening\_drinks,breakfast\_out,lunch\_out,dinner\_out,about\_to\_working,about\_to\_commute\_from\_home,about\_to\_commute\_from\_work,about\_to\_children\_drop\_off,about\_to\_sport,about\_to\_shopping,nearby\_poi | True     |
| category      | String | Category ID of this MomentDefinition, if any. Possible values: activity,semantic\_time,travel,geography,location,about\_to\_routine                                                                                                                                                                                                                                                                                                                                                                                                                                            | True     |
| display\_name | String | A displayable name for this MomentDefinition.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | True     |
| description   | String | A short description about this MomentDefinition.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |

### MomentFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IFeedback, IMomentFeedback

| Property         | Type                   | Description                                                                        | Nullable |
| ---------------- | ---------------------- | ---------------------------------------------------------------------------------- | -------- |
| type             | FeedbackType           | 'MomentFeedback'                                                                   | True     |
| start            | String                 | Start time the feedback relates to, sourced by the event, moment or user-provided. | False    |
| end              | String                 | End time the feedback relates to, sourced by the event, moment or user-provided.   | True     |
| created          | String                 | Time when this feedback entry was created.                                         | True     |
| projection\_time | String                 | Time to provide when the feedback data was read from the API. ISO8601. Optional.   | True     |
| moment\_feedback | MomentFeedbackFeedback |                                                                                    | True     |
| moment           | IMoment                | The Moment this feedback refers to.                                                | True     |

### MomentFeedbackFeedback

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property                           | Type               | Description                                                 | Nullable |
| ---------------------------------- | ------------------ | ----------------------------------------------------------- | -------- |
| moment\_definition\_id\_assessment | FeedbackAssessment | If the user thinks our detected moment is correct.          | True     |
| moment\_definition\_id\_feedback   | String             | Correction by the user in case our detection was incorrect. | True     |

### MomentType

**Kind**: ENUM

* **GenericMoment**
* **CityMoment**
* **CountryMoment**

### OccurrenceCountAnomaly

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

**Implements**: IAnomaly, IOccurrenceCountAnomaly, IAggregatedAnomaly, IStationaryAnomaly, ITransportAnomaly, IMomentAnomaly

| Property                  | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Nullable |
| ------------------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| type                      | AnomalyType           | 'OccurrenceCountAnomaly'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | True     |
| start                     | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| end                       | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| analysis\_type            | AnalysisType          | <p><br><strong><code>Deprecation notice</code></strong><br>analysis_type is deprecated.<br>After significantly improving our platform's real-timeliness, we now don't need the analysis of a trip to go through multiple phases. This means you no longer need to filter our Firehose or API output by AnalysisType. Previously, trips had three analysis types based on processing latency. They were, namely, 'processed,' 'indepth,' and 'preliminary.' Based on your use cases, you may have filtered out certain types. As we will deprecate this field on Dec 10, 2021, you will need to change your backend if you use the AnalysisType field.</p> | True     |
| anomaly                   | Anomaly               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| sigma                     | Float                 | The observed standard deviation from expected behavior for this anomaly. If the standard deviation is high, the anomaly confidence will be low.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| probability               | Float                 | The larger the probability, the more anomaly. Value is between 0.0 and 1.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | True     |
| period                    | AnomalyTimePeriod     | Aggregation period over which the data is calculated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | True     |
| day\_part                 | DayPart               | Optional additional aggregation over which the data is calculated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | True     |
| observed\_occurrences     | Float                 | Observed amount of occurrences.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| expected\_occurrences     | Float                 | Expected amount of occurrences.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| place\_category           | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| location\_significance    | LocationSignificance  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| transport\_mode           | TransportMode         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| transport\_mode\_category | TransportModeCategory |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |
| moment\_definition\_id    | String                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | True     |

### OndeviceMLModel

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Name of the models that were used to detect the crash. Mainly used as internal reference.

| Property | Type   | Description | Nullable |
| -------- | ------ | ----------- | -------- |
| version  | String |             | True     |
| name     | String |             | True     |
| flavor   | String |             | True     |

### OperatingSystem

**Kind**: ENUM

* **android**
* **ios**

### Paging

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging information that allows you to paginate through a large response list.

| Property | Type          | Description                                            | Nullable |
| -------- | ------------- | ------------------------------------------------------ | -------- |
| type     | String        | 'Paging'                                               | True     |
| cursors  | PagingCursors | The offset cursors to use when paging through results. | True     |

### PagingCursors

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

The paging cursors that you use to paginate through a large response set.

| Property | Type   | Description                                                                             | Nullable |
| -------- | ------ | --------------------------------------------------------------------------------------- | -------- |
| type     | String | 'PagingCursors'                                                                         | True     |
| before   | String | This is the cursor that points to the start of the page of data that has been returned. | True     |
| after    | String | This is the cursor that points to the end of the page of data that has been returned.   | True     |

### PredictionInterval

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

| Property | Type   | Description | Nullable |
| -------- | ------ | ----------- | -------- |
| start    | String |             | True     |
| end      | String |             | True     |

### PredictionTree

**Kind**: [Object](https://graphql.org/learn/schema/#object-types-and-fields)

Multiple possible events that might occur for a user.

| Property    | Type         | Description                                                                                                                                                                                                                      | Nullable |
| ----------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| is\_updated | Boolean      |                                                                                                                                                                                                                                  | True     |
| probability | Float        | <p>Percentage probability of these events taking place.<br><br><strong><code>Deprecation notice</code></strong><br>probability is deprecated.<br>No longer relevant.</p>                                                         | True     |
| events      | IBranchEvent | The list of events predicted to occur.                                                                                                                                                                                           | True     |
| branches    | Branch       | <p><br><strong><code>Deprecation notice</code></strong><br>branches is deprecated.<br>Going forward only one prediction will be valid instead of multiple branching predictions. Please check the <code>events</code> field.</p> | True     |

### PredictionType

**Kind**: ENUM

* **StationaryIntervalPrediction**: Prediction of a Stationary event.
* **TransportIntervalPrediction**: Prediction of a Transport event.
