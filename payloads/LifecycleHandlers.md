## Lifecycle Handlers Payload Examples

Lifecycle Handlers start or stop a given solution. The payload examples in this document apply to all processes: user key in, user key out and context change.

See [the LifecycleHandler documentation at GPII wiki](https://wiki.gpii.net/w/Lifecycle_Handler) for what lifecycle handlers are.

### Table of Contents
1. [Input Payload](#user-content-input-payload)
2. [Return Payload](#user-content-return-payload)

### Input Payload

An example of a "start" action:
```
{
    "start": [
        {
            "type": "gpii.launch.exec",
            "command": "gsettings set org.gnome.desktop.a11y.applications screen-reader-enabled true"
        }
    ]
}
```

An example of a "stop" action:
```
{
    "stop": [
        {
            "type": "gpii.launch.exec",
            "command": "gsettings set org.gnome.desktop.a11y.applications screen-magnifier-enabled false"
        }
    ]
}
```

An example of a "configure" action:
```
{
    "configure": [
        "settings.configuration"
    ]
}
```

#### Return Payload

* None with windows platform
* The process id with linux platform (currently not in use).
