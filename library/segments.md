# Segments

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

Segments are actionable labels we assign to users, learned from their behavior over time.

They show what kind of lifestyle users have, if and how they go to work, in what geographical areas they live, what kind of drivers they are, if they go out a lot and so on.

You can use these segments to build a better user experience.

### Example (segments highlighted)

A user has a **rural home**, is an **early bird** and a **city worker**. While going to work, he has a **long commute**, where he shows **anticipative driver behavior**. His lifestyle shows a **sportive** person, while also being a **resto-lover**.

See the SDK or [REST API](../backend/rest-api/) docs on how to access these segments in your app or backend.



## Leisure <a href="#segment-leisure" id="segment-leisure"></a>

| Segment                      | Description                                                                  | Identifier                                             |
| ---------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------ |
| Bar visitor                  | Someone who enjoys evenings out at a pub or bar                              | leisure.entertainment.bar\_goer                        |
| Beauty shop visitor          | Someone who shops for beauty products a lot.                                 | leisure.shopping.beauty\_queen                         |
| Brand Loyal : Bar            | Someone who is brand loyal to a pub or bar                                   | leisure.wining\_and\_dining.brand\_loyal.bar           |
| Brand Loyal : Cafe           | Someone who is brand loyal to a specific cafe                                | leisure.wining\_and\_dining.brand\_loyal.cafe          |
| Brand Loyal : Restaurant     | Someone who is brand loyal to a specific restaurant                          | leisure.wining\_and\_dining.brand\_loyal.restaurant    |
| Brand Loyal : Retail         | Someone who is brand loyal to a retail brand or shop                         | leisure.shopping.brand\_loyal.retail                   |
| Brand Loyalty                | Person who shows a brand loyal behavior                                      | leisure.shopping.brand\_loyalty                        |
| Brand Loyalty : Supermarket  | Person who is loyal to a specific supermarket brand                          | leisure.shopping.brand\_loyalty.supermarket            |
| Culture Buff                 | Person who like to visit musea, operas, arts centres, etc.                   | leisure.entertainment.culture\_buff                    |
| Fashion enthusiast           | Someone who shops for clothes a lot.                                         | leisure.shopping.fashionista                           |
| Fresh food enthusiast        | Someone who shops for food often                                             | leisure.shopping.foodie                                |
| Healthy Biker                | Person who frequently bikes for long distances                               | leisure.wellbeing.healthy\_biker                       |
| Healthy Walker               | Person who frequently walks for long distances                               | leisure.wellbeing.healthy\_walker                      |
| Interests: Games of chance   | Someone who frequents casinos or betting centres                             | leisure.entertainment.gamer                            |
| Interests: Nightlife         | Someone who enjoys evenings out (clubs, pubs, bars)                          | leisure.entertainment.clubber                          |
| Nature Lover                 | Someone who likes to go out to a park, public garden, zoo or nature reserve. | leisure.entertainment.nature\_lover                    |
| Physical Activity : Limited  | Profile based on user physical activity score                                | leisure.wellbeing.physical\_activity.limited           |
| Physical Activity : Moderate | Profile based on user physical activity score                                | leisure.wellbeing.physical\_activity.moderate          |
| Physical Activity : High     | Profile based on user physical activity score                                | leisure.wellbeing.physical\_activity.high              |
| Resto Lover                  | Someone who likes eating out                                                 | leisure.wining\_and\_dining.resto\_lover               |
| Resto Lover : American       | Someone who likes to eat American out.                                       | leisure.wining\_and\_dining.resto\_lover.american      |
| Resto Lover : Asian          | Someone who likes to eat Asian out.                                          | leisure.wining\_and\_dining.resto\_lover.asian         |
| Resto Lover : Fastfood       | Someone who likes to eat fastfood out.                                       | leisure.wining\_and\_dining.resto\_lover.fastfood      |
| Resto Lover : French         | Someone who likes to eat French out.                                         | leisure.wining\_and\_dining.resto\_lover.french        |
| Resto Lover : German         | Someone who likes to eat German out.                                         | leisure.wining\_and\_dining.resto\_lover.german        |
| Resto Lover : Greek          | Someone who likes to eat Greek out.                                          | leisure.wining\_and\_dining.resto\_lover.greek         |
| Resto Lover : Grill          | Someone who likes to eat grilled food out.                                   | leisure.wining\_and\_dining.resto\_lover.grill         |
| Resto Lover : International  | Someone who likes to eat international out.                                  | leisure.wining\_and\_dining.resto\_lover.international |
| Resto Lover : Italian        | Someone who likes to eat Italian out.                                        | leisure.wining\_and\_dining.resto\_lover.italian       |
| Resto Lover : Mexican        | Someone who likes to eat Mexican out.                                        | leisure.wining\_and\_dining.resto\_lover.mexican       |
| Resto Lover : Seafood        | Someone who likes to eat seafood out.                                        | leisure.wining\_and\_dining.resto\_lover.seafood       |
| Resto Lover : Snack          | Someone who likes to eat a snack out.                                        | leisure.wining\_and\_dining.resto\_lover.snack         |
| Shopaholic                   | Person who shops a lot                                                       | leisure.shopping.shopaholic                            |
| Sportive                     | Someone who sports regularly.                                                | leisure.wellbeing.sportive                             |



