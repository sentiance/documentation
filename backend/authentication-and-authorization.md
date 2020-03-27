# Authentication and Authorization

The Sentiance Backend speaks REST and GraphQL, and share the same authentication mechanism.

An `authorization` header with content `Bearer <token>` authenticates and authorizes your request. Based on what kind of token is supplied, the level of access is determined and could affect the functionality of various calls.

#### Example:

```text
Authorization: Bearer e5c3b842284045d98ed042814f31543f
```

## The User Token

To understand the usage of a User Token, let us first talk about the the two types of Users the platform supports: **SDKUser** and **ControlUser.**

### **SDKUser**

**SDKUsers** are created when the [SDK initializes with an App ID and App Secret](../sdk/getting-started/android-sdk/initialization.md). They only have a userID and are only authenticated by their token. You can [retrieve this token from an initialized SDK](../sdk/appendix/user-credentials.md#get-user-and-token).

### ControlUsers

**ControlUsers** are created when you sign up via [Journeys](https://www.sentiance.com/demo/) or [Insights](https://insights.sentiance.com). They have an email/password pair that can be used to get a token. [See below.](authentication-and-authorization.md#authenticating-with-a-control-user)

User Tokens identify one unique user and can be used to retrieve any data belonging _only_ to that user.

Common use-cases of this token included getting user timeline, retrieving segments, retrieving predictions, etc. to create a unique UI for the user to view their own data.

## The Server Token \(Deprecated\)

{% hint style="danger" %}
Server Tokens \(a.k.a. App Tokens\) have been replaced by API Keys and should not be used anymore. **Please find more information on using API Keys below.** 
{% endhint %}

Server Tokens provide you access to all the user data under one application. As such they should only be used in server-side integrations and should never be transmitted to end-user devices.

You can retrieve the Server Token by visiting [apps page on Insights](https://insights.sentiance.com/#/apps), if you have [Developer](../library/glossary.md#developer) access.

Common use-cases of this token include building internal dashboards to view within your team, run batch processes on users, etc.

{% hint style="warning" %}
Server Tokens will be **deprecated on April 27th 2020.** 
{% endhint %}

## API Keys

Our current Server Token implementation does not have token expiry, scoping or naming. There is no revocation mechanism and no rotation mechanism. To remedy this we introduce **API Keys:** a revocable, rotatable, scopeable key with which to query the API**.** 

API Keys are generated on-demand with a **name**, **scope**, and **expiry date** and are disclosed to the creator **only once**. Please ensure the API Key is immediately stored somewhere secure.

#### Name

A name can be given by the developer generating the key. The name is for visual purposes only and has no operational impact. Choose a name that would help you identify the key.

**Scopes**

Scopes allow you to specify what operations an API Key can perform. Currently, we offer 3 different scopes: _**user.read**_**,** _**user.delete**_ and _**user.link**_. We strongly suggest that you use multiple API Keys with limited scopes for different operations.

| Scope | Description |
| :--- | :--- |
| **user.read** | Use this scope to read user data. This scope should be used with the GraphQL and Rest APIs that are exposed by the sentiance platform to read user data. |
| **user.delete** | Use this scope to delete a user along with all historical data. This scope should be used with the [user delete API](https://docs.sentiance.com/backend/rest-api#user-delete)  |
| **user.link** | Use this scope to link third party users with sentiance a user. This scope should be used with the [user link API](https://docs.sentiance.com/backend/rest-api#user-link) |

![API Key scopes](../.gitbook/assets/screenshot-2020-02-18-at-15.26.15.png)

**Self-Expiring**

For increased security, API Keys are self-expiring. The expiry time is 90 days from time of creation. After  90 days, the old API Key will stop working and a new one will have to be created. We allow up to 10 active API Keys at a time for an app. An active key is one that hasn't been revoked or expired.

{% hint style="warning" %}
Please make sure you add the renewal of API Keys to your existing maintenance process and keep track of expiry dates. **Developers on your account will receive a reminder e-mail one month before the expiry date and one week before the expiry date.**  
{% endhint %}

#### Manage Your Own API Keys

While in the past creating, revoking and general Server Token management required you to contact the Sentiance team, with API Keys, you can do it yourself. Our developer portal has all the tools you need, including a full history of API Keys created, revoked or expired. See it in action [here.](https://insights.sentiance.com/#/login)

> Customers who use one of our **platforms based in the US or Australia**, can go to `https://insights.d4.sentiance.com` and `https://insights.e6.sentiance.com` respectively.

## Authenticating With a Control User

If you've signed up via the [Insights](https://insights.sentiance.com) dashboard or [Journeys](https://www.sentiance.com/demo/), you have a ControlUser to play around with. You can use the following steps to get a token for your user using your email/password pair. The token can then be used to call all GQL and [REST](rest-api.md) endpoints.

This involves two steps:

* [Pass in email/password to get a short-lived \(&lt; 10 mins\), **Authorization Code**](authentication-and-authorization.md#email-password-greater-than-authorization-code).
* [Exchange **Authorization Code** for **Authentication Token**.](authentication-and-authorization.md#authorization-code-greater-than-authentication-token)

Note that neither step is optional. You can't make any calls with the **Authorization Code** apart from exchanging it for the **Authentication Token** which you can then use for other API calls.

{% api-method method="post" host="https://api.sentiance.com" path="/auth/local" %}
{% api-method-summary %}
Email/Password --&gt; Authorization Code
{% endapi-method-summary %}

{% api-method-description %}
Pass in the email/user pair for a short-lived **Authorization Code**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="username" type="string" required=true %}
The email you signed up with.
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
Your password.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "user": "5ca289e00000000000000000",
    "authorization_code": "277378a4aa719a24d173e4d71d5f962561c95b9e67a0eee79f5f85b699422165f66d989ebf2fb195f4b7de026663aa8743d04b34fb313c33138c"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.sentiance.com" path="/auth/token" %}
{% api-method-summary %}
Authorization Code --&gt; Authentication Token
{% endapi-method-summary %}

{% api-method-description %}
Exchange authorization code for a longer-lived **Authentication Token**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
Set this to "code".
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=true %}
Place here the authorization code retrieved in the previous call.
{% endapi-method-parameter %}

{% api-method-parameter name="token\_type" type="string" required=true %}
Set this to "manage".
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
You will get back a short-lived token authentication token and a refresh token. The refresh token can be used to retrieve a new authentication token.
{% endapi-method-response-example-description %}

```javascript
{
    "id": "8ccbed3b-87b2-a71f-05f680ccb1dd",
    "user_id": "5a97cc743992560500000008",
    "token": "e2580b3dfd7c8a36d10e61a82a3ff7d3c198a22d9c7aabe44774847ba566ef02083e861632ca913b3990293eeb0c4779194c304c9982786470b08",
    "refresh_token": "506fe2ee2217d263bea480ad9a0711f3f4febbcf04ae86025bddabd0de008df65020bfeb24c4a0974668ad33729b0cc3bb0053de",
    "expires_at": "2019-04-02T13:22:22.508Z",
    "token_type": "self",
    "updated_at": "2019-04-02T09:22:22.508Z",
    "created_at": "2019-04-02T09:22:22.508Z",
    "app_id": "00000000000000000000000a"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Your token may expire after an unspecified period of time. When that happens you can use the refresh token received in the previous API call to get a new **Authentication Token**.

{% api-method method="post" host="https://api.sentiance.com" path="/auth/token" %}
{% api-method-summary %}
Token Refresh
{% endapi-method-summary %}

{% api-method-description %}
Used to refresh an authentication token. You may have noticed this is same endpoint as the Code Exchange, but the _grant\_type_ has a different value.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
Set this to "refresh\_token"
{% endapi-method-parameter %}

{% api-method-parameter name="refresh\_token" type="string" required=true %}
Set here the refresh token received during a Code Exchange or a previous Token Refresh call.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
This will return a new auth token/refresh token pair.
{% endapi-method-response-example-description %}

```
{
    "id": "8ccbed3b-87b2-a71f-05f680ccb1dd",
    "user_id": "5a97cc743992560500000008",
    "token": "e2580b3dfd7c8a36d10e61a82a3ff7d3c198a22d9c7aabe44774847ba566ef02083e861632ca913b3990293eeb0c4779194c304c9982786470b08",
    "refresh_token": "506fe2ee2217d263bea480ad9a0711f3f4febbcf04ae86025bddabd0de008df65020bfeb24c4a0974668ad33729b0cc3bb0053de",
    "expires_at": "2019-04-02T13:22:22.508Z",
    "token_type": "self",
    "updated_at": "2019-04-02T09:22:22.508Z",
    "created_at": "2019-04-02T09:22:22.508Z",
    "app_id": "00000000000000000000000a"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

