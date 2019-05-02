# Firehose

## Motivation

### Why Firehose?

A common desire among clients is to react to their user's activities when they happen. You might want to enhance their experience in a travel app based on their mode of transport or show them relevant offers when they plan to visit a store. Receiving updates of a user's activities as they happen is necessary in such cases.

Enter the Firehose: our way of sending you updates on the activities of your users.

## Webhooks

Delivery of messages in Firehose is done via Webhooks. Webhooks are a well-known and much used integration pattern and quite popular in linking applications for [message](https://zapier.com/blog/what-are-webhooks/) [delivery](https://sendgrid.com/blog/whats-webhook/).

## Setup

### Things We Need from You

In order to receive events over Firehose we need you to set up an endpoint capable of receiving **HTTP POST** requests in **JSON format**, compressed with gzip. Messages are based on events that take place on the Sentiance platform. You tell us which events you want to listen to and the details of your endpoint and we start sending you messages whenever we have a new event for a user of your app.

### Message Format

All messages will have a general envelope format and then a `data` field with a unique format per event type.

```javascript
{
  "data": [
    {
      "meta": {
        "message_type": <typeOfEvent>,
        "message_timestamp": <timestampOfEvent>
      },
      "data": {
        "user_id": <idOfUser>
      }
    }
  ]
}
```

A message will always be a JSON object with a `data` field which is an array of various events. These events could be of different types and from different users, batched into one request.

Each item will have a `meta` JSON object with fields `message_type` and `message_timestamp`. On webhooks configured to listen to only one type of event, the `message_type` will always be the same. If you wish to receive more than one type of event on the same webhook, you will need to check the `message_type` field to determine which event you are looking at. The `message_timestamp` field will tell you when the event was generated in our system. These timestamps are in ISO 8601 format.

Based on the value of `message_type` you'll need to parse the `data` field. 

All messages are gzipped before sending over the wire.

### Batching

To save on network bandwidth we batch messages sent over the webhook. Batching is done over both time and space, the defaults are **5 seconds** and **1 MB**, that is to say that once we have 1 MB worth of data or 5 seconds have passed, we will create a batch of data and send a request. These values can be configured so let us know what you want. The ranges are **1 - 300 seconds** and **23kb - 4MB**.

**Note:** The batching by size is done before gzip compression.

### Security

To ensure that your messages originate from Sentiance and not from a malicious third party, we will set a BasicAuth header on every request. You can send us these basic credentials \(we prefer SMS or [https://onetimesecret.com/](https://onetimesecret.com/) for security\) and we attach them to all our requests.

Furthermore, we request that you secure your connection with TLS. [https://www.ssllabs.com/](https://www.ssllabs.com/) is a great place to inspect your endpoint and ensure it meets ongoing security standards. We **require** a B grade or above to ensure all data is transmitted securely.

**Both these security measures are mandatory.**

Furthermore all our calls originate from the following dedicated IPs, if you wish to protect your endpoint with IP whitelisting please add these to your whitelist.

* 52.213.134.71
* 34.252.131.81

## Errors

### Handling them like a Champ

If your endpoint is unreachable, whether it be network fluctuations or a temporary server outage, we aim to still send the message to you. Firehose expects a 200 OK response for every message sent. If it gets back anything else, it will keep **retrying with exponential backoff from 100 ms up to 5 minutes**.

### Retention

Every webhook has a **retention period**. This is the **amount of time we will keep messages** for that webhook before discarding them. This ensures that we avoid sending stale information.

For example, if your retention period has been set to 30 minutes and your endpoint has been down for 40 minutes, on resuming you will only receive messages that are up to 30 minutes old. Messages from the first 10 minutes of downtime will have been dropped.

You can request a specific retention period when requesting the webhook setup. The retention period can be set up to as high as **24 hours**.

## Event Reference

### Predictions <a id="predictions"></a>

```javascript
{
  "meta": {
    "message_type": "event_prediction",
    "message_timestamp": "2018-07-14T17:01:52.000+00:00"
  },
  "data": {
    "user_id": "595a29d58fbb430700000027",
    "branches": [
      {
        "events": [
          {
            "probability": 0.75,
            "start": "2018-07-14T17:06:31.000+00:00",
            "end": "2018-07-14T17:11:08.000+00:00",
            "type": "TRANSPORT_CAR"
          },
          {
            "probability": 0.41,
            "start": "2018-07-14T17:11:08.000+00:00",
            "end": "2018-07-14T17:41:18.000+00:00",
            "type": "STATIONARY_SHOP"
          }
        ]
      }
    ]
  }
}
```

### Transports <a id="#transports"></a>

```javascript
{
  "meta": {
    "message_type": "transport",
    "message_timestamp": "2018-07-14T17:21:00.000+00:00"
  },
  "data": {
    "user_id": "595a29d58fbb430700000027",
    "mode": "car",
    "start": "2018-07-14T14:31:58.416+00:00",
    "end": "2018-07-14T17:21:00.000+00:00",
    "distance": 282159,
    "behavior_scores": {
      "overall": 0.81,
      "smooth": 0.88,
      "legal": 0.7,
      "anticipative": 0.86,
      "focus": 1,
      "mounted": 0,
      "hard_accel": 0.25,
      "hard_brake": 0.75,
      "hard_events": 0.83,
      "legal_v2": 0.65,
      "hard_turn": 0.5,
      "smooth_v2": 0.88,
      "anticipative_v2": 0.68
    },
    "start_location": {
      "timestamp": "2018-07-14T17:06:31.000+00:00",
      "longitude": 4.0696,
      "latitude": 49.23617
    },
    "end_location": {
      "timestamp": "2018-07-14T17:11:08.000+00:00",
      "longitude": 4.06919,
      "latitude": 49.23614
    }
  }
}
```

