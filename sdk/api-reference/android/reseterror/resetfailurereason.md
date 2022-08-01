# ResetFailureReason

Represents the failure reason.

| **SDK\_INIT\_IN\_PROGRESS** | SDK initialization is in progress. Resetting at this time is not allowed.                                                                  |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **USER\_ALREADY\_LINKED**   | SDK reset is already in progress.                                                                                                          |
| **EXCEPTION\_OR\_ERROR**    | An exception or an error occurred during reset. See the corresponding `throwable` inside [`ResetError#getException().`](./#getexception)`` |
