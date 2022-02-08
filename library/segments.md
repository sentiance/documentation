# Segments

Segments are actionable labels we assign to users, learned from their behavior over time.

They show what kind of lifestyle users have, if and how they go to work, in what geographical areas they live,
 what kind of drivers they are, if they go out a lot and so on.

You can use these segments to build a better user experience.

### Example \(segments highlighted\)

A user has a **rural home**, is an **early bird** and a **city worker**. While going to work, he has a
 **long commute**, where he shows **anticipative driver behavior**. His lifestyle shows a **sportive**
  person, while also being a **resto-lover**.

See the SDK or [REST API](../backend/rest-api/) docs on how to access these segments in your app or backend.

---

## Leisure <a id="segment-leisure"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| Bar visitor | Someone who enjoys evenings out at a pub or bar | leisure.entertainment.bar_goer |
| Beauty shop visitor | Someone who shops for beauty products a lot. | leisure.shopping.beauty_queen |
| Brand Loyal : Bar | Someone who is brand loyal to a pub or bar | leisure.wining_and_dining.brand_loyal.bar |
| Brand Loyal : Cafe | Someone who is brand loyal to a specific cafe | leisure.wining_and_dining.brand_loyal.cafe |
| Brand Loyal : Restaurant | Someone who is brand loyal to a specific restaurant | leisure.wining_and_dining.brand_loyal.restaurant |
| Brand Loyal : Retail | Someone who is brand loyal to a retail brand or shop | leisure.shopping.brand_loyal.retail |
| Brand Loyalty | Person who shows a brand loyal behavior | leisure.shopping.brand_loyalty |
| Brand Loyalty : Supermarket | Person who is loyal to a specific supermarket brand | leisure.shopping.brand_loyalty.supermarket |
| Culture Buff | Person who like to visit musea, operas, arts centres, etc. | leisure.entertainment.culture_buff |
| Fashion enthusiast | Someone who shops for clothes a lot. | leisure.shopping.fashionista |
| Fresh food enthusiast | Someone who shops for food often | leisure.shopping.foodie |
| Healthy Biker | Person who frequently bikes for long distances | leisure.wellbeing.healthy_biker |
| Healthy Walker | Person who frequently walks for long distances | leisure.wellbeing.healthy_walker |
| Interests: Games of chance | Someone who frequents casinos or betting centres | leisure.entertainment.gamer |
| Interests: Nightlife | Someone who enjoys evenings out (clubs, pubs, bars) | leisure.entertainment.clubber |
| Nature Lover | Someone who likes to go out to a park, public garden, zoo or nature reserve. | leisure.entertainment.nature_lover |
| Physical Activity : Limited | Profile based on user physical activity score | leisure.wellbeing.physical_activity.limited |
| Physical Activity : Moderate | Profile based on user physical activity score | leisure.wellbeing.physical_activity.moderate |
| Physical Activity : High | Profile based on user physical activity score | leisure.wellbeing.physical_activity.high |
| Resto Lover | Someone who likes eating out | leisure.wining_and_dining.resto_lover |
| Resto Lover : American | Someone who likes to eat American out. | leisure.wining_and_dining.resto_lover.american |
| Resto Lover : Asian | Someone who likes to eat Asian out. | leisure.wining_and_dining.resto_lover.asian |
| Resto Lover : Fastfood | Someone who likes to eat fastfood out. | leisure.wining_and_dining.resto_lover.fastfood |
| Resto Lover : French | Someone who likes to eat French out. | leisure.wining_and_dining.resto_lover.french |
| Resto Lover : German | Someone who likes to eat German out. | leisure.wining_and_dining.resto_lover.german |
| Resto Lover : Greek | Someone who likes to eat Greek out. | leisure.wining_and_dining.resto_lover.greek |
| Resto Lover : Grill | Someone who likes to eat grilled food out. | leisure.wining_and_dining.resto_lover.grill |
| Resto Lover : International | Someone who likes to eat international out. | leisure.wining_and_dining.resto_lover.international |
| Resto Lover : Italian | Someone who likes to eat Italian out. | leisure.wining_and_dining.resto_lover.italian |
| Resto Lover : Mexican | Someone who likes to eat Mexican out. | leisure.wining_and_dining.resto_lover.mexican |
| Resto Lover : Seafood | Someone who likes to eat seafood out. | leisure.wining_and_dining.resto_lover.seafood |
| Resto Lover : Snack | Someone who likes to eat a snack out. | leisure.wining_and_dining.resto_lover.snack |
| Shopaholic | Person who shops a lot | leisure.shopping.shopaholic |
| Sportive | Someone who sports regularly. | leisure.wellbeing.sportive |

