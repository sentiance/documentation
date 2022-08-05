# SDK Initialization

## What Does Initialization Do?

If a Sentiance user has not yet been created on the device, initialization simply sets up internal SDK components to make it possible to create a user at a later time.

If a Sentiance user is already present on the device, during initialization, the SDK constructs all the components that are necessary to do detections, networking, and maintenance work. Moreover, if detections were previously enabled, initialization will resume these detections in the background, without requiring app intervention.

## Why Initialize in the Application / AppDelegate Class?

During initialization, aside from of setting up internal components, the SDK sets the necessary delegates and listeners at the OS level, to allow the capturing of OS generated events, such as geofence exits, significant location changes, and visits.

When such events are detected, if your app is not alive, the OS starts it up in the background, and waits for your app to set up the necessary delegates and listeners during the _startup phase_, before delivering the events. In order to not miss such events, the SDK has to have its delegates and listeners set up during this startup phase too. This is the reason why the SDK must be initialized during app startup.

{% hint style="info" %}
On iOS, during initialization, in addition to setting up delegates, the SDK registers its own background processing tasks with the OS. It is vital that the registration happens during the startup phase, otherwise the tasks will not run.
{% endhint %}

On iOS, the startup phase ends when `application(_:didFinishLaunchingWithOptions:)` __ returns. On Android, it ends when `Application.onCreate()` returns.

Keep in mind that the app startup logic runs on the main thread. If you offload the SDK initialization to a background thread, even during the app's startup phase, there is no way to guarantee that the SDK initialization will happen before the startup phase ends. Therefore, it is important to do the initialization without branching off to a different thread. We have designed the initialization to be as quick as possible, in order to not delay your app's startup.

## Initialize On Every Startup, Once

You must initialize the SDK on every app startup. In most cases, you need to initialize it only once during the lifetime of the app process. Subsequent initialization requests will fail, unless you have reset the SDK.

Technically, you can keep initializing the SDK as long as there is no Sentiance user, for example, to overwrite the Sentiance options that you had passed to the initializer. But once a Sentiance user is created, subsequent initializations during the same lifetime of the app will fail.

To check whether the SDK has been initialized, check the `initState` property of the `Sentiance` class..
