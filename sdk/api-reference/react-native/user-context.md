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

#### Request the current user context data

```javascript
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