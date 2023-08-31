# Driving Offloads

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Driving Events Offloads

The driving events offloads are contained in a JSONL (JSON Lines) file, each line containing a JSON object corresponding
to a transport.

### Available Fields

#### Main structure

| Field name         | Type   | Description                                                                            |
|--------------------|--------|----------------------------------------------------------------------------------------|
| `mode`             | string | The transport mode (e.g. `car`, `train`, etc.).                                        |
| `metadata_user_id` | string | The user ID from the customer's side.                                                  |
| `event_id`         | string | The event ID of the transport in question.                                             |
| `user_id`          | string | The user ID from Sentiance's side.                                                     |
| `start`            | string | The start time of the transport in ISO 8601 format (e.g. `2022-06-26T11:26:48+01:00`). |
| `end`              | string | The end time of the transport in ISO 8601 format (e.g. `2022-06-26T12:26:48+01:00`).   |
| `behavior_events`  | object | The JSON object containing the different events that occurred in the transport.        |

#### `behavior_events` object

| Field name     | Type  | Description                      |
|----------------|-------|----------------------------------|
| `acceleration` | array | An array of acceleration events. |
| `idle`         | array | An array of idle events.         |
| `breakdown`    | array | An array of breakdown events.    |
| `boundaries`   | array | An array of boundaries events.   |
| `turn`         | array | An array of turn events.         |
| `anomalies`    | array | An array of anomalies events.    |
| `mounted`      | array | An array of mounted events.      |
| `crash`        | array | An array of crash events.        |
| `traffic`      | array | An array of traffic events.      |

#### Individual events objects

Each behavior event JSON object (e.g. `acceleration`) contains a set of common fields.

Some of these fields only appear on certain types of events, so all possible fields will be listed.

| Field name  | Type   | Description                                                                                                                |
|-------------|--------|----------------------------------------------------------------------------------------------------------------------------|
| `duration`  | float  | The duration of the event in seconds. Precision is 3 decimal places.                                                       |
| `features`  | object | A JSON object, which contains a field `magnitude`. The magnitude is measured in (0.2*m)/s². Precision is 3 decimal places. |
| `mean`      | float  | The mean magnitude in (0.2*m)/s² of this event. Precision is 3 decimal places.                                             |
| `start`     | string | The start time of the event in ISO 8601 format (e.g. `2022-06-26T11:26:48+01:00`).                                         |
| `end`       | string | The end time of the event in ISO 8601 format (e.g. `2022-06-26T12:26:48+01:00`).                                           |
| `magnitude` | float  | The magnitude of the event (always has a value of `0`, so it can be ignored).                                              |
| `category`  | string | The main category of the event (e.g. `acceleration`).                                                                      |
| `type`      | string | The sub type of the event (e.g. `brake` or `acceleration`).                                                                |
| `peaks`     | array  | An array of peak objects detected in the event.                                                                            |

#### Peak object

| Field name    | Type    | Description                                                                          |
|---------------|---------|--------------------------------------------------------------------------------------|
| `duration`    | float   | The duration of the peak in seconds. Precision is 3 decimal places.                  |
| `max`         | float   | The max magnitude in (0.2*m)/s² detected in the peak. Precision is 3 decimal places. |
| `integral`    | float   | The integral of the magnitude of the peak. Precision is 3 decimal places.            |
| `mean`        | float   | The mean magnitude in (0.2*m)/s² of the peak. Precision is 3 decimal places.         |
| `start`       | string  | The start time of the peak in ISO 8601 format (e.g. `2022-06-26T11:26:48+01:00`).    |
| `end`         | string  | The end time of the peak in ISO 8601 format (e.g. `2022-06-26T12:26:48+01:00`).      |
| `is_positive` | boolean | Whether or not the peak has a positive value.                                        |

## Mapped Waypoints Offloads

The mapped waypoints offloads are contained in a JSONL (JSON Lines) file, each line containing a JSON object corresponding
to a transport.

#### Main structure

