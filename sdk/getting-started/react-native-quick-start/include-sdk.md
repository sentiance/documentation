# 1. Including the SDK

## Install the 'core' module

Run the following command in your terminal, inside the project directory:

```bash
npm install @sentiance-react-native/core
```

The Sentiance Core React Native module should now be added to your **** project's **package.json** file.

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

## iOS Setup

#### Update the Podfile

Add the following line to the **Podfile** file in your project's **ios** directory:

{% code title="ios/Podfile" %}
```ruby
pod 'RNSentianceCore', :path => '../node_modules/@sentiance-react-native/core/ios'
```
{% endcode %}

Then in the terminal, run the following command inside your project's **ios** directory:

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

## Android setup

#### Update Project Repositories

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

Once that's done, the Sentiance Core library needs to be linked to your project and your application needs to be rebuilt. The [autolinking](https://github.com/react-native-community/cli/blob/master/docs/autolinking.md) feature that comes with React Native 0.60 will take care of linking the library for you. Sentiance libraries are supported for React Native **0.60** and above, so you normally do not need to do any manual linking step.&#x20;
