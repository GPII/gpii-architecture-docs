## Device Reporter Payload Examples

The device reporter collects the device information including the OS that the device is running as well as available solutions.

See [the description of Device Reporter at GPII wiki](https://wiki.gpii.net/w/Architecture_Overview#Device_Characteristics_Reporter) for more details.

### Table of Contents
1. [Input - GET Request](#user-content-input---get-request)
2. [Return Payload](#user-content-return-payload)

### Input - GET Request

URL: `/device`

### Return Payload
 
An example of the output payload:
```
{
    "solutions": [{
        "id": "org.gnome.desktop.interface"
    }, {
        "id": "org.gnome.shell.overrides"
    }, {
        "id": "org.gnome.desktop.wm.preferences"
    }, {
        "id": "org.gnome.nautilus"
    }, {
        "id": "org.gnome.desktop.a11y.keyboard"
    }, {
        "id": "org.gnome.desktop.a11y.applications.onscreen-keyboard"
    }, {
        "id": "org.gnome.orca"
    }, {
        "id": "org.gnome.desktop.a11y.magnifier"
    }, {
        "id": "com.microsoft.windows.magnifier"
    }, {
        "id": "com.microsoft.windows.onscreenKeyboard"
    }, {
        "id": "com.microsoft.windows.highContrast"
    }, {
        "id": "com.microsoft.windows.mouseTrailing"
    }, {
        "id": "com.microsoft.windows.cursors"
    }, {
        "id": "com.android.activitymanager"
    }, {
        "id": "com.android.talkback"
    }, {
        "id": "com.android.freespeech"
    }, {
        "id": "com.ilunion.cloud4chrome"
    }, {
        "id": "com.android.settings.secure"
    }, {
        "id": "com.android.audioManager"
    }, {
        "id": "com.android.persistentConfiguration"
    }, {
        "id": "org.alsa-project"
    }, {
        "id": "org.freedesktop.xrandr"
    }, {
        "id": "com.android.settings.system"
    }],
    "OS": {
        "id": "linux",
        "version": "4.3.4-200.fc22.x86-64"
    }
}
```

