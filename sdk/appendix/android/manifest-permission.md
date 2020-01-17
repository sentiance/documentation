# Manifest Permissions

The gradle build system will merge the following Sentiance SDK permissions during the process of generating the final application manifest.

* android.permission.INTERNET
* android.permission.WAKE\_LOCK
* android.permission.ACCESS\_WIFI\_STATE
* android.permission.ACCESS\_NETWORK\_STATE
* android.permission.ACCESS\_FINE\_LOCATION
* android.permission.RECEIVE\_BOOT\_COMPLETED
* android.permission.WRITE\_EXTERNAL\_STORAGE \(api level 18 and lower\)
* android.permission.FOREGROUND\_SERVICE
* android.permission.READ\_PHONE\_STATE \(api level 22 and lower\)
* com.google.android.gms.permission.ACTIVITY\_RECOGNITION

