# Meta-Users

## Motivation

The Meta User feature allows you to associate your user's ID on your own app to the user's ID on Sentiance. During initialization, the Sentiance SDK authenticates and creates a new install ID to associate with the app. If the app is re-installed or the user moves to another device, a new install ID is created. Meta User is a way to associate these disparate install IDs to one canonical person, using your app's user ID.

## Prerequisites

For the Meta User feature to work it has to be enabled for your app. If you are creating a new app and wish to enable this feature, or have an existing app and want to start using this feature, let us know and we'll enable it for you.

The feature uses a process we call Linking, in which we receive an HTTP call from you telling us which user ID \(from your system\) you wish to associate with a specific install ID. This requires the use of a server token for authentication and thus a server side implementation on your end.

Do not send us the linking request directly from a mobile device. This would require the server token to be present on the mobile device and could lead to a security breach.

## SDK

During initialization of a Meta User enabled app the SDK will call the `link(String)`method of your `MetaUserLinker` object from a background thread, passing to it the SDK **install ID**. In this method you must call your server and send it the **install ID**. Your server must then call ours, sending us the **install ID** and the **external User ID** \(this is the ID of the user on your system\).

For details please check out: [SDK Config for Meta User](../sdk/appendix/meta-users.md)

## API

Our linking API lives at:`https://api.sentiance.com/users/<install_id>/link`

Send us a **POST** request substituting the **install ID** in the url and a body:

```javascript
{
  "external_id": "your-user-id"
}
```

If linking succeeds you will receive the Sentiance ID associated with the user. All future associations of an install ID with one of your system's user IDs will return this same Sentiance ID.

If the linking fails, you will be returned an error. For details please check out: [Meta User API Reference](https://developers.sentiance.com/docs/metausers-api)

### Diagram

![](https://developers.sentiance.com/views/public/docs/assets/rest/MetaUsersScheme.png)

