# UserContext

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents the user's context during a specific moment in time. The context includes:‌

* a list of recent events, such as stationaries and transports;
* the user's active moments and segments at the time this context was constructed;
* the user's home and work locations;
* the user's last know location, if SDK detections were running.‌

## UserContext API <a href="#usercontext-api" id="usercontext-api"></a>

| ​                               | ​                                                   |
| ------------------------------- | --------------------------------------------------- |
| List<[Moment](moment/)>         | ​[getActiveMoments](./#getactivemoments) ()         |
| List<[Segment](segment/)>       | ​[getActiveSegments](./#getactivesegments) ()       |
| List<[Event](event/)>           | ​[getEvents](./#getevents) ()                       |
| ​[Venue](venue/)​               | ​[getHome](./#gethome) ()                           |
| ​[GeoLocation](geolocation.md)​ | ​[getLastKnownLocation](./#getlastknownlocation) () |
| ​[Venue](venue/)​               | ​[getWork](./#getwork) ()                           |

​‌

### `getActiveMoments()` <a href="#getactivemoments" id="getactivemoments"></a>

> ```java
> List<Moment> getActiveMoments()
> ```
>
> Returns the active moments detected for the user at the time this context was constructed.

### `getActiveSegments()` <a href="#getactivesegments" id="getactivesegments"></a>

> ```java
> List<Segment> getActiveSegments()
> ```
>
> Returns the active segments detected for the user at the time this context was constructed.

### ‌`getEvents()`

> ```java
> List<Event getEvents()
> ```
>
> Returns a list of recent events, composed of stationaries, transports, and off-the-grids. The list is ordered from the most recent event to the oldest one, and includes the last detected event at the time this context was constructed, plus all preceding events up until the last stationary or off-the-grid.

### `getHome()` <a href="#gethome" id="gethome"></a>

> ```
> @Nullable Venue getHome()
> ```
>
> Returns the user's home location if known, otherwise returns null.

### `getLastKnownLocation()` <a href="#getlastknownlocation" id="getlastknownlocation"></a>

> ```
> @Nullable GeoLocation getLastKnownLocation()
> ```
>
> Returns the user's last know location at the time this context was constructed. If the user's last detected event was off-the-grid, or no location information was available, null is returned instead.

### `getWork()` <a href="#getwork" id="getwork"></a>

> ```
> @Nullable Venue getWork()
> ```
>
> Returns the user's work location if known, otherwise returns null.