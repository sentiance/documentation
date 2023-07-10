# UserContextUpdateListener

An interface for handling updates to the user's context. Used with [`UserContextApi.addUserContextUpdateListener(UserContextUpdateListener)`](./#addusercontextupdatelistener)

## UserContextUpdateListener API

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
