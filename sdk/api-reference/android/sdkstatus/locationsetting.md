# LocationSetting

Represents the location mode settings on the device. The location mode indicates which location providers are enabled.

<table><thead><tr><th width="202"></th><th></th></tr></thead><tbody><tr><td>OK</td><td>All location providers are enabled.</td></tr><tr><td>DISABLED</td><td>None of the location providers are enabled.</td></tr><tr><td>BATTERY_SAVING</td><td>In "battery saving" mode, only the network-based location provider is enabled (e.g. wifi, cell towers). The GPS-based location provider is disabled. This is still generally okay for SDK detections.</td></tr><tr><td>DEVICE_ONLY</td><td>In "device only" mode, only the GPS-based network provider is enabled. The network-based location provider is disabled. This is generally not okay for SDK detections, because GPS cannot provide accurate indoor positioning.</td></tr></tbody></table>

