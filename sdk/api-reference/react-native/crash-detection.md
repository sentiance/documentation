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

You can find a reference to all the types mentioned on this page [here](https://github.com/sentiance/react-native-sentiance/blob/main/packages/crash-detection/lib/index.d.ts).

### Vehicle Crash Event Detection

Listen to vehicle crash events:

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
// returns Promise<boolean>
await SentianceCrashDetection.invokeDummyVehicleCrash();
```

#### Check if crash detection is supported

```javascript
// returns Promise<boolean>
const isCrashDetectionSupported =
  await SentianceCrashDetection.isVehicleCrashDetectionSupported();
if (isCrashDetectionSupported) {
  // setup vehicle crash event listener
}
```

### Vehicle Crash Diagnostic Data

Listen to vehicle crash diagnostic data.

```javascript
await SentianceCrashDetection.addVehicleCrashDiagnosticListener(diagnostic => {
    // New diagnostic data
}
```