---

## Mobility <a id="segment-mobility"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| Brand Loyalty : Gas Stations | Person who is loyal to a specific gas station brand | mobility.driving.brand_loyalty.gas_stations |
| Die Hard Driver | Uses the car for almost every trip. | mobility.driving.die_hard_driver |
| Easy Commuter | User has an easy commute to/from work. | mobility.commute.easy_commuter |
| Frequent Flyer | Person who frequently flies | mobility.travel.frequent_flyer |
| Green Commuter | Mostly sticks to walking and biking for commutes | mobility.commute.green_commuter |
| Heavy Commuter | User has a heavy commute to/from work. | mobility.commute.heavy_commuter |
| Long Commuter | User lives far from his work location | mobility.commute.long_commuter |
| Mobility : Limited | Profile based on user mobility score | mobility.transport.mobility.limited |
| Mobility : Moderate | Profile based on user mobility score | mobility.transport.mobility.moderate |
| Mobility : High | Profile based on user mobility score | mobility.transport.mobility.high |
| Normal Commuter | User has an average commute time and distance | mobility.commute.normal_commuter |
| Public Transports User | Person who often travel with public transports | mobility.transport.public_transports_user |
| Public transports commuter | Person who often commute with public transports | mobility.transport.public_transports_commuter |
| Short Commuter | User lives close to his work location | mobility.commute.short_commuter |

---

## Work life <a id="segment-work_life"></a>

| Segment | Description | Identifier |
| :--- | :--- | :--- |
| City Home | Lives in the city | work_life.home.city_home |
| City Worker | Works mostly in the city | work_life.work.city_worker |
| DIYer | Someone who works around the house. | work_life.home.do_it_yourselver |
| Early Bird | Person whose first morning activity is earlier than average | work_life.home.early_bird |
| Fulltime Worker | Someone who works full-time | work_life.work.fulltime_worker |
| Home Bound | Someone who does not leave the house very often or travels very far | work_life.home.home_bound |
| Homebody | Someone who prefers to stay at home on weekends and outside business hours | work_life.home.homebody |
| Homeworker | Person who works from home or who is unemployed | work_life.work.homeworker |
| Late Worker | Someone who works until late | work_life.work.late_worker |
| Night Owl | Person whose last evening activity is later than average | work_life.home.night_owl |
| Nightworker | Person who works at night | work_life.work.nightworker |
| Parttime Worker | Someone who works part-time | work_life.work.parttime_worker |
| Pet Owner | Someone who owns a pet. | work_life.home.pet_owner |
| Rural Home | Lives in town or rural area | work_life.home.rural_home |
| Rural Worker | Works in a rural neighborhood or town | work_life.work.rural_worker |
| Sleep Deprived | Someone who sleeps very little. | work_life.home.sleep_deprived |
| Social Activity : Limited | Profile based on user work/social activities score | work_life.social.social_activity.limited |
| Social Activity : Moderate | Profile based on user work/social activities score | work_life.social.social_activity.moderate |
| Social Activity : High | Profile based on user work/social activities score | work_life.social.social_activity.high |
| Student or teacher | Person is a student or teacher | work_life.work.student |
| Town Home | Lives in the town | work_life.home.town_home |
| Town Worker | Works mostly in the town | work_life.work.town_worker |
| Uber Parent | Parent who drives his/her kids to school, day care or to gym, sport centers | work_life.family.uber_parent |
| Work Life Balance | Person who has a good balance between work and home life | work_life.home.work_life_balance |
| Work Traveller | Person who works a lot remotely (travelling or in remote environments) | work_life.work.work_traveller |
| Workaholic | Person who works more than average | work_life.work.workaholic |

_( based on decision engine v0.3.1 )_
