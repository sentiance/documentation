# MetaUserLinker

This interface is used with [`setMetaUserLinker(MetaUserLinker)`](sdkconfig/sdkconfig-builder.md#setmetauserlinker).

Learn more about Meta-Users [here](../../appendix/meta-users.md).

## MetaUserLinker API

|  |  |
| :--- | :--- |
| boolean | [link](metauserlinker.md#link) \(String installId\) |



### `link()`

> ```java
> boolean link()
> ```
>
> This method will be called during the first ever SDK initialization, and will execute on a background thread.
>
> Returns `true` only if linking succeeds.
>
> | Parameters |  |
> | :--- | :--- |
> | installId | A unique ID set to the current instance of the SDK |

