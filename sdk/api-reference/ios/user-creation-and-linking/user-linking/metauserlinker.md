# SENTUserLinker

Implement this to handle the linking of your app user to a Sentiance user, during user creation.

For details on how to link users, see [here.](https://docs.sentiance.com/sdk/appendix/user-linking)



| Parameter     | Description                                                                           |
| ------------- | ------------------------------------------------------------------------------------- |
| installId     | A unique Sentiance id representing the current installation.                          |
| linkSuccess() | Pass this closure which will be called if linking succeeded on the Sentiance backend. |
| linkFailure() | This closure will be called if linking failed.                                        |

