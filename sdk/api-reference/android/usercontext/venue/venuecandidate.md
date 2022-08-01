# VenueCandidate

{% hint style="info" %}
This class is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Represents a venue the user was likely at, with a corresponding likelihood, and a list of historic visits to this venue.

## VenueCandidate API

|                         |                                                     |
| ----------------------- | --------------------------------------------------- |
| float                   | [getLikelihood](venuecandidate.md#getlikelihood) () |
| [Venue](./)             | [getVenue](venuecandidate.md#getvenue) ()           |
| List<[Visit](visit.md)> | [getVisits](venuecandidate.md#getvisits) ()         |



### `getLikelihood()`

> ```java
> float getLikelihood()
> ```
>
> Returns the likelihood of the user being at this venue, having a value between 0 and 1, where 1 represents extreme likelihood.

### `getVenue()`

> ```java
> Venue getVenue()
> ```
>
> Returns the venue the user was likely at.

### `getVisits()`

> ```java
> List<Visit> getVisits()
> ```
>
> Returns a list of historic visits to this venue.
