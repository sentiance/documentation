# MetaUserLinker

{% hint style="warning" %}
This class was replaced by UserLinker in v6.0.0.
{% endhint %}

This interface is used with [`setMetaUserLinker(MetaUserLinker)`](sdkconfig/sdkconfig-builder.md#setmetauserlinker).

Learn more about Meta-Users [here](../../appendix/user-linking.md).

## MetaUserLinker API

|         |                                               |
| ------- | --------------------------------------------- |
| boolean | [link](userlinker.md#link) (String installId) |



### `link()`

> ```java
> boolean link(String installId)
> ```
>
> This method will be called when your app needs to handle MetaUser linking, normally during the first ever SDK initialization, but also if MetaUsers are enabled afterwards. This method will be executed on a background thread.
>
> Returns `true` only if linking succeeds.

| Parameters |                                                             |
| ---------- | ----------------------------------------------------------- |
| installId  | A unique Sentiance ID representing the current installation |
