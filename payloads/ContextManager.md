## Context Manager Payload Examples

The context manager running on GPII Cloud is the provisional part of the GPII architecture. It takes the filtered output of the matchmaking process, evaluates the current context, and decides which context should be selected.

See [the ContextManager documentation](https://github.com/GPII/universal/blob/master/documentation/ContextManager.md) for more details.

### Table of Contents
1. [Input Payload](#user-content-input-payload)
2. [Return Payload](#user-content-return-payload)

### Input Payload

The payload received at the context manager is identical with [the payload returned by the OAuth server](OAuthServer.md#user-content-return-payload).

#### Return Payload

```
{
    "activeContexts": [
        "gpii-default"
    ],
    "environmentReporter": {

    },
    "inferredCommonTerms": {
        "gpii-default": {

        },
        "subway": {

        }
    },
    "gpiiKey": "vladimir",
    "preferences": {
        "contexts": {
            "gpii-default": {
                "name": "Default preferences",
                "preferences": {
                    "http://registry.gpii.net/common/highContrastEnabled": true,
                    "http://registry.gpii.net/common/highContrastTheme": "white-black",
                    "http://registry.gpii.net/common/cursorSize": 0.5,
                    "http://registry.gpii.net/common/mouseTrailing": 5,
                    "http://registry.gpii.net/common/screenReaderTTSEnabled": true,
                    "http://registry.gpii.net/common/speechRate": 300,
                    "http://registry.gpii.net/applications/org.chrome.cloud4chrome": {
                        "fontSize": "medium",
                        "highContrastEnabled": true
                    },
                    "http://registry.gpii.net/common/matchMakerType": "RuleBased"
                },
                "metadata": [
                    {
                        "type": "required",
                        "scope": [
                            "http://registry.gpii.net/common/screenReaderTTSEnabled"
                        ],
                        "value": 1024
                    },
                    {
                        "type": "priority",
                        "scope": [
                            "http://registry.gpii.net/applications/com.freedomScientific.jaws"
                        ],
                        "value": 1024
                    }
                ]
            },
            "subway": {
                "name": "subway",
                "preferences": {
                    "http://registry.gpii.net/common/highContrastEnabled": true,
                    "http://registry.gpii.net/common/highContrastTheme": "white-black",
                    "http://registry.gpii.net/common/cursorSize": 0.5,
                    "http://registry.gpii.net/common/mouseTrailing": 5,
                    "http://registry.gpii.net/common/screenReaderTTSEnabled": true,
                    "http://registry.gpii.net/common/speechRate": 300,
                    "http://registry.gpii.net/common/volumeTTS": 0.9,
                    "http://registry.gpii.net/applications/org.chrome.cloud4chrome": {
                        "fontSize": "medium",
                        "highContrastEnabled": true
                    },
                    "http://registry.gpii.net/common/matchMakerType": "RuleBased"
                },
                "metadata": [
                    {
                        "type": "required",
                        "scope": [
                            "http://registry.gpii.net/common/screenReaderTTSEnabled"
                        ],
                        "value": 1024
                    },
                    {
                        "type": "priority",
                        "scope": [
                            "http://registry.gpii.net/applications/com.freedomScientific.jaws"
                        ],
                        "value": 1024
                    }
                ],
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "min": 400,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/visual\\.luminance"
                    }
                ]
            }
        }
    },
    "deviceContext": {
        "solutions": [
            {
                "id": "org.gnome.desktop.interface"
            },
            {
                "id": "org.gnome.shell.overrides"
            },
            {
                "id": "org.gnome.desktop.wm.preferences"
            },
            {
                "id": "org.gnome.nautilus"
            },
            {
                "id": "org.gnome.desktop.a11y.keyboard"
            },
            {
                "id": "org.gnome.desktop.a11y.applications.onscreen-keyboard"
            },
            {
                "id": "org.gnome.orca"
            },
            {
                "id": "org.gnome.desktop.a11y.magnifier"
            },
            {
                "id": "com.microsoft.windows.magnifier"
            },
            {
                "id": "com.microsoft.windows.onscreenKeyboard"
            },
            {
                "id": "com.microsoft.windows.highContrast"
            },
            {
                "id": "com.microsoft.windows.mouseTrailing"
            },
            {
                "id": "com.microsoft.windows.cursors"
            },
            {
                "id": "com.android.activitymanager"
            },
            {
                "id": "com.android.talkback"
            },
            {
                "id": "com.android.freespeech"
            },
            {
                "id": "com.ilunion.cloud4chrome"
            },
            {
                "id": "com.android.settings.secure"
            },
            {
                "id": "com.android.audioManager"
            },
            {
                "id": "com.android.persistentConfiguration"
            },
            {
                "id": "org.alsa-project"
            },
            {
                "id": "org.freedesktop.xrandr"
            },
            {
                "id": "com.android.settings.system"
            }
        ],
        "OS": {
            "id": "linux",
            "version": "4.3.4-200.fc22.x86-64"
        }
    },
    "solutionsRegistryEntries": {
        "org.gnome.desktop.a11y.magnifier": {
            "name": "GNOME Shell Magnifier",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "options": {
                        "schema": "org.gnome.desktop.a11y.magnifier"
                    },
                    "capabilities": [
                        "applications.org\\.gnome\\.desktop\\.a11y\\.magnifier.id",
                        "display.screenEnhancement.screenMagnification.applications.org\\.gnome\\.desktop\\.a11y\\.magnifier.name"
                    ],
                    "capabilitiesTransformations": {
                        "mag-factor": "http://registry\\.gpii\\.net/common/magnification",
                        "show-cross-hairs": "http://registry\\.gpii\\.net/common/showCrosshairs",
                        "transform": {
                            "type": "fluid.transforms.arrayToSetMembership",
                            "inputPath": "http://registry\\.gpii\\.net/common/tracking",
                            "presentValue": "proportional",
                            "missingValue": "none",
                            "options": {
                                "focus": "focus-tracking",
                                "caret": "caret-tracking",
                                "mouse": "mouse-tracking"
                            }
                        },
                        "screen-position": {
                            "transform": {
                                "type": "fluid.transforms.valueMapper",
                                "inputPath": "http://registry\\.gpii\\.net/common/magnifierPosition",
                                "defaultInputValue": "Custom",
                                "options": {
                                    "FullScreen": {
                                        "outputValue": "full-screen"
                                    },
                                    "Lens": {
                                        "outputValue": "full-screen"
                                    },
                                    "LeftHalf": {
                                        "outputValue": "left-half"
                                    },
                                    "RightHalf": {
                                        "outputValue": "right-half"
                                    },
                                    "TopHalf": {
                                        "outputValue": "top-half"
                                    },
                                    "BottomHalf": {
                                        "outputValue": "bottom-half"
                                    },
                                    "Custom": {
                                        "outputValue": "full-screen"
                                    }
                                }
                            }
                        }
                    }
                }
            },
            "update": [
                "settings.configuration"
            ],
            "configure": [
                "settings.configuration"
            ],
            "restore": [
                "settings.configuration"
            ],
            "start": [
                {
                    "type": "gpii.launch.exec",
                    "command": "gsettings set org.gnome.desktop.a11y.applications screen-magnifier-enabled true"
                }
            ],
            "stop": [
                {
                    "type": "gpii.launch.exec",
                    "command": "gsettings set org.gnome.desktop.a11y.applications screen-magnifier-enabled false"
                }
            ],
            "isInstalled": [
                {
                    "type": "gpii.packageKit.find",
                    "name": "gnome-shell"
                }
            ]
        },
        "org.gnome.desktop.interface": {
            "name": "GNOME Interface Settings",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "capabilities": [
                        "display.screenEnhancement.applications.org\\.gnome\\.desktop\\.interface.name",
                        "applications.org\\.gnome\\.desktop\\.interface.id"
                    ],
                    "capabilitiesTransformations": {
                        "text-scaling-factor": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/fontSize",
                                "factor": 0.08333333333333333
                            }
                        },
                        "cursor-size": {
                            "transform": {
                                "type": "gpii.transformer.quantize",
                                "inputPath": "http://registry\\.gpii\\.net/common/cursorSize",
                                "ranges": [
                                    {
                                        "upperBound": 0,
                                        "output": -1
                                    },
                                    {
                                        "upperBound": 0.333,
                                        "output": 20
                                    },
                                    {
                                        "upperBound": 0.666,
                                        "output": 29
                                    },
                                    {
                                        "output": 41
                                    }
                                ]
                            }
                        },
                        "gtk-theme": {
                            "transform": {
                                "type": "fluid.transforms.condition",
                                "conditionPath": "http://registry\\.gpii\\.net/common/highContrastEnabled",
                                "true": {
                                    "literalValue": "HighContrast"
                                },
                                "false": {
                                    "literalValue": "Adwaita"
                                }
                            }
                        },
                        "icon-theme": {
                            "transform": {
                                "type": "fluid.transforms.condition",
                                "conditionPath": "http://registry\\.gpii\\.net/common/highContrastEnabled",
                                "true": {
                                    "literalValue": "HighContrast"
                                },
                                "false": {
                                    "literalValue": "gnome"
                                }
                            }
                        }
                    },
                    "options": {
                        "schema": "org.gnome.desktop.interface"
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
            ]
        },
        "org.gnome.nautilus": {
            "name": "GNOME Nautilus Settings",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "capabilities": [
                        "applications.org\\.gnome\\.nautilus.id",
                        "display.screenEnhancement.applications.org\\.gnome\\.nautilus.name"
                    ],
                    "capabilitiesTransformations": {
                        "font": "http://registry\\.gpii\\.net/common/0"
                    },
                    "options": {
                        "schema": "org.gnome.nautilus.desktop"
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
                    "name": "nautilus"
                }
            ]
        },
        "org.gnome.desktop.a11y.applications.onscreen-keyboard": {
            "name": "GNOME Assistive Technology - Screen Keyboard",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.settingsHandlers.noSettings",
                    "capabilities": [
                        "control.onscreenKeyboard",
                        "control.onscreenKeyboard.applications.org\\.gnome\\.desktop\\.a11y\\.applications\\.onscreen-keyboard.name",
                        "applications.org\\.gnome\\.desktop\\.a11y\\.applications\\.onscreen-keyboard.id"
                    ]
                }
            },
            "start": [
                {
                    "type": "gpii.launch.exec",
                    "command": "gsettings set org.gnome.desktop.a11y.applications screen-keyboard-enabled true"
                }
            ],
            "stop": [
                {
                    "type": "gpii.launch.exec",
                    "command": "gsettings set org.gnome.desktop.a11y.applications screen-keyboard-enabled false"
                }
            ],
            "isInstalled": [
                {
                    "type": "gpii.packageKit.find",
                    "name": "gnome-shell"
                }
            ]
        },
        "org.gnome.desktop.a11y.keyboard": {
            "name": "GNOME Shell Keyboard Settings",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "capabilities": [
                        "applications.org\\.gnome\\.desktop\\.a11y\\.keyboard.id",
                        "control.onscreenKeyboard.applications.org\\.gnome\\.desktop\\.a11y\\.keyboard.name",
                        "control.keyboardEnhancement.applications.org\\.gnome\\.desktop\\.a11y\\.keyboard.name"
                    ],
                    "capabilitiesTransformations": {
                        "stickykeys-enable": "http://registry\\.gpii\\.net/common/stickyKeys",
                        "slowkeys-enable": "http://registry\\.gpii\\.net/common/slowKeysEnable",
                        "slowkeys-delay": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/slowKeysInterval",
                                "factor": 1000
                            }
                        },
                        "bouncekeys-enable": "http://registry\\.gpii\\.net/common/debounceEnable",
                        "bouncekeys-delay": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/debounceInterval",
                                "factor": 1000
                            }
                        },
                        "mousekeys-enable": "http://registry\\.gpii\\.net/common/mouseEmulationEnabled",
                        "mousekeys-init-delay": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/initDelay",
                                "factor": 1000
                            }
                        },
                        "mousekeys-max-speed": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/cursorSpeed",
                                "factor": 1000
                            }
                        },
                        "mousekeys-accel-time": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/cursorAcceleration",
                                "factor": 1000
                            }
                        }
                    },
                    "options": {
                        "schema": "org.gnome.desktop.a11y.keyboard"
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
            ]
        },
        "org.gnome.desktop.wm.preferences": {
            "name": "GNOME desktop Window Manager preferences",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "capabilities": [
                        "applications.org\\.gnome\\.desktop\\.wm\\.preferences.id",
                        "display.screenEnhancement.applications.org\\.gnome\\.desktop\\.wm\\.preferences.name"
                    ],
                    "options": {
                        "schema": "org.gnome.desktop.wm.preferences"
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
                    "name": "gnome-shell"
                }
            ]
        },
        "org.gnome.shell.overrides": {
            "name": "GNOME Shell overrides",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "capabilities": [
                        "applications.org\\.gnome\\.shell\\.overrides.id",
                        "display.screenEnhancement.applications.org\\.gnome\\.shell\\.overrides.name"
                    ],
                    "options": {
                        "schema": "org.gnome.shell.overrides"
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
                    "name": "gnome-shell"
                }
            ]
        },
        "org.gnome.orca": {
            "name": "ORCA Screen Reader",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.orca",
                    "options": {
                        "user": "${{gpiiKey}}"
                    },
                    "capabilities": [
                        "display.screenReader",
                        "applications.org\\.gnome\\.orca.id",
                        "display.screenReader.applications.org\\.gnome\\.orca.name"
                    ],
                    "capabilitiesTransformations": {
                        "enableTutorialMessages": "http://registry\\.gpii\\.net/common/speakTutorialMessages",
                        "enableEchoByCharacter": "http://registry\\.gpii\\.net/common/keyEcho",
                        "enableEchoByWord": "http://registry\\.gpii\\.net/common/wordEcho",
                        "enableBraille": "http://registry\\.gpii\\.net/common/screenReaderBrailleOutput",
                        "enableSpeech": "http://registry\\.gpii\\.net/common/screenReaderTTSEnabled",
                        "sayAllStyle": {
                            "transform": {
                                "type": "fluid.transforms.valueMapper",
                                "inputPath": "http://registry\\.gpii\\.net/common/readingUnit",
                                "defaultInputValue": "sentence",
                                "options": {
                                    "line": {
                                        "outputValue": 0
                                    },
                                    "sentence": {
                                        "outputValue": 1
                                    }
                                }
                            }
                        },
                        "voices\\.default\\.rate": {
                            "transform": {
                                "type": "fluid.transforms.binaryOp",
                                "right": 50,
                                "operator": "+",
                                "left": {
                                    "transform": {
                                        "type": "fluid.transforms.binaryOp",
                                        "operator": "/",
                                        "left": {
                                            "transform": {
                                                "type": "fluid.transforms.binaryOp",
                                                "leftPath": "http://registry\\.gpii\\.net/common/speechRate",
                                                "operator": "-",
                                                "right": 170
                                            }
                                        },
                                        "right": {
                                            "transform": {
                                                "type": "fluid.transforms.condition",
                                                "condition": {
                                                    "transform": {
                                                        "type": "fluid.transforms.binaryOp",
                                                        "leftPath": "http://registry\\.gpii\\.net/common/speechRate",
                                                        "operator": "<",
                                                        "right": 170
                                                    }
                                                },
                                                "true": 1.8,
                                                "false": 4.4
                                            }
                                        }
                                    }
                                }
                            }
                        },
                        "voices\\.default\\.average-pitch": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/pitch",
                                "factor": 10
                            }
                        },
                        "voices\\.default\\.gain": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/volumeTTS",
                                "factor": 10
                            }
                        },
                        "voices\\.default\\.family": {
                            "transform": {
                                "type": "fluid.transforms.valueMapper",
                                "inputPath": "http://registry\\.gpii\\.net/common/auditoryOutLanguage",
                                "defaultInputValue": "en",
                                "options": {
                                    "en": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "english"
                                                }
                                            }
                                        }
                                    },
                                    "en-GB": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "english"
                                                }
                                            }
                                        }
                                    },
                                    "en-US": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "english-us"
                                                }
                                            }
                                        }
                                    },
                                    "en-scotland": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "en-scottish"
                                                }
                                            }
                                        }
                                    },
                                    "en-BZ": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "en-westindies"
                                                }
                                            }
                                        }
                                    },
                                    "en-BS": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "en-westindies"
                                                }
                                            }
                                        }
                                    },
                                    "en-AG": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "en-westindies"
                                                }
                                            }
                                        }
                                    },
                                    "en-AI": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "en",
                                                    "name": "en-westindies"
                                                }
                                            }
                                        }
                                    },
                                    "af": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "af",
                                                    "name": "afrikaans"
                                                }
                                            }
                                        }
                                    },
                                    "bg": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "bg",
                                                    "name": "bulgarian-test"
                                                }
                                            }
                                        }
                                    },
                                    "bs": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "bs",
                                                    "name": "bosnian"
                                                }
                                            }
                                        }
                                    },
                                    "ca": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "ca",
                                                    "name": "catalan"
                                                }
                                            }
                                        }
                                    },
                                    "cs": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "cs",
                                                    "name": "czech"
                                                }
                                            }
                                        }
                                    },
                                    "cy": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "cy",
                                                    "name": "welsh-test"
                                                }
                                            }
                                        }
                                    },
                                    "da": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "da",
                                                    "name": "danish"
                                                }
                                            }
                                        }
                                    },
                                    "de": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "de",
                                                    "name": "german"
                                                }
                                            }
                                        }
                                    },
                                    "el": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "el",
                                                    "name": "greek"
                                                }
                                            }
                                        }
                                    },
                                    "grc": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "grc",
                                                    "name": "greek-ancient"
                                                }
                                            }
                                        }
                                    },
                                    "eo": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "eo",
                                                    "name": "esperanto"
                                                }
                                            }
                                        }
                                    },
                                    "es": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "es",
                                                    "name": "spanish"
                                                }
                                            }
                                        }
                                    },
                                    "es-419": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "es",
                                                    "name": "spanish-latin-american"
                                                }
                                            }
                                        }
                                    },
                                    "et": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "et",
                                                    "name": "estonian"
                                                }
                                            }
                                        }
                                    },
                                    "fi": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "fi",
                                                    "name": "finnish"
                                                }
                                            }
                                        }
                                    },
                                    "fr": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "fr",
                                                    "name": "french"
                                                }
                                            }
                                        }
                                    },
                                    "fr-BE": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "(Belgium)",
                                                    "name": "french"
                                                }
                                            }
                                        }
                                    },
                                    "hi": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "hi",
                                                    "name": "hindi"
                                                }
                                            }
                                        }
                                    },
                                    "hr": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "hr",
                                                    "name": "croatian"
                                                }
                                            }
                                        }
                                    },
                                    "hu": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "hu",
                                                    "name": "hungarian"
                                                }
                                            }
                                        }
                                    },
                                    "hy": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "hy",
                                                    "name": "armenian"
                                                }
                                            }
                                        }
                                    },
                                    "hy-arevmda": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "hy",
                                                    "name": "armenian-west"
                                                }
                                            }
                                        }
                                    },
                                    "id": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "id",
                                                    "name": "indonesian-test"
                                                }
                                            }
                                        }
                                    },
                                    "is": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "is",
                                                    "name": "icelandic-test"
                                                }
                                            }
                                        }
                                    },
                                    "it": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "it",
                                                    "name": "italian"
                                                }
                                            }
                                        }
                                    },
                                    "jbo": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "jbo",
                                                    "name": "lojban"
                                                }
                                            }
                                        }
                                    },
                                    "ka": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "ka",
                                                    "name": "georgian-test"
                                                }
                                            }
                                        }
                                    },
                                    "kn": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "kn",
                                                    "name": "kannada"
                                                }
                                            }
                                        }
                                    },
                                    "ku": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "ku",
                                                    "name": "kurdish"
                                                }
                                            }
                                        }
                                    },
                                    "la": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "la",
                                                    "name": "latin"
                                                }
                                            }
                                        }
                                    },
                                    "lv": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "lv",
                                                    "name": "latvian"
                                                }
                                            }
                                        }
                                    },
                                    "mk": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "mk",
                                                    "name": "macedonian-test"
                                                }
                                            }
                                        }
                                    },
                                    "ml": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "ml",
                                                    "name": "malayalam"
                                                }
                                            }
                                        }
                                    },
                                    "nl": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "nl",
                                                    "name": "dutch-test"
                                                }
                                            }
                                        }
                                    },
                                    "no": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "no",
                                                    "name": "norwegian"
                                                }
                                            }
                                        }
                                    },
                                    "pap": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "pap",
                                                    "name": "papiamento-test"
                                                }
                                            }
                                        }
                                    },
                                    "pl": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "pl",
                                                    "name": "polish"
                                                }
                                            }
                                        }
                                    },
                                    "pt-BR": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "pt",
                                                    "name": "brazil"
                                                }
                                            }
                                        }
                                    },
                                    "pt-PT": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "pt",
                                                    "name": "portugal"
                                                }
                                            }
                                        }
                                    },
                                    "ro": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "ro",
                                                    "name": "romanian"
                                                }
                                            }
                                        }
                                    },
                                    "ru": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "ru",
                                                    "name": "russian_test"
                                                }
                                            }
                                        }
                                    },
                                    "sk": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "sk",
                                                    "name": "slovak"
                                                }
                                            }
                                        }
                                    },
                                    "sq": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "sq",
                                                    "name": "albanian"
                                                }
                                            }
                                        }
                                    },
                                    "sr": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "sr",
                                                    "name": "serbian"
                                                }
                                            }
                                        }
                                    },
                                    "sv": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "sv",
                                                    "name": "swedish"
                                                }
                                            }
                                        }
                                    },
                                    "sw": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "sw",
                                                    "name": "swahili-test"
                                                }
                                            }
                                        }
                                    },
                                    "ta": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "ta",
                                                    "name": "tamil"
                                                }
                                            }
                                        }
                                    },
                                    "tr": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "tr",
                                                    "name": "turkish"
                                                }
                                            }
                                        }
                                    },
                                    "vi": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "vi",
                                                    "name": "vietnam"
                                                }
                                            }
                                        }
                                    },
                                    "zh-cmn": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "zh",
                                                    "name": "Mandarin"
                                                }
                                            }
                                        }
                                    },
                                    "cmn": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "zh",
                                                    "name": "Mandarin"
                                                }
                                            }
                                        }
                                    },
                                    "zh-yue": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "zh",
                                                    "name": "cantonese"
                                                }
                                            }
                                        }
                                    },
                                    "yue": {
                                        "outputValue": {
                                            "transform": {
                                                "type": "fluid.transforms.literalValue",
                                                "value": {
                                                    "locale": "zh",
                                                    "name": "cantonese"
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        },
                        "verbalizePunctuationStyle": {
                            "transform": {
                                "type": "fluid.transforms.valueMapper",
                                "inputPath": "http://registry\\.gpii\\.net/common/punctuationVerbosity",
                                "defaultInputValue": "most",
                                "options": {
                                    "none": {
                                        "outputValue": 3
                                    },
                                    "some": {
                                        "outputValue": 2
                                    },
                                    "most": {
                                        "outputValue": 1
                                    },
                                    "all": {
                                        "outputValue": 0
                                    }
                                }
                            }
                        }
                    }
                }
            },
            "configure": [
                "settings.configuration"
            ],
            "restore": [
                "settings.configuration"
            ],
            "start": [
                {
                    "type": "gpii.launch.exec",
                    "command": "gsettings set org.gnome.desktop.a11y.applications screen-reader-enabled true"
                }
            ],
            "stop": [
                {
                    "type": "gpii.launch.exec",
                    "command": "gsettings set org.gnome.desktop.a11y.applications screen-reader-enabled false"
                }
            ],
            "isInstalled": [
                {
                    "type": "gpii.packageKit.find",
                    "name": "orca"
                }
            ]
        },
        "org.alsa-project": {
            "name": "ALSA System Volume",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.alsa",
                    "capabilities": [
                        "applications.org\\.alsa-project.id"
                    ],
                    "capabilitiesTransformations": {
                        "masterVolume": {
                            "transform": {
                                "type": "fluid.transforms.linearScale",
                                "valuePath": "http://registry\\.gpii\\.net/common/volume",
                                "factor": 100
                            }
                        }
                    }
                }
            },
            "configure": [
                "settings.configuration"
            ],
            "restore": [
                "settings.configuration"
            ],
            "update": [
                "settings.configuration"
            ],
            "isInstalled": [
                {
                    "type": "gpii.packageKit.find",
                    "name": "alsa"
                },
                {
                    "type": "gpii.packageKit.find",
                    "name": "alsa-lib"
                }
            ]
        },
        "org.freedesktop.xrandr": {
            "name": "Xrandr",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.xrandr",
                    "capabilities": [
                        "display.screenEnhacements",
                        "applications.org\\.freedesktop\\.xrandr.id"
                    ]
                }
            },
            "configure": [
                "settings.configuration"
            ],
            "stop": [
                "settings.configuration"
            ],
            "isInstalled": [
                {
                    "type": "gpii.packageKit.find",
                    "name": "libXrandr"
                }
            ]
        },
        "com.ilunion.cloud4chrome": {
            "name": "Cloud4all Chrome extension",
            "contexts": {
                "OS": [
                    {
                        "id": "linux",
                        "version": ">=2.6.26"
                    }
                ]
            },
            "settingsHandlers": {
                "chromeconf": {
                    "type": "gpii.settingsHandlers.webSockets",
                    "options": {
                        "path": "com.ilunion.cloud4chrome"
                    },
                    "capabilities": [
                        "applications.com\\.ilunion\\.cloud4chrome.id"
                    ],
                    "capabilitiesTransformations": {
                        "screenReaderTTSEnabled": "http://registry\\.gpii\\.net/common/screenReaderTTSEnabled",
                        "fontSize": {
                            "transform": {
                                "type": "gpii.transformer.quantize",
                                "inputPath": "http://registry\\.gpii\\.net/common/fontSize",
                                "input": 9,
                                "ranges": [
                                    {
                                        "upperBound": 12,
                                        "output": "medium"
                                    },
                                    {
                                        "upperBound": 18,
                                        "output": "large"
                                    },
                                    {
                                        "output": "x-large"
                                    }
                                ]
                            }
                        },
                        "magnifierEnabled": "http://registry\\.gpii\\.net/common/magnifierEnabled",
                        "magnification": {
                            "transform": {
                                "type": "gpii.transformer.quantize",
                                "inputPath": "http://registry\\.gpii\\.net/common/magnification",
                                "input": 1,
                                "ranges": [
                                    {
                                        "upperBound": 1.2,
                                        "output": 1
                                    },
                                    {
                                        "upperBound": 2.5,
                                        "output": 2
                                    },
                                    {
                                        "output": 3
                                    }
                                ]
                            }
                        },
                        "highContrastEnabled": "http://registry\\.gpii\\.net/common/highContrastEnabled",
                        "highContrastTheme": "http://registry\\.gpii\\.net/common/highContrastTheme",
                        "invertColours": "http://registry\\.gpii\\.net/common/invertColours"
                    }
                }
            },
            "configure": [
                "settings.chromeconf"
            ],
            "restore": [
                "settings.chromeconf"
            ],
            "start": [],
            "stop": [],
            "isInstalled": [
                {
                    "type": "gpii.deviceReporter.alwaysInstalled"
                }
            ]
        }
    },
    "matchMakerOutput": {
        "inferredConfiguration": {
            "gpii-default": {
                "applications": {
                    "org.gnome.desktop.interface": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/highContrastTheme": "white-black"
                        }
                    }
                }
            },
            "subway": {
                "applications": {
                    "org.gnome.desktop.interface": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/highContrastTheme": "white-black"
                        }
                    }
                },
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "min": 400,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/visual\\.luminance"
                    }
                ]
            }
        }
    },
    "activeContextName": "gpii-default",
    "activeConfiguration": {
        "applications": {
            "org.gnome.desktop.interface": {
                "active": true,
                "settings": {
                    "http://registry.gpii.net/common/highContrastTheme": "white-black"
                }
            }
        }
    }
}
```
