# Authentication and Authorization

The Sentiance Backend speaks REST and GraphQL, both of which share the same authentication mechanism.

An `authorization` header with content `Bearer <token>` authenticates and authorizes your request. Based on what kind of token is supplied, the level of access is determined and could affect the functionality of various calls.

#### Example:

```text
Authorization: Bearer e5c3b842284045d98ed042814f31543f
```

## User Tokens

**SDKUsers** are created when the [SDK initializes with an App ID and App Secret](../sdk/getting-started/android-sdk/initialization.md). They have a userID and are only authenticated by their token. You can [retrieve this token from an initialized SDK](../sdk/appendix/user-credentials.md#get-user-and-token).

## API Keys

**API Keys** are ****a revocable, rotatable, scopeable key with which to query the API**.** 

API Keys are generated on-demand with a **name**, **scope**, and **expiry date** and are disclosed to the creator **only once**. Please ensure the API Key is immediately stored somewhere secure.

{% hint style="danger" %}
API Keys should be **stored securely** and should **never be shared outside your company**. A Sentiance employee will **never** ask for your API Key\(s\). Any leaked key \(even to Sentiance employees\) will immediately be revoked and flagged as a security incident.
{% endhint %}

#### Name

A name can be given by the developer generating the key. The name is for visual purposes only and has no operational impact. Choose a name that would help you identify the key.

**Scopes**

Scopes allow you to specify what operations an API Key can perform. Currently, we offer 3 different scopes: _**user.read**_**,** _**user.delete**_ and _**user.link**_. We strongly suggest that you use multiple API Keys with limited scopes for different operations.

| Scope | Description |
| :--- | :--- |
| **user.read** | Use this scope to read user data. This scope should be used with the GraphQL and Rest APIs that are exposed by the sentiance platform to read user data. |
| **user.delete** | Use this scope to delete a user along with all historical data. This scope should be used with the [user delete API](https://docs.sentiance.com/backend/rest-api#user-delete). |
| **user.link** | Use this scope to link third party users with a sentiance user. This scope should be used with the [user link API](https://docs.sentiance.com/backend/rest-api#user-link). |

![API Key scopes](../.gitbook/assets/screenshot-2020-02-18-at-15.26.15.png)

**Self-Expiring**

For increased security, API Keys are self-expiring. The expiry time is 1 year \(recently changed from 90 days\) from time of creation. After 1 year, the old API Key will stop working and a new one will have to be created. We allow up to 10 active API Keys at any given time, per app. An active key is one that hasn't been revoked or expired.

{% hint style="warning" %}
Please make sure you add the renewal of API Keys to your existing maintenance process and keep track of expiry dates. **Developers on your account will receive a reminder e-mail two weeks before the expiry date and one week before the expiry date.**  
{% endhint %}

#### Manage Your Own API Keys

You can manage your own API Keys from our developer portal. Our developer portal has all the tools you need, including a full history of API Keys created, revoked or expired. See it in action [here.](https://insights.sentiance.com/#/login)

> Most of our clients **are based on our European platform** \(even US and Australian clients\) at `https://insights.sentiance.com`.   
>   
> If you are using our US-based or Australian-based platform, please use respectively `https://insights.d4.sentiance.com` and `https://insights.e6.sentiance.com.`

