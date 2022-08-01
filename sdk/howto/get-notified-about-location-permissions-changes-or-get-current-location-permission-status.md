# Check the Location Permissions

To get current location permission status, use the `getSdkStatus` method ([iOS](../api-reference/ios/sentiance.md#getsdkstatus) / [Android](broken-reference)).

{% tabs %}
{% tab title="iOS" %}
```objectivec
SENTSDKStatus *currentStatus = [[SENTSDK sharedInstance] getSdkStatus];
if(currentStatus.isLocationPermGranted) {
	// We are good!
} else {
	// Permission denied
}
```
{% endtab %}

{% tab title="Android" %}
```java
SdkStatus currentStatus = Sentiance.getInstance(context).getSdkStatus();
if(currentStatus.isLocationPermGranted) {
	// We are good!
} else {
	// Permission denied
}
```
{% endtab %}
{% endtabs %}

In the above example, `getSdkStatus` returns an SDK status object ([iOS](../api-reference/ios/sentsdkstatus.md) / [Android](../api-reference/android/sdkstatus/)) which has an `isLocationPermGranted` field, indicating if the correct permission has been granted by the user to allow SDK detections.

{% hint style="info" %}
The user must grant the background location access permission in order for SDK detections to work. This is presented as the "**always**" option on iOS and the "**allow all the time**" option on Android 10+.
{% endhint %}

To be notified of SDK status changes such as permission changes, quota updates, and the detection or SDK start status, you can set up an SDK status listener on the SDK's config object as follows:&#x20;

{% tabs %}
{% tab title="iOS" %}
```objectivec
SENTConfig *conf = [[SENTConfig alloc] initWithAppId:APPID
secret:SECRET launchOptions:launchOptions];

conf.didReceiveSdkStatusUpdate = ^(SENTSDKStatus *status) {
	if(status.isLocationPermGranted) {
		//We are good!
	} else {
		//Permission denied
	}
};

[[SENTSDK sharedInstance] initWithConfig:conf
success:^{
	// SDK init success.
	// Start SDK here
} failure:^(SENTInitIssue issue) {
	//SDK Failed to init
}];
```
{% endtab %}

{% tab title="Android" %}
```java
SdkConfig config = new SdkConfig.Builder(appId, secret, notification)
        .setOnSdkStatusUpdateHandler(new OnSdkStatusUpdateHandler() {
            @Override
            public void onSdkStatusUpdate (SdkStatus status) {
                if (status.isLocationPermGranted) {
                    //We are good!
                } else {
                   //Permission denied 
                }
            }
        })
        .build();
                
// Initialize the Sentiance SDK.
Sentiance.getInstance(this).init(config, this);
```
{% endtab %}
{% endtabs %}
