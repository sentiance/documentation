---
description: High level integration guide
---

# A standard integration

{% hint style="danger" %}
This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com.
{% endhint %}

## Get important updates on bug fixes, changes and new features.

[Subscribe to our Technical Release Notes](https://sentiance.us4.list-manage.com/subscribe/post?u=20d6a5a74b902f67b939e3648\&amp;id=cdc37b7e30\&name=).

## Getting data on the platform

The first step should always be to start with the [SDK integration](sdk/getting-started/). In our experience this is where most issues pop-up that take some time to resolve.

Our guide(s) are pretty extensive and should get you to a correct integration. But running over [the validation page](guide/verifying-your-integration.md) and sending us your integration code is usually a good way to prevent unexpected behaviour.

## Looking at & investigating your data

**Non-developers**

To investigate your data without any real code integration you can refer to our [Insights dashboard](https://insights.sentiance.com/#/). Please note that this is for demo purposes only and should **not** be used in a production scenario.

**Developers**

We also provide a [data explorer](data-explorer/data-explorer/) per environment. This tool allows you to freely try out and construct queries.

_\*Pro tip: Hold "cmd" or the windows key while clicking a term and the data model will give you all available fields._

## Retrieving your data

**Pull based**

Use the[ API / GraphQL](backend/graphql.md). These end points can be used by both server and user based tokens. They are ideal for displaying information in your app or querying for data based on your internal triggers (Or for example a firehose message).

**Push based // Real-time**

Use the [firehose](guide/firehose.md) integration. If you need your data as quickly as possible this is the way to go. Its fast and light weight and will alert you to relevant changes to your user's data.

**For analytics // Batch**

Refer to the offloads. The offloads are a file based system that put a dozen or so files on a regular interval on a dedicated S3 bucket. The files will contain all of the data for all of your users. These are ideal to push into your own data crunching platform or to get a quick global overview of your population.
