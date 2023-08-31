# REST API Reference

'{% hint style='danger' %} This document refers to deprecated parts of the platform and has been left intact to help customers with legacy integrations. In order to access the latest platform features and documentation, please go to https://docs.sentiance.com. {% endhint %}

All endpoints speak JSON. A `Content-Type` header with value `application/json` is expected to always be present.

The base url is `https://api.sentiance.com/<version>/` for all REST endpoints, where the currently supported versions are `v2` and `v3`. `v1` has been fully deprecated. Note that not all APIs are common between `v2` and `v3` versions.

**Note:** The [user deletion API](rest-api.md#delete-user) is the only exception to the versioned endpoints rule. It stands on its own as `DELETE /users/:user_id`

For details on how to authenticate requests, have a look at the [Authentication and Authorization page](../important-topics/authentication-and-authorization.md).

{% hint style="danger" %}
For other environments, please ask your sales representative or [support@sentiance.com](mailto:support@sentiance.com) for the custom endpoint linked to your environment. 
{% endhint %}

### V2 Endpoints

{% api-method method="get" host="" path="/v2/segment\_definitions" %}
{% api-method-summary %}
Segment Definitions
{% endapi-method-summary %}

{% api-method-description %}
Fetches all Moment Definitions available on the platform.  
**Does not require authentication.**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "SegmentDefinition",
        "id": "lifestyle.culture_buff",
        "display_name": "Culture buff",
        "description": "Person who like to visit musea, operas, arts centres, etc."
    },
    {
        "type": "SegmentDefinition",
        "id": "lifestyle.resto_lover",
        "display_name": "Resto-lover",
        "description": "Someone who likes eating out"
    },
    {
        "type": "SegmentDefinition",
        "id": "lifestyle.sportive",
        "display_name": "Sportive",
        "description": "Someone who sports regularly."
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/moment\_definitions" %}
{% api-method-summary %}
Moment Definitions
{% endapi-method-summary %}

{% api-method-description %}
Fetches all Moment Definitions available on the platform.  
**Does not require authentication.**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "MomentDefinition",
        "id": "commute_from_work",
        "display_name": "Commute to home",
        "description": "This moment will be active when the user leaves his work and the prediction is that he is going home."
    },
    {
        "type": "MomentDefinition",
        "id": "commute_from_home",
        "display_name": "Commute to work",
        "description": "This moment will be active when the user leaves his home and the prediction is that he is going to work."
    },
    {
        "type": "MomentDefinition",
        "id": "working_at_work",
        "display_name": "Working at work",
        "description": "This moment will be active when the user is working at his work location. If the prediction is that he is working and he goes away for a short time the moment will stay active."
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/me" %}
{% api-method-summary %}
User's Own Profile
{% endapi-method-summary %}

{% api-method-description %}
When called with a User Token, returns the user's own data. It fails if an API Key is used.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "type": "ControlUser",
    "id": "5c9417700000000000000000",
    "can_login": true,
    "created_at": "2016-11-29T23:00:49.621+00:00",
    "sdk": {
        "type": "UserSdkSettings",
        "flavor": "offline_driving",
        "killswitch_action": "enable_sdk",
        "debug_logging": null
    },
    "application_id": "5c9417700000000000000000",
    "email": "name@email.com",
    "account_roles": [
        {
            "type": "UserAccountRole",
            "user_id": "5c9417700000000000000000",
            "account_id": "5c9417700000000000000000",
            "role": "basic",
            "account": {
                "id": "5c9417700000000000000000",
                "display_name": "Example",
                "created_at": "2015-04-02T14:22:24.936+00:00"
            }
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id" %}
{% api-method-summary %}
Profile by User ID
{% endapi-method-summary %}

{% api-method-description %}
Can be used with both User Token and API Key to retrieve profile data of a user identified by their ID.  
If a User Token is used, the calling user must have permission to view the called user's data.  
If an API Key is used, the user whose data is being fetched must belong to the App to which the API Key belongs to.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose profile is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "type": "ControlUser",
    "id": "5c9417700000000000000000",
    "can_login": true,
    "created_at": "2016-11-29T23:00:49.621+00:00",
    "sdk": {
        "type": "UserSdkSettings",
        "flavor": "offline_driving",
        "killswitch_action": "enable_sdk",
        "debug_logging": null
    },
    "application_id": "5c9417700000000000000000",
    "email": "name@email.com",
    "account_roles": [
        {
            "type": "UserAccountRole",
            "user_id": "5c9417700000000000000000",
            "account_id": "5c9417700000000000000000",
            "role": "basic",
            "account": {
                "id": "5c9417700000000000000000",
                "display_name": "Example",
                "created_at": "2015-04-02T14:22:24.936+00:00"
            }
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/events?from=:from&to=:to" %}
{% api-method-summary %}
Timeline Events
{% endapi-method-summary %}

{% api-method-description %}
Returns all events on the timeline for a user from a specified start date to a specified end date.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose timeline is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="from" type="string" required=true %}
Include results from this date.  
  
**Format**: YYYY-MM-DD  
**Example**: 2019-01-01
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="string" required=true %}
Include results up to this date.  
  
**Format**: YYYY-MM-DD  
**Example**: 2019-01-02
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "Transport",
        "start": "2019-03-22T08:37:45.000+01:00",
        "end": "2019-03-22T09:39:00.000+01:00",
        "analysis_type": "indepth",
        "event_id": "b699235f9e1e0b140b3d531466f0b79811044bb22925ed0e4d420e3fa44d65d6",
        "mode": "car",
        "distance": 51918,
        "behavior_features": {
            "phone_handling": 396000,
            "distance_during_annotations": 46426
        }
    },
    {
        "type": "Stationary",
        "start": "2019-03-21T20:08:00.000+01:00",
        "end": "2019-03-22T08:37:45.000+01:00",
        "analysis_type": "indepth",
        "event_id": "37954206-7468-407f-bfa6-33c9ddaab785",
        "latitude": 51.78561,
        "longitude": 41.49692,
        "duration": 44985000,
        "location": {
            "type": "StationaryLocation",
            "significance": "home",
            "place": {
                "type": "LocationPlaceCandidate",
                "name": "Wonder Palace",
                "categories": [
                    "building",
                    "residential"
                ]
            }
        },
        "address": {
            "type": "Address",
            "country": "België / Belgique / Belgien",
            "city": "Ostend",
            "city_type": "TOWN"
        }
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/events/:start" %}
{% api-method-summary %}
Timeline Event by Start Time
{% endapi-method-summary %}

{% api-method-description %}
**Note: This has been deprecated in favour of EventID based retrieval.**  
Returns a single Event corresponding to the start time of the event.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose event is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="start" type="string" required=true %}
ISO Formatted Date String. Event fetched is the one that matches this timestamp.  
  
**Example**: 2019-03-21T20:08:00.000+01:00
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "Stationary",
        "start": "2019-03-21T20:08:00.000+01:00",
        "end": "2019-03-22T08:37:45.000+01:00",
        "analysis_type": "indepth",
        "event_id": "37954206-7468-407f-bfa6-33c9ddaab785",
        "latitude": 51.78561,
        "longitude": 41.49692,
        "duration": 44985000,
        "location": {
            "type": "StationaryLocation",
            "significance": "home",
            "place": {
                "type": "LocationPlaceCandidate",
                "name": "Wonder Palace",
                "categories": [
                    "building",
                    "residential"
                ]
            }
        },
        "address": {
            "type": "Address",
            "country": "België / Belgique / Belgien",
            "city": "Ostend",
            "city_type": "TOWN"
        }
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/events/:start/trajectory" %}
{% api-method-summary %}
Trajectories by Start Time
{% endapi-method-summary %}

{% api-method-description %}
**Note: This has been deprecated in favour of EventID based retrieval. Check below.**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="start" type="string" required=true %}
ISO Formatted Date String. Transport whose Trajectories are fetched is the one that matches this timestamp.  
  
**Example**: 2019-02-22T08:37:45.000+01:00
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "waypoints": [
        {
            "type": "TrajectoryWaypoint",
            "latitude": 50.78568,
            "longitude": 4.49673,
            "timestamp": "2019-03-22T08:37:45.000+01:00",
            "road_type": "residential",
            "speed": 23,
            "distance": 65.5,
            "speed_limit": 50
        },
        {
            "type": "TrajectoryWaypoint",
            "latitude": 50.78618,
            "longitude": 4.49722,
            "timestamp": "2019-03-22T08:37:54.714+01:00",
            "road_type": "residential",
            "speed": 21.2,
            "distance": 9.2,
            "speed_limit": 50
        },
        {
            "type": "TrajectoryWaypoint",
            "latitude": 50.78624,
            "longitude": 4.49731,
            "timestamp": "2019-03-22T08:37:56.080+01:00",
            "road_type": "residential",
            "speed": 20.8,
            "distance": 7.9,
            "speed_limit": 50
        }
    ],
    "encoded": "oa~tHqgmZcBaBKQIOCOAO@_Bc@C{@EYGAFGPs@zB{BnHy@|BUr@Qh@Y|@Wz@oA|DsAhEEJCLcBhFs@zBs@xBKZk@fBy@fCELEJk@jBa@nAu@zBq@zBCDUr@uBvGY`AITIX?BI`@]tBMt@GXIRMRa@`AOPk@|A]`AITk@fBkCrIYbAUv@yAzE_CtFi@fAKRkBhE?@Ul@wAfEsAfEiCdIs@zBOf@m@`AQZUv@]bAkAxDu@~Ba@jAa@lAi@~@g@bAQROHM?KAGAWMMIsAs@}A{@]QmDmBs@a@s@_@kAo@OEo@Q}DwByI}EwBiA}CeBgH{D{CaBwMgHWMmJgFkBcAaOgIeBaAmKiGgCkAoAe@eBq@eCg@gAImCKeEMeAGkAMu@QYK]MmAg@_C{A{YoPk@[aFuBoE{@_EOqF@uKVcBDsO\\}CVuCf@cBf@uChAiBbAGB}A~@cHxEeJrGcDxB{CvB}AfAq@b@q@d@kAv@kE|Ba@RkBt@eA\\s@VgE~@cBX}ARsAJaABy@DuAD{BF}@F_AFwAN{@Lg@JoCx@mAb@{Ap@kAl@mEfC}AbA}A`AwCdBoAt@mAr@YR_I|EoFhDiDvBaDpBiCbBsAx@eDjBeAj@WTe@Vc@V_FzCeHdEc@VkCzAqBnAwA|@{CjBcAn@mDtBqHnEcC|@{B^S@wAJoBFqBBsBLsCl@}BhA_CbByDrDgBbBeB`BaB|A_BpA_FtE}I|HQNaElEcDtE{BfE_AtBoAlDaBvEiGpQsBhG{BrGcChHeApB{@zB}@hBu@fAk@l@_@Xm@d@w@Xq@PcAHy@?A?g@Gi@Mc@Ms@]o@c@e@a@e@m@m@k@e@iAy@oCw@{C}@oDo@mC[gAsDyNoAmEiB{FEO}BuGmBeEcA{BwE{I[g@eAkBiE{FsCgDoCiC}A}A}@w@c@_@aBsAwAgAmCoBgBqAUQqByAcCgBwFaEAA}@s@cBmAkDeCyG}EaMaJwAcAqAaA_[_UuMqJ{DyCuBsAmBwAiBqAqAaA{BeBkGkEcTwOcAu@wImGcAq@yGaFiLeIiBoAsQqJ{LsEyAi@uPwFaPoFeEuAaPcF}GgByDm@kFy@qDc@qDOiFSoF@uEPkAFwALiFh@mB\\qDt@kIrBgJlDE@wEvBsEfCaAp@[R}DnCiBtAuCdCsCjC}B`CgBlBmGtHmFvHS\\_@h@uExHkEhIcDlGaCzEuFfJmCtDsDzEwB|BiBtBgG`HwHzIoB~BuDdEoAtAcEpEuEdFyArAyH~GeC|BkB|AsC~BoBbB{@p@wDvCQLWPqBtAyAbAwJrF_CpAcCtA}BpAk@ZOH}BpAcExBaAh@aBv@kCzAk@Ze@VoAp@uAr@mCrAeBz@]NmHzCaF|AYH_GtAcHjAk@J}N~@gFEW?eCEyEWaKcAYIsEcAkBa@c@Kk@SkAa@wDqAyEsBk@WsG_DmCsAeAk@aDcBa@S_@SsAq@}EcCYQmAk@kAg@e@S}@_@eAc@wAg@s@UkCs@gDi@gAGwCOkDCeADoAB}C^k@Jw@NwAXaAXUFiA\\_Bj@eBj@cDtAsAl@c@TwKzEaQxHyIzDoEnBaBt@_FhBeKxDwA`@yCz@sA`@y@VcE~@uBd@qIvAaC^yFp@yF`@G?oG\\aCF_EDyDD}PIK?qDAg@SaAGeAA}EA[AmD?aLCSGICEAKEA?ICMw@UuAIs@Is@KkAImBMwE?]Ao@EqAE{AQ\\KFU`@BpANN@@RNBbA?pAFdCJfCPhB?BBLBZBLVfBA^?V?b@GZQ^_@LwBv@qCbAwGjDD\\kBr@wHtCsBx@_C`AyM~EkC`AgFlBgJlDeXdKq@ViG|BwTlIwAh@iGtBaEdAiFvAuEx@oCf@gFx@eCVcFp@uHf@O@}DBwCDqBBeCBkCD}CBU?Y?qA@aZLeA@s@DI?M?gA@oNH{FD{@@_ADoGDcBBsDFkHDuCHoCHoA@yA@eCLsCVsBZSD{Bp@eA^eAb@iBz@iDnBiBdAeAp@_Al@sJzFy@d@aKjGsNpI}FnDsLhHeIbFmAv@kHhEq@`@}NbJsElCmCzAoB`AgDpAC@uBj@yA^UDeCZ}ALuCCS?cCKeAGkBOcAIwD_@gGm@}@KuEc@kHmAcGyByHsFwFmDs@]k@Ww@UoAWcCU}CCiDT_Dn@aC|@_IxCaHrCU\\]NkDpAoEbB}HtCkAb@{ElBqCdAc@PmAf@IBKFQHk@RMDy@XAr@BbBDVLl@Lf@Rr@Nb@HZJl@D^Jx@?bBIhBAVEXKt@Ql@a@KGAyB_AQImCcAQGWKgBi@OUIEOEWMQZELAJMf@Mb@WFw@Z_@RKLc@R??"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/events/:start/behavior\_scores" %}
{% api-method-summary %}
Behavior Scores by Start Time
{% endapi-method-summary %}

{% api-method-description %}
**Note: This has been deprecated in favour of EventID based retrieval. Check below.**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=false %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="start" type="string" required=false %}
ISO Formatted Date String. Transport whose Behavior Scores are fetched is the one that matches this timestamp.  
  