| Field name         | Type   | Description                                                                                             |
|--------------------|--------|---------------------------------------------------------------------------------------------------------|
| `mapped_waypoints` | array  | An array of waypoint objects.                                                                           |
| `session_id`       | string | The session ID of the transport in question (note: multiple transports can have the same `session_id`). |
| `start`            | string | The start time of the transport in ISO 8601 format (e.g. `2022-06-26T11:26:48+01:00`).                  |
| `end`              | string | The end time of the transport in ISO 8601 format (e.g. `2022-06-26T12:26:48+01:00`).                    |
| `user_id`          | string | The user ID from Sentiance's side.                                                                      |

#### <a name="waypoint-object"></a>Waypoint object

| Field name           | Type   | Description                                                                                        |
|----------------------|--------|----------------------------------------------------------------------------------------------------|
| `latitude`           | float  | The latitude of the waypoint. Precision is 5 decimal places.                                       |
| `longitude`          | float  | The longitude of the waypoint. Precision is 5 decimal places.                                      |
| `speed_v2`           | float  | The speed in km/h at the moment the waypoint was mapped. Precision is 1 decimal place.             |
| `speedlimit`         | float  | The speed limit in km/h of the road where the waypoint was mapped. Precision is 2 decimal places.  |
| `waypoint_timestamp` | string | The timestamp corresponding to the waypoint in ISO 8601 format (e.g. `2022-06-26T11:26:48+01:00`). |

## Scores Offloads

The scores offloads are contained in a CSV file, where the first line is a header containing the field names and subsequent
lines contain the values themselves.

All scores are between 0 and 1 (or -1 when we did not receive sufficient data), with a precision of 2 decimal places.

| Field name        | Type    | Description                                                                                                                                                                                                                                                                                 |
|-------------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `timestamp`       | integer | The timestamp in UTC epoch milliseconds of the beginning of the transport.                                                                                                                                                                                                                  |
| `user_id`         | string  | The user ID from Sentiance's side.                                                                                                                                                                                                                                                          |
| `smooth`          | float   | The smooth driving score measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. The use of coasting results in a higher score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! |
| `legal`           | float   | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits!                                                                                                                                                         |
| `anticipative`    | float   | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The use of coasting results in a higher score. The higher your score, the more anticipative you drive!                              |
| `focus`           | float   | The proportion of time (percentage) the user is focused while driving, being focused means: not using the phone, which is detected through phone handling.                                                                                                                                  |
| `mounted`         | float   | The proportion of time (percentage) the phone is mounted while driving.                                                                                                                                                                                                                     |
| `hard_events`     | float   | This is a combination of hard_accel and hard_brake score. The hard brakes and accelerations are also normalized by the total number of events.                                                                                                                                              |
| `hard_accel`      | float   | Measures how often you accelerate hard. Every hard acceleration will be penalised by subtracting a percentage of your score.                                                                                                                                                                |
| `hard_brake`      | float   | Measures how often you need to brake hard. Every hard brake will be penalised by subtracting a percentage of your score.                                                                                                                                                                    |
| `legal_v2`        | float   | Same as `legal` score, the difference is that this score has better speed estimation.                                                                                                                                                                                                       |
| `smooth_v2`       | float   | Same as `smooth` score, Beside an updated normalization, the difference is that turns are also taken in account.                                                                                                                                                                            |
| `anticipative_v2` | float   | Same as `anticipative` score. Beside an updated normalization, this new version has a more accurate detection of brakes in turns.                                                                                                                                                           |
| `hard_turn`       | float   | Measures how often you turn hard. Every hard turn will be penalised by subtracting a percentage of your score.                                                                                                                                                                              |

## Transports Offloads

The transports offloads are contained in a CSV file, where the first line is a header containing the field names and subsequent
lines contain the values themselves.

Each line corresponds to an individual transport.

