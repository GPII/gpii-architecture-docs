## Preferences Server Payload Examples

See [the PreferencesServer documentation](https://github.com/GPII/universal/blob/master/documentation/PreferencesServer.md) for what the preferences server is and its API.

### Table of Contents
1. [Input - GET Request](#user-content-input---get-request)
2. [Return Payload](#user-content-return-payload)

### Input - GET Request

URL: `/preferences/:gpiiKey`

An example of the request parameter `gpiiKey`: `vladimir`

### Return Payload
 
```
{
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
}
```
