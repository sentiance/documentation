# InitializationFailureReason

Represents the initialiation failure.

| **UNSUPPORTED\_OS\_VERSION**       | The SDK does not support the existing OS version.                                                                                                 |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **REINITIALIZATION\_NOT\_ALLOWED** | Reinitialization is not allowed while a Sentiance user exists, unless done across app restarts or after an SDK [reset](../sentiance.md.md#reset). |
| **EXCEPTION\_OR\_ERROR**           | An exception or an error occurred during initialization. See [InitializationResult#getThrowable()](./#getthrowable).                              |
| **SDK\_RESET\_IN\_PROGRESS**       | Cannot initialize the SDK while it's being reset. Wait for the the reset operation to complete first.                                             |

