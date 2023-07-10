# Examples

### Install the module

Run the following command to install the module (make sure to install the **core** module beforehand):

```bash
npm i @sentiance-react-native/user-context
```

### Import the module

```javascript
import SentianceUserContext from "@sentiance-react-native/user-context";
```

You can find a reference to all the types mentioned on this page [here](https://github.com/sentiance/react-native-sentiance/blob/main/packages/user-context/lib/index.d.ts).

#### Request the current user context data

```javascript
// returns Promise<UserContext>
const userContext = await SentianceUserContext.requestUserContext();

/* 
a list of recent events, composed of stationaries, transports, and off-the-grids. 
The list is ordered from the most recent event to the oldest one, 
and includes the last detected event at the time this context was constructed, 
plus all preceding events up until the last stationary or off-the-grid.
*/
const events = userContext.events; 

// the active segments detected for the user at the time this context was constructed
const activeSegments = userContext.activeSegments;

/*
the user's last known location at the time this context was constructed. 
If the user's last detected event was an off-the-grid, 
or no location information was available, null is returned instead.
*/
const lastKnownLocation = userContext.lastKnownLocation;

// the user's home location if known, otherwise returns null.
const home = userContext.home;

// the user's work location if known, otherwise returns null.
const work = userContext.work;

// the user's semantic time.
const semanticTime = userContext.semanticTime;
```

#### Listen to user context updates

```javascript
import {addUserContextUpdateListener} from "@sentiance-react-native/user-context";

const subscription = addUserContextUpdateListener(userContext => {
  // User context update received
});

// Don't forget to unsubscribe, typically in componentWillUnmount
subscription.remove();
```
