# TokenResultCallback

This interface is used with [`getUserAccessToken(TokenResultCallback)`](sentiance.md#submitdetections).

## TokenResultCallback API

|  |  |
| :--- | :--- |
| void | [onSuccess](tokenresultcallback.md#onsuccess) \([Token](token.md) token\) |
| void  | [onFailure](tokenresultcallback.md#onfailure) \(\) |



### `onSuccess()`

> ```java
> void onSuccess(Token token)
> ```
>
> Called when the Sentiance SDK has a working token \(either previously cached or newly obtained\).
>
> | Parameters |  |
> | :--- | :--- |
> | token | A [`Token`](token.md) object containing token ID and expiry date. |

### `onFailure()`

> ```java
> void onFailure()
> ```
>
> Called when a token could not be obtained. This can happen if both of the following conditions are met:
>
> * The token has expired,
> * there is no network connection that can be used to get a new token from the Sentiance API.

