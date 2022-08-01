# UserLinker

This interface is used with [`UserCreationOptions`](usercreationoptions/).

Learn more about user linking [here](../../appendix/user-linking.md).

## UserLinker API

### `link()`

> ```java
> boolean link(String installId)
> ```
>
> This method will be called when your app needs to handle user linking, normally during the first ever SDK initialization, but also if user linking is enabled afterwards. This method will be executed on a background thread.
>
> Returns `true` only if linking succeeds.

| Parameters |                                                             |
| ---------- | ----------------------------------------------------------- |
| installId  | A unique Sentiance ID representing the current installation |

### NO\_OP

> ```java
> UserLinker NO_OP
> ```
>
> Set this linker in the [`UserCreationOptions`](usercreationoptions/) supplied to [`Sentiance#createUser(UserCreationOptions)`](sentiance.md.md#createuser) to create an unlinked user.
>
> If you wish to link this user at a later time, you can use either one of Sentiance#linkUser(UserLinker), Sentiance#linkUser(UserLinkerAsync), or Sentiance#linkUser(String). However, note that linking a user after its creation has certain limitations (see the below note).
>
> **Note:**
>
> An unlinked Sentiance user cannot be linked to an app user that already exists on the Sentiance Platform (i.e. with an app user identifier that you already supplied to Sentiance during a past linking request). You can only link to an app user that is new to Sentiance. This is because an existing app user will already have a corresponding Sentiance user on the platform, and that Sentiance user cannot be restored here anymore. To restore that user, you must reset the SDK and recreate a linked Sentiance user instead.
