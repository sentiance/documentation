# 3. Initialization

Initialization is a very important step; before initialization, almost none of the methods on the Sentiance SDK interface are allowed to be called \(with the exception of [`getInstance()`](../../api-reference/android/sentiance.md#getinitstate), [`init()`](../../api-reference/android/sentiance.md#init) and [`getInitState()`](../../api-reference/android/sentiance.md#getinitstate)\).

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

{% code-tabs %}
{% code-tabs-item title="MyApplication.java" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

Upon successful initialization, [`onInitSuccess()`](../../api-reference/android/oninitcallback/#oninitsuccess) will be called. If it fails, [`onInitFailure()`](../../api-reference/android/oninitcallback/#oninitfailure) will be called with an appropriate [`InitIssue`](../../api-reference/android/oninitcallback/initissue.md).

To learn more about initialization, see the [SDK Initialization](../../appendix/sdk-initialization.md) section.

