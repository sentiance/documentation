# HardEvent

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

{% hint style="warning" %}
**Deprecated**

This class was deprecated in v4.21.0, as part of the Trip Profiling feature deprecation.
{% endhint %}

A HardEvent is any unusual and/or rigorous force that is applied to the device and detected by the SDK.

## HardEvent API

### `getMagnitude()`

> ```java
> public double getMagnitude()
> ```
>
> Returns the magnitude of this hard event in m/s2.

### `getTimestamp()`

> ```java
> public long getTimestamp()
> ```
>
> Returns the UTC time of this hard event, in milliseconds since January 1, 1970.
