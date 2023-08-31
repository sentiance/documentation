# Glossary

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

## Access Roles

As a Sentiance user you could have various access roles assigned to you which grant or restrict data access.

### Default

By default no data access is granted which means you only have access to your own data. Insights will show your own timeline and any GraphQL or REST queries for your own user will return data.

### Spectator

With the **Spectator** role granted to your user on your organisation's **Account**, you can view data for all users of all **Applications** which belong to that organisation's **Account**. This includes user data in dashboards such as Insights, and making GraphQL or REST queries.

### Developer

With the **Developer** role granted to your user on your organisation's **Account**, you have all the same data access capabilities as **Spectators**, and can, additionally, perform developer-centric operations on all **Applications** belonging to that organisation's **Account.** 

Currently, as a **Developer**, you can do the following things:

* View the **Secret Key** of any **Application** under that **Account.** This is the **Secret** used in initialising the SDK.
* Administrate **Webhooks** of any **Application** under that **Account,** for the Firehose to connect to**.** You can submit requests for a new **Webhook** or update/delete/enable/disable an existing **Webhook**.
* Administrate **API Keys** of any **Application** under that **Account.** You can view or revoke all existing **API Keys**, or create new ones.



