# Venue

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a place of interest.

## Venue API

|                                  |                                  |
| -------------------------------- | -------------------------------- |
| Map\<String, String>             | [getLabels](./#getlabels) ()     |
| [GeoLocation](../geolocation.md) | [getLocation](./#getlocation) () |
| String                           | [getName](./#getname) ()         |



### `getLabels()`

> ```java
> Map<String, String> getLabels()
> ```
>
> Returns a map of labels assigned to the venue.
>
> Note: due to ongoing development, the contents of this mapping are subject to change.

### `getLocation()`

> ```java
> GeoLocation getLocation()
> ```
>
> Returns the location of the venue.

### `getName()`

> ```java
> @Nullable String getName()
> ```
>
> Returns the name of the venue if available. Otherwise, returns null.
