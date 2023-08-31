---
description: >-
  A description of the error codes you might encounter while working with our
  REST API.
---

# Error Codes \(REST API\)

{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

* [CANNOT\_LINK\_EXISTING\_PERSON\_TO\_OTHER\_PERSON](error-codes.md#cannot_link_existing_person_to_other_person)
* [INSTALL\_NOT\_FOUND](error-codes.md#install_not_found)
* [INSTALL\_DOES\_NOT\_BELONG\_TO\_APP](error-codes.md#install_does_not_belong_to_app)
* [INSTALL\_DISABLED](error-codes.md#install_disabled)
* [INSTALL\_DELETED](error-codes.md#install_deleted)
* [INSTALL\_DEACTIVATED](error-codes.md#install_deactivated)
* [INSTALL\_LINKED\_TO\_OTHER\_USER](error-codes.md#install_linked_to_other_user)
* [MULTIPLE\_INSTALLS\_ACTIVE](error-codes.md#multiple_installs_active)
* [USERLINKING\_NOT\_CONFIGURED](error-codes.md#userlinking_not_configured)
* [USER\_DOES\_NOT\_BELONG\_TO\_APP](error-codes.md#user_does_not_belong_to_app)
* [USER\_NOT\_FOUND](error-codes.md#user_not_found)

### CANNOT\_LINK\_EXISTING\_PERSON\_TO\_OTHER\_PERSON

This error code will be returned when a User-Linking REST API request tries to link an active **install\_id** to an existing **external\_id** which already has a linked **install\_id**.

{% hint style="info" %}
This primarily happens when legacy users, who were first created before user linking was introduced in the app, are switching to a new device. Because they were created before user linking was introduced, they got 'hardlinked' to the initial install id. As a result, they cannot be linked to a new device. To resolve this, create a new user under a different Sentiance id.
{% endhint %}

### INSTALL\_NOT\_FOUND

This error code will be returned when the given **install\_id** cannot be found in a User-Linking REST API request.

### INSTALL\_DOES\_NOT\_BELONG\_TO\_APP

This error code will be returned when the given **install\_id**'s **app\_id** doesn't match the given **app\_id** in a User-Linking REST API request.

{% hint style="info" %}
Make sure you've used the right app\_id. Most clients use multiple environments \(production, staging, development, ...\). Make sure you are using the app\_id belonging to the right environment. These are not interchangeable.
{% endhint %}

### INSTALL\_DISABLED

This error code will be returned when the given **install\_id** is found to be disabled by the platform in a User-Linking REST API request.

### INSTALL\_DELETED

This error code will be returned when the given **install\_id** is found to be deleted by the platform in a User-Linking REST API request.

### INSTALL\_DEACTIVATED

This error code will be returned when the given **install\_id** is already linked and is no longer active in a User-Linking REST API request.

### INSTALL\_LINKED\_TO\_OTHER\_USER

This error code will be returned when the given **install\_id** is found to have a linked external\_id while this linked external\_id doesn't match the given **external\_id** in a User-Linking REST API request.

### MULTIPLE\_INSTALLS\_ACTIVE

This error code will be returned when there are two or more active **install\_ids** found in the platform by the given **external\_id** in a User-Linking REST API request.

### USERLINKING\_NOT\_CONFIGURED

This error code will be returned when the app is found to not have user-linking enabled in a User-Linking REST API request.

{% hint style="info" %}
For most apps, User Linking will be turned on by default. If this is not the case for your app, please reach out to Support and they'll set things up for you.
{% endhint %}

### USER\_DOES\_NOT\_BELONG\_TO\_APP

This error code will be returned when the **app\_id** of the given users doesn't match the given **app\_id** in a Custom-Event REST API request.

### USER\_NOT\_FOUND

This error code will be returned when any of the given users cannot be found in the platform in a Custom-Event REST API request.

{% hint style="info" %}
Make sure you've used the right Sentiance id. Most of our REST API queries expect to receive the Sentiance ID, not your external ID.
{% endhint %}

