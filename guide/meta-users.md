# Meta Users

## Motivation

On ever install of an app which embeds the Sentiance SDK, our system generates a new User ID. Normally this is not a problem. But in today's world of constantly changing phones and end-users installing/uninstalling an app multiple times, it can be hard to keep track of these multiple User IDs generated on each install, and map them to their corresponding account on your system.

Classically customers have solved this problem by maintaining a one-to-many mapping of their own user account data to the Sentiance User IDs generated on each install.

But this is cumbersome, and requires a lot of work from you, our customer. Moreover, each new install is seen as a new User ID in our system. These users do not share a timeline and the thorough analysis we'd already one is lost on the next iteration.

We can do better.

## Introducing, Meta Users

The Meta User feature \(not to be confused with [Meta Data](../sdk/appendix/custom-user-metadata.md)\) allows you to associate your user's ID \(i.e., the account you already have in your own system\) to the user's ID on Sentiance. 

We introduce a new term, the Install ID. When the SDK initializes, you receive an ID as usual, but instead of calling it a User ID, we shall call it the Install ID, since it is unique to that installation of the app and a re-install would generate a new Install ID.

By linking these disparate Install IDs with a single Person ID on our system, we unify the timelines and maintain all the good data analysis and inference. Furthermore we also associate this Person ID to the account information from your system.

During initialization, the Sentiance SDK authenticates and creates a new install ID to associate with the app. If the app is re-installed or the user moves to another device, a new install ID is created. Meta User is a way to associate these disparate install IDs to one canonical person, using your app's user ID.

## Prerequisites

For the Meta User feature to work it has to be enabled for your app. If you are creating a new app and wish to enable this feature, or have an existing app and want to start using this feature, let us know and we'll enable it for you.

The feature uses a process we call Linking, in which we receive an HTTP call from you telling us which user ID \(from your system\) you wish to associate with a specific install ID. This requires the use of a server token for authentication and thus a server side implementation on your end.

Do not send us the linking request directly from a mobile device. This would require the server token to be present on the mobile device and could lead to a security breach.

## SDK

During initialization of a Meta User enabled app the SDK will call the `link(String)`method of your `MetaUserLinker` object from a background thread, passing to it the SDK **install ID**. In this method you must call your server and send it the **install ID**. Your server must then call ours, sending us the **install ID** and the **external User ID** \(this is the ID of the user on your system\).

For details please check out: [SDK Config for Meta User](../sdk/appendix/meta-users.md#usage)

## API

Check out the [reference for the linking call.](../api-1/rest-api.md#meta-user-link)

If linking succeeds you will receive the Sentiance ID associated with the user. All future associations of an install ID with one of your system's user IDs will return this same Sentiance ID.

If the linking fails, you will be returned an error. For details please check out: [Meta User API Reference](../api-1/rest-api.md#meta-user-link)

### Diagram

![](https://developers.sentiance.com/views/public/docs/assets/rest/MetaUsersScheme.png)

