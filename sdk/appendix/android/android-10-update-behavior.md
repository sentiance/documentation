# Android 10 Update Behavior

If you are still targeting API level 28 or lower, please note that the permission behaviour described in the Android documentation can be misleading.

Android 10 looks into both your app's target API level and the presence of manifest permissions to determine if your app can be auto-granted some permissions. The presence of any of the new background location and activity recognition permissions in your app's manifest \(either directly or indirectly via a dependency, such as the Sentiance SDK\), will disable the auto-grant feature. That is why the Sentiance SDK does not add these permissions to your manifest. You must therefore add them once you decide to target API level 29+.

## Background Location Permission

<table>
  <thead>
    <tr>
      <th style="text-align:left">Target API</th>
      <th style="text-align:left">Was Already Granted?</th>
      <th style="text-align:left">Manifest Permissions</th>
      <th style="text-align:left">Location Access on Android 10</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">28</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left">ACCESS_FINE_LOCATION</td>
      <td style="text-align:left">No access</td>
    </tr>
    <tr>
      <td style="text-align:left">28</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">ACCESS_FINE_LOCATION</td>
      <td style="text-align:left">Foreground &amp; background</td>
    </tr>
    <tr>
      <td style="text-align:left">28</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">
        <p>ACCESS_FINE_LOCATION</p>
        <p>ACCESS_BACKGROUND_LOCATION</p>
      </td>
      <td style="text-align:left"><b>Foreground access only</b>
      </td>
    </tr>
  </tbody>
</table>The [Android documentation](https://developer.android.com/about/versions/10/privacy/changes#access_when_device_is_upgraded_to) is missing the last scenario, where the background location permission is included in the app's manifest, despite targeting API level 28. In this case, background location access will not be auto-granted.

## Activity Recognition Permission

<table>
  <thead>
    <tr>
      <th style="text-align:left">Target API</th>
      <th style="text-align:left">Manifest Permissions</th>
      <th style="text-align:left">Activity Recognition Access on Android 10</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">28</td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">No</td>
    </tr>
    <tr>
      <td style="text-align:left">28</td>
      <td style="text-align:left">com.google.android.gms.permission.ACTIVITY_RECOGNITION</td>
      <td style="text-align:left">Yes</td>
    </tr>
    <tr>
      <td style="text-align:left">28</td>
      <td style="text-align:left">
        <p>com.google.android.gms.permission.ACTIVITY_RECOGNITION</p>
        <p>android.permission.ACTIVITY_RECOGNITION</p>
      </td>
      <td style="text-align:left"><b>No</b>
      </td>
    </tr>
  </tbody>
</table>The [Android documentation](https://developer.android.com/about/versions/10/privacy/changes#physical-activity-recognition) does not mention the last scenario, where the new activity recognition permission is included in the app's manifest, despite targeting API level 28. In this case, activity recognition access is not granted.

