# UserContextUpdateListener

{% hint style="info" %}
This interface is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

An interface for handling updates to the user's context. Used with [`UserContextApi.addUserContextUpdateListener(UserContextUpdateListener)`](./#addusercontextupdatelistener)``

## UserContextUpdateListener API

|      |                                                                                                                                                                                                  |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| void | [onUserContextUpdated](usercontextupdatelistener.md#onusercontextupdated) (List<[UserContextUpdateCriteria](usercontextupdatecriteria.md)> criteria, [UserContext](../usercontext/) userContext) |



### `onUserContextUpdated()`

> ```java
> void onUserContextUpdated(List<UserContextUpdateCriteria> criteria, UserContext userContext)
> ```
>
> Returns the new user context.

| Parameters  |                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------ |
| criteria    | A list that filters which [`UserContextUpdateCriteria`](usercontextupdatecriteria.md) to return. |
| userContext | A [`UserContext`](../usercontext/) object that contains the user's context.                      |
