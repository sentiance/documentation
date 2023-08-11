# GraphQL

Our API primarily speaks [GraphQL](https://graphql.org/learn/) (GQL, for short). While explaining how GraphQL works is beyond the scope of this guide, there are excellent resources available on the interwebs.

Here we will introduce the basic request-response structure of the Sentiance GraphQL API.

## Endpoint and Authorization

Our default GraphQL endpoint lives at **POST** `https://api.sentiance.com/v2/gql` and accepts the same [bearer token based authorization](../important-topics/authentication-and-authorization.md) as our[ REST endpoints.](rest-api/)

We adhere to the [GraphQL specification](https://graphql.org/learn/serving-over-http/#post-request) but do not support multiple operation types.

Since it is possible for a single HTTP request to encompass multiple GraphQL queries with some of them succeeding and some of them failing, the endpoint always returns a 200 OK, unless something severe enough happens on the server-side to guarantee failure of the entire response (such as a 500 status code). After checking for the 200 status code, please also check the body of the response for `data` and `error` properties.

{% hint style="danger" %}
For other environments, please ask your sales representative or [support@sentiance.com](mailto:support@sentiance.com) for the custom endpoint linked to your environment.
{% endhint %}

{% swagger baseUrl="https://api.sentiance.com" path="/v2/gql" method="post" summary="GQL Request" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Bearer
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="false" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" name="query" type="string" required="false" %}
The GraphQL query.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="variables" type="object" required="false" %}
A flat JSON object describing the variables to substitute in the query.
{% endswagger-parameter %}

{% swagger-response status="200" description="This would depend on the query made. An example of query/response is presented here." %}
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
{% endswagger-response %}
{% endswagger %}

### Introspection

While you can always discover and play around with Graphql in our [Data Explorers](../data-explorer/data-explorer/), you might wish to programatically introspect our Schema for your own tools to parse. You can do so by firing off an Introspection Query.

```javascript
QUERY
query IntrospectionQuery {
  __schema {
    queryType {
      name
    }
    mutationType {
      name
    }
    subscriptionType {
      name
    }
    types {
      ...FullType
    }
    directives {
      name
      description
      locations
      args {
        ...InputValue
      }
    }
  }
}

fragment FullType on __Type {
  kind
  name
  description
  fields(includeDeprecated: true) {
    name
    description
    args {
      ...InputValue
    }
    type {
      ...TypeRef
    }
    isDeprecated
    deprecationReason
  }
  inputFields {
    ...InputValue
  }
  interfaces {
    ...TypeRef
  }
  enumValues(includeDeprecated: true) {
    name
    description
    isDeprecated
    deprecationReason
  }
  possibleTypes {
    ...TypeRef
  }
}

fragment InputValue on __InputValue {
  name
  description
  type {
    ...TypeRef
  }
  defaultValue
}

fragment TypeRef on __Type {
  kind
  name
  ofType {
    kind
    name
    ofType {
      kind
      name
      ofType {
        kind
        name
        ofType {
          kind
          name
          ofType {
            kind
            name
            ofType {
              kind
              name
              ofType {
                kind
                name
              }
            }
          }
        }
      }
    }
  }
}
```

## Examples

Some examples of various GQL queries with example response are presented here. With GraphQL you can fetch as much or as little as you wish.

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
