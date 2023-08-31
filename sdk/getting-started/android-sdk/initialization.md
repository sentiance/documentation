# 3. Initialization

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Initialization is a very important step; before initialization, none of the methods on the Sentiance SDK interface will work, with the exception of [`getInstance()`](../../api-reference/android/sentiance.md#getinitstate), [`init()`](../../api-reference/android/sentiance.md#init) and [`getInitState()`](../../api-reference/android/sentiance.md#getinitstate).

## Create an Application Class

Initialization [must be done](../../appendix/sdk-initialization.md#why-initialize-in-the-application-appdelegate-class) in the `onCreate()` method of your `Application` class. If you don't already have a custom application class, first create a new class that extends `Application`.

```java
import android.app.Application;
public class MyApplication extends Application {
    @Override
    public void onCreate() {
    }
}
```

Then reference this new class in the application tag of the `AndroidManifest.xml`

```java
<application android:name="com.example.appname.MyApplication">
  <!-- Activities -->
</application>
```

## Call the SDK init Method

In the `onCreate()` method of your `Application` class, call [`init()`](../../api-reference/android/sentiance.md#init) and pass the [`SdkConfig`](../../api-reference/android/sdkconfig/) you created in the previous step, plus an instance of [`OnInitCallback`](../../api-reference/android/oninitcallback/) to handle the initialization result. 

{% code title="MyApplication.java" %}
```java
@Override
public void onCreate() {
    // Creation of SdkConfig here, see previous step
    
    OnInitCallback initCallback = new OnInitCallback() {
        @Override
        public void onInitSuccess() {
        }
        @Override
        public void onInitFailure(InitIssue issue, @Nullable Throwable th) {
        }
    };
        
    Sentiance.getInstance(this).init(sdkConfig, initCallback);
}
```
{% endcode %}

Upon successful initialization, [`onInitSuccess()`](../../api-reference/android/oninitcallback/#oninitsuccess) will be called. If it fails, [`onInitFailure()`](../../api-reference/android/oninitcallback/#oninitfailure) will be called with an appropriate [`InitIssue`](../../api-reference/android/oninitcallback/initissue.md).

{% hint style="warning" %}
The [`init()`](../../api-reference/android/sentiance.md#init) call must be executed before `onCreate()` returns. Therefore, you must call it synchronously on the main thread. If you plan to add a remote flag to control the initialization \(e.g. Firebase Remote Config\), make sure the check is synchronous \(e.g. using a cached flag\).

See [here](../../appendix/sdk-initialization.md#why-initialize-in-the-application-appdelegate-class) to understand more about why this is important. An [example app](https://github.com/sentiance/sdk-starter-android-sdk-control/blob/master/app/src/main/java/com/sentiance/sdkstarter/MyApplication.java#L53) demonstrating this can be found on our [Github](https://github.com/sentiance/sdk-starter-android-sdk-control).
{% endhint %}

To learn more about initialization, see the [SDK Initialization](../../appendix/sdk-initialization.md) section.

