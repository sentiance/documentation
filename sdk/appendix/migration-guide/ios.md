# iOS

## Migrating from 4.6.x to 5.x

### Updating compiler build settings

1\. Go to the **Build Settings** tab of your target settings \
2\. Look for **Other Linker Flags** in the **Linking** section. \
3\. Add `-lc++` flag

### Include the SDK bundle in your project

1\. Go to the **Build Phases** tab of your target settings \
2\. Expand the **Copy Bundle Resources** row and click the `+` button \
3\. Choose the `SENTSDK.bundle` file located inside `SENTSDK.framework`

### Permission message

Make sure a value for the key `NSLocationAlwaysAndWhenInUseUsageDescription`has been added to the **Info.plist**

### Sentiance SDK import update

Replace `#import <SENTTransportDetectionSDK/SENTTransportDetectionSDK.h>` to `@import SENTSDK;` in the import section

### CoreData import

Make sure you have added `CoreData` library as linked framework in your Xcode project

### User access token API change

If you need to get the user access token, change the callback to NSString as in example below:

```objectivec
NSString* userId = [[SENTSDK sharedInstance] getUserId];
[[SENTSDK sharedInstance] getUserAccessToken:^(SENTToken *token) {
    NSString* accessToken = [token tokenId];
} failure:^{

}];
```

Replace the code above with the code below:

```objectivec
NSString* userId = [[SENTSDK sharedInstance] getUserId];
[[SENTSDK sharedInstance] getUserAccessToken:^(NSString *token) {
    NSString* accessToken = token;
} failure:^{

}];
```

### SDK Control

The `stopAfter(seconds)` method is no longer available.

### User Metadata

User metadata methods no longer accept a `success/failure` block parameter. Adding and removing metadata is now done asynchronously via the payload submission system.

### External Events

Registering external events is no longer available.

### Trip Control

#### Starting and Stopping Trips

`startTrip()` and `stopTrip()` methods now require a `success` and `failure(sdkStatus)` block parameters respectively.

#### Trip Details

The SDK no longer returns a `Trip` object when a trip is stopped. The `setTripTimeOutListener()` callback of the SDK no longer returns a `Trip` object.

#### Checking Ongoing Trips

The `isTripOngoing()` method now expects a parameter of type `TripType`.

### Other

`getWiFiLastSeenTimestamp()` is no longer available.
