## Lifecycle Manager Payload Examples

See [the description of Lifecycle Manager at GPII wiki](https://wiki.gpii.net/w/Architecture_Overview#Lifecycle_Manager) for what the lifecycle manager is.

This document contains payload examples for both the user key in process and the context change process.

### Input Payload

At the user key in process, the payload received at the lifecycle manager is identical with [the payload returned by the cloud based flow mananger](CloudBasedFlowManagerUntrustedSettings.md#user-content-return-payload).

During the context change process, the payload received is identical with [the payload returned by the local transformer](LocalTransformer.md#user-content-return-payload).

### Output Payload
Lifecycle Manager coordinates [Settings Handler](https://wiki.gpii.net/w/Settings_Handler) and [Lifecycle Handlers](https://wiki.gpii.net/w/Lifecycle_Handler) to manage the lifecycle of solutions. See:

* [Settings Handler Payload Examples](SettingsHandler.md)
* [Lifecycle Handlers Payload Examples](LifecycleHandlers.md)
