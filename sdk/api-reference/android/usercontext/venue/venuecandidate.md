# VenueCandidate

Represents a venue the user was likely at, with a corresponding likelihood, and a list of historic visits to this venue.

## VenueCandidate API

|  |  |
| :--- | :--- |
| [Venue](./) | [getVenue](venuecandidate.md#getvenue) \(\) |
| float | [getLikelihood](venuecandidate.md#getlikelihood) \(\) |
| List&lt;[Visit](visit.md)&gt; | [getVisits](venuecandidate.md#getvisits) \(\) |



### `getVenue()`

> ```java
> Venue getVenue()
> ```
>
> Returns the venue the user was likely at.

### `getLikelihood()`

> ```java
> float getLikelihood()
> ```
>
> Returns the likelihood of the user being at this venue, having a value between 0 and 1, where 1 represents extreme likelihood.

### `getVisits()`

> ```java
> List<Visit> getVisits()
> ```
>
> Returns a list of historic visits to this venue.

