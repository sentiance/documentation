# UserCreationOptions.Builder

Builder class for UserCreationOptions.

## UserCreationOptions.Builder API

### `Builder(String)`

> ```java
> Builder(String authenticationCode)
> ```
>
> The supplied authentication code is used to find the app user to link to during the user creation process. Therefore, before calling this method, make sure that you have obtained a valid code from the backend Sentiance API. This code request is authenticated using a Sentiance API key, which must never be transmitted to the app. Hence why the request must come from your backend.
>
> Here are the complete steps:
>
> * Initiate an authentication code request via your backend towards the Sentiance backend. This request will include your app's user identifier, which will be temporarily coupled to the code that you will receive.
> * Retrieve the code in your app and supply it to this constructor.
> * Build and pass a UserCreationOptions object containing this code to `Sentiance#createUser(UserCreationOptions)`, to create a linked user.
>
> If the authentication code references an app user that exists on the Sentiance platform (i.e. an app user identifier that was previously supplied to Sentiance), its corresponding Sentiance user will be restored on this device. Any other SDK instance with this user will then get disabled.

| Parameters         |                                                 |
| ------------------ | ----------------------------------------------- |
| authenticationCode | A code obtained from the backend Sentiance API. |

### `Builder(String, String, UserLinkerAsync)`

> ```java
> Builder(String appId, String secret, UserLinkerAsync linker) 
> ```
>
> Accepts Sentiance app credentials and a linker, to create a linked Sentiance user.
>
> During the user creation process, the SDK will call the link method of the supplied [`UserLinkerAsync`](../userlinkerasync.md), and will pass to it an installation ID. Your app must then forward this installation ID to the Sentiance backend (via your backend), and initiate user linking. Finally, when the linking completes, you must invoke the proper linker callback to complete the process.
>
> Here are the complete steps:&#x20;
>
> * Call this constructor and supply your Sentiance app credentials and a linker.
> * Your linker will be invoked during the user creation process, and an installation ID will be supplied.&#x20;
> * In your linker, forward the installation ID to your backend to initiate a linking request towards the Sentiance backend. This request will include the installation ID and your app's user identifier.
> * Retrieve the response from the Sentiance backend and forward the result to the app.
> * Based on the result, invoke the linker callback's success or failure method. The callback is supplied to your linker along with the installation ID.
> * If it was successful, the SDK will confirm the result with the Sentiance backend to complete the user creation.

| Parameters |                                                                                   |
| ---------- | --------------------------------------------------------------------------------- |
| appId      | Sentiance app ID.                                                                 |
| secret     | Sentiance app secret.                                                             |
| linker     | A [linker](../userlinkerasync.md) which will be invoked to initiate user linking. |

### `Builder(String, String, UserLinker)`

> ```java
> Builder(String appId, String secret, UserLinker linker)
> ```
>
>
>
> Accepts Sentiance app credentials and a linker, to create a linked Sentiance user.
>
> During the user creation process, the SDK will call the link method of the supplied [`UserLinker`](../userlinker.md), and will pass to it an installation ID. Your app must then forward this installation ID to the Sentiance backend (via your backend), and initiate user linking. you must return a proper result to complete the process.
>
> Here are the complete steps:&#x20;
>
> * Call this constructor and supply your Sentiance app credentials and a linker.
> * Your linker will be invoked during the user creation process, and an installation ID will be supplied.&#x20;
> * In your linker, forward the installation ID to your backend to initiate a linking request towards the Sentiance backend. This request will include the installation ID and your app's user identifier.
> * Retrieve the response from the Sentiance backend and forward the result to the app.
> * In your linker, return `true` if the result was successful, and otherwise return `false`.
> * If it was successful, the SDK will confirm the result with the Sentiance backend to complete the user creation.

| Parameters |                                                                              |
| ---------- | ---------------------------------------------------------------------------- |
| appId      | Sentiance app ID.                                                            |
| secret     | Sentiance app secret.                                                        |
| linker     | A [linker](../userlinker.md) which will be invoked to initiate user linking. |

### `setPlatformUrl`

> ```java
> Builder setPlatformUrl(String url)
> ```
>
> Sets the Sentiance Platform URL.

| Parameters |                                   |
| ---------- | --------------------------------- |
| url        | Platform URL for creating a user. |

### `build()`

> ```java
> UserCreationOptions build()
> ```
>
> Builds an [`UserCreationOptions`](./) object.
