# 1. Including the SDK

## React Native

Install the Sentiance Core React Native module, by running the following command in your terminal, inside the project directory:

```bash
npm install @sentiance-react-native/core
```

The module should now be added to your project's **package.json** file.

{% code title="package.json" %}
```groovy
{
  ...,
  "dependencies": {
    ...,
    "@sentiance-react-native/core": "^6.x.x"
  }
}
```
{% endcode %}

The `@sentiance-react-native/core` module must be installed before using any other Sentiance service.

## Native

All Sentiance modules support [autolinking](https://github.com/react-native-community/cli/blob/main/docs/autolinking.md), which is available since React Native v0.60, the minimum supported React Native version by Sentiance. Autolinking takes care of discovering and linking the native code dependencies to your project.

### iOS Setup

In the terminal, run the following command inside your project's **ios** directory:

```bash
pod install --repo-update
```

<details>

<summary>Building for the arm64 (M1 Mac) simulator</summary>

The Sentiance SDK itself supports the arm64 simulator architecture. However, the SDK has a dependency on TensorFlow Lite v2.7.0, which does not support arm64 simulators. To address this limitation, use our custom TensorFlow Lite v2.7.0 framework. In your **Podfile**, add the following entry:

{% code title="Podfile" %}
```
pod 'TensorFlowLiteC', :podspec => 'https://sentiance-u1-sdk-downloads.s3.eu-west-1.amazonaws.com/ios/frameworks/TensorFlowLiteC/2.7.0/TensorFlowLiteC.podspec'
```
{% endcode %}

More information about this custom framework can be found on [this page](../../appendix/ios/m1-simulator-support.md).

</details>

### Android setup

Add the Sentiance maven repository to the **build.gradle** file in your project's **android** directory:

{% code title="android/build.gradle" %}
```groovy
allprojects {
    repositories {
        ...
        maven { url "https://repository.sentiance.com" }
    }
}
```
{% endcode %}

This will allow Gradle to find and download the necessary native Sentiance SDK libraries.
