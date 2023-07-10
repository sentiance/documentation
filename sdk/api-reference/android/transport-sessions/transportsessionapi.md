# TransportSessionApi

Use this API to subscribe to, and retrieve transport sessions. A transport session contains information about a completed transport, such as the transport mode and the raw sensor data used during it classification.

## TransportSessionApi API

### `enableTransportSessionRecording()`

> ```java
> void enableTransportSessionRecording()
> ```
>
> Enables transport session recording.
>
> This setting is persistent across app restarts, so you only need to enable session recording once. Note however that the setting is reset to 'disabled' after an SDK reset. See [reset](../sentiance.md.md#reset).
>
> Recorded sessions are stored on the device until the time that you request their deletion. See [`deleteTransportSession(String)`](transportsessionapi.md#deletetransportsession).
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

### `disableTransportSessionRecording()`

> ```java
> void disableTransportSessionRecording()
> ```
>
> Disables transport session recording.
>
> This setting is persistent across app restarts, so you only need to disable session recording once.
>
> If you no longer need session recording, make sure to delete previously recorded sessions if you no longer need them. See [`deleteAllTransportSessions()`](transportsessionapi.md#deletealltransportsessions).
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

### `getAvailableTransportSessions()`

> ```java
> List<TransportSession> getAvailableTransportSessions()
> ```
>
> Returns a list of recorded and completed transport sessions.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

### `isTransportSessionRecordingEnabled()`

> ```java
> boolean isTransportSessionRecordingEnabled()
> ```
>
> Returns whether transport session recording is enabled.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

### `setTransportSessionListener()`

> ```java
> void setTransportSessionListener(@Nullable TransportSessionListener listener)
> ```
>
> Sets a listener that will be invoked to deliver transport sessions. A session is delivered after a transport ends.
>
> Transport sessions are stored on the device until the time that you request their deletion. See [`deleteTransportSession(String)`](transportsessionapi.md#deletetransportsession).
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

<table><thead><tr><th width="182">Parameters</th><th></th></tr></thead><tbody><tr><td>listener</td><td>A TransportSessionListener to receive transport sessions, or <code>null</code> to remove a previously set listener.</td></tr></tbody></table>

### `deleteAllTransportSessions()`

> ```java
> void deleteAllTransportSessions()
> ```
>
> Deletes all recorded transport sessions.
>
> Recorded sessions are stored on the device. It is your responsibility to call this method, or [`deleteTransportSession(String)`](transportsessionapi.md#deletetransportsession), to request their deletion, when you no longer need them.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

### `deleteTransportSession()`

> ```java
> void deleteTransportSession(String sessionId)
> ```
>
> Deletes the transport session with the specified ID.
>
> Recorded sessions are stored on the device. It is your responsibility to call this method, or [`deleteAllTransportSessions()`](transportsessionapi.md#deletealltransportsessions), to request their deletion, when you no longer need them.
>
> Note: calling this method on an uninitialized SDK will throw an [SdkException](../sdkexception.md).

<table><thead><tr><th width="183">Parameters</th><th></th></tr></thead><tbody><tr><td>sessionId</td><td>The ID of the session to delete.</td></tr></tbody></table>
