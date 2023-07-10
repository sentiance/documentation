# Examples

{% hint style="info" %}
Note that the driving insights feature is in [Early Access](../../../appendix/feature-production-readiness.md). The API is subject to change in the future.
{% endhint %}

### Install the module

Run the following command to install the module (make sure to install the **core** module beforehand):

```bash
npm i @sentiance-react-native/driving-insights
```

### Import the module

```javascript
import SentianceDrivingInsights from "@sentiance-react-native/driving-insights";
```

You can find a reference to all the types mentioned on this page [here](https://github.com/sentiance/react-native-sentiance/blob/main/packages/user-context/lib/index.d.ts).

#### Get driving insights

```javascript
// returns Promise<DrivingInsights>
const drivingInsights = await SentianceDrivingInsights.getDrivingInsights(transportId);

// the transport event corresponding to driving insights.
const transportEvent = drivingInsights.transportEvent; 

// safety scores for the driving event.
const safetyScores = drivingInsights.safetyScores;

// Smooth driving score value, between 0 and 1, where 1 is the perfect score.
const smoothScore = safetyScores.smoothScore;

// Focused driving score value, between 0 and 1, where 1 is the perfect score.
const focusScore = safetyScores.focusScore;
```

#### Get Harsh Driving Events

```javascript
const harshDrivingEvents = await SentianceDrivingInsights.getHarshDrivingEvents(transportId);
```

#### Listen to driving insights updates

<pre class="language-javascript"><code class="lang-javascript"><strong>const subscription = await SentianceDrivingInsights.addDrivingInsightsReadyListener(drivingInsights => {
</strong>  // Driving insights received
});

// Don't forget to unsubscribe, typically in componentWillUnmount
subscription.remove();
</code></pre>
