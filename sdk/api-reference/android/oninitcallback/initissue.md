# InitIssue

Indicates the SDK initialization failure reason.

| **Attributes** |  |
| :--- | :--- |
| **INVALID\_CREDENTIALS** | Your app ID and secret could not be used to create a Sentiance user account. Make sure they are correct, and try again. |
| **CHANGED\_CREDENTIALS** | The app ID and/or secret have changed. The Sentiance SDK does not support changing app credentials. If this was intentional, uninstall the app \(or clear the data\) and retry. |
| **SERVICE\_UNREACHABLE** | An issue was encountered while trying to reach the Sentiance API. Make sure your internet connection is working and retry. |
| **LINK\_FAILED** | An issue was encountered when trying to link the installation ID to the meta-user. |
| **REMOTE\_DISABLED** | This user was remote disabled. If this is not what you expect, double check the rollout settings of your Sentiance app. |