**Example:** 2019-02-22T08:37:45.000+01:00
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "type": "CarBehaviorScores",
    "overall": 0.79,
    "smooth": 0.79,
    "legal": 0.72,
    "anticipative": 0.86,
    "hard_accel": 0.9,
    "hard_brake": 0.65,
    "hard_events": 0.85,
    "hard_turn": 0.95,
    "legal_v2": 0.79,
    "smooth_v2": 0.78,
    "anticipative_v2": 0.85
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/events/:start/behavior\_annotations" %}
{% api-method-summary %}
Behavior Annotations by Start Time
{% endapi-method-summary %}

{% api-method-description %}
**Note: This has been deprecated in favor of EventID based retrieval. Check below.**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="start" type="string" required=true %}
ISO Formatted Date String. Transport whose Behavior Annotations are fetched is the one that matches this timestamp.  
  
**Example**: 2019-02-22T08:37:45.000+01:00
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "BoundaryBehaviorAnnotation",
        "start": "2019-03-22T08:37:48.303000+01:00",
        "end": "2019-03-22T08:40:35.303000+01:00",
        "quality": "valid"
    },
    {
        "type": "AccelerationBehaviorAnnotation",
        "start": "2019-03-22T08:38:10.781456+01:00",
        "end": "2019-03-22T08:38:16.102097+01:00",
        "acceleration": "accelerate",
        "duration": 5321,
        "magnitude": 0.189,
        "path": [
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78664,
                "longitude": 4.49807
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78679,
                "longitude": 4.49808
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78685,
                "longitude": 4.4981
            }
        ]
    },
    {
        "type": "TurnBehaviorAnnotation",
        "start": "2019-03-22T08:38:16.866289+01:00",
        "end": "2019-03-22T08:38:21.479824+01:00",
        "duration": 4614,
        "maneuver": "left_turn",
        "magnitude": 0.467,
        "path": [
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78688,
                "longitude": 4.49811
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78692,
                "longitude": 4.49812
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78693,
                "longitude": 4.49808
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78697,
                "longitude": 4.49799
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78703,
                "longitude": 4.49785
            }
        ]
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/segments" %}
{% api-method-summary %}
User's Segments
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "GenericSegment",
        "segment_definition_id": "lifestyle.brand_loyalty.supermarket",
        "explanation_you": "Because you usually shop at colruyt overijse"
    },
    {
        "type": "GenericSegment",
        "segment_definition_id": "mobility.long_commuter",
        "explanation_you": "Because your commute distance from Overijse to Antwerpen is about 52.0 km"
    },
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/moments?from=:from&to=:to" %}
{% api-method-summary %}
Moment History
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="from" type="string" required=true %}
Include results from this date.  
  
