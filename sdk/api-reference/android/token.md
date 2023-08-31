# Token

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

A token can be used to communicate with the [Sentiance API](https://developers.sentiance.com/docs/rest).

## Token API

### `getExpiryDate()`

> ```java
> Date getExpiryDate()
> ```
>
> Returns a [`Date`](https://developer.android.com/reference/java/util/Date) object indicating the token expiry date.&#x20;
>
> The SDK will always attempt to return a valid token, granted proper network connectivity exists to allow token refresh.

### `getTokenId()`

> ```java
> String getTokenId()
> ```
>
> Returns the token ID.

### `isExpired()`

> ```java
> boolean isExpired()
> ```
>
> Returns true if the token is expired.

### `setExpiryDate()`

> ```java
> void setExpiryDate(Date expiryDate)
> ```
>
> Sets the token expiryDate

| Parameters |                                                                                                             |
| ---------- | ----------------------------------------------------------------------------------------------------------- |
| expiryDate | A [`Date`](https://developer.android.com/reference/java/util/Date) object indicating the token expiry date. |

### `setTokenId()`

> ```java
> void setTokenId(String tokenId)
> ```
>
> Sets the token ID.

| Parameters |               |
| ---------- | ------------- |
| tokenId    | The token ID. |
