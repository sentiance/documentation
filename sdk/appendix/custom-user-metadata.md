# Custom User Metadata

Custom metadata allows you to store text-based key-value user properties into the Sentiance Platform. These keys and values are treated as opaque strings and are meant for retrieval only. There is a limit of 50 properties per user and a limit of 500 characters for keys and values.

Typical examples include custom user and application-related properties you need after the processing.

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
