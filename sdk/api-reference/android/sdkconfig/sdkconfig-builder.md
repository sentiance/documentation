# Builder

This class is used with [`Sentiance.init(SdkConfig, OnInitCallback)`](../sentiance.md#init).

## Builder API

| constructor |  |
| :--- | :--- |
| [Builder](sdkconfig-builder.md#builder) \(String appId, String secret, [Notification](https://developer.android.com/reference/android/app/Notification) notification\) |  |

|  |  |
| :--- | :--- |
| [SdkConfig](./) | [build](sdkconfig-builder.md#build) \(\) |
| [Builder](sdkconfig-builder.md) | [setMetaUserLinker](sdkconfig-builder.md#setmetauserlinker) \([MetaUserLinker](../metauserlinker.md) linker\) |
| [Builder](sdkconfig-builder.md) | [setNotificationId](sdkconfig-builder.md#setnotificationid) \(int id\) |
| [Builder](sdkconfig-builder.md) | [setOnSdkStatusUpdateHandler](sdkconfig-builder.md#setonsdkstatusupdatehandler) \([OnSdkStatusUpdateHandler](../onsdkstatusupdatehandler.md) handler\) |
| [Builder](sdkconfig-builder.md) | [setTriggeredTripsEnabled](sdkconfig-builder.md#settriggeredtripsenabled) \(boolean enabled\) |



### `Builder`

> ```java
> Builder(String appId, String secret, Notification notification)
> ```
>
> Creates a builder object used for initializing the Sentiance SDK.
>
> **Please note: hard-coded credentials are not secure. Load your Sentiance credentials from a secure source such a remote server, and store them securely on the device.**
>
> | Parameters |  |
> | :--- | :--- |
> | appId | The Sentiance app credential ID. |
> | secret | The Sentiance app credential secret. |
> | notification  | A [`Notification`](https://developer.android.com/reference/android/app/Notification) used by the SDK when starting a foreground service. |



### `build()`

> ```java
> SdkConfig build()
> ```
>
> Builds an [`SdkConfig`](./) object.
>
> | Parameters |  |
> | :--- | :--- |
> | id | The ID used when starting a foreground service. |

### `setMetaUserLinker`

> ```java
> Builder setMetaUserLinker(MetaUserLinker linker)
> ```
>
> Sentiance assigns to each user a unique ID. You can link your app's user to the Sentiance user using meta-user linking. The linking step involves server-to-server communication, and is triggered by the SDK via this meta-user linking callback.
>
> Learn more about Meta-User linking [here](../../../appendix/meta-users.md).
>
> | Parameters |  |
> | :--- | :--- |
> | linker | A [`MetaUserLinker`](../metauserlinker.md) which will handle the linking. |

### `setNotificationId`

> ```java
> Builder setNotificationId(int Id)
> ```
>
> The default notification ID used by the SDK when starting a service is **2123874432**. If your app already shows a persistent notification when running, you can pass your existing notification ID and have a single notification show up in the panel.
>
> | Parameters |  |
> | :--- | :--- |
> | id | The ID used when starting a foreground service. |

### `setOnSdkStatusUpdateHandler`

> ```java
> Builder setOnSdkStatusUpdateHandler(OnSdkStatusUpdateHandler handler)
> ```
>
> At runtime, the SDK will occasionally send status updates to your app. These are concerning the detection status and environment changes \(e.g. location availability, device configuration changes, etc.\). You can set a handler here to capture these updates.
>
> | Parameters |  |
> | :--- | :--- |
> | handler | The [`OnSdkStatusUpdateHandler`](../onsdkstatusupdatehandler.md) which will receive [`SdkStatus`](../sdkstatus/) updates. |

### `setTriggeredTripsEnabled`

> ```java
> Builder setTriggeredTripsEnabled(boolean enabled)
> ```
>
> Enables triggered trips mode on the SDK.
>
> Learn more about triggered trips [here](../../../appendix/controlled-detections/controlled-trips-only.md).
>
> | Parameters |  |
> | :--- | :--- |
> | enabled | `true` to enable triggered trips. |
