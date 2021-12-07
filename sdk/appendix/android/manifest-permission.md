# Manifest Permissions

The gradle build system will merge the following Sentiance SDK permissions during the process of generating the final application manifest.

* android.permission.INTERNET
* android.permission.WAKE\_LOCK
* android.permission.ACCESS\_WIFI\_STATE
* android.permission.ACCESS\_NETWORK\_STATE
* android.permission.ACCESS\_COARSE\_LOCATION
* android.permission.ACCESS\_FINE\_LOCATION
* android.permission.RECEIVE\_BOOT\_COMPLETED
* android.permission.FOREGROUND\_SERVICE
* android.permission.HIGH\_SAMPLING\_RATE\_SENSORS
* android.permission.SCHEDULE\_EXACT\_ALARM
* com.google.android.gms.permission.ACTIVITY\_RECOGNITION

{% hint style="info" %}
After adding the Sentiance SDK, if you have a permission issue with `READ_PHONE_STATE` due to the API level restriction, please read [this troubleshooting guide](../../troubleshooting/android.md#permission-revoked-when-adding-the-sentiance-sdk) in order to resolve it.
{% endhint %}

