# Segments

Segments are actionable labels we assign to users, learned from their behavior over time.

They show what kind of lifestyle users have, if and how they go to work, in what geographical areas they live, what kind of drivers they are, if they go out a lot and so on.

You can use these segments to build a better user experience.

### Example \(segments highlighted\)

A user has a **rural home**, is an **early bird** and a **city worker**. While going to work, he has a **long commute**, where he shows **anticipative driver behavior**. His lifestyle shows a **sportive** person, while also being a **resto-lover**.

See the SDK or [REST API](../backend/rest-api/) docs on how to access these segments in your app or backend.

## Behavior <a id="segment-behavior"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| City Home | Lives in a city | behavior.city\_home |
| City Worker | Works mostly in a city | behavior.city\_worker |
| Early Bird | Person whose first morning activity is earlier than most people | behavior.early\_bird |
| Homeworker | Person who works from home or who is unemployed | behavior.homeworker |
| Night Owl | Person whose last evening activity is later than most people | behavior.night\_owl |
| Nightworker | Person who works at night | behavior.nightworker |
| Recently Changed Job | Individual who has recently changed jobs | behavior.recently\_changed\_job |
| Recently Moved Home | Individual who has recently moved to a new home | behavior.recently\_moved\_home |
| Rural Home | Lives in town or rural area | behavior.rural\_home |
| Rural Worker | Works in a rural neighborhood or town | behavior.rural\_worker |
| Shopaholic | Person who shops a lot | behavior.shopaholic |
| Town Home | Lives in a town | behavior.town\_home |
| Town Worker | Works mostly in a town | behavior.town\_worker |
| Work Traveller | Person who works remotely a lot \(traveling or in remote environments\) | behavior.work\_traveller |
| Workaholic | Person who works more than most people | behavior.workaholic |

## Driver behavior <a id="segment-driver_behavior"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| Aggressive Driver | Profile score based on intensity of accelerations and decelerations | driver\_behavior.aggressive\_driver |
| Anticipative Driver | Profile score based on sequences of coasting, cruising, accelerating, decelerating and turning | driver\_behavior.anticipative\_driver |
| City Driver | Drives mostly in cities | driver\_behavior.city\_driver |
| Distracted Driver | Profile score based on the amount of phone usage during car trips | driver\_behavior.distracted\_driver |
| Efficient Driver | Profile score based on intensity of accelerations and decelerations | driver\_behavior.efficient\_driver |
| Illegal Driver | Profile score based on speed limit violations | driver\_behavior.illegal\_driver |
| Legal Driver | Profile score based on speed limit violations | driver\_behavior.legal\_driver |
| Motorway Driver | Drives mostly in motorway | driver\_behavior.motorway\_driver |

## Geography <a id="segment-geography"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| Home : Antwerp | Lives in Antwerp | geography.home.antwerpen |
| Home : Brussels | Lives in Brussels | geography.home.bruxelles |
| Home : Ghent | Lives in Ghent | geography.home.gent |
| Work : Antwerp | Works in Antwerp | geography.work.antwerpen |
| Work : Brussels | Works in Brussels | geography.work.bruxelles |
| Work : Ghent | Works in Ghent | geography.work.gent |

## Lifestyle <a id="segment-lifestyle"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| Brand Loyalty | Person showing brand loyal behavior | lifestyle.brand\_loyalty |
| Brand Loyalty : Gas Stations | Person loyal to a specific gas station brand | lifestyle.brand\_loyalty.gas\_stations |
| Brand Loyalty : Restaurant Bar | Person loyal to a specific restaurant or bar | lifestyle.brand\_loyalty.restaurant\_bar |
| Brand Loyalty : Supermarket | Person loyal to a specific supermarket brand | lifestyle.brand\_loyalty.supermarket |
| Culture Buff | Person who likes to visit musea, operas, arts centres, etc. | lifestyle.culture\_buff |
| Dog Walker | Dog owner who regularly takes his/her dog for a walk. | lifestyle.dog\_walker |
| Fulltime Worker | Someone worksingfull-time | lifestyle.fulltime\_worker |
| Healthy Biker | Person who frequently bikes for long distances | lifestyle.healthy\_biker |
| Healthy Walker | Person who frequently walks for long distances | lifestyle.healthy\_walker |
| Homebody | Person spending most of their free time at and around home. | lifestyle.couch\_potato |
| Interests: Nightlife | Someone who enjoys evenings out \(clubs, pubs, bars\) | lifestyle.clubber |
| Late Worker | Someone working until late | lifestyle.late\_worker |
| Parttime Worker | Someone working part-time | lifestyle.parttime\_worker |
| Physical Activity : High | Profile based on the user's physical activity score | lifestyle.physical\_activity.high |
| Physical Activity : Limited | Profile based on the user's physical activity score | lifestyle.physical\_activity.limited |
| Physical Activity : Moderate | Profile based on the user's physical activity score | lifestyle.physical\_activity.moderate |
| Resto Lover | Someone who likes eating out | lifestyle.resto\_lover |
| Social Activity : High | Profile based on the user's work/social activities score | lifestyle.social\_activity.high |
| Social Activity : Limited | Profile based on the user's work/social activities score | lifestyle.social\_activity.limited |
| Social Activity : Moderate | Profile based on the user's work/social activities score | lifestyle.social\_activity.moderate |
| Sportive | Someone who sports regularly. | lifestyle.sportive |
| Student or teacher | Person is a student or teacher | lifestyle.student |
| Uber Parent | Parent who drives his/her kids to school, day care or to gym, sport centers | lifestyle.uber\_parent |
| Work Life Balance | Person having a good balance between work and home life | lifestyle.work\_life\_balance |

## Mobility <a id="segment-mobility"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| Die Hard Driver | Uses the car for almost every trip. | mobility.die\_hard\_driver |
| Easy Commuter | User has an easy commute to/from work. | mobility.easy\_commuter |
| Frequent Flyer | Person who frequently flies | mobility.frequent\_flyer |
| Green Commuter | Mostly sticks to walking and biking for commutes | mobility.green\_commuter |
| Heavy Commuter | User has a heavy commute to/from work. | mobility.heavy\_commuter |
| Long Commuter | User lives far from his work location | mobility.long\_commuter |
| Mobility : High | Profile based on user mobility score | mobility.mobility.high |
| Mobility : Limited | Profile based on user mobility score | mobility.mobility.limited |
| Mobility : Moderate | Profile based on user mobility score | mobility.mobility.moderate |
| Normal Commuter | User has an average commute time and distance | mobility.normal\_commuter |
| Public Transports User | Person who often travels with public transports | mobility.public\_transports\_user |
| Short Commuter | User lives close to his work location | mobility.short\_commuter |

