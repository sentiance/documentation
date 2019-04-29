# Moments

Moments bring meaning and context to what a user is doing. You can use these contextual moments to build a better user experience. Multiple moments can be active at the same time.

### Example \(moments highlighted\)

After a **long commute** and enjoying his **morning routine**, the user is currently **at work**. His **morning semantic time** is about to end. We are quite confident he will go out to lunch in one hour and afterwards will continue **work** for 5 hours before **commuting home** by bus.

## About to routine <a id="moment-about_to_routine"></a>

| Moment definition | Description | Identifier |
| :--- | :--- | :--- |
| About to commute to home | This moment should be active when we predict that the user will be commuting to home soon. | about\_to\_commute\_from\_work |
| About to commute to work | This moment should be active when we predict that the user will be commuting to work soon. | about\_to\_commute\_from\_home |
| About to drop off/pick up kids | This moment should be active when we predict that the user will be dropping off or picking up his kids soon. | about\_to\_children\_drop\_off |
| About to go shopping | This moment should be active when we predict that the user is about to go shopping. | about\_to\_shopping |
| About to sport | This moment should be active when we predict that the user is about to go sporting. | about\_to\_sport |
| About to work at work | This moment should be active when we predict that the user will be working at his usual working location soon. | about\_to\_working |

## Activity <a id="moment-activity"></a>

| Moment definition | Description | Identifier |
| :--- | :--- | :--- |
| Afternoon drinks | This moment will be active when the user is in his semantic afternoon or early evening and is at a drinks related venue, or we predict he is moving toward such a location. | afternoon\_drinks |
| Breakfast out | This moment will be active when the user is in his semantic \(late\) morning and is at a drinks or restaurant related venue, or we predict he is moving toward it. | breakfast\_out |
| Commute to home | This moment should be active during a users commute from work to home. The moment can also remain active during short stops in commutes. | commute\_from\_work |
| Commute to work | This moment should be active during a users commute from home to work. The moment can also remain active during short stops in commutes. | commute\_from\_home |
| Dinner out | This moment will be active when the user is in his semantic evening and is at a restaurant related venue, or we predict he is moving toward it. | dinner\_out |
| Evening drinks | This moment will be active when the user is in his semantic evening and is at a drinks related venue, or we predict he is moving toward such a location. | evening\_drinks |
| Evening entertainment | This moment will be active when the user is in his semantic afternoon or evening and is either at a culture or leisure related venue, or we predict he is moving toward such a location. | evening\_entertainment |
| Home | This moment will be active when the user is home and will stay active even if he takes short walks around his home. | home |
| Kids drop off/pick up | This moment should be active when we detect an onging drop off or pick up. The moment should be started when the user leaves his home or an education or sport location and we predict that the user is picking up or dropping off kids. | children\_drop\_off |
| Lunch out | This moment will be active when the user is in his semantic lunch and is at a restaurant related venue, or we predict he is moving toward it. | lunch\_out |
| Night out | This moment will be active when the user is in his semantic night and is either at a drinks or leisure related venue, or we predict he is moving toward such a location. | night\_out |
| Shopping | This moment will be active when the user is shopping, or we predict the user is moving toward his usual shopping location. | shopping\_routine |
| Sporting | This moment will be active when the user is sporting, or we predict the user is moving toward his usual sporting location. | sport\_routine |
| Working at work | This moment should be active when the user is working at his work location. It will also remain active when the user leaves his work location for short, small trips. For example, when getting a sandwich at a shop. | working\_at\_work |
| Working remote | This moment should be active when the user is working at a remote location, or is in a transport to that location. | working\_remote |

## Geography <a id="moment-geography"></a>

| Moment definition | Description | Identifier |
| :--- | :--- | :--- |
| Nearby POI | This moment should be active when we see a user nearby a poi location. | nearby\_poi |
| Nearby home | This moment will be active when user is not at his home location, but within a radius of one km. | nearby\_home |
| Nearby work | This moment will be active when user is not at his usual work location, but within a radius of one km. | nearby\_work |

## Location <a id="moment-location"></a>

| Moment definition | Description | Identifier |
| :--- | :--- | :--- |
| At city | This moment will be active when a user is in a city \(by name\). The city name can be found in the meta data, under the 'name' key. | city\_name |
| At country | This moment will be active when a user is at a country. The country name can be found in the meta data, under the 'name' key. | country |

## Semantic time <a id="moment-semantic_time"></a>

| Moment definition | Description | Identifier |
| :--- | :--- | :--- |
| Afternoon | This moment will be active for the first half of the time between lunch and evening. | afternoon |
| Evening | This moment will be active for the evening period a user experiences before going to bed. | evening |
| Lunch | This moment will be active for the user mid-day period, which regularly includes lunch. | lunch |
| Morning | This moment will be active for the first half of the time between wake up and lunch. | morning |
| Night | This moment will be active when the user is sleeping or expected to. | night |

## Travel <a id="moment-travel"></a>

| Moment definition | Description | Identifier |
| :--- | :--- | :--- |
| Business trip | This moment will be active when the user is on a trip and has visited a conference or when the user is on a trip far from home and has visited an office-related location. The moment will remain active until the user is bach at home or work. | business\_trip |
| Leisure trip | This moment will be active when the user is far from home or has spent at least one night not at home. It will stay active until the user is back at home or at work. | holiday |

