# MetaUserLinker

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

This interface is used with MetaUsersLinker class.

Learn more about Meta-Users [here](../../appendix/user-linking.md).

### MetaUserLinker API

Linker method will be called during the first ever SDK initialization, and will execute on a background thread. 

```objectivec
typedef void (^MetaUserLinker)(NSString *installId, 
                                void (^linkSuccess) (void), 
                                void (^linkFailed) (void)
                                );
```

| Parameter | Description |
| :--- | :--- |
| installId | A unique Sentiance id representing the current installation. |
| linkSuccess\(\) | should be called if linking is succeeded |
| linkFailed\(\) | should be called if linking is failed |

