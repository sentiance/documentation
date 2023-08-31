# GraphQL

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Our API primarily speaks [GraphQL](https://graphql.org/learn/) \(GQL, for short\). While explaining how GraphQL works is beyond the scope of this guide, there are excellent resources available on the interwebs.

Here we will introduce the basic request response structure of the Sentiance GraphQL API.

## Endpoint and Authorization

Our GraphQL endpoint lives at **POST** `https://api.sentiance.com/v2/gql` and accepts the same [bearer token based authorization](authentication-and-authorization.md) as our[ REST endpoints.](rest-api.md)

We adhere to the [GraphQL specification](https://graphql.org/learn/serving-over-http/#post-request) but do not support multiple operation types.

{% api-method method="post" host="https://api.sentiance.com" path="/v2/gql" %}
{% api-method-summary %}
GQL Request
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer &lt;token&gt;
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="query" type="string" required=true %}
The GraphQL query.
{% endapi-method-parameter %}

{% api-method-parameter name="variables" type="object" required=true %}
A flat JSON object describing the variables to substitute in the query.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
This would depend on the query made. An example of query/response is presented here.
{% endapi-method-response-example-description %}

```javascript
REQUEST 
{
  "query": "query($user_id: String!) {\n  user(id: $user_id) {\n    id\n    event_history(from: \"2019-04-01\", to:\"2019-04-02\") {\n      type\n      start\n      end\n      analysis_type\n      ... on Stationary {\n        latitude\n        longitude\n        location {\n          significance\n        }\n      }\n      ... on Transport {\n        mode\n        distance\n      }\n    }\n  }\n}",
  "variables": {
    "user_id": "5a93deb3d8e7d90600001e6f"
  }
}

RESPONSE
{
  "data": {
    "user": {
      "id": "5a93deb3d8e7d90600001e6f",
      "event_history": [
        {
          "type": "Stationary",
          "start": "2019-02-05T09:25:01.000+01:00",
          "end": null,
          "analysis_type": "indepth",
          "latitude": 51.19654,
          "longitude": 4.40794,
          "location": {
            "significance": "new"
          }
        }
      ]
    }
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Examples

Some examples of various GQL queries with example response are presented here. With GraphQL you can fetch as much or as little as you wish, and these 

### Moment Definitions

```javascript
QUERY
query {
  moment_definitions {
    id
    type
    category
    display_name
  } 
}

RESPONSE
{
  "data": {
    "moment_definitions": [
      {
        "id": "working_at_work",
        "type": "MomentDefinition",
        "category": "activity",
        "display_name": "Working at work"
      },
      {...}
    ]
  }
}
```

### Alpha Segments

```javascript
QUERY
query {
  segment_definitions(status: ALPHA) {
    id
    type
    category
    display_name
  } 
}

RESPONSE
{
  "data": {
    "segment_definitions": [
      {
        "id": "mobility.passenger",
        "type": "SegmentDefinition",
        "category": "passenger",
        "display_name": "Passenger"
      },
      {...}
    ]
  }
}
```

### User Timeline Query

```javascript
QUERY
query($user_id: String!, $from:String, $to: String) {
  user(id: $user_id) {
    event_history(from: $from, to:$to) {
      type
      start
      end
      analysis_type
      ... on Stationary {
        latitude
        longitude
        location {
          significance
        }
      }
      ... on Transport {
        mode
        distance
      }
    }
  }
}

VARIABLES
{ 
  "user_id": "583e08a1cd99250700000002",
  "from": "2019-03-22",
  "to": "2019-03-23"
}

RESPONSE
{
  "data": {
    "user": {
      "event_history": [
        {
          "type": "Stationary",
          "start": "2019-03-23T19:51:49.000+01:00",
          "end": "2019-03-25T08:30:21.000+01:00",
          "analysis_type": "indepth",
          "latitude": 51.78561,
          "longitude": 42.49694,
          "location": {
            "significance": "home"
          }
        },
        {
          "type": "Transport",
          "start": "2019-03-23T19:49:49.000+01:00",
          "end": "2019-03-23T19:51:49.000+01:00",
          "analysis_type": "indepth",
          "mode": "walking",
          "distance": null
        },
        {...}
      ]
    }
  }
}
```

### User Moment History

```javascript
QUERY
query($user_id: String!, $from:String, $to: String) {
  user(id: $user_id) {
    id
    moment_history(from: $from, to:$to) {
      start
      end
      analysis_type
      moment_definition_id
    }
  }
}

VARIABLES
{ 
  "user_id": "583e08a1cd99250700000002",
  "from": "2019-03-22",
  "to": "2019-03-23"
}

RESPONSE
{
  "data": {
    "user": {
      "id": "583e08a1cd99250700000002",
      "moment_history": [
        {
          "start": "2019-03-23T19:51:49.000+01:00",
          "end": "2019-03-25T08:30:21.000+01:00",
          "analysis_type": "processed",
          "moment_definition_id": "home"
        },
        {
          "start": "2019-03-23T19:22:40.000+01:00",
          "end": "2019-03-23T19:49:49.000+01:00",
          "analysis_type": "processed",
          "moment_definition_id": "shopping_routine"
        },
        {...}
      ]
    }
  }
}
```



