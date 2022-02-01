# User Credentials

User credentials allow you to interact with the Sentiance API. You need a token and user to authorize requests and query the right data.

## Get User and Token

If the SDK is initialized, you can get the userID and token as follows:

{% tabs %}
{% tab title="iOS" %}
```objectivec
NSString* userId = [[SENTSDK sharedInstance] getUserId];
[[SENTSDK sharedInstance] getUserAccessToken:^(NSString *token) {
    NSString* accessToken = token;
} failure:^{
}];
```
{% endtab %}

{% tab title="Android" %}
```java
String userID = sentianceSdk.getUserId();

sentianceSdk.getUserAccessToken(new TokenResultCallback() {
    @Override
    public void onSuccess(Token token) {
        String accessToken = token.getTokenId();
    }

    @Override
    public void onFailure() {
    }
});
```
{% endtab %}
{% endtabs %}

If the token has expired, the SDK will get a new access token before passing it to the callback.

## Failure

Generally, this operation will complete instantly by returning a cached access token, but if a new token has to be obtained from the Sentiance API, there is a possibility it will fail.

Specifically, failure in this case can occur if there is no network connection that can be used to communicate with the Sentiance API.

