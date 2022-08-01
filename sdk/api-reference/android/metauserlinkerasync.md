# MetaUserLinkerAsync

{% hint style="warning" %}
This class was replaced by UserLinkerAsync in v6.0.0.
{% endhint %}

This interface is used with [`setMetaUserLinker(MetaUserLinkerAsync)`](sdkconfig/sdkconfig-builder.md#setmetauserlinker-1).

Learn more about Meta-Users [here](../../appendix/user-linking.md).

## MetaUserLinker API

|         |                                                                                                         |
| ------- | ------------------------------------------------------------------------------------------------------- |
| boolean | [link](userlinker.md#link) (String installId, [MetaUserLinkerCallback](userlinkercallback.md) callback) |



### `link()`

> ```java
> boolean link(String installId, MetaUserLinkerCallback callback)
> ```
>
> This method will be called when your app needs to handle MetaUser linking, normally during the first ever SDK initialization, but also if MetaUsers are enabled afterwards. This method will be executed on a background thread.

| Parameters |                                                                                                                |
| ---------- | -------------------------------------------------------------------------------------------------------------- |
| installId  | A unique Sentiance ID representing the current installation                                                    |
| callback   | A [`MetaUserLInkerCallback`](userlinkercallback.md) you must invoke to inform the SDK about the linking result |
