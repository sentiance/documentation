# MetaUserLinker

This interface is used with MetaUsersLinker.

Learn more about Meta-Users [here](../../appendix/meta-users.md).

### MetaUserLinker API

Linker method will be called during the first ever SDK initialization, and will execute on a background thread. 

| Class | Method |
| :--- | :--- |
| **MetaUserLinker** | ^\(NSString \*installId, void \(^linkSuccess\)\(void\), void \(^linkFailed\)\(void\)\)link |

| Parameter | Description |
| :--- | :--- |
| NSString\* **installId** | A unique Sentiance id representing the current installation. |
| linkSuccess\(\) | should be called if linking is succeeded |
| linkFailed\(\) | should be called if linking is failed |