**Format**: YYYY-MM-DD  
**Example**: 2019-03-21
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="string" required=true %}
Include results up to this date.  
  
**Format**: YYYY-MM-DD  
**Example**: 2019-03-22
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "GenericMoment",
        "start": "2019-03-22T14:26:00.000+01:00",
        "end": null,
        "moment_definition_id": "afternoon",
        "analysis_type": "preliminary"
    },
    {
        "type": "GenericMoment",
        "start": "2019-03-22T12:31:00.000+01:00",
        "end": "2019-03-22T14:26:00.000+01:00",
        "moment_definition_id": "lunch",
        "analysis_type": "preliminary"
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/active\_moments" %}
{% api-method-summary %}
Active Moments
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "GenericMoment",
        "start": "2019-03-22T14:26:00.000+01:00",
        "end": null,
        "analysis_type": "preliminary",
        "moment_definition_id": "afternoon"
    },
    {
        "type": "GenericMoment",
        "start": "2019-03-22T09:39:00.000+01:00",
        "end": null,
        "analysis_type": "preliminary",
        "moment_definition_id": "working_at_work"
    },
    {
        "type": "CityMoment",
        "start": "2019-03-22T09:39:00.000+01:00",
        "end": null,
        "analysis_type": "preliminary",
        "moment_definition_id": "city_name",
        "city_name": "Antwerpen"
    },
    {
        "type": "CountryMoment",
        "start": "2019-03-18T20:08:00.000+01:00",
        "end": null,
        "analysis_type": "preliminary",
        "moment_definition_id": "country",
        "country_name": "België / Belgique / Belgien"
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/location\_clusters" %}
{% api-method-summary %}
Location Clusters
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "LocationCluster",
        "last_visit": "2019-03-21T08:51:00+01:00",
        "latitude": 50.78561,
        "longitude": 4.49692,
        "radius": 39,
        "is_poi": true,
        "significance": "home",
        "address": {
            "type": "Address",
            "country": "België / Belgique / Belgien",
            "city": "Overijse",
            "city_type": null
        },
        "place": {
            "type": "LocationPlaceCandidate",
            "name": null,
            "categories": [
                "building",
                "residential"
            ]
        }
    },
    {
        "type": "LocationCluster",
        "last_visit": "2019-03-21T12:59:00+01:00",
        "latitude": 51.19655,
        "longitude": 4.40808,
        "radius": 98,
        "is_poi": true,
        "significance": "work",
        "address": {
            "type": "Address",
            "country": "België / Belgique / Belgien",
            "city": "Antwerpen",
            "city_type": null
        },
        "place": {
            "type": "LocationPlaceCandidate",
            "name": "Sentiance HQ",
            "categories": [
                "office",
                "company"
            ]
        }
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/location" %}
{% api-method-summary %}
Location
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "type": "Waypoint",
    "latitude": 51.19766,
    "longitude": 4.41042,
    "timestamp": "2019-03-22T14:04:31.929+01:00"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/car\_behavior" %}
{% api-method-summary %}
Aggregated Behavior Scores
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "type": "UserCarBehavior",
    "scores": {
        "l7d": {
            "type": "ZoneCarBehaviorScores",
            "all": {
                "type": "CarBehaviorScores",
                "overall": 0.743,
                "smooth": 0.75,
                "legal": 0.68,
                "anticipative": 0.8,
                "focus": 0.95,
                "mounted": 0.05,
                "hard_accel": 0.85,
                "hard_brake": 0.84,
                "hard_events": 0.74,
                "hard_turn": 0.89,
                "legal_v2": 0.67,
                "smooth_v2": 0.74,
                "anticipative_v2": 0.77
            },
            "motorway": {
                "type": "CarBehaviorScores",
                "overall": 0.44,
                "smooth": -1,
                "legal": 0.44,
                "anticipative": -1,
                "hard_accel": 0.93,
                "hard_brake": 0.9,
                "hard_events": 0.79,
                "hard_turn": 0.95,
                "legal_v2": 0.31,
                "smooth_v2": 0.84,
                "anticipative_v2": 0.92
            },
            "city": {
                "type": "CarBehaviorScores",
                "overall": 0.97,
                "smooth": -1,
                "legal": 0.97,
                "anticipative": -1,
                "hard_accel": 0.93,
                "hard_brake": 0.99,
                "hard_events": 0.68,
                "hard_turn": 0.97,
                "legal_v2": 0.98,
                "smooth_v2": 0.59,
                "anticipative_v2": 0.71
            },
            "non_city": {
                "type": "CarBehaviorScores",
                "overall": 0.99,
                "smooth": -1,
                "legal": 0.99,
                "anticipative": -1,
                "hard_accel": 0.91,
                "hard_brake": 0.89,
                "hard_events": 0.65,
                "hard_turn": 0.93,
                "legal_v2": 0.98,
                "smooth_v2": 0.58,
                "anticipative_v2": 0.74
            },
            "total": {
                "type": "CarBehaviorScores",
                "overall": 0.783,
                "smooth": 0.75,
                "legal": 0.8,
                "anticipative": 0.8,
                "hard_accel": 0.92,
                "hard_brake": 0.93,
                "hard_events": 0.71,
                "hard_turn": 0.95,
                "legal_v2": 0.76,
                "smooth_v2": 0.67,
                "anticipative_v2": 0.79
            }
        },
        "past": {
            "type": "ZoneCarBehaviorScores",
            "all": {
                "type": "CarBehaviorScores",
                "overall": 0.747,
                "smooth": 0.8,
                "legal": 0.65,
                "anticipative": 0.79,
                "focus": 0.96,
                "mounted": 0.33,
                "hard_accel": 0.87,
                "hard_brake": 0.88,
                "hard_events": 0.78,
                "hard_turn": 0.91,
                "legal_v2": 0.57,
                "smooth_v2": 0.79,
                "anticipative_v2": 0.78
            },
            "motorway": {
                "type": "CarBehaviorScores",
                "overall": 0.38,
                "smooth": -1,
                "legal": 0.38,
                "anticipative": -1,
                "hard_accel": 0.95,
                "hard_brake": 0.9,
                "hard_events": 0.83,
                "hard_turn": 0.96,
                "legal_v2": 0.28,
                "smooth_v2": 0.85,
                "anticipative_v2": 0.91
            },
            "city": {
                "type": "CarBehaviorScores",
                "overall": 0.93,
                "smooth": -1,
                "legal": 0.93,
                "anticipative": -1,
                "hard_accel": 0.94,
                "hard_brake": 0.97,
                "hard_events": 0.62,
                "hard_turn": 0.97,
                "legal_v2": 0.98,
                "smooth_v2": 0.61,
                "anticipative_v2": 0.7
            },
            "non_city": {
                "type": "CarBehaviorScores",
                "overall": 0.96,
                "smooth": -1,
                "legal": 0.96,
                "anticipative": -1,
                "hard_accel": 0.92,
                "hard_brake": 0.95,
                "hard_events": 0.69,
                "hard_turn": 0.93,
                "legal_v2": 0.97,
                "smooth_v2": 0.67,
                "anticipative_v2": 0.73
            },
            "total": {
                "type": "CarBehaviorScores",
                "overall": 0.783,
                "smooth": 0.8,
                "legal": 0.76,
                "anticipative": 0.79,
                "hard_accel": 0.94,
                "hard_brake": 0.94,
                "hard_events": 0.71,
                "hard_turn": 0.95,
                "legal_v2": 0.74,
                "smooth_v2": 0.71,
                "anticipative_v2": 0.78
            }
        }
    },
    "features": {
        "type": "UserCarBehaviorFeatures",
        "l7d": {
            "type": "TimeWindowUserCarBehaviorFeatures",
            "phone_handling": 181200,
            "distance": 557301
        },
        "past": {
            "type": "TimeWindowUserCarBehaviorFeatures",
            "phone_handling": 137400,
            "distance": 5079771
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v2/users/:user\_id/anomalies?from=:from&to=:to" %}
{% api-method-summary %}
Anomaly History
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="from" type="string" required=true %}
Include results from this date.  
  
**Format**: YYYY-MM-DD  
**Example**: 2019-03-21
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="string" required=true %}
Include results up to this date.  
  
**Format**: YYYY-MM-DD  
**Example**: 2019-03-21
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "AggregatedDurationAnomaly",
        "start": "2019-03-21T00:00:00+00:00",
        "end": "2019-03-21T23:59:59.999999+00:00",
        "analysis_type": "processed",
        "sigma": 597.098,
        "probability": 1,
        "anomaly": "stationary_location_significance_day_part_duration",
        "observed_duration": null,
        "expected_duration": 7675,
        "period": "day",
        "day_part": "evening",
        "place_category": null,
        "location_significance": "work",
        "transport_mode": null,
        "transport_mode_category": null,
        "moment_definition_id": null
    },
    {
        "type": "AggregatedDurationAnomaly",
        "start": "2019-03-21T00:00:00+00:00",
        "end": "2019-03-21T23:59:59.999999+00:00",
        "analysis_type": "processed",
        "sigma": null,
        "probability": 1,
        "anomaly": "stationary_location_significance_day_part_duration",
        "observed_duration": null,
        "expected_duration": 14340,
        "period": "day",
        "day_part": "noon",
        "place_category": null,
        "location_significance": "work",
        "transport_mode": null,
        "transport_mode_category": null,
        "moment_definition_id": null
    },
    {
        "type": "AggregatedDurationAnomaly",
        "start": "2019-03-21T00:00:00+00:00",
        "end": "2019-03-21T23:59:59.999999+00:00",
        "analysis_type": "processed",
        "sigma": 1224.012,
        "probability": 1,
        "anomaly": "stationary_location_significance_duration",
        "observed_duration": null,
        "expected_duration": 34446,
        "period": "day",
        "day_part": null,
        "place_category": null,
        "location_significance": "work",
        "transport_mode": null,
        "transport_mode_category": null,
        "moment_definition_id": null
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v2/users/:install\_id/link" %}
{% api-method-summary %}
User Link
{% endapi-method-summary %}

{% api-method-description %}
Used to link an Install ID to your system's UserID. The JSON body should contain a single parameter as described below.  
Check out the guide for further details on how User Linking work and how it can benefit you.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="install\_id" type="string" required=true %}
The ID of the user returned by the SDK into the Linker's callback function.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Unlike other endpoints, which can be called with both a user token and an API Key, this endpoint can ONLY be called with an API Key with \`user.link\` scope. User tokens will be rejected.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="external\_id" type="string" required=true %}
This is the unique ID of the user in your system.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The returned \`person\_id\` is linked to all installs for the same user, going forward and should be used thenceforth.
{% endapi-method-response-example-description %}

```javascript
{
  "id": "5a18fc4b0962209e0000000d"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "message": "Install does not belong to this application.",
  "errorCode": "INSTALL_DOES_NOT_BELONG_TO_APP",
  "ref": "403b03b1-35ea-4ae4-af0a-7ebb65211543"
}

