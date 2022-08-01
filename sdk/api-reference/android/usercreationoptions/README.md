# UserCreationOptions

The UserCreationOptions class allows you to specify SDK user creation options. This class is used with [`Sentiance.createUser(UserCreationOptions)`](../sentiance.md.md#createuser).

See: [UserCreationOptions.Builder](usercreationoptions.builder.md).

## UserCreationOptions API

### `getPlatformUrl()`

> ```java
> String getPlatformUrl()
> ```
>
> Returns the Sentiance Platform URL.

### `getAuthCode()`

> ```java
> String getAuthCode()
> ```
>
> Returns the authentication code that should be used when creating a user. Returns `null` if it wasn't set.

### getAppId`()`

> ```java
> String getAppId()
> ```
>
> Returns the Sentiance app ID that should be used when creating a user. Returns `null` if it wasn't set.

### getSecret`()`

> ```java
> String getSecret()
> ```
>
> Returns the Sentiance app secret that should be used when creating a user. Returns `null` if it wasn't set.



### getUserLinkerAsync`()`

> ```java
> UserLinkerAsync getUserLinkerAsync()
> ```
>
> Returns the user linker that should be invoked during the user creation process. Returns `null` if it wasn't set.



### getUserLinker`()`

> ```java
> UserLinker getUserLinker()
> ```
>
> Returns the user linker that should be invoked during the user creation process. Returns `null` if it wasn't set.
