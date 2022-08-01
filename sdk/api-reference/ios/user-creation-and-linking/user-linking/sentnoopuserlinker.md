---
description: >-
  A no-operation user linker. Use this linker to create an unlinked (anonymous)
  Sentiance user.
---

# SENTNoOpUserLinker

Set this linker in the SENTUserCreationOptions supplied to&#x20;

`createUserWithOptions: completionHandler:`&#x20;

method to create an unlinked user.\


&#x20;If you wish to link this user at a later time, you can use either one of&#x20;

`linkUserWithLinker: completionHandler` or&#x20;

`linkUserWithAuthCode: completionHandler:`

However, note that linking a user after its creation has certain limitations.\


An unlinked Sentiance user cannot be linked to an app user that already exists on the Sentiance Platform (i.e. with an app user identifier that you already supplied to Sentiance during a past linking request). You can only link to an app user that is new to Sentiance. This is because an existing app user will already have a corresponding Sentiance user on the platform, and that Sentiance user cannot be restored here anymore. To restore that user, you must reset the SDK and recreate a linked Sentiance user instead.
