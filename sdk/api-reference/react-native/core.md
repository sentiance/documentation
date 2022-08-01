# core

```javascript
import SentianceCore from "@sentiance-react-native/core";
```

### Create a Sentiance user&#x20;

#### Without User Linking

```javascript
const createUserResult = await SentianceCore.createUser({
    appId, 
    appSecret, 
    platformUrl
});
```

#### With User Linking

_Please refer to_ [_this guide_](../../appendix/user-linking.md) _for documentation on the user linking._

```javascript
const createUserResult = await SentianceCore.createUser({
    appId, 
    appSecret, 
    platformUrl,
    linker: async (installId) => {
        // request your backend to perform user linking
        await linkUser(installId);

        // return true to indicate to the SDK that user linking on your backend was successful
        return true;
  }
});
```

> _If your backend was unable to link the user to the Sentiance platform, then `return false` instead to notify the SDK that the linking failed._

### Link a Sentiance user on the device to a third party ID

#### Using a linker

```javascript
const userLinkingResult = await SentianceCore.linkUser(async (installId) => {
        // request your backend to perform user linking
        await linkUser(installId);

        // return true to indicate to the SDK that user linking on your backend was successful
        return true;
  }
);
```

#### Using an authentication code

```javascript
const userLinkingResult = await SentianceCore.linkUser(authenticationCode);
```

### Enabling detections on the SDK

```javascript
const enableDetectionsResult = await SentianceCore.enableDetections();
console.log('SDK detection status is now ' + enableDetectionsResult.detectionStatus);
```

You can also enable detections while also setting a future expiry date for the detections to stop automatically:

```javascript
const expiryDate = Date.now() + 60 * 60 * 1000; // 1 hour from now
const enableDetectionsResult = await SentianceCore.enableDetectionsWithExpiryDate(expiryDate);
console.log('SDK detection status is now ' + enableDetectionsResult.detectionStatus);
```

### Disabling detections on the SDK

Stopping is only allowed after successful initialization. While it's possible to "pause" the detections modules of the Sentiance SDK's, it's not recommended.

```javascript
try {
  const disableDetectionsResult = await SentianceCore.disableDetections();
  // SDK stopped properly.
} catch (err) {
  // An error prevented the SDK from stopping correctly
}
```

### Init status

Checking if SDK is initialized

```javascript
const initState = await SentianceCore.getInitState();
const isInitialized = initState == "INITIALIZED";
```

### SDK status

The status of the Sentiance SDK

```javascript
const sdkStatus = await SentianceCore.getSdkStatus();
```

The SDK can signal SDK status updates to JavaScript without being invoked directly. You can subscribe to these status updates:

```javascript
const subscription = SentianceCore.addSdkStatusUpdateListener(sdkStatus => {
  // Access sdkStatus
});

// Don't forget to unsubscribe, typically in componentWillUnmount
subscription.remove();
```

### Get SDK version

```javascript
const version = await SentianceCore.getVersion();
```

### Get user id

If the SDK is initialized, you can get the user id as follows. This user id will allow you to interact with the API's from Sentiance. You need a token and user to authorize requests and query the right data.

```javascript
const userId = await SentianceCore.getUserId();
```

### Check if user exists on device

```javascript
const doesUserExist = await SentianceCore.userExists();
```

### Check if the current user is linked to a third party ID

```javascript
const isUserLinked = await SentianceCore.isUserLinked();
```

### Get user access token

If the SDK is initialized, you can get a user access token as follows. This token will allow you to interact with the API's from Sentiance. You need a token and user to authorize requests and query the right data. If the token has expired, or will expire soon, the SDK will get a new bearer token before passing it to the callback. Generally, this operation will complete instantly by returning a cached bearer token, but if a new token has to be obtained from the Sentiance API, there is a possibility it will fail.

```javascript
const userAccessToken = await SentianceCore.requestUserAccessToken();
```

### Adding custom metadata

Custom metadata allows you to store text-based key-value user properties into the Sentiance platform. Examples are custom user id's, application related properties you need after the processing, ...

```javascript
const label = "correlation_id";
const value = "3a5276ec-b2b2-4636-b893-eb9a9f014938";

await SentianceCore.addUserMetadataField(label, value);
```

### Remove custom metadata

You can remove previously added metadata fields by passing the metadata label to the removeUserMetadataField function.

```javascript
const label = "correlation_id";

await SentianceCore.removeUserMetadataField(label);
```

### Adding multiple custom metadata fields

You can add multiple custom metadata fields by passing an object to the addUserMetadataFields function.

```javascript
const metadata = { corrolation_id: "3a5276ec-b2b2-4636-b893-eb9a9f014938" };

await SentianceCore.addUserMetadataFields(metadata);
```

### Starting trip