{
  "message": "Install is disabled.",
  "errorCode": "INSTALL_DISABLED",
  "ref": "403b03b1-35ea-4ae4-af0a-7ebb65211543"
}

{
  "message": "Install is deleted.",
  "errorCode": "INSTALL_DELETED",
  "ref": "403b03b1-35ea-4ae4-af0a-7ebb65211543"
}

{
  "message": "This install is already in use, linking to another install is not possible.",
  "errorCode": "CANNOT_LINK_EXISTING_PERSON_TO_OTHER_PERSON",
  "ref": "403b03b1-35ea-4ae4-af0a-7ebb65211543"
}

{
  "message": "Install linked to another user.",
  "errorCode": "INSTALL_LINKED_TO_OTHER_USER",
  "ref": "403b03b1-35ea-4ae4-af0a-7ebb65211543"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "message": "Install was not found by the install ID provided.",
  "errorCode": "INSTALL_NOT_FOUND",
  "ref": "403b03b1-35ea-4ae4-af0a-7ebb65211543"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### V3 Endpoints

{% api-method method="get" host="" path="/v3/users/:user\_id/events/:event\_id" %}
{% api-method-summary %}
Timeline Event by EventId
{% endapi-method-summary %}

{% api-method-description %}
Returns a single Event based on the type and ID provided.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose event is being retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="event\_id" type="string" required=true %}
ID of the event being retrieved. This will be present in the **event\_id** field of the 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "Stationary",
        "start": "2019-03-21T20:08:00.000+01:00",
        "end": "2019-03-22T08:37:45.000+01:00",
        "analysis_type": "indepth",
        "event_id": "37954206-7468-407f-bfa6-33c9ddaab785",
        "latitude": 51.78561,
        "longitude": 41.49692,
        "duration": 44985000,
        "location": {
            "type": "StationaryLocation",
            "significance": "home",
            "place": {
                "type": "LocationPlaceCandidate",
                "name": "Wonder Palace",
                "categories": [
                    "building",
                    "residential"
                ]
            }
        },
        "address": {
            "type": "Address",
            "country": "België / Belgique / Belgien",
            "city": "Ostend",
            "city_type": "TOWN"
        }
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v3/users/:user\_id/events/:event\_id/trajectory" %}
{% api-method-summary %}
Trajectories by EventID
{% endapi-method-summary %}

