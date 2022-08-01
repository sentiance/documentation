# SENTUserCreationOptions

### SENTUserCreationOptions

Wrapper class for the user creation parameters including the credentials and the linker object.



### appId

Sentiance app ID that should be used when creating a user. Returns nil if it wasn't set.

```
@property (nonatomic, copy, nullable) NSString *appId;
```



### secret

Sentiance app secret that should be used when creating a user. Returns nil if it wasn't set.

```
@property (nonatomic, copy, nullable) NSString *secret;
```



### authCode

Authentication code that should be used when creating a user. Returns nil if it wasn't set.

```
@property (nonatomic, copy, nullable) NSString *authCode;
```



### linker

User linker that should be invoked during the user creation process. Returns nil if it wasn't set.

```
@property (nonatomic, strong, nullable) SENTUserLinker linker;
```



### platformUrl

Sentiance platform URL.

```
@property (nonatomic, copy, nullable) NSString *platformUrl;
```

###

### initWithAppId: secret: linker:

Accepts Sentiance app credentials and a linker, to create a linked Sentiance user.



During the user creation process, the SDK will call the link method of the supplied SENTUserLinker, and will pass to it an installation ID. Your app must then forward this installation ID to the Sentiance backend (via your backend), and initiate user linking. Finally, when the linking completes, you must invoke the proper linker callback to complete the process.

&#x20;Here are the complete steps:

&#x20;1\. Call this constructor and supply your Sentiance app credentials and a linker. Your linker will be invoked during the user creation process, and an installation ID will be supplied.

&#x20;2\. In your linker, forward the installation ID to your backend to initiate a linking request towards the Sentiance backend. This request will include the installation ID and your app's user identifier.

&#x20;3\. Retrieve the response from the Sentiance backend and forward the result to the app.

&#x20;4\. Based on the result, invoke the linker callback's success or failure method. The callback is supplied to your linker along with the installation ID. If it was successful, the SDK will confirm the result with the Sentiance backend to complete the user creation.

```objectivec
- (instancetype)initWithAppId:(NSString *)appId secret:(NSString *)secret linker:(SENTUserLinker)linker;
```

| Parameter  | Description                             |
| ---------- | --------------------------------------- |
| **appId**  | Your Sentiance App Id                   |
| **secret** | Your Sentiance App secret               |
| **linker** | Linker invoked to initiate user linking |



### initWithAuthenticationCode:

Accepts an authentication code, which will be used to create a linked Sentiance user.

&#x20;The supplied authentication code is used to find the app user to link to during the user creation process. Therefore, before calling this method, make sure that you have obtained a valid code from the backend Sentiance API. This code request is authenticated using a Sentiance API key, which must never be transmitted to the app. Hence why the request must come from your backend.

&#x20;Here are the complete steps:

&#x20;1\. Initiate an authentication code request via your backend towards the Sentiance backend. This request will include your app's user identifier, which will be temporarily coupled to the code that you will receive.

&#x20;2\. Retrieve the code in your app and supply it to this constructor.

&#x20;3\. Build and pass a SENTUserCreationOptions object containing this code to createUserWithOptions: completionHandler: to create a linked user. If the authentication code references an app user that exists on the Sentiance platform (i.e. an app user identifier that was previously supplied to Sentiance), its corresponding Sentiance user will be restored on this device. Any other SDK instance with this user will then get disabled.



```objectivec
- (instancetype)initWithAuthenticationCode:(NSString *)authenticationCode;
```

| Parameter              | Description                                    |
| ---------------------- | ---------------------------------------------- |
| **authenticationCode** | a code obtained from the backend Sentiance API |
