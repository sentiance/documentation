# PoiLocation

Holds more information about a stationary location.

## PoiLocation API

|  |  |
| :--- | :--- |
| List&lt;[PoiPlace](poiplace.md)&gt; | [getPlaceCandidates](poilocation.md#getplacecandidates) \(\) |
| PoiPlace | [getPoiPlace](poilocation.md#getpoiplace) \(\) |
| String | [getSignificance](poilocation.md#getsignificance) \(\) |



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