{% api-method-description %}
Retrieve Trajectories of a Transport by its EventID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="event\_id" type="string" required=true %}
ID of the Transport whose Trajectories are being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "waypoints": [
        {
            "type": "TrajectoryWaypoint",
            "latitude": 50.78568,
            "longitude": 4.49673,
            "timestamp": "2019-03-22T08:37:45.000+01:00",
            "road_type": "residential",
            "speed": 23,
            "distance": 65.5,
            "speed_limit": 50
        },
        {
            "type": "TrajectoryWaypoint",
            "latitude": 50.78618,
            "longitude": 4.49722,
            "timestamp": "2019-03-22T08:37:54.714+01:00",
            "road_type": "residential",
            "speed": 21.2,
            "distance": 9.2,
            "speed_limit": 50
        },
        {
            "type": "TrajectoryWaypoint",
            "latitude": 50.78624,
            "longitude": 4.49731,
            "timestamp": "2019-03-22T08:37:56.080+01:00",
            "road_type": "residential",
            "speed": 20.8,
            "distance": 7.9,
            "speed_limit": 50
        }
    ],
    "encoded": "oa~tHqgmZcBaBKQIOCOAO@_Bc@C{@EYGAFGPs@zB{BnHy@|BUr@Qh@Y|@Wz@oA|DsAhEEJCLcBhFs@zBs@xBKZk@fBy@fCELEJk@jBa@nAu@zBq@zBCDUr@uBvGY`AITIX?BI`@]tBMt@GXIRMRa@`AOPk@|A]`AITk@fBkCrIYbAUv@yAzE_CtFi@fAKRkBhE?@Ul@wAfEsAfEiCdIs@zBOf@m@`AQZUv@]bAkAxDu@~Ba@jAa@lAi@~@g@bAQROHM?KAGAWMMIsAs@}A{@]QmDmBs@a@s@_@kAo@OEo@Q}DwByI}EwBiA}CeBgH{D{CaBwMgHWMmJgFkBcAaOgIeBaAmKiGgCkAoAe@eBq@eCg@gAImCKeEMeAGkAMu@QYK]MmAg@_C{A{YoPk@[aFuBoE{@_EOqF@uKVcBDsO\\}CVuCf@cBf@uChAiBbAGB}A~@cHxEeJrGcDxB{CvB}AfAq@b@q@d@kAv@kE|Ba@RkBt@eA\\s@VgE~@cBX}ARsAJaABy@DuAD{BF}@F_AFwAN{@Lg@JoCx@mAb@{Ap@kAl@mEfC}AbA}A`AwCdBoAt@mAr@YR_I|EoFhDiDvBaDpBiCbBsAx@eDjBeAj@WTe@Vc@V_FzCeHdEc@VkCzAqBnAwA|@{CjBcAn@mDtBqHnEcC|@{B^S@wAJoBFqBBsBLsCl@}BhA_CbByDrDgBbBeB`BaB|A_BpA_FtE}I|HQNaElEcDtE{BfE_AtBoAlDaBvEiGpQsBhG{BrGcChHeApB{@zB}@hBu@fAk@l@_@Xm@d@w@Xq@PcAHy@?A?g@Gi@Mc@Ms@]o@c@e@a@e@m@m@k@e@iAy@oCw@{C}@oDo@mC[gAsDyNoAmEiB{FEO}BuGmBeEcA{BwE{I[g@eAkBiE{FsCgDoCiC}A}A}@w@c@_@aBsAwAgAmCoBgBqAUQqByAcCgBwFaEAA}@s@cBmAkDeCyG}EaMaJwAcAqAaA_[_UuMqJ{DyCuBsAmBwAiBqAqAaA{BeBkGkEcTwOcAu@wImGcAq@yGaFiLeIiBoAsQqJ{LsEyAi@uPwFaPoFeEuAaPcF}GgByDm@kFy@qDc@qDOiFSoF@uEPkAFwALiFh@mB\\qDt@kIrBgJlDE@wEvBsEfCaAp@[R}DnCiBtAuCdCsCjC}B`CgBlBmGtHmFvHS\\_@h@uExHkEhIcDlGaCzEuFfJmCtDsDzEwB|BiBtBgG`HwHzIoB~BuDdEoAtAcEpEuEdFyArAyH~GeC|BkB|AsC~BoBbB{@p@wDvCQLWPqBtAyAbAwJrF_CpAcCtA}BpAk@ZOH}BpAcExBaAh@aBv@kCzAk@Ze@VoAp@uAr@mCrAeBz@]NmHzCaF|AYH_GtAcHjAk@J}N~@gFEW?eCEyEWaKcAYIsEcAkBa@c@Kk@SkAa@wDqAyEsBk@WsG_DmCsAeAk@aDcBa@S_@SsAq@}EcCYQmAk@kAg@e@S}@_@eAc@wAg@s@UkCs@gDi@gAGwCOkDCeADoAB}C^k@Jw@NwAXaAXUFiA\\_Bj@eBj@cDtAsAl@c@TwKzEaQxHyIzDoEnBaBt@_FhBeKxDwA`@yCz@sA`@y@VcE~@uBd@qIvAaC^yFp@yF`@G?oG\\aCF_EDyDD}PIK?qDAg@SaAGeAA}EA[AmD?aLCSGICEAKEA?ICMw@UuAIs@Is@KkAImBMwE?]Ao@EqAE{AQ\\KFU`@BpANN@@RNBbA?pAFdCJfCPhB?BBLBZBLVfBA^?V?b@GZQ^_@LwBv@qCbAwGjDD\\kBr@wHtCsBx@_C`AyM~EkC`AgFlBgJlDeXdKq@ViG|BwTlIwAh@iGtBaEdAiFvAuEx@oCf@gFx@eCVcFp@uHf@O@}DBwCDqBBeCBkCD}CBU?Y?qA@aZLeA@s@DI?M?gA@oNH{FD{@@_ADoGDcBBsDFkHDuCHoCHoA@yA@eCLsCVsBZSD{Bp@eA^eAb@iBz@iDnBiBdAeAp@_Al@sJzFy@d@aKjGsNpI}FnDsLhHeIbFmAv@kHhEq@`@}NbJsElCmCzAoB`AgDpAC@uBj@yA^UDeCZ}ALuCCS?cCKeAGkBOcAIwD_@gGm@}@KuEc@kHmAcGyByHsFwFmDs@]k@Ww@UoAWcCU}CCiDT_Dn@aC|@_IxCaHrCU\\]NkDpAoEbB}HtCkAb@{ElBqCdAc@PmAf@IBKFQHk@RMDy@XAr@BbBDVLl@Lf@Rr@Nb@HZJl@D^Jx@?bBIhBAVEXKt@Ql@a@KGAyB_AQImCcAQGWKgBi@OUIEOEWMQZELAJMf@Mb@WFw@Z_@RKLc@R??"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v3/users/:user\_id/events/:event\_id/behavior\_scores" %}
{% api-method-summary %}
Behavior Scores by EventID
{% endapi-method-summary %}

