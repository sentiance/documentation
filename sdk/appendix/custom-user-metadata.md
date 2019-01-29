# Custom User Metadata

Custom metadata allows you to store text-based key-value user properties into the Sentiance platform. Examples are custom user IDs and application related properties you need after the processing.

## Example

Here we will add a single field "correlation\_id" to the metadata, with a value of '3a5276ec-b2b2-4636-b893-eb9a9f014938'.

{% tabs %}
{% tab title="iOS" %}
```objectivec
[[SENTSDK sharedInstance] addUserMetadataField:@"correlation_id" value:@"3a5276ec-b2b2-4636-b893-eb9a9f014938"];
```
{% endtab %}

{% tab title="Android" %}
```java
sentianceSdk.addUserMetadataField("correlation_id", "3a5276ec-b2b2-4636-b893-eb9a9f014938");
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The field `"user_id"` is special. When it is set, it shows up in all our exported reports under `metadata` as `metadata.user_id`. Use this to map the users from your app to their Sentiance user ids.
{% endhint %}

