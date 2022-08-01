# crash-detection

### Install the module

Run the following command to install the module (make sure to install the **core** module beforehand):

```bash
npm i @sentiance-react-native/crash-detection
```

### Import the module

```javascript
import SentianceCrashDetection from "@sentiance-react-native/crash-detection";
```

### Vehicle Crash Event Detection

Listen to vehicle crash events.

```javascript
import {addVehicleCrashEventListener} from "@sentiance-react-native/crash-detection";

const subscription = addVehicleCrashEventListener(vehicleCrashEvent => {
  // New vehicle crash event
});

// Don't forget to unsubscribe, typically in componentWillUnmount
subscription.remove();
```

#### Invoke a dummy vehicle crash event

```javascript
await SentianceCrashDetection.invokeDummyVehicleCrash();
```

#### Check if crash detection is supported

```javascript
const isCrashDetectionSupported =
  await SentianceCrashDetection.isVehicleCrashDetectionSupported();
if (isCrashDetectionSupported) {
  // setup vehicle crash event listener
}
```
