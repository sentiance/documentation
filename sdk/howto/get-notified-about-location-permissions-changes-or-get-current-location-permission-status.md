# Check the Location Permissions

#### To get **current** location permission status you should use public method getSdkStatus\([iOS](../api-reference/ios/sentsdk/#getsdkstatus) / [Android](../api-reference/android/sentiance.md#getsdkstatus)\)

{% tabs %}
{% tab title="iOS" %}
```objectivec
SENTSDKStatus *currentStatus = [[SENTSDK sharedInstance] getSdkStatus];
if(currentStatus.isLocationPermGranted) {
	//We are good!
} else {
	//Permission denied
}
```
{% endtab %}

{% tab title="Android" %}
```java
SdkStatus currentStatus = Sentiance.getInstance(context).getSdkStatus();
if(currentStatus.isLocationPermGranted) {
	//We are good!
} else {
	//Permission denied
}
```
{% endtab %}
{% endtabs %}

In example above it returning status \([iOS](../api-reference/ios/sentsdk/sentsdkstatus.md) / [Android](../api-reference/android/sdkstatus/)\) which have property isLocationPermGranted showing does Sentiance SDK have enough permission right to start tracking.

{% hint style="info" %}
iOS - Currently application should have “Always” location permission to run SDK.
{% endhint %}

With the list of all other statuses like is Sentiance SDK is running or not you can get for iOS [**here**](../api-reference/ios/sentsdk/sentsdkstatus.md) and Android [**here**](../api-reference/android/sdkstatus/).

#### To be notified about changes in statuses. It will be permission, quotas, start status or other you should set a listener during creating Config class like this:

{% tabs %}
{% tab title="iOS" %}
```objectivec
conf.didReceiveSdkStatusUpdate = ^(SENTSDKStatus *status) {
	if(status.isLocationPermGranted) {
		//We are good!
	} else {
		//Permission denied
	}
};
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
```
{% endtab %}
{% endtabs %}

where callback will be called every time status change is detected.

#### Example code to set status listener:

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

