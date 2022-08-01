# UserCreationFailureReason

Represents the failure reason.

| **SDK\_RESET\_IN\_PROGRESS**     | A user cannot be created while the SDK is being reset.                                                                                                     |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **USER\_CREATION\_IN\_PROGRESS** | User creation is already in progress.                                                                                                                      |
| **USER\_ALREADY\_EXISTS**        | A user already exists. There cannot be more than one Sentiance user at a time on the device. See [`Sentiance#userExists()`](../sentiance.md.md#userexists) |
| **NETWORK\_ERROR**               | A network error occurred.                                                                                                                                  |
| **SERVER\_ERROR**                | A server error occurred.                                                                                                                                   |
| **UNEXPECTED\_ERROR**            | An unexpected error occurred. Check the corresponding [`UserCreationError#getDetails()` ](./#getdetails)for more info.                                     |
| **APP\_SIDE\_LINKING\_FAILED**   | The application failed to complete the user linking step. See [`UserLinker`](../userlinker.md), [`UserLinkerAsync`](../userlinkerasync.md)                 |

