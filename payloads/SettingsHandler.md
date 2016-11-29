## Settings Handler Payload Examples

The payload examples in this document apply to all processes: user key in, user key out and context change.

At the user key in and context change processes, the settings handler configures solution settings. The solutions can be applications, access features, or assistive technology.

During the user key out process, the settings handler restores solutions back to their original states.

See [the SettingsHandler documentation at GPII wiki](https://wiki.gpii.net/w/Settings_Handler) for what a settings handler is.

### Table of Contents
1. [Input Payload - Solution ID](#user-content-input-payload---solution-id)
2. [Input Payload - Handler Spec](#user-content-input-payload---handler-spec)
3. [Return Payload](#user-content-return-payload)

### Input Payload - Solution ID

An example of a solution ID: ```org.gnome.desktop.interface```

### Input Payload - Handler Spec

An example of a handler spec:
```
{
    "type": "gpii.gsettings",
    "options": {
        "schema": "org.gnome.desktop.interface"
    },
    "settings": {
        "gtk-theme": "HighContrast",
        "icon-theme": "HighContrast",
        "cursor-size": 29
    }
}
```

### Return Payload

An example of the return payload:
```
{
    "org.gnome.desktop.interface": [
        {
            "settings": {
                "gtk-theme": "HighContrast",
                "icon-theme": "HighContrast",
                "cursor-size": 29
            },
            "options": {
                "schema": "org.gnome.desktop.interface"
            }
        }
    ]
}
```
