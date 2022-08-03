# user-context

{% hint style="info" %}
Note that the user context feature is in [Early Access](../../appendix/feature-production-readiness.md). The API is subject to change in the future.
{% endhint %}

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
