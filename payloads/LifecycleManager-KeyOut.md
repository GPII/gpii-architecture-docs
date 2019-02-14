## Lifecycle Manager Payload Examples during User Key Out Process

During the user key out process, Lifecycle Manager coordinates [Settings Handler](https://wiki.gpii.net/w/Settings_Handler) and [Lifecycle Handlers](https://wiki.gpii.net/w/Lifecycle_Handler) to restore the original solution states that were saved before the user's settings are applied.

See [the description of Lifecycle Manager at GPII wiki](https://wiki.gpii.net/w/Architecture_Overview#Lifecycle_Manager) for what the lifecycle manager is.

### Table of Contents
1. [Input Payload - GPII Key](#user-content-input-payload---gpii-key)
2. [Return Payload](#user-content-return-payload)

### Input Payload - GPII Key

An example of an `gpiiKey`: `vladimir`

### Return Payload
Lifecycle Manager coordinates [Settings Handler](https://wiki.gpii.net/w/Settings_Handler) and [Lifecycle Handlers](https://wiki.gpii.net/w/Lifecycle_Handler) to restore the original solution states. See:

* [Settings Handler Payload Examples](SettingsHandler.md)
* [Lifecycle Handlers Payload Examples](LifecycleHandlers.md)
