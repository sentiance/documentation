---
description: Self-serve test plan to verify your Sentiance integration before go-live.
---

# Verifying your integration

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Non functional

In order to get to a smooth roll-out there's some best practices you may want to follow to provide your end-users with a great experience

* Each development environment uses it's own app-id
* The mobile application has a clear user on-boarding flow that explains why you are collecting the end-users data.
* If applicable you have a system set up to guide end-users through whitelisting. More info on this can be found at [https://dontkillmyapp.com/](https://dontkillmyapp.com/). 
* You have shared you rollout plan and volume with us.

## [SDK](../sdk/getting-started/android-sdk/include-sdk.md)

* You are using the [latest SDK](../sdk/changelog/)
* Share your integration with us via Testflight or an APK
* Sentiance users are being created properly
* User linking works as expected
* Event collection is happening
* Proper timeline construction without gaps

## [GraphQL / API](../backend/graphql.md)

* Backend queries use the API Keys
* App / user based queries use a user token
* You are not using GraphQL / API queries for real-time use cases \(e.g. polling\)
* Heavy / Large queries are validated by us

## Offloads

* Connection to your S3 bucket is successful
* Offloads are visible & generated on a daily / weekly basis
* Automatic transfer of offloads to your own backend

## [Firehose](firehose.md)

* Your endpoint is set up
* You are receiving messages in real-time based on your requirements