| Field name         | Type    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|--------------------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_id`          | string  | The user ID from Sentiance's side.                                                                                                                                                                                                                                                                                                                                                                                                             |
| `metadata_user_id` | string  | The user ID from the customer's side.                                                                                                                                                                                                                                                                                                                                                                                                          |
| `start`            | string  | The start time of the transport in ISO 8601 format (e.g. `2022-06-26T11:26:48+01:00`).                                                                                                                                                                                                                                                                                                                                                         |
| `end`              | string  | The end time of the transport in ISO 8601 format (e.g. `2022-06-26T12:26:48+01:00`).                                                                                                                                                                                                                                                                                                                                                           |
| `mode`             | string  | The transport mode (e.g. `car`, `train`, etc.).                                                                                                                                                                                                                                                                                                                                                                                                |
| `distance`         | integer | The total distance travelled in meters.                                                                                                                                                                                                                                                                                                                                                                                                        |
| `waypoints`        | array   | An array of waypoint objects containing the fields `latitude`, `longitude`, and `timestamp`, having the same types and units as the [waypoint object](#waypoint-object).                                                                                                                                                                                                                                                                       |
| `duration`         | integer | The total duration of the transport in seconds.                                                                                                                                                                                                                                                                                                                                                                                                |
| `smooth`           | float   | The smooth driving score measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. The use of coasting results in a higher score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                     |
| `legal`            | float   | The legal driving score measures how well you adhere to speed limits. The higher your score, the more you respect the speed limits! The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                                                                                                                              |
| `anticipative`     | float   | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The use of coasting results in a higher score. The higher your score, the more anticipative you drive! The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                   |
| `focus`            | float   | The proportion of time (percentage) the user is focused while driving, being focused means: not using the phone, which is detected through phone handling. The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                                                                                                       |
| `mounted`          | float   | The proportion of time (percentage) the phone is mounted while driving. The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                                                                                                                                                                                          |
| `session_id`       | string  | The session ID of the transport in question (note: multiple transports can have the same `session_id`).                                                                                                                                                                                                                                                                                                                                        |
| `hard_events`      | float   | This is a combination of hard_accel and hard_brake score. The hard brakes and accelerations are also normalized by the total number of events. The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                                                                                                                   |
| `hard_accel`       | float   | Measures how often you accelerate hard. Every hard acceleration will be penalised by subtracting a percentage of your score. The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                                                                                                                                     |
| `hard_brake`       | float   | Measures how often you need to brake hard. Every hard brake will be penalised by subtracting a percentage of your score. The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                                                                                                                                         |
| `legal_v2`         | float   | Same as `legal` score, the difference is that this score has better speed estimation. The higher your score, the smoother you drive! Precision is 6 decimal places.                                                                                                                                                                                                                                                                            |
| `event_id`         | string  | A unique ID corresponding to the individual transport event.                                                                                                                                                                                                                                                                                                                                                                                   |
| `occupant_role`    | string  | Whether the user is the `driver` or `passenger` of the vehicle in the transport.                                                                                                                                                                                                                                                                                                                                                               |
| `aggr_v2`          | float   | Measures how smooth you drive. High accelerations, heavy braking and heavy turning result in a lower score. Scores are normalized with respect to a wide population. The higher your score, the smoother you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Precision is 6 decimal places.                                                                                                 |
| `anti_v2`          | float   | The anticipative driving score measures how well you anticipate turns. Hard accelerations before or hard braking during a turn result in a lower score. The higher your score, the more anticipative you drive! When we do not have sufficient sensor data characterizing your drive, the value will be -1. Beside an updated normalization, this new version has a more accurate detection of brakes in turns. Precision is 6 decimal places. |
| `hard_turn`        | float   | Measures how often you turn hard. Every hard turn will be penalised by subtracting a percentage of your score. When we do not have sufficient data this value will be -1. Precision is 6 decimal places.                                                                                                                                                                                                                                       |
| `attention`        | float   | A combined score of handheld calling, hands-free calling and handling without calling. Precision is 6 decimal places.                                                                                                                                                                                                                                                                                                                          |
