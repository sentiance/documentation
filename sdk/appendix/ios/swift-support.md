---
description: Sentiance SDK is compatible and is refined to be used with Swift Apps.
---

# Swift Support

Steps to integrate the Sentiance SDK into iOS Apps written in Swift:

1. After the [integration steps](../../getting-started/ios-sdk/), in the [Bridging Header](https://developer.apple.com/documentation/swift/importing-objective-c-into-swift) for your application, import the Sentiance SDK in the files you want to use the API.
2. Access the API using the singleton instance `Sentiance.shared`.

Example:

```swift
@import SENTSDK

class MyClass {
    func run() {
        let sentiance = Sentiance.shared
    }
}
```