Whenever you call startTrip on the SDK, you override moving state detection and the SDK will track the trip until you call stopTrip or until the timeout (2 hours) is reached. `startTrip` accepts a metadata object and a transport mode hint (`number`) as parameters.

Transport mode hint:

```
SENTTransportModeUnknown = 1,
SENTTransportModeCar = 2,
SENTTransportModeBicycle = 3,
SENTTransportModeOnFoot = 4,
SENTTransportModeTrain = 5,
SENTTransportModeTram = 6,
SENTTransportModeBus = 7,
SENTTransportModePlane = 8,
SENTTransportModeBoat = 9,
SENTTransportModeMetro = 10,
SENTTransportModeRunning = 11
```

Example:

```javascript
const metadata = { corrolation_id: "3a5276ec-b2b2-4636-b893-eb9a9f014938" };
const transportModeHint = 1;

try {
  await SentianceCore.startTrip(metadata, transportModeHint);
  // Trip is started
} catch (err) {
  // Unable to start trip
}
```

### Stopping trip

```javascript
try {
  const trip = await SentianceCore.stopTrip();
  // Stopped trip
} catch (err) {
  // Unable to stop trip
}
```

The SDK can also signal trip timeouts to JavaScript. You can subscribe to these trip timeouts:

```javascript
const subscription = SentianceCore.addTripTimeoutListener(() => {
  // Trip timeout event received
});

// Don't forget to unsubscribe, typically in componentWillUnmount
subscription.remove();
```

### Trip status

Checking trip status

```javascript
const isTripOngoing = await SentianceCore.isTripOngoing();
```

### Control sending data

If you want to override the default behavior, you can initiate a forced submission of detections. Ideally, you use this method only after explaining to the user that your app will consume more bandwidth in case the device is not connected to Wi-Fi.

```javascript
try {
  await SentianceCore.submitDetections();
} catch (err) {
  // Something went wrong with submitting data, for more information, see the error variable
}
```

### Disk, mobile network and Wi-Fi quotas

The actual usages and limits in bytes can be obtained using the getWiFiQuotaUsage, getWiFiQuotaLimit and similar methods on the Sentiance SDK interface.

```javascript
const limit = await SentianceCore.getWiFiQuotaLimit();
```

All quota functions:

* `getWiFiQuotaLimit`
* `getWiFiQuotaUsage`
* `getMobileQuotaLimit`
* `getMobileQuotaUsage`
* `getDiskQuotaLimit`
* `getDiskQuotaUsage`

### User Activity

Get user current activity

```javascript
const userActivity = await SentianceCore.getUserActivity();
```

The SDK can signal user activity updates to JavaScript without being invoked directly. You can subscribe to these user activity updates:

```javascript
const subscription = SentianceCore.addSdkUserActivityUpdateListener(userActivity => {
  // Handle user activity
});

// Don't forget to unsubscribe, typically in componentWillUnmount
subscription.remove();
```

Handling user activity:

```javascript
const { type, tripInfo, stationaryInfo } = userActivity;

if (type === "USER_ACTIVITY_TYPE_STATIONARY") {
  const { location } = stationaryInfo;

  if (location) {
    const { latitude, longitude } = location;
  }
  //..
} else if (type === "USER_ACTIVITY_TYPE_TRIP") {
  //..
} else if (type === "USER_ACTIVITY_TYPE_UNKNOWN") {
  //..
}
```

### Update SDK foreground notification (ANDROID ONLY)

Updates the title and text of SDK notification. After calling this method, any notification shown by the SDK will be updated.

Note that this change is valid only during the process's lifetime. After the app process restarts, the SDK will display the default notification.

```javascript
/** {string} title {string} message */
await SentianceCore.updateSdkNotification("RN SDK Sample", "SDK is running");
```

### Clearing/Resetting the SDK

To delete the Sentiance user and its data from the device, you can reset the SDK by calling `SentianceCore.reset()`. This allows you to create a new Sentiance user by reinitializing the SDK, and link it to a new third party ID.

```javascript
try {
  await SentianceCore.reset();
  // The SDK was successfully cleared and reset
} catch (err) {
  // Resetting the SDK failed
  // err.name has three values:
  // SDK_INIT_IN_PROGRESS, SDK_RESET_IN_PROGRESS, SDK_RESET_UNKNOWN_ERROR
}
```

### Enable/Disable app session data collection

Call `setAppSessionDataCollectionEnabled` and pass in a `boolean` to enable/disable app session data collection:

```javascript
await SentianceCore.setAppSessionDataCollectionEnabled(true);
```

### Check app session data collection status

```javascript
const isAppSessionDataCollectionEnabled = 
    await SentianceCore.isAppSessionDataCollectionEnabled();
```

### Disable battery optimization

```javascript
await SentianceCore.disableBatteryOptimization();
```
