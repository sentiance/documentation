# Vehicle Crash Detection

## App Integration

Follow the below steps to set up vehicle crash detection in you app.

### 1. Integrate the Sentiance SDK

If you haven't already integrated the Sentiance SDK, follow the steps in our [Getting Started](../sdk/getting-started/) guide to complete the integration. Once you have completed those steps, continue along with the steps documented below.

### 2. Check if Vehicle Crash Detection Is Supported

There are several reasons why vehicle crash detection may not be supported on the device. The two most common of these are:

* the feature is not enabled for your app;
* the device lacks the necessary sensors \(e.g. accelerometer\).

You can check to see whether vehicle crash detection is support on the device, as follows.

{% tabs %}
{% tab title="Android" %}
```java
Sentiance.getInstance(context).isVehicleCrashDetectionSupported(TripType.SDK_TRIP);
```
{% endtab %}

{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] isVehicleCrashDetectionSupported:SENTTripTypeSDK];
```
{% endtab %}
{% endtabs %}

As the Sentiance SDK supports both [automatic detections and manual trips](../sdk/appendix/controlled-detections/automatic-detections-with-forced-trips.md) \(i.e. explicitly starting and stopping a trip\), the availability of vehicle crash detection is also controlled at the level of the trip type. In the above example, we pass a trip type of `SDK_TRIP` or `SENTTripTypeSDK` to check if the feature is available for automatic trips. To check if it's available for manually started trips, pass `EXTERNAL_TRIP` or `SENTTripTypeExternal` instead.

### 3. Subscribe for Vehicle Crash Events

In order to be notified of vehicle crash events, you must set a listener that the SDK can invoke whenever it detects vehicle crashes.

{% tabs %}
{% tab title="Android" %}
```java
Sentiance.getInstance(context).setVehicleCrashListener(new VehicleCrashListener() {
    @Override
    public void onVehicleCrash(VehicleCrashEvent crashEvent) {
        // Handle the vehicle crash event
        
        long epochTimeMs = crashEvent.getTime();
        Location location = crashEvent.getLocation();
        Float speedAtImpact = crashEvent.getSpeedAtImpact();
        Float magnitude = crashEvent.getMagnitude();
        Float deltaV = crashEvent.getDeltaV();
        Integer confidence = crashEvent.getConfidence();
    }
});
```
{% endtab %}

{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] setVehicleCrashHandler:^(SENTVehicleCrashEvent *crashEvent) {
    // Handle the vehicle crash event
    
    NSDate *date = crashEvent.date;
    CLLocation *location = crashEvent.location;
    Float32 speedAtImpact = crashEvent.speedAtImpact;
    Float32 magnitude = crashEvent.magnitude;
    Float32 deltaV = crashEvent.deltaV;
    NSInteger confidence = crashEvent.confidence;
}];
```
{% endtab %}
{% endtabs %}

The crash event contains the time and location of the detected crash, in addition to a number of metrics to estimate the severity of the crash.

### 4. Test Your Integration

The final step is checking your integration, to make sure that your vehicle crash listener is properly set up to handle crash events. Add the following method call in your app to trigger a dummy crash event.

{% tabs %}
{% tab title="Android" %}
```java
Sentiance.getInstance(context).invokeDummyVehicleCrash();
```
{% endtab %}

{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] invokeDummyVehicleCrashHandler];
```
{% endtab %}
{% endtabs %}

This should invoke a dummy crash event, passing it to the listener that you previously set. You can then test how your app handles the event at runtime.

