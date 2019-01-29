# Token

A token can be used to communicate with the [Sentiance API](https://developers.sentiance.com/docs/rest).

## Token API

|  |  |
| :--- | :--- |
| String | [getTokenId](token.md#gettokenid) \(\) |
| void | [setTokenId](token.md#settokenid) \(String tokenId\) |
| [Date](https://developer.android.com/reference/java/util/Date) | [getExpiryDate](token.md#getexpirydate) \(\) |
| void | [setExpiryDate](token.md#setexpirydate) \([Date](https://developer.android.com/reference/java/util/Date) expiryDate\) |



### `getTokenId()`

> ```java
> String getTokenId()
> ```
>
> Returns the token ID.

### `setTokenId()`

> ```java
> void setTokenId(String tokenId)
> ```
>
> Sets the token ID.
>
> | Parameters |  |
> | :--- | :--- |
> | tokenId | The token ID. |

### `getExpiryDate()`

> ```java
> Date getExpiryDate()
> ```
>
> Returns a [`Date`](https://developer.android.com/reference/java/util/Date) object indicating the token expiry date. 
>
> The SDK will always attempt to return a valid token, granted proper network connectivity exists to allow token refresh.

### `setExpiryDate()`

> ```java
> void setExpiryDate(Date expiryDate)
> ```
>
> Sets the token expiryDate
>
> | Parameters |  |
> | :--- | :--- |
> | expiryDate | A [`Date`](https://developer.android.com/reference/java/util/Date) object indicating the token expiry date. |

