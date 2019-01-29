# SubmitDetectionsCallback

This interface is used with [`submitDetections(SubmitDetectionsCallback)`](sentiance.md#submitdetections).

## SubmitDetectionsCallback API

|  |  |
| :--- | :--- |
| void | [onSuccess](submitdetectionscallback.md#onsuccess) \(\) |
| void  | [onFailure](submitdetectionscallback.md#onfailure) \(\) |



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



