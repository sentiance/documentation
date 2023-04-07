# StationaryEvent

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a duration of time when the user was stationary.

## StationaryEvent API

{% hint style="info" %}
This class extends [Event](./). See [Event](./) for additional properties and methods.
{% endhint %}

### `getLocation()`

> ```java
> @Nullable GeoLocation getLocation()
> ```
>
> Returns the location where the user is stationary at.

### `getVenue()`

> ```java
> Venue getVenue()
> ```
>
> Returns the venue of this stationary.
