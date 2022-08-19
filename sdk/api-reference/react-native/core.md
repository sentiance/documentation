# core

```javascript
import SentianceCore from "@sentiance-react-native/core";
```

You can find a reference to all the types mentioned on this page [here](https://github.com/sentiance/react-native-sentiance/blob/main/packages/core/lib/index.d.ts).

### Create a Sentiance user&#x20;

#### Using an Authentication Code (Recommended)

Refer to [this guide](../../appendix/user-creation.md) for documentation on user creation.

```javascript
// returns Promise<CreateUserResult>
const createUserResult = await SentianceCore.createUser({authCode});
```

#### With User Linking

Refer to [this guide](../../appendix/user-linking.md) for documentation on user linking.

```javascript
// returns Promise<CreateUserResult>
const createUserResult = await SentianceCore.createUser({
    appId, 
    appSecret, 
    platformUrl,
    linker: async (installId) => {
        // request your backend to perform user linking
        await linkUser(installId);

        // return true to indicate to the SDK that user linking on your 
        // backend was successful. return false otherwise.
        return true;
  }
});
```

> _If your backend was unable to link the user to the Sentiance platform, then `return false` instead to notify the SDK that the linking failed._

#### Without User Linking (Not Recommended)

Creates an unlinked (anonymous) Sentiance user.

```javascript
// returns Promise<CreateUserResult>
const createUserResult = await SentianceCore.createUser({
    appId, 
    appSecret, 
    platformUrl
});
```

### Link a Sentiance user on the device to a third party ID

Use this function to link an anonymous Sentiance user, which you've created by not specifying a user-linker, to your app's user.

#### Using an Authentication Code (Recommended)

```javascript
// returns Promise<UserLinkingResult>
const userLinkingResult = await SentianceCore.linkUser(authenticationCode);
```

#### Using a Linker

```javascript
// returns Promise<UserLinkingResult>
const userLinkingResult = await SentianceCore.linkUser(async (installId) => {
    // request your backend to perform user linking
    await linkUser(installId);
    
    // return true to indicate to the SDK that user linking on your 
    // backend was successful. return false otherwise.
    return true;
  }
);
```

### Enabling detections on the SDK

```javascript
// returns Promise<EnableDetectionsResult>
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

While it's possible to "pause" the detections of the Sentiance SDK's, it's not recommended, as it can lead to missed detections (e.g. trips).

```javascript
// returns Promise<DisableDetectionsResult>
const disableDetectionsResult = await SentianceCore.disableDetections();
```

### Init status

Checking if SDK is initialized

```javascript
// returns Promise<SdkInitState>
const initState = await SentianceCore.getInitState();
const isInitialized = initState == "INITIALIZED";
```

### SDK status

Getting the status of the SDK:

```javascript
// returns Promise<SdkStatus>
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

### Get the SDK version

```javascript
// returns Promise<string>
const version = await SentianceCore.getVersion();
```

### Get the user ID

If the SDK is initialized, you can get the user ID as follows. This user ID will allow you to interact with the APIs from Sentiance. You need a token and a user ID to authorize requests and query the right data.

```javascript
// returns Promise<string>
const userId = await SentianceCore.getUserId();
```

### Check if user exists on device

```javascript
// returns Promise<boolean>
const doesUserExist = await SentianceCore.userExists();
```

### Check if the current user is linked to a third party ID

```javascript
// returns Promise<boolean>
const isUserLinked = await SentianceCore.isUserLinked();
```

### Get the user access token

If the SDK is initialized, you can get a user access token as follows. This token will allow you to interact with the APIs from Sentiance. You need a token and a user ID to authorize requests and query the right data. If the token has expired, or will expire soon, the SDK will get a new bearer token before returning it. Generally, this operation will complete instantly by returning a cached bearer token, but if a new token has to be obtained from the Sentiance API, there is a possibility that it will fail.

```javascript
// returns Promise<UserAccessToken>
const userAccessToken = await SentianceCore.requestUserAccessToken();
```

### Adding custom metadata

Custom metadata allows you to store text-based key-value user properties on the Sentiance platform, such as application related properties, which you can then obtain when processing data offloads (generated by Sentiance).

```javascript
const label = "correlation_id";
const value = "3a5276ec-b2b2-4636-b893-eb9a9f014938";

// returns Promise<void>
await SentianceCore.addUserMetadataField(label, value);
```

### Remove custom metadata

You can remove previously added metadata fields by passing the metadata label to the removeUserMetadataField function.

```javascript
const label = "correlation_id";

// returns Promise<void>
await SentianceCore.removeUserMetadataField(label);
```

### Adding multiple custom metadata fields

You can add multiple custom metadata fields by passing an object to the addUserMetadataFields function.

```javascript
const metadata = { corrolation_id: "3a5276ec-b2b2-4636-b893-eb9a9f014938" };

// returns Promise<void>
await SentianceCore.addUserMetadataFields(metadata);
```

### Starting trip

When you call `startTrip` on the SDK, you override automatic SDK detections and force trip data collection, until you call `stopTrip`, or until the trip times out (only applicable to the triggered trip SDK flavor). `startTrip` accepts a metadata object and a transport mode hint (numeric) as parameters.

Transport mode hint:

```
export enum TransportMode {
    UNKNOWN = 1,
    CAR,
    BICYCLE,
    ON_FOOT,
    TRAIN,
    TRAM,
    BUS,
    PLANE,
    BOAT,
    METRO,
    RUNNING
}
```

Example:

```javascript
const metadata = { corrolation_id: "3a5276ec-b2b2-4636-b893-eb9a9f014938" };
const transportModeHint = 1;

try {
  // returns Promise<void>
  await SentianceCore.startTrip(metadata, transportModeHint);
  // Trip is started
} catch (err) {
  // Unable to start trip
}
```

### Stopping trip

```javascript
try {
  // returns Promise<void>
  const trip = await SentianceCore.stopTrip();
  // Stopped trip
} catch (err) {
  // Unable to stop trip
}
```

You can also receive trip timeout events:

```javascript
const subscription = SentianceCore.addTripTimeoutListener(() => {
  // Trip timeout event received
});

// Don't forget to unsubscribe, typically in componentWillUnmount
subscription.remove();
```

### Trip status

Checking an ongoing trip status:

```javascript
// returns Promise<boolean>
const isTripOngoing = await SentianceCore.isTripOngoing();
```

### Control sending data

If you want to override the default SDK data submission behavior, you can initiate a forced submission of detections. Ideally, you use this method only after explaining to the user that your app will consume more bandwidth in case the device is not connected to Wi-Fi.

```javascript
try {
  // returns Promise<void>
  await SentianceCore.submitDetections();
} catch (err) {
  // Something went wrong with submitting data, for more information, see the error variable
}
```

### Disk, mobile network and Wi-Fi quotas

The usage and limits of network and disk capacity in bytes can be obtained using the getWiFiQuotaUsage, getWiFiQuotaLimit and similar methods on the Sentiance SDK interface.

```javascript
// returns Promise<string>
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

To get the user's current activity:

```javascript
// returns Promise<UserActivity>
const userActivity = await SentianceCore.getUserActivity();
```

You can subscribe to receive user activity updates:

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

### Update the SDK foreground notification (ANDROID ONLY)

Updates the title and text of SDK notification. After calling this method, any notification shown by the SDK will be updated.

Note that this change is valid only during the process's lifetime. After the app process restarts, the SDK will display the default notification.

```javascript
// returns Promise<void>
await SentianceCore.updateSdkNotification("RN SDK Sample", "SDK is running");
```

### Resetting the SDK

To delete the Sentiance user and its data from the device, you can reset the SDK by calling `SentianceCore.reset()`. This allows you to create a new Sentiance user afterwards.

```javascript
try {
  // returns Promise<ResetResult>
  await SentianceCore.reset();
  // The SDK was successfully cleared and reset
} catch (err) {
  // Resetting the SDK failed
  // err.name has three values:
  // SDK_INIT_IN_PROGRESS, SDK_RESET_IN_PROGRESS, SDK_RESET_UNKNOWN_ERROR
}
```

### Enable/Disable app session data collection

When the app is foregrounded, the SDK may collect various sensor data for analytics purposes. You can enables or disable this. By default, it's disabled.

```javascript
// returns Promise<void>
await SentianceCore.setAppSessionDataCollectionEnabled(true);
```

### Check app session data collection status

```javascript
// returns Promise<boolean>
const isAppSessionDataCollectionEnabled = 
    await SentianceCore.isAppSessionDataCollectionEnabled();
```

### Disable battery optimization (Android)

```javascript
// returns Promise<void>
await SentianceCore.disableBatteryOptimization();
```
<!---
 testing comment
 -->
 