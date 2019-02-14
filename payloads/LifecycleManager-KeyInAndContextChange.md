## Lifecycle Manager Payload Examples

See [the description of Lifecycle Manager at GPII wiki](https://wiki.gpii.net/w/Architecture_Overview#Lifecycle_Manager) for what the lifecycle manager is.

This document contains payload examples for both the user key in process and the context change process.

### Input Payload

At the user key in process, the payload received at the lifecycle manager is identical with [the payload returned by the cloud based flow mananger](CloudBasedFlowManagerUntrustedConfig.md#user-content-return-payload).

During the context change process, the payload received is identical with [the payload returned by the local transformer](LocalTransformer.md#user-content-return-payload).

### Output Payload

Lifecycle Manager converts the received payload into lifecycle instructions that is responsible for setting up appropriate solutions and settings. It also coordinates [Settings Handler](https://wiki.gpii.net/w/Settings_Handler) and [Lifecycle Handlers](https://wiki.gpii.net/w/Lifecycle_Handler) to manage the lifecycle of solutions. See:

* [Settings Handler Payload Examples](SettingsHandler.md)
* [Lifecycle Handlers Payload Examples](LifecycleHandlers.md)

Below is an example of lifecycle instructions:

```
"lifecycleInstructions": {
    "org.gnome.desktop.a11y.magnifier": {
        "name": "GNOME Shell Magnifier",
        "settingsHandlers": {
            "configuration": {
                "type": "gpii.gsettings",
                "liveness": "live",
                "options": {
                    "schema": "org.gnome.desktop.a11y.magnifier"
                },
                "supportedSettings": {
                    "mag-factor": {

                    },
                    "show-cross-hairs": {

                    },
                    "focus-tracking": {

                    },
                    "caret-tracking": {

                    },
                    "mouse-tracking": {

                    },
                    "screen-position": {

                    }
                },
                "inverseCapabilitiesTransformations": {
                    "http://registry\\.gpii\\.net/common/magnification": "mag-factor",
                    "http://registry\\.gpii\\.net/common/showCrosshairs": "show-cross-hairs",
                    "transform": [
                        {
                            "type": "fluid.transforms.valueMapper",
                            "defaultInputPath": "screen-position",
                            "defaultOutputPath": "http://registry\\.gpii\\.net/common/magnifierPosition",
                            "match": {
                                "full-screen": "FullScreen",
                                "left-half": "LeftHalf",
                                "right-half": "RightHalf",
                                "top-half": "TopHalf",
                                "bottom-half": "BottomHalf"
                            }
                        },
                        {
                            "type": "fluid.transforms.valueMapper",
                            "defaultOutputPath": "http://registry\\.gpii\\.net/common/tracking",
                            "defaultInputPath": "mouse-tracking",
                            "match": {
                                "centered": "mouse"
                            }
                        }
                    ]
                },
                "settings": {
                    "mag-factor": 3,
                    "screen-position": "full-screen"
                }
            }
        },
        "launchHandlers": {
            "launcher": {
                "type": "gpii.gsettings.launch",
                "options": {
                    "schema": "org.gnome.desktop.a11y.applications",
                    "key": "screen-magnifier-enabled"
                }
            }
        },
        "update": [
            "settings.configuration"
        ],
        "isInstalled": [
            {
                "type": "gpii.packageKit.find",
                "name": "gnome-shell"
            }
        ],
        "active": true
    },

    "org.gnome.desktop.interface": {
        "name": "GNOME Interface Settings",
        "settingsHandlers": {
            "configuration": {
                "type": "gpii.gsettings",
                "options": {
                    "schema": "org.gnome.desktop.interface"
                },
                "settings": {
                    "gtk-theme": "Adwaita",
                    "icon-theme": "gnome"
                }
            }
        },
        "configure": [
            "settings.configuration"
        ],
        "restore": [
            "settings.configuration"
        ],
        "isInstalled": [
            {
                "type": "gpii.packageKit.find",
                "name": "gsettings-desktop-schemas"
            }
        ],
        "active": true
    }
}
```