{% api-method-description %}
Retrieve Behavior Scores of a Transport by its EventID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="event\_id" type="string" required=true %}
ID of the Transport whose Behavior Scores are being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "type": "CarBehaviorScores",
    "overall": 0.79,
    "smooth": 0.79,
    "legal": 0.72,
    "anticipative": 0.86,
    "hard_accel": 0.9,
    "hard_brake": 0.65,
    "hard_events": 0.85,
    "hard_turn": 0.95,
    "legal_v2": 0.79,
    "smooth_v2": 0.78,
    "anticipative_v2": 0.85
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v3/users/:user\_id/events/:event\_id/behavior\_annotations" %}
{% api-method-summary %}
Behavior Annotations by EventID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is being retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="event\_id" type="string" required=true %}
ID of the Transport whose Behavior Annotations are being retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "type": "BoundaryBehaviorAnnotation",
        "start": "2019-03-22T08:37:48.303000+01:00",
        "end": "2019-03-22T08:40:35.303000+01:00",
        "quality": "valid"
    },
    {
        "type": "AccelerationBehaviorAnnotation",
        "start": "2019-03-22T08:38:10.781456+01:00",
        "end": "2019-03-22T08:38:16.102097+01:00",
        "acceleration": "accelerate",
        "duration": 5321,
        "magnitude": 0.189,
        "path": [
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78664,
                "longitude": 4.49807
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78679,
                "longitude": 4.49808
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78685,
                "longitude": 4.4981
            }
        ]
    },
    {
        "type": "TurnBehaviorAnnotation",
        "start": "2019-03-22T08:38:16.866289+01:00",
        "end": "2019-03-22T08:38:21.479824+01:00",
        "duration": 4614,
        "maneuver": "left_turn",
        "magnitude": 0.467,
        "path": [
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78688,
                "longitude": 4.49811
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78692,
                "longitude": 4.49812
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78693,
                "longitude": 4.49808
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78697,
                "longitude": 4.49799
            },
            {
                "type": "BehaviorAnnotationPathWaypoint",
                "latitude": 50.78703,
                "longitude": 4.49785
            }
        ]
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="" path="/v3/users/:user\_id/aggregated\_driving\_scores" %}
{% api-method-summary %}
Time Aggregated Driving Scores 
{% endapi-method-summary %}

