# Segments

Segments are actionable labels we assign to users, learned from their behavior over time.

They show what kind of lifestyle users have, if and how they go to work, in what geographical areas they live, what kind of drivers they are, if they go out a lot and so on.

You can use these segments to build a better user experience.

### Example \(segments highlighted\)

A user has a **rural home**, is an **early bird** and a **city worker**. While going to work, he has a **long commute**, where he shows **anticipative driver behavior**. His lifestyle shows a **sportive** person, while also being a **resto-lover**.

See the SDK or [REST API](../backend/rest-api.md) docs on how to access these segments in your app or backend.

## Behavior <a id="segment-behavior"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
City Home | Lives in the city | behavior.city_home
Town Home | Lives in the town | behavior.town_home
Recently Moved Home | Individual who has recently moved to a new home | behavior.recently_moved_home
Early Bird | Person whose first morning activity is earlier than average | behavior.early_bird
Night Owl | Person whose last evening activity is later than average | behavior.night_owl
Rural Home | Lives in town or rural area | behavior.rural_home
Nightworker | Person who works at night | behavior.nightworker
Work Traveller | Person who works a lot remotely (travelling or in remote environments) | behavior.work_traveller
Town Worker | Works mostly in the town | behavior.town_worker
Homeworker | Person who works from home or who is unemployed | behavior.homeworker
City Worker | Works mostly in the city | behavior.city_worker
Workaholic | Person who works more than average | behavior.workaholic
Rural Worker | Works in a rural neighborhood or town | behavior.rural_worker
Recently Changed Job | Individual who has recently changed job | behavior.recently_changed_job
Shopaholic | Person who shops a lot | behavior.shopaholic

## Driver Behavior <a id="segment-driver_behavior"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
Chinese Die Hard Driver | based on the number of hours driven in the last weeks | driver_behavior.chinese_die_hard_driver
Legal Driver | Profile score based on speed limit violations | driver_behavior.legal_driver
Illegal Driver | Profile score based on speed limit violations | driver_behavior.illegal_driver
Aggressive Driver | Profile score based on intensity of accelerations and decelerations | driver_behavior.aggressive_driver
City Driver | Drives a lot in city | driver_behavior.city_driver
Anticipative Driver | Profile score based on sequences of coasting, cruising, accelerating, decelerating and turning | driver_behavior.anticipative_driver
Motorway Driver | Drives mostly in motorway | driver_behavior.motorway_driver
Efficient Driver | Profile score based on intensity of accelerations and decelerations | driver_behavior.efficient_driver
Distracted Driver | Profile score based on the amount of phone usage during car trips | driver_behavior.distracted_driver

## Geography <a id="segment-geography"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
Work : Antwerp | Works in Antwerp | geography.work.antwerpen
Work : Ghent | Works in Ghent | geography.work.gent
Work : Brussels | Works in Brussels | geography.work.bruxelles
Home : Antwerp | Lives in Antwerp | geography.home.antwerpen
Home : Ghent | Lives in Ghent | geography.home.gent
Home : Brussels | Lives in Brussels | geography.home.bruxelles

## Lifestyle <a id="segment-lifestyle"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
Dog Walker | Dog owner who regularly takes his/her dog for a walk. | lifestyle.dog_walker
Work Life Balance | Person who has a good balance between work and home life | lifestyle.work_life_balance
Homebody | Person who spends most of their free time at and around home. | lifestyle.couch_potato
Student or teacher | Person is a student or teacher | lifestyle.student
Parttime Worker | Someone who works part-time | lifestyle.parttime_worker
Fulltime Worker | Someone who works full-time | lifestyle.fulltime_worker
Late Worker | Someone who works until late | lifestyle.late_worker
Uber Parent | Parent who drives his/her kids to school, day care or to gym, sport centers | lifestyle.uber_parent
Social Activity : Limited | Profile based on user work/social activities score | lifestyle.social_activity.limited
Social Activity : Moderate | Profile based on user work/social activities score | lifestyle.social_activity.moderate
Social Activity : High | Profile based on user work/social activities score | lifestyle.social_activity.high
Brand Loyalty | Person who shows a brand loyal behavior | lifestyle.brand_loyalty
Brand Loyalty : Supermarket | Person who is loyal to a specific supermarket brand | lifestyle.brand_loyalty.supermarket
Resto Lover | Someone who likes eating out | lifestyle.resto_lover
Brand Loyalty : Restaurant Bar | Person who is loyal to a specific restaurant or bar | lifestyle.brand_loyalty.restaurant_bar
Sportive | Someone who sports regularly. | lifestyle.sportive
Physical Activity : High | Profile based on user physical activity score | lifestyle.physical_activity.high
Healthy Walker | Person who frequently walks for long distances | lifestyle.healthy_walker
Healthy Biker | Person who frequently bikes for long distances | lifestyle.healthy_biker
Physical Activity : Limited | Profile based on user physical activity score | lifestyle.physical_activity.limited
Physical Activity : Moderate | Profile based on user physical activity score | lifestyle.physical_activity.moderate
Culture Buff | Person who like to visit musea, operas, arts centres, etc. | lifestyle.culture_buff
Interests: Nightlife | Someone who enjoys evenings out (clubs, pubs, bars) | lifestyle.clubber
Brand Loyalty : Gas Stations | Person who is loyal to a specific gas station brand | lifestyle.brand_loyalty.gas_stations

## Mobility <a id="segment-mobility"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
Outdoor Sportive | Person who does outdoor sport: running, walking, cycling | mobility.outdoor_sportive
Frequent Flyer | Person who frequently flies | mobility.frequent_flyer
Normal Commuter | User has an average commute time and distance | mobility.normal_commuter
Short Commuter | User lives close to his work location | mobility.short_commuter
Heavy Commuter | User has a heavy commute to/from work. | mobility.heavy_commuter
Green Commuter | Mostly sticks to walking and biking for commutes | mobility.green_commuter
Long Commuter | User lives far from his work location | mobility.long_commuter
Easy Commuter | User has an easy commute to/from work. | mobility.easy_commuter
Die Hard Driver | Uses the car for almost every trip. | mobility.die_hard_driver
Mobility : Limited | Profile based on user mobility score | mobility.mobility.limited
Public Transports User | Person who often travel with public transports | mobility.public_transports_user
Mobility : Moderate | Profile based on user mobility score | mobility.mobility.moderate
Mobility : High | Profile based on user mobility score | mobility.mobility.high


