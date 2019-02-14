## Environment Reporter Payload Examples

With the current GPII implementation, the Environment Reporter detects and reports environmental information to the context manager every 20 seconds. For now, this information only contains the system timestamp. An example of the current environment report:

```
{
    "http://registry.gpii.net/common/environment/timestamp": 1459262359548,
    "http://registry.gpii.net/common/environment/timeOfDay": "14:39"
}
```

### The Environment Report at Brightness Change

This context change example shows the desired payload flow when the brightness is changed.

Below is an example payload of the environment report when the brightness changes. In this example, the value of ```http://registry.gpii.net/common/environment/illuminance``` is changed from ```200``` to ```500``` and the value of ```"http://registry.gpii.net/common/environment/auditory.noise"``` stays unchanged:

```
{
    "http://registry.gpii.net/common/environment/timestamp": 1459262359548,
    "http://registry.gpii.net/common/environment/timeOfDay": "14:39",
    "http://registry.gpii.net/common/environment/illuminance": 500,
    "http://registry.gpii.net/common/environment/auditory.noise": 10000
}
```