## Mobility <a href="#segment-mobility" id="segment-mobility"></a>

| Segment                      | Description                                         | Identifier                                      |
| ---------------------------- | --------------------------------------------------- | ----------------------------------------------- |
| Brand Loyalty : Gas Stations | Person who is loyal to a specific gas station brand | mobility.driving.brand\_loyalty.gas\_stations   |
| Die Hard Driver              | Uses the car for almost every trip.                 | mobility.driving.die\_hard\_driver              |
| Easy Commuter                | User has an easy commute to/from work.              | mobility.commute.easy\_commuter                 |
| Frequent Flyer               | Person who frequently flies                         | mobility.travel.frequent\_flyer                 |
| Green Commuter               | Mostly sticks to walking and biking for commutes    | mobility.commute.green\_commuter                |
| Heavy Commuter               | User has a heavy commute to/from work.              | mobility.commute.heavy\_commuter                |
| Long Commuter                | User lives far from his work location               | mobility.commute.long\_commuter                 |
| Mobility : Limited           | Profile based on user mobility score                | mobility.transport.mobility.limited             |
| Mobility : Moderate          | Profile based on user mobility score                | mobility.transport.mobility.moderate            |
| Mobility : High              | Profile based on user mobility score                | mobility.transport.mobility.high                |
| Normal Commuter              | User has an average commute time and distance       | mobility.commute.normal\_commuter               |
| Public Transports User       | Person who often travel with public transports      | mobility.transport.public\_transports\_user     |
| Public transports commuter   | Person who often commute with public transports     | mobility.transport.public\_transports\_commuter |
| Short Commuter               | User lives close to his work location               | mobility.commute.short\_commuter                |



## Work life <a href="#segment-work_life" id="segment-work_life"></a>

| Segment                    | Description                                                                 | Identifier                                  |
| -------------------------- | --------------------------------------------------------------------------- | ------------------------------------------- |
| City Home                  | Lives in the city                                                           | work\_life.home.city\_home                  |
| City Worker                | Works mostly in the city                                                    | work\_life.work.city\_worker                |
| DIYer                      | Someone who works around the house.                                         | work\_life.home.do\_it\_yourselver          |
| Early Bird                 | Person whose first morning activity is earlier than average                 | work\_life.home.early\_bird                 |
| Fulltime Worker            | Someone who works full-time                                                 | work\_life.work.fulltime\_worker            |
| Home Bound                 | Someone who does not leave the house very often or travels very far         | work\_life.home.home\_bound                 |
| Homebody                   | Someone who prefers to stay at home on weekends and outside business hours  | work\_life.home.homebody                    |
| Homeworker                 | Person who works from home or who is unemployed                             | work\_life.work.homeworker                  |
| Late Worker                | Someone who works until late                                                | work\_life.work.late\_worker                |
| Night Owl                  | Person whose last evening activity is later than average                    | work\_life.home.night\_owl                  |
| Nightworker                | Person who works at night                                                   | work\_life.work.nightworker                 |
| Parttime Worker            | Someone who works part-time                                                 | work\_life.work.parttime\_worker            |
| Pet Owner                  | Someone who owns a pet.                                                     | work\_life.home.pet\_owner                  |
| Rural Home                 | Lives in town or rural area                                                 | work\_life.home.rural\_home                 |
| Rural Worker               | Works in a rural neighborhood or town                                       | work\_life.work.rural\_worker               |
| Sleep Deprived             | Someone who sleeps very little.                                             | work\_life.home.sleep\_deprived             |
| Social Activity : Limited  | Profile based on user work/social activities score                          | work\_life.social.social\_activity.limited  |
| Social Activity : Moderate | Profile based on user work/social activities score                          | work\_life.social.social\_activity.moderate |
| Social Activity : High     | Profile based on user work/social activities score                          | work\_life.social.social\_activity.high     |
| Student or teacher         | Person is a student or teacher                                              | work\_life.work.student                     |
| Town Home                  | Lives in the town                                                           | work\_life.home.town\_home                  |
| Town Worker                | Works mostly in the town                                                    | work\_life.work.town\_worker                |
| Uber Parent                | Parent who drives his/her kids to school, day care or to gym, sport centers | work\_life.family.uber\_parent              |
| Work Life Balance          | Person who has a good balance between work and home life                    | work\_life.home.work\_life\_balance         |
| Work Traveller             | Person who works a lot remotely (travelling or in remote environments)      | work\_life.work.work\_traveller             |
| Workaholic                 | Person who works more than average                                          | work\_life.work.workaholic                  |

_( based on decision engine v0.3.1 )_
