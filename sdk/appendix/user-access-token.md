# User Access Token

The user access token allows you to interact with the Sentiance API directly from within your app.

## Get the User ID and Token

If a Sentiance user has been created, you can get the user ID and token as follows:

{% tabs %}
{% tab title="iOS" %}
```objectivec
 Sentiance.shared.requestUserAccessToken { result, error in
    if let result = result {
        print("Token: \(result.token)")
    }
}
```
{% endtab %}

{% tab title="Android" %}
```java
sentiance.requestUserAccessToken().addOnCompleteListener { operation ->
    if (operation.isSuccessful) {
        val token = operation.result
    } else {
        val error = operation.error
        Log.e(TAG, "Failed to get access token, reason ${error.reason.name}.")
    }
}
```
{% endtab %}
{% endtabs %}

## Failure

The token is normally valid for a limited time (several days). Generally, requesting a token from the SDK will complete instantly by returning a cached token. But if a new one has to be obtained from the Sentiance API, there is a possibility that it will fail (e.g. no network connection).

{% hint style="info" %}
Use `error.failureReason` to know the failure reason in case of failure.
{% endhint %}
