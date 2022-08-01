# UserLinkingFailureReason

Represents the failure reason.

| **NO\_USER**                   | No user present on the device. Call [`Sentiance#createUser(UserCreationOptions)`](../sentiance.md.md#createuser) to create a user.         |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **USER\_ALREADY\_LINKED**      | The user is already linked.                                                                                                                |
| **NETWORK\_ERROR**             | A network error occurred.                                                                                                                  |
| **SERVER\_ERROR**              | A server error occurred.                                                                                                                   |
| **USER\_DISABLED\_REMOTELY**   | The user is disabled remotely.                                                                                                             |
| **UNEXPECTED\_ERROR**          | An unexpected error occurred. Check the corresponding [UserLinkingError`#getDetails()`](./#getdetails) `` for more info.                   |
| **APP\_SIDE\_LINKING\_FAILED** | The application failed to complete the user linking step. See [`UserLinker`](../userlinker.md), [`UserLinkerAsync`](../userlinkerasync.md) |

