# SENTVenueType

{% hint style="info" %}
This type is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

Enum values representing stationary venue types.

```objectivec
typedef NS_ENUM(NSUInteger, SENTVenueType) {
    /**
     * Unknown venue
     */
    SENTVenueTypeUnknown = 0,

    /**
     * Cafes, coffee bars, tea rooms, etc
     */
    SENTVenueTypeDrinkDay,

    /**
     * Bars, pubs and in general places where one goes for drinks in evenings.
     */
    SENTVenueTypeDrinkEvening,

    /**
     * Educational institutions visited by the user on his own for their own studies. High schools, universities, colleges, etc.
     */
    SENTVenueTypeEducationIndependent,

    /**
     * Schools and kindergartens visited by parents.
     */
    SENTVenueTypeEducationParents,

    /**
     * Hospitals, clinics, emergency rooms.
     */
    SENTVenueTypeHealth,

    /**
     * Buildings tagged as “industrial” on OSM, built for some manufacturing process.
     */
    SENTVenueTypeIndustrial,

    /**
     * Beaches, resorts and swimming areas.
     */
    SENTVenueTypeLeisureBeach,

    /**
     * Bowling, billiards and other entertainment places.
     */
    SENTVenueTypeLeisureDay,

    /**
     * Cinemas, theatres and music halls.
     */
    SENTVenueTypeLeisureEvening,

    /**
     * Museums.
     */
    SENTVenueTypeLeisureMuseum,

    /**
     * Forests, lakes, national parks, etc.
     */
    SENTVenueTypeLeisureNature,

    /**
     * City parks, gardens, zoos.
     */
    SENTVenueTypeLeisurePark,

    /**
     * Office buildings. For example, of private lawyers, notaries or company representatives.
     */
    SENTVenueTypeOffice,

    /**
     * Churches, mosques and other religion related buildings.
     */
    SENTVenueTypeReligion,

    /**
     * Apartment blocks, houses.
     */
    SENTVenueTypeResidential,

    /**
     * Food courts, restaurants, snack bars.
     */
    SENTVenueTypeRestoMid,

    /**
     * Ice cream, fast food, donut stores.
     */
    SENTVenueTypeRestoShort,

    /**
     * Supermarkets, malls, wholesales, shopping centres.
     */
    SENTVenueTypeShopLong,

    /**
     * Small grocery stores, butchers, bakers.
     */
    SENTVenueTypeShopShort,

    /**
     * Gyms, sport centres. Venues visited to exercise.
     */
    SENTVenueTypeSport,

    /**
     * Stadiums. Venues visited to attend a sport event.
     */
    SENTVenueTypeSportAttend,

    /**
     * Bus stops.
     */
    SENTVenueTypeTravelBus,

    /**
     * Conference, convention, exhibition centres.
     */
    SENTVenueTypeTravelConference,

    /**
     * Gas stations.
     */
    SENTVenueTypeTravelFill,

    /**
     * travel_hotel- Hotels, motels, guest rooms, etc.
     */
    SENTVenueTypeTravelHotel,

    /**
     * Airports.
     */
    SENTVenueTypeTravelLong,

    /**
     * Public transport stations, railway stations.
     */
    SENTVenueTypeTravelShort,
};
```
