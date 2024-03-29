# Firehose

## Motivation

### Why Firehose?

A common need among Sentiance customers is to react to _their_ user's activities. You might want to enhance their experience in a travel app based on their mode of transport, or show them relevant offers when they plan to visit a store. Receiving updates of a user's event stream in real-time is an invaluable tool.

Enter the **Firehose**: our way of sending you updates on the activity stream of your users.

## Webhooks

Delivery of messages in Firehose is done via Webhooks. Webhooks are a well-known and much used integration pattern and quite popular in linking applications for [message](https://zapier.com/blog/what-are-webhooks/) [delivery](https://sendgrid.com/blog/whats-webhook/).

## Setup

### Things We Need from You

In order to receive events over Firehose we need you to set up an endpoint capable of receiving **HTTP POST** requests in **JSON format**, compressed with **gzip,** secured by [BasicAuth](https://www.httpwatch.com/httpgallery/authentication/). Messages are based on events that take place on the Sentiance platform. You tell us which events you want to listen to and the details of your endpoint through the Insights [webhooks dashboard](https://insights.sentiance.com/) and we start sending you messages whenever we have a new event for a user of your app.

> Our US and Australian customers can go to `https://insights.d4.sentiance.com` and `https://insights.e6.sentiance.com` respectively.

We also need you to create a **HTTP GET** version of the webhook endpoint. This should be secured with the same BasicAuth credentials as the POST version and should respond with a JSON in the following format.

```javascript
{ "app_id": "<yourAppID>" }
```

This ensures that the data gets sent to the correct Application ID.

In case incorrect credentials are received by either POST or GET endpoint, a status **401** is expected as response.

### Message Format

All messages will have a general envelope format and a `data` field with a unique format per event type.

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

The **POST body** will always be a **JSON object** with a `data` field which is an array of multiple events. These events could be of [different types](firehose.md#event-reference) and from different users, batched into one request.

Each item will have a `meta` JSON object with fields `message_type` and `message_timestamp`. On webhooks configured to listen to only one type of event, the `message_type` will always be the same. If you wish to receive more than one type of event on the same webhook, you will need to check the `message_type` field to determine which event you are looking at. The `message_timestamp` field will tell you when the event was generated in our system. These timestamps are in ISO 8601 format.

Based on the value of `message_type` you'll need to parse the `data` field. 

All messages are gzipped before sending over the wire.

### Batching

To save on network bandwidth we batch messages sent over the webhook. Batching is done over both time and space, the defaults are **5 seconds** and **1 MB.** 

That is to say that once _we have 1 MB worth of data_ or _5 seconds have passed_, we will create a batch of data and send a request. These values can be configured when creating or updating a webhook. The ranges are **1 - 300 seconds** and **23kb - 4MB**.

**Note:** Batching by size is done before gzip compression.

### Delivery

On each successful delivery we expect a **200 OK** Status Code. If we don't get one, we will keep retrying \(see below\). We try our best to guarantee **at least** **once** delivery. This means we might sometimes send multiples of the same message if our server fails to recognise a successful acceptance of our POST. _We don't read the body when the response is a 200 OK._

### Security

To ensure that your messages originate from Sentiance and not from a malicious third party, we will set a **BasicAuth** header on every request as per the requested configuration in the [webhooks dashboard](https://insights.sentiance.com/).

Your connection _**must**_ be secured with TLS. [https://www.ssllabs.com/](https://www.ssllabs.com/) is a great place to inspect your endpoint and ensure it meets ongoing security standards. We _**require**_ a B grade or above to ensure all data is transmitted securely.

Furthermore all our calls originate from the following dedicated IPs, if you wish to protect your endpoint with IP whitelisting please add these to your whitelist.

* 52.213.134.71
* 34.252.131.81

We perform a list of verifications before activating webhooks. 

* We check for a valid SSL certificate present on your endpoint
* Valid BasicAuth credentials
* Correct implementation of BasicAuth security
* Intended AppID to which messages are being delivered
* The ability to successfully receive messages

We will be calling the **GET** endpoint to ensure the data gets sent to the correct Application ID. We will also call the endpoints with _incorrect_ credentials to verify they are being rejected.

We will be sending test payloads to the **POST** endpoint to ensure that the endpoint can handle our data formats. These test payloads can be identified by looking for the HTTP header `sentiance-payload-type: test`

Once automated verifications have passed, your request will be forwarded to a member of the Sentiance Client team for final validation. If everything looks good your Webhook will be made active and you will be informed over email. In case there is a problem a Sentiance Delivery Team member will reach out to you.

## Errors

### Handling them like a Champ

If your endpoint is unreachable, whether it be network fluctuations or a temporary server outage, we aim to still attempt delivery. Firehose expects a **200 OK** response for every message sent. If it gets back anything else, it will keep **retrying with exponential backoff starting from 100 ms up to 5 minutes**.

### Retention

Every webhook has a **Message TTL**. This is the **amount of time we will keep messages** for that webhook before discarding them. This ensures that we avoid sending stale information.

For example, if your **Message TTL** has been set to 30 minutes and your endpoint has been down for 40 minutes, on resuming you will only receive messages that are up to 30 minutes old. Messages from the first 10 minutes of downtime will have been dropped.

You can request a specific **Message TTL** during Webhook setup.

## Testing

To test out the viability of your newly created endpoint, you can try the following curl:

```text
curl -X POST \
  https://example.com/webhook \
  -H 'Authorization: Basic c2VudGlhbmNlOnNlY3VyZXBhc3N3b3Jk' \
  -H 'Content-Encoding: gzip' \
  -H 'Content-Type: application/json; charset=utf-8' \
  --data-binary @firehose-transport-example.gzip
```

{% file src="../.gitbook/assets/firehose-transport-example.json.gz" caption="firehose-transport-example" %}

You'll have to change the url being targeted, but for the rest you can use as is. The encoded basic auth credentials are `sentiance` and `securepassword`. The provided example file is a [Transports](firehose.md##transports) event as shown at the end of the page.

Additionally example server implementations can be found [here](https://github.com/sentiance/firehose-receiver-example).

## FAQ

#### Do you support multiple endpoints per webhook?

Unfortunately we don't. We have tried to keep the design of the Firehose as simple and fast as possible which means keeping the core feature-set minimal and maintainable.

#### Can I receive messages from multiple apps on the same endpoint?

While this is possible, it comes with the catch that you won't know which messages are from which app. One way to remedy that is to use a dynamic route parameter in your endpoint that encodes the appId.

For example:

* https://example.com/webhook/appId1
* https://example.com/webhook/appId2

With `https://example.com/webhook/:appId` being the route that handles and parse `appId`. Check our [example server implementation](https://github.com/sentiance/firehose-receiver-example) for how such an endpoint might be written.

## Event Reference

### Car Transports <a id="#transports"></a>

> Note: This message is sent for both the driver and the passenger. Do not assume that the user of this transport is necessarily the driver.

```javascript
{
	"meta": {
		"message_type": "transport",
		"message_timestamp": "2020-02-02T12:24:44.000+01:00"
	},
	"data": {
		"user_id": "5d0cb0d05160df0600000abc",
		"event_id": "199ea63edee3f182d46d0ff5d138184113c16e4db9674587e49de786e20a7abc",
		"mode": "car",
		"start": "2020-02-02T12:05:09+01:00",
		"end": "2020-02-02T12:24:44+01:00",
		"distance": 10127,
		"behavior_scores": {
			"overall": 0.73,
			"smooth": 0.73,
			"legal": 0.74,
			"anticipative": 0.71,
			"focus": 0.89,
			"mounted": 0.13,
			"hard_accel": 0.9,
			"hard_brake": 0.9,
			"hard_events": 0.73,
			"legal_v2": 1,
			"hard_turn": 0.85,
			"smooth_v2": 0.65,
			"anticipative_v2": 0.65
		},
		"start_location": {
			"timestamp": "2020-02-02T12:05:09+01:00",
			"longitude": 13.36925,
			"latitude": 52.53772
		},
		"end_location": {
			"timestamp": "2020-02-02T12:24:44+01:00",
			"longitude": 13.30897,
			"latitude": 52.49215
		}
	}
}
```

### All Transports <a id="predictions"></a>

If you subscribe to **All Transports**, you will receive events for all transport modes including **car.** The primary difference between mode **car** and other modes is the presence of `behavior_scores` on car transports.

#### Example 1

```javascript
{
	"meta": {
		"message_type": "transport",
		"message_timestamp": "2020-02-04T11:40:00.000+09:00"
	},
	"data": {
		"user_id": "5cc240cf42641b0600000abc",
		"event_id": "15d4ab88085924a15d23667e6e969aa253d32f4169242908d6f74888036a9f03",
		"mode": "biking",
		"start": "2020-02-04T11:37:21+09:00",
		"end": "2020-02-04T11:40:00+09:00",
		"distance": 884,
		"start_location": {
			"timestamp": "2020-02-04T11:37:21+09:00",
			"longitude": 139.79201,
			"latitude": 35.737
		},
		"end_location": {
			"timestamp": "2020-02-04T11:40:00+09:00",
			"longitude": 139.78759,
			"latitude": 35.74073
		}
	}
}
```

#### Example 2

```javascript
{
	"meta": {
		"message_type": "transport",
		"message_timestamp": "2020-02-02T12:24:44.000+01:00"
	},
	"data": {
		"user_id": "5d0cb0d05160df0600000abc",
		"event_id": "199ea63edee3f182d46d0ff5d138184113c16e4db9674587e49de786e20a7abc",
		"mode": "car",
		"start": "2020-02-02T12:05:09+01:00",
		"end": "2020-02-02T12:24:44+01:00",
		"distance": 10127,
		"behavior_scores": {
			"overall": 0.73,
			"smooth": 0.73,
			"legal": 0.74,
			"anticipative": 0.71,
			"focus": 0.89,
			"mounted": 0.13,
			"hard_accel": 0.9,
			"hard_brake": 0.9,
			"hard_events": 0.73,
			"legal_v2": 1,
			"hard_turn": 0.85,
			"smooth_v2": 0.65,
			"anticipative_v2": 0.65
		},
		"start_location": {
			"timestamp": "2020-02-02T12:05:09+01:00",
			"longitude": 13.36925,
			"latitude": 52.53772
		},
		"end_location": {
			"timestamp": "2020-02-02T12:24:44+01:00",
			"longitude": 13.30897,
			"latitude": 52.49215
		}
	}
}
```

### Predictions <a id="predictions"></a>

```javascript
{
	"meta": {
		"message_type": "event_prediction",
		"message_timestamp": "2020-01-30T10:32:25.895Z"
	},
	"data": {
		"user_id": "5db1c944f73d460600000abc",
		"events": [{
			"end": "2020-01-30T11:52:30.000-05:00",
			"location_type": "Shop",
			"significance": "regular",
			"type": "StationaryPrediction",
			"start": "2020-01-30T11:41:30.508-05:00",
			"latitude": 43.7628,
			"longitude": -79.41037,
			"probability": 0.12,
			"place": {
				"name": "Yonge Sheppard Centre",
				"category_hierarchy": ["shop", "general", "mall"]
			}
		}, {
			"probability": 0.36,
			"mode": "walking",
			"type": "TransportPrediction",
			"start": "2020-01-30T11:52:30.000-05:00",
			"end": "2020-01-30T12:05:12.000-05:00"
		}, {
			"location_type": "Work",
			"significance": "work",
			"latitude": 43.76143,
			"longitude": -79.41004,
			"type": "StationaryPrediction",
			"start": "2020-01-30T12:05:12.000-05:00",
			"end": "2020-01-30T16:37:30.000-05:00"
		}, {
			"start": "2020-01-30T16:37:30.000-05:00",
			"end": "2020-01-30T16:43:32.000-05:00",
			"probability": 0.18,
			"mode": "walking",
			"type": "TransportPrediction"
		}],
		"trigger_time": "2020-01-30T16:31:30.508+00:00",
		"probability": 0.0000011920713741376413
	}
}
```

### Locations

```javascript
{
	"meta": {
		"message_type": "location",
		"message_timestamp": "2020-01-30T16:31:48.592Z"
	},
	"data": {
		"previous_location": {
			"latitude": 43.76277,
			"longitude": -79.4107,
			"accuracy": "14",
			"time": "2020-01-30T11:29:33.296-05:00"
		},
		"user_id": "5db1c944f73d460600000abc",
		"last_location": {
			"latitude": 43.76277,
			"longitude": -79.4107,
			"accuracy": 14,
			"time": "2020-01-30T11:25:05.083-05:00"
		}
	}
}
```

### Stationaries

```javascript
{
	"meta": {
		"message_type": "stationary",
		"message_timestamp": "2020-01-29T12:03:10.000+01:00",
		"updated_attributes": ["location"]
	},
	"data": {
		"user_id": "5dadf781b8271f0600000b5c",
		"event_id": "d945a24769b079eeae9e0305129b61d4fe426dc1b7560ba4b30378b5c5881997",
		"start": "2020-01-29T11:58:38.000+01:00",
		"end": "2020-01-29T12:03:10.000+01:00",
		"location": {
			"longitude": 4.54461,
			"latitude": 50.93558
		}
	}
}
```

### Moments

Moment message type sends moment upsert \(moment\_changed\) and moment removal \(moment\_removed\) actions which can be correlated by the moment identifier \(moment\_id\).

```javascript
{
	"meta": {
		"message_type": "moment",
		"message_timestamp": "2021-03-10T14:00:26.029Z",
		"updated_attributes": null
	},
	"data": {
		"app_id": "000000000000000000000abc",
		"events": [
      {
        "action": "moment_removed",
        "moment_id": "4f78074e0a3e9ab5e8e03895d0bbeca343dc2a8fcb4519f1a3bdaf3caada2b87"
      },
      {
        "action": "moment_removed",
        "moment_id": "82adc6bac2af5d4f824a4900a4fc98a2ddc7efc099753ce643f59bcc019e2288"
      },
      {
        "action": "moment_changed",
        "category": "semantic_time",
        "end": "2021-03-10T12:30:00.000-05:00",
        "moment_id": "d1d74e92289d9447d261267434e5e2dc3e4ed28a02ba8e185f544e2bffb99155",
        "start": "2021-03-10T10:00:00.000-05:00",
        "type": "late_morning"
      },
      {
        "action": "moment_changed",
        "category": "semantic_time",
        "end": "2021-03-10T14:32:00.000-05:00",
        "moment_id": "105d7ef1e8746b75f2822f4e42afb3df24ea066cddd2e084bbd3afe82faceee5",
        "start": "2021-03-10T12:30:00.000-05:00",
        "type": "lunch"
      },
      {
        "action": "moment_changed",
        "category": "semantic_time",
        "end": "2021-03-10T16:46:00.000-05:00",
        "moment_id": "b74b6acc1534773fdabf278c22ab416a46a5ead5bb2be5442d2c5111b7217487",
        "start": "2021-03-10T14:32:00.000-05:00",
        "type": "afternoon"
      }
    ],
		"user_id": "5cc0514c7af8ce0600000abc"
	}
}
```

