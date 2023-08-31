# PoiPlace

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

A place selected from one of our data sources.

## PoiPlace API

### `getCategoryHierarchy()`

> ```java
> @Nullable List<String> getCategoryHierarchy()
> ```
>
> Returns a list of venue categories in hierarchical order, or `null` if not available.
>
> The first item represents the broadest category, with each subsequent item representing a more specific one. For example: \["shop", "food", "grocery", "supermarket"].

### `getLatitude()`

> ```java
> @Nullable Doube getLatitude()
> ```
>
> Returns the place latitude, or `null` if not available.

### `getLongitude()`

> ```java
> @Nullable Doube getLongitude()
> ```
>
> Returns the place longitude, or `null` if not available.

### `getName()`

> ```java
> @Nullable String getName()
> ```
>
> Returns the name of the place, or `null` if not available.

### `getProbability()`

> ```java
> @Nullable Doube getProbability()
> ```
>
> Returns the probability of the place's candidacy, or `null` if not available.
