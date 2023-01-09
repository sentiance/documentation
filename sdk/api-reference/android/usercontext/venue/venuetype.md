# VenueType

{% hint style="info" %}
This type is part of an [Early Access](../../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Enum representation of the type of venue.

```
/**
 * Unknown venue
 */
UNKNOWN,

/**
 * Cafes, coffee bars, tea rooms, etc
 */
DRINK_DAY,

/**
 * Bars, pubs and in general places where one goes for drinks in evenings.
 */
DRINK_EVENING,

/**
 * Educational institutions visited by the user on his own for their own studies. High schools, universities, colleges, etc.
 */
EDUCATION_INDEPENDENT,

/**
 * Schools and kindergartens visited by parents.
 */
EDUCATION_PARENTS,

/**
 * Hospitals, clinics, emergency rooms.
 */
HEALTH,

/**
 * Buildings tagged as “industrial” on OSM, built for some manufacturing process.
 */
INDUSTRIAL,

/**
 * Beaches, resorts and swimming areas.
 */
LEISURE_BEACH,

/**
 * Bowling, billiards and other entertainment places.
 */
LEISURE_DAY,

/**
 * Cinemas, theatres and music halls.
 */
LEISURE_EVENING,

/**
 * Museums.
 */
LEISURE_MUSEUM,

/**
 * Forests, lakes, national parks, etc.
 */
LEISURE_NATURE,

/**
 * City parks, gardens, zoos.
 */
LEISURE_PARK,

/**
 * Office buildings. For example, of private lawyers, notaries or company representatives.
 */
OFFICE,

/**
 * Churches, mosques and other religion related buildings.
 */
RELIGION,

/**
 * Apartment blocks, houses.
 */
RESIDENTIAL,

/**
 * Food courts, restaurants, snack bars.
 */
RESTO_MID,

/**
 * Ice cream, fast food, donut stores.
 */
RESTO_SHORT,

/**
 * Supermarkets, malls, wholesales, shopping centres.
 */
SHOP_LONG,

/**
 * Small grocery stores, butchers, bakers.
 */
SHOP_SHORT,

/**
 * Gyms, sport centres. Venues visited to exercise.
 */
SPORT,

/**
 * Stadiums. Venues visited to attend a sport event.
 */
SPORT_ATTEND,

/**
 * Bus stops.
 */
TRAVEL_BUS,

/**
 * Conference, convention, exhibition centres.
 */
TRAVEL_CONFERENCE,

/**
 * Gas stations.
 */
TRAVEL_FILL,

/**
 * travel_hotel- Hotels, motels, guest rooms, etc.
 */
TRAVEL_HOTEL,

/**
 * Airports.
 */
TRAVEL_LONG,

/**
 * Public transport stations, railway stations.
 */
TRAVEL_SHORT
```
