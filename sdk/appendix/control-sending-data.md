# Control Sending Data

The Sentiance SDK optimizes under which circumstances data submission occurs, to optimize network and battery usage.

For certain users with specific usage patterns (e.g. someone who rarely connects to Wi-Fi), it could take a long time before detections are finally submitted.

If you want to override the default behavior, you can initiate a forced submission of detections. Ideally, you use this method only after explaining to the user that your app will consume more bandwidth in case the device is not connected to Wi-Fi.

In order to know when it makes sense to do this, you can check the disk, mobile network and WiFi quotas of the [`SdkStatus`](../api-reference/android/sdkstatus/) and [`SENTSdkStatus`](broken-reference) objects.

{% tabs %}
{% tab title="iOS" %}
```objectivec
Sentiance.shared.submitDetections { result, error in 
    guard let result = result else {
        // Error
        print("Error: \(error!.failureReason)")
        return 
    }
    
    // Successfully submitted
}
```
{% endtab %}

{% tab title="Android" %}
```kotlin
sentiance.submitDetections().addOnCompleteListener { operation ->
    if (operation.isSuccessful) {
        Log.d(TAG, "Detections submitted successfully.")
    } els
        val error = operation.error
        Log.e(TAG, "submitDetections failed with reason ${error.reason.name}.")
    }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
[SubmitDetectionsResult](../api-reference/android/submitdetectionsresult.md) is an empty object at this time. A non-nil result object signifies successful submission.
{% endhint %}

