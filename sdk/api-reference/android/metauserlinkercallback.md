# MetaUserLinkerCallback

{% hint style="warning" %}
This class was replaced by UserLinkerCallback in v6.0.0.
{% endhint %}

This interface is used with [`MetaUserLinkerAsync`](userlinkerasync.md#link).

## MetaUserLinkerCallback API

|      |                                                 |
| ---- | ----------------------------------------------- |
| void | [onSuccess](userlinkercallback.md#onsuccess) () |
| void | [onFailure](userlinkercallback.md#onfailure) () |



### `onSuccess()`

> ```java
> void onSuccess()
> ```
>
> Call this method after linking succeeds.

### `onFailure()`

> ```java
> void onFailure()
> ```
>
> Call this method after linking fails.
