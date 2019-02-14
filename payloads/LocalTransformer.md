## Local Transformer Payload Examples

The local transformer transforms [the output of the local context manager](LocalContextManager-EvaluateMatch.md#user-content-return-payload) into the lifecycle instructions.

See [the Transformer documentation](https://github.com/GPII/universal/blob/master/documentation/Transformer.md) for more details.

### Table of Contents
1. [Input Payload](#user-content-input-payload)
2. [Return Payload](#user-content-return-payload)

### Input Payload

The payload received at the local transformer is identical with [the payload returned by the local context manager, evaluate match process](LocalContextManager-EvaluateMatch.md#user-content-return-payload).

#### Return Payload

```
{
    "lifecycleInstructions": {
        "org.gnome.desktop.a11y.magnifier": {
            "name": "GNOME Shell Magnifier",
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "options": {
                        "schema": "org.gnome.desktop.a11y.magnifier"
                    },
                    "settings": {
                        "mag-factor": 1.5,
                        "screen-position": "full-screen"
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
            ],
            "active": true
        },
        "org.alsa-project": {
            "name": "ALSA System Volume",
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.alsa",
                    "settings": {
                        "masterVolume": 50
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
            ],
            "active": true
        }
    },
    "activeContexts": [
        "gpii-default"
    ],
    "environmentReporter": {
        
    },
    "inferredCommonTerms": {
        "gpii-default": {
            
        },
        "bright": {
            
        },
        "noise": {
            
        },
        "brightandnoise": {
            
        }
    },
    "gpiiKey": "vladimir",
    "preferences": {
        "contexts": {
            "gpii-default": {
                "name": "Default preferences",
                "preferences": {
                    "http://registry.gpii.net/common/magnification": 1.5,
                    "http://registry.gpii.net/common/volume": 0.5
                }
            },
            "bright": {
                "name": "bright",
                "preferences": {
                    "http://registry.gpii.net/common/magnification": 2
                },
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 400000,
                        "min": 400,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
                    }
                ]
            },
            "noise": {
                "name": "noise",
                "preferences": {
                    "http://registry.gpii.net/common/volume": 1
                },
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 200000,
                        "min": 20000,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
                    }
                ]
            },
            "brightandnoise": {
                "name": "bright and noise",
                "preferences": {
                    "http://registry.gpii.net/common/volume": 1,
                    "http://registry.gpii.net/common/magnification": 2
                },
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 400000,
                        "min": 400,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
                    },
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 200000,
                        "min": 20000,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
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
                "id": "org.gnome.desktop.a11y.magnifier"
            },
            {
                "id": "org.alsa-project"
            },
            {
                "id": "org.gnome.desktop.a11y.keyboard"
            }
        ],
        "OS": {
            "id": "linux",
            "version": "2.6.26"
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
        }
    },
    "matchMakerOutput": {
        "inferredConfiguration": {
            "gpii-default": {
                "applications": {
                    "org.gnome.desktop.a11y.magnifier": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/magnification": 1.5,
                            "http://registry.gpii.net/common/volume": 0.5
                        }
                    },
                    "org.alsa-project": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/magnification": 1.5,
                            "http://registry.gpii.net/common/volume": 0.5
                        }
                    }
                }
            },
            "bright": {
                "applications": {
                    "org.gnome.desktop.a11y.magnifier": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/magnification": 2
                        }
                    }
                },
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 400000,
                        "min": 400,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
                    }
                ]
            },
            "noise": {
                "applications": {
                    "org.alsa-project": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/volume": 1
                        }
                    }
                },
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 200000,
                        "min": 20000,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
                    }
                ]
            },
            "brightandnoise": {
                "applications": {
                    "org.gnome.desktop.a11y.magnifier": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/volume": 1,
                            "http://registry.gpii.net/common/magnification": 2
                        }
                    },
                    "org.alsa-project": {
                        "active": true,
                        "settings": {
                            "http://registry.gpii.net/common/volume": 1,
                            "http://registry.gpii.net/common/magnification": 2
                        }
                    }
                },
                "conditions": [
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 400000,
                        "min": 400,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
                    },
                    {
                        "type": "http://registry.gpii.net/conditions/inRange",
                        "max": 200000,
                        "min": 20000,
                        "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
                    }
                ]
            }
        }
    },
    "activeContextName": "gpii-default",
    "activeConfiguration": {
        "applications": {
            "org.gnome.desktop.a11y.magnifier": {
                "active": true,
                "settings": {
                    "http://registry.gpii.net/common/magnification": 1.5,
                    "http://registry.gpii.net/common/volume": 0.5
                }
            },
            "org.alsa-project": {
                "active": true,
                "settings": {
                    "http://registry.gpii.net/common/magnification": 1.5,
                    "http://registry.gpii.net/common/volume": 0.5
                }
            }
        }
    }
}
Got final payload {
  "lifecycleInstructions": {
    "org.gnome.desktop.a11y.magnifier": {
      "name": "GNOME Shell Magnifier",
      "settingsHandlers": {
        "configuration": {
          "type": "gpii.gsettings",
          "options": {
            "schema": "org.gnome.desktop.a11y.magnifier"
          },
          "settings": {
            "mag-factor": 1.5,
            "screen-position": "full-screen"
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
      ],
      "active": true
    },
    "org.alsa-project": {
      "name": "ALSA System Volume",
      "settingsHandlers": {
        "configuration": {
          "type": "gpii.alsa",
          "settings": {
            "masterVolume": 50
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
      ],
      "active": true
    }
  },
  "activeContexts": [
    "gpii-default"
  ],
  "environmentReporter": {},
  "inferredCommonTerms": {
    "gpii-default": {},
    "bright": {},
    "noise": {},
    "brightandnoise": {}
  },
  "gpiiKey": "vladimir",
  "preferences": {
    "contexts": {
      "gpii-default": {
        "name": "Default preferences",
        "preferences": {
          "http://registry.gpii.net/common/magnification": 1.5,
          "http://registry.gpii.net/common/volume": 0.5
        }
      },
      "bright": {
        "name": "bright",
        "preferences": {
          "http://registry.gpii.net/common/magnification": 2
        },
        "conditions": [
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 400000,
            "min": 400,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
          }
        ]
      },
      "noise": {
        "name": "noise",
        "preferences": {
          "http://registry.gpii.net/common/volume": 1
        },
        "conditions": [
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 200000,
            "min": 20000,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
          }
        ]
      },
      "brightandnoise": {
        "name": "bright and noise",
        "preferences": {
          "http://registry.gpii.net/common/volume": 1,
          "http://registry.gpii.net/common/magnification": 2
        },
        "conditions": [
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 400000,
            "min": 400,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
          },
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 200000,
            "min": 20000,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
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
        "id": "org.gnome.desktop.a11y.magnifier"
      },
      {
        "id": "org.alsa-project"
      },
      {
        "id": "org.gnome.desktop.a11y.keyboard"
      }
    ],
    "OS": {
      "id": "linux",
      "version": "2.6.26"
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
    }
  },
  "matchMakerOutput": {
    "inferredConfiguration": {
      "gpii-default": {
        "applications": {
          "org.gnome.desktop.a11y.magnifier": {
            "active": true,
            "settings": {
              "http://registry.gpii.net/common/magnification": 1.5,
              "http://registry.gpii.net/common/volume": 0.5
            }
          },
          "org.alsa-project": {
            "active": true,
            "settings": {
              "http://registry.gpii.net/common/magnification": 1.5,
              "http://registry.gpii.net/common/volume": 0.5
            }
          }
        }
      },
      "bright": {
        "applications": {
          "org.gnome.desktop.a11y.magnifier": {
            "active": true,
            "settings": {
              "http://registry.gpii.net/common/magnification": 2
            }
          }
        },
        "conditions": [
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 400000,
            "min": 400,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
          }
        ]
      },
      "noise": {
        "applications": {
          "org.alsa-project": {
            "active": true,
            "settings": {
              "http://registry.gpii.net/common/volume": 1
            }
          }
        },
        "conditions": [
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 200000,
            "min": 20000,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
          }
        ]
      },
      "brightandnoise": {
        "applications": {
          "org.gnome.desktop.a11y.magnifier": {
            "active": true,
            "settings": {
              "http://registry.gpii.net/common/volume": 1,
              "http://registry.gpii.net/common/magnification": 2
            }
          },
          "org.alsa-project": {
            "active": true,
            "settings": {
              "http://registry.gpii.net/common/volume": 1,
              "http://registry.gpii.net/common/magnification": 2
            }
          }
        },
        "conditions": [
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 400000,
            "min": 400,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
          },
          {
            "type": "http://registry.gpii.net/conditions/inRange",
            "max": 200000,
            "min": 20000,
            "inputPath": "http://registry\\.gpii\\.net/common/environment/auditory\\.noise"
          }
        ]
      }
    }
  },
  "activeContextName": "gpii-default",
  "activeConfiguration": {
    "applications": {
      "org.gnome.desktop.a11y.magnifier": {
        "active": true,
        "settings": {
          "http://registry.gpii.net/common/magnification": 1.5,
          "http://registry.gpii.net/common/volume": 0.5
        }
      },
      "org.alsa-project": {
        "active": true,
        "settings": {
          "http://registry.gpii.net/common/magnification": 1.5,
          "http://registry.gpii.net/common/volume": 0.5
        }
      }
    }
  }
}
15:27:32.962:  Mock exec handler for command gsettings set org.gnome.desktop.a11y.applications screen-magnifier-enabled true args undefined
15:27:32.963:  No start actions defined for solution org.alsa-project
15:27:32.964:  Lifecycle manager startLifecycle returned: true
!!!*!*!!* checkConfiguration - expected {
  "gpii.gsettings": {
    "data": [
      {
        "settings": {
          "mag-factor": 1.5
        }
      }
    ]
  },
  "gpii.alsa": {
    "data": [
      {
        "settings": {
          "masterVolume": 50
        }
      }
    ]
  }
} actual {
  "gpii.gsettings": {
    "data": [
      {
        "settings": {
          "mag-factor": 1.5
        }
      }
    ]
  },
  "gpii.alsa": {
    "data": [
      {
        "settings": {
          "masterVolume": 50
        }
      }
    ]
  }
}
15:27:32.984:  Sending a PUT request to: /environmentChanged on port 8081
15:27:32.986:  Invoking handler gpii.contextManager.environmentChanged.handler for route /environmentChanged with expectedGrade kettle.request.http
15:27:32.994:  Kettle server allocated request object with type gpii.contextManager.environmentChanged.handler
15:27:32.995:  Updating context with: {
    "http://registry.gpii.net/common/environment/illuminance": 500,
    "http://registry.gpii.net/common/environment/auditory.noise": 10000
}
15:27:32.999:  Active contexts calculated to be: bright,gpii-default
15:27:32.999:  New active contexts: bright,gpii-default
15:27:33.000:  ===Context Manager evaluateConditions() - output payload: {
    "gpiiKey": "vladimir",
    "lifecycleInstructions": {
        "org.gnome.desktop.a11y.magnifier": {
            "name": "GNOME Shell Magnifier",
            "settingsHandlers": {
                "configuration": {
                    "type": "gpii.gsettings",
                    "options": {
                        "schema": "org.gnome.desktop.a11y.magnifier"
                    },
                    "settings": {
                        "mag-factor": 2,
                        "screen-position": "full-screen"
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
            ],
            "active": true
        }
    },
    "activeContextName": "bright",
    "activeConfiguration": {
        "applications": {
            "org.gnome.desktop.a11y.magnifier": {
                "active": true,
                "settings": {
                    "http://registry.gpii.net/common/magnification": 2
                }
            }
        },
        "conditions": [
            {
                "type": "http://registry.gpii.net/conditions/inRange",
                "max": 400000,
                "min": 400,
                "inputPath": "http://registry\\.gpii\\.net/common/environment/illuminance"
            }
        ]
    }
}
```
