# TransportSessionListener

{% hint style="info" %}
This interface is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

This interface is used in combination with [`setTransportSessionListener(TransportSessionListener)`](transportsessionapi.md#settransportsessionlistener).

## TransportSessionListener API

### `onTransportSessionCompleted()`

> ```java
> void onTransportSessionCompleted(TransportSession session)
> ```
>
> Invoked when a transport session is completed.

| Parameters |                                                                                      |
| ---------- | ------------------------------------------------------------------------------------ |
| session    | a [TransportSession](transportsession.md) object containing the session information. |
