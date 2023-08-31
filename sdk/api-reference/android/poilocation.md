# PoiLocation

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Holds more information about a stationary location.

## PoiLocation API

### `getPlaceCandidates()`

> ```java
> List<PoiPlace> getPlaceCandidates()
> ```
>
> Returns a list of of additional place candidates of type [`PoiPlace`](poiplace.md).

### `getPoiPlace()`

> ```java
> PoiPlace getPoiPlace()
> ```
>
> Returns the place candidate of type [`PoiPlace`](poiplace.md).

### `getSignificance()`

> ```java
> String getSignificance()
> ```
>
> Returns a string representation of what this location means for the user, or the frequency it's being visited.
