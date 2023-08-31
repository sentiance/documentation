# SubmitDetectionsCallback

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with [`submitDetections(SubmitDetectionsCallback)`](sentiance.md#submitdetections).

## SubmitDetectionsCallback API

### `onSuccess()`

> ```java
> void onSuccess()
> ```
>
> All detections have been successfully submitted.

### `onFailure()`

> ```java
> void onFailure()
> ```
>
> At least one detection was not successfully submitted.
>
> Due to constraints on detection submission order, failure to submit certain detections will cause the entire submission run to be stopped.