{% api-method-description %}
Retrieve the time aggregated scores of a user, i.e. **daily**, **weekly**, **monthly** or **all** aggregated scores. The API can be used with or without a date parameter. If no date parameter is given, the API will default to the last available \(ongoing\) day, week or month. The **all** score will aggregate all available scores \(max. 9 weeks\).  
  
The date parameter accepts either the 1st day of the week \(Monday\) or the 1st day of the month for type: week and type: month respectively.  
  
_Note: this endpoint is available on the EU platform only._
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Type of aggregated scores you want to retrieve.  
  
**Accepts:** day, week, month, all.
{% endapi-method-parameter %}

{% api-method-parameter name="date" type="string" required=false %}
Optional: if you want to retrieve aggregated scores for a different period than the current one.   
  
**Format:** YYYY-MM-DD  
**Accepts:** any day, any monday, any 1st of month.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
A user token or an API Key with scope 'user.read'.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Depending on the type \(day, week, month or all\) you have chosen, you will be returned one of the responses below.
{% endapi-method-response-example-description %}

```
{
    "day": {
        "smooth": 0.64,
        "legal": 1,
        "anticipative": 0.69,
        "focus": 1,
        "mounted": 0.17,
        "hard_accel": 0.95,
        "hard_brake": 0.9,
        "hard_events": 0.69,
        "legal_v2": 1,
        "hard_turn": 1,
        "smooth_v2": 0.68,
        "anticipative_v2": 0.68,
        "handheld_calling": 1,
        "handheld_calling_duration": -1,
        "handsfree_calling": 1,
        "handling_without_calling": 0.95,
        "handling_without_calling_duration": 10,
        "attention": 0.95
    }
}
{
    "week": {
        "smooth": 0.64,
        "legal": 1,
        "anticipative": 0.69,
        "focus": 1,
        "mounted": 0.17,
        "hard_accel": 0.95,
        "hard_brake": 0.9,
        "hard_events": 0.69,
        "legal_v2": 1,
        "hard_turn": 1,
        "smooth_v2": 0.68,
        "anticipative_v2": 0.68,
        "handheld_calling": 1,
        "handheld_calling_duration": -1,
        "handsfree_calling": 1,
        "handling_without_calling": 0.95,
        "handling_without_calling_duration": 10,
        "attention": 0.95
    }
}
{
    "month": {
        "smooth": 0.66,
        "legal": 0.72,
        "anticipative": 0.6,
        "focus": 1,
        "mounted": 0.96,
        "hard_accel": 0.93,
        "hard_brake": 0.9,
        "hard_events": 0.68,
        "legal_v2": 0.8,
        "hard_turn": 0.95,
        "smooth_v2": 0.61,
        "anticipative_v2": 0.61,
        "handheld_calling": 1,
        "handheld_calling_duration": -1,
        "handsfree_calling": 1,
        "handling_without_calling": 0.95,
        "handling_without_calling_duration": 705,
        "attention": 0.95
    }
}
{
    "all": {
        "smooth": 0.67,
        "legal": 0.6,
        "anticipative": 0.59,
        "focus": 0.99,
        "mounted": 0.85,
        "hard_accel": 0.9,
        "hard_brake": 0.92,
        "hard_events": 0.7,
        "legal_v2": 0.52,
        "hard_turn": 0.93,
        "smooth_v2": 0.63,
        "anticipative_v2": 0.84,
        "handheld_calling": 1,
        "handheld_calling_duration": 0,
        "handsfree_calling": 0.97,
        "handling_without_calling": 0,
        "handling_without_calling_duration": 2101,
        "attention": 0
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Unversioned Routes \(no version prefix applied\)

{% api-method method="delete" host="" path="/users/:user\_id" %}
{% api-method-summary %}
Delete User
{% endapi-method-summary %}

{% api-method-description %}
Deletes the user data along with the history.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
ID of the user whose data is to be deleted.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
A user token or an API Key with \`user.delete\` scope
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

