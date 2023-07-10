# UserContextApi

Use this API to access and listen to the user's context.

## UserContextApi API

### `addUserContextUpdateListener()`

> ```java
> void addUserContextUpdateListener(UserContextUpdateListener listener)
> ```
>
> Adds a listener to handle updates to the user's context.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

| Parameters |                                                                                                                      |
| ---------- | -------------------------------------------------------------------------------------------------------------------- |
| listener   | A [`UserContextUpdateListener`](usercontextupdatelistener.md) that gets triggered when the user context has changed. |

### `addUserContextUpdateListener()`

> ```java
> void addUserContextUpdateListener(List<UserContextUpdateCriteria> criteria, UserContextUpdateListener listener)
> ```
>
> Adds a listener to handle updates to the user's context, with the option of filtering the context criteria.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

| Parameters |                                                                                                                      |
| ---------- | -------------------------------------------------------------------------------------------------------------------- |
| criteria   | A list that filters which [`UserContextUpdateCriteria`](usercontextupdatecriteria.md) to return.                     |
| listener   | A [`UserContextUpdateListener`](usercontextupdatelistener.md) that gets triggered when the user context has changed. |

### `requestUserContext()`

> ```java
> PendingOperation<UserContext, RequestUserContextError> requestUserContext()
> ```
>
> Retrieves the user's current context.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

### `removeUserContextUpdateListener()`

> ```java
> void removeUserContextUpdateListener(UserContextUpdateListener listener)
> ```
>
> Removes a previously set user context update listener.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

| Parameters |                                                                                                                      |
| ---------- | -------------------------------------------------------------------------------------------------------------------- |
| listener   | A [`UserContextUpdateListener`](usercontextupdatelistener.md) that gets triggered when the user context has changed. |



