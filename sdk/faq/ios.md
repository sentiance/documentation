# iOS

### What app permissions are required by the SDK?

Our SDK requires location and motion activity permissions. For the location permission, it is mandatory that the user grants the "always" permission, and not just the "when in use". This is important because a critical part of the SDK's functionality is to obtain the device location when in the background, as it is expected that the user will not always be actively interacting with your app. Not granting the "always" permission will halt the SDK detections until this permission is granted.

Motion activity is also important, and may be critical as well depending on your use-case. Unlike the location permission however, if the user denies this permission, the SDK will continue with the detections.

