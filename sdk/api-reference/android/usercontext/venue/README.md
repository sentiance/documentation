# Venue

Represents a place of interest.

## Venue API

|  |  |
| :--- | :--- |
| String | [getName](./#getname) \(\) |
| [GeoLocation](../geolocation.md) | [getLocation](./#getlocation) \(\) |
| Map&lt;String, String&gt; | [getLabels](./#getlabels) \(\) |



### `getName()`

> ```java
> @Nullable String getName()
> ```
>
> Returns the name of the venue if available. Otherwise, returns null.

### `getLocation()`

> ```java
> GeoLocation getLocation()
> ```
>
> Returns the location of the venue.

### `getLabels()`

> ```java
> Map<String, String> getLabels()
> ```
>
> Returns a map of labels assigned to the venue.
>
> Note: due to ongoing development, the contents of this mapping are subject to change.

