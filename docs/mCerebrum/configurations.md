# Configuration
**mCerebrum** is primarily configured and controlled by a set of JSON configuration files.  This document describes how to utilize and adapt these configurations to your own requirements.

# Generic structures

## Data source
A data source uniquely represents a single data stream within mCerebrum.  Subsets of a data source definition can be utilized to query for multiple streams. This example contains all possible fields:

```JSON
{
  "type": "MEMORY",
  "id": "DataSourceID",
  "platform": {
    "id": "Phone1",
    "type": "PHONE",
    "metadata": {
      "OPERATING_SYSTEM": "5.1.1",
      "MODEL": "SAMSUNG-SM-G900A",
      "MANUFACTURER": "samsung",
      "NAME": "Phone"
    }
  },
  "platformapp": {
    "id": "platformapp1",
    "type": "PHONEAPP",
    "metadata": {
      "NAME": "PhoneApp"
    }
  },
  "application": {
    "id": "org.md2k.phonesensor",
    "type": "PhoneApp",
    "metadata": {
      "VERSION_NAME": "0.8.0",
      "VERSION_NUMBER": "11"
    }
  },
  "dataDescriptors": [
    {
      "UNIT": "megabyte",
      "DESCRIPTION": "Size of the memory",
      "FREQUENCY": "1.0 Hz",
      "MAX_VALUE": "2048",
      "MIN_VALUE": "0",
      "DATA_TYPE": "float",
      "NAME": "Size"
    },
    {
      "UNIT": "megabyte",
      "DESCRIPTION": "Available memory",
      "FREQUENCY": "1.0 Hz",
      "MAX_VALUE": "2048",
      "MIN_VALUE": "0",
      "DATA_TYPE": "float",
      "NAME": "Available"
    }
  ],
  "metadata": {
    "DESCRIPTION": "measures usage of memory",
    "FREQUENCY": "1.0 Hz",
    "DATA_TYPE": "org.md2k.datakitapi.datatype.DataTypeFloatArray",
    "NAME": "Memory"
  }
}
```

Querying supports a subset of the fields as specified below and all fields are optional to include additional data stream.  Any data stream that matches all specified parameter is returned.

- `type`: String specification designating the type of the object
- `id`: TODO: What does id mean here?

`Platform`, `platformapp`, and `application` each contain specific `type` and `id` fields that are identically defined.

```JSON
{
  "type": "MEMORY",
  "id": "DataSourceID",
  "platform": {
    "id": "Phone1",
    "type": "PHONE"
  },
  "platformapp": {
    "id": "platformapp1",
    "type": "PHONEAPP"
  },
  "application": {
    "id": "org.md2k.phonesensor",
    "type": "PhoneApp"
  }
}
```


## Privacy type options
Privacy options are define by specifying the following four parameters and are utilized by DataKit to provide a mechanism
that prevents data sources that match the define `source` criteria from being routed and recorded.

- `id`: unique privacy id string (TODO: What is the meaning of `id` in general?)
- `title`: String suitable for display on the user interface
- `summary`: Summary description for display on the user interface for additional details
- `source`: list of [data sources](#data-source) (TODO: Why is this different than the listed data source definition?)

```JSON
{
  "id": "location",
  "title": "Location",
  "summary": "",
  "source": [
    {
      "datasource_type": "LOCATION"
    }
  ]
}
```

## Notification

```JSON
[
  {
    "id": "MICROSOFT_BAND_VIBRATE_3",
    "name": "Microsoft Band Vibration",
    "type": "VIBRATION",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "MICROSOFT_BAND"
      }
    },
    "format": "THREE_TONE_HIGH",
    "repeat": 3,
    "duration": 2000
  },
  {
    "id": "MICROSOFT_BAND_MESSAGE_EMA",
    "name": "Microsoft Band Message (EMA)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "MICROSOFT_BAND"
      }
    },
    "repeat": 1,
    "duration": 300000,
    "message": [
      "Survey",
      "Time to take a Survey"
    ]
  },
  {
    "id": "MICROSOFT_BAND_MESSAGE_MOODSURFING",
    "name": "Microsoft Band Message (MoodSurfing)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "MICROSOFT_BAND"
      }
    },
    "repeat": 1,
    "duration": 300000,
    "message": [
      "Mood Surfing",
      "Take a moment to surf your mood"
    ]
  },
  {
    "id": "MICROSOFT_BAND_MESSAGE_HEADSPACE",
    "name": "Microsoft Band Message (Head Space)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "MICROSOFT_BAND"
      }
    },
    "repeat": 1,
    "duration": 300000,
    "message": [
      "HeadSpace",
      "Time a moment to make some head space"
    ]
  },
  {
    "id": "MICROSOFT_BAND_MESSAGE_THOUGHTSHAKEUP",
    "name": "Microsoft Band Message (Thought Shakeup)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "MICROSOFT_BAND"
      }
    },
    "repeat": 1,
    "duration": 300000,
    "message": [
      "Thought Shakeup",
      "Take a moment to shake up your thoughts"
    ]
  },
  {
    "id": "PHONE_VIBRATE_3",
    "name": "Phone Vibration",
    "type": "VIBRATION",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "format": "THREE_TONE",
    "repeat": 3,
    "duration": 1500
  },
  {
    "id": "PHONE_TONE_3",
    "name": "Phone Tone",
    "type": "TONE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "format": "THREE_TONE_HIGH",
    "repeat": 3,
    "duration": 1500
  },
  {
    "id": "PHONE_SCREEN",
    "name": "Phone Screen",
    "type": "SCREEN",
    "priority": 0,
    "repeat": 1,
    "duration": 300000,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    }
  },
  {
    "id": "PHONE_MESSAGE_DELAY_EMA",
    "name": "Phone Message (EMA)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "repeat": 1,
    "duration": 300000,
    "message": [
      "Survey",
      "Time to take a Survey",
      "OK",
      "Cancel",
      "Delay 10 Minutes"
    ],
    "response_option": {
      "ok": true,
      "cancel": true,
      "delay": true,
      "delay_time": 600000
    }
  },
  {
    "id": "PHONE_MESSAGE_DELAY_EMA_15_30_60_120",
    "name": "Phone Message (EMA)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "repeat": 1,
    "duration": 300000,
    "message": [
      "Survey",
      "Time to take a Survey",
      "OK",
      "Cancel",
      "Delay"
    ],
    "response_option": {
      "ok": true,
      "cancel": true,
      "delay": true,
      "delay_time": -1
    }
  },
  {
    "id": "PHONE_MESSAGE_MOODSURFING",
    "name": "Phone Message (MoodSurfing)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "repeat": 1,
    "duration": 120000,
    "message": [
      "Mood Surfing",
      "Take a moment to surf your mood",
      "OK",
      "Cancel"
    ],
    "response_option": {
      "ok": true,
      "cancel": true,
      "delay": false
    }
  },
  {
    "id": "PHONE_MESSAGE_THOUGHTSHAKEUP",
    "name": "Phone Message (ThoughtShakeup)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "repeat": 1,
    "duration": 120000,
    "message": [
      "Thought Shakeup",
      "Take a moment to shake up your thoughts",
      "OK",
      "Cancel"
    ],
    "response_option": {
      "ok": true,
      "cancel": true,
      "delay": false
    }
  },
  {
    "id": "PHONE_MESSAGE_HEADSPACE",
    "name": "Phone Message (HeadSpace)",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "repeat": 1,
    "duration": 120000,
    "message": [
      "HeadSpace",
      "Time a moment to make some head space",
      "OK",
      "Cancel"
    ],
    "response_option": {
      "ok": true,
      "cancel": true,
      "delay": false
    }
  }
]
```

## Study notifications

```JSON
[
  {
    "id": "PHONE_VIBRATE",
    "name": "Phone Vibration",
    "type": "VIBRATION",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "format": "THREE_TONE",
    "repeat": 60,
    "duration": 10800000
  },
  {
    "id": "PHONE_TONE",
    "name": "Phone Tone",
    "type": "TONE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "format": "THREE_TONE_HIGH",
    "repeat": 60,
    "duration": 10800000
  },
  {
    "id": "PHONE_SCREEN",
    "name": "Phone Screen",
    "type": "SCREEN",
    "priority": 0,
    "repeat": 1,
    "duration": 10000,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    }
  },
  {
    "id": "PHONE_MESSAGE_START_DAY",
    "name": "Start Day",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "repeat": 1,
    "duration": 3600000000,
    "message": [
      "Start Day",
      "Please start the Day",
      "OK"
    ],
    "response_option": {
      "ok": true,
      "cancel": false,
      "delay": false
    }
  },
  {
    "id": "PHONE_MESSAGE_END_DAY",
    "name": "End Day",
    "type": "MESSAGE",
    "priority": 0,
    "datasource": {
      "platform": {
        "type": "PHONE"
      }
    },
    "repeat": 1,
    "duration": 3600000000,
    "message": [
      "End Day",
      "Please end the Day",
      "OK"
    ],
    "response_option": {
      "ok": true,
      "cancel": false,
      "delay": false
    }
  }
]
```

## Conditions
Conditions provide a mechanism to specify constraints based on the output of various sensors and data streams.  They are
defined as follows  and referenced by `id` within other documents.

- `id`: Unique string identifier to be used as reference within other JSON configurations
- `type`: defines the type category of condition and is user specified
- `name`: String describing the condition and could be shown to a participant
- `values`: List of input values for the evaluation function
- `data_source`: An single object as defined in the [data source](#data-source) query support


Example:
```JSON
[
  {
    "id": "PHONE_BATTERY_10",
    "type": "PHONE_BATTERY",
    "name": "Phone battery percentage is greater than 10",
    "values": [
      "10"
    ],
    "data_source": {
      "application": {
        "id": "org.md2k.phonesensor"
      },
      "type": "BATTERY"
    }
  },
  {
    "id": "NOT_ACTIVE_1",
    "type": "NOT_ACTIVE",
    "name": "Not physically active in last 1 minute",
    "values": [
      "60000",
      "0"
    ],
    "data_source": {
      "application": {
        "id": "org.md2k.streamprocessor"
      },
      "type": "STRESS_ACTIVITY"
    }
  },
  {
    "id": "NOT_DRIVING_5",
    "type": "NOT_DRIVING",
    "name": "Not driving in last 5 minutes",
    "values": [
      "300000",
      "60"
    ]
  },
  {
    "id": "DATA_QUALITY_5",
    "type": "DATA_QUALITY",
    "name": "Data quality good in last 5 minutes",
    "values": [
      "300000",
      "80"
    ],
    "data_source": {
      "platform": {
        "type": "AUTOSENSE_CHEST"
      },
      "type": "DATA_QUALITY",
      "id": "RESPIRATION"
    }
  },
  {
    "id": "DATA_QUALITY_DAY_START",
    "type": "DATA_QUALITY",
    "name": "Data quality good from the day started",
    "values": [
      "DAY_START",
      "60"
    ],
    "data_source": {
      "platform": {
        "type": "AUTOSENSE_CHEST"
      },
      "type": "DATA_QUALITY",
      "id": "RESPIRATION"
    }
  },
  {
    "id": "EMA_ANSWER_5",
    "type": "EMA_ANSWER",
    "name": "EMA answered in 5 Minutes",
    "values": [
      "300000"
    ]
  },
  {
    "id": "RANDOM_EMA_60",
    "type": "LAST_EMA_EMI",
    "name": "Last Triggered Random EMA 60 minute ago",
    "values": [
      "3600000"
    ],
    "source": {
      "id": "RANDOM_EMA",
      "type": "EMA"
    }
  },
  {
    "id": "RANDOM_EMA_10",
    "type": "LAST_EMA_EMI",
    "name": "Last Triggered Random EMA 10 minute ago",
    "values": [
      "600000"
    ],
    "source": {
      "id": "RANDOM_EMA",
      "type": "EMA"
    }
  },
  {
    "id": "SMOKING_EMA_10",
    "type": "LAST_EMA_EMI",
    "name": "Last Triggered SMOKING EMA 10 minute ago",
    "values": [
      "600000"
    ],
    "source": {
      "id": "SMOKING_EMA",
      "type": "EMA"
    }
  },
  {
    "id": "SMOKING_EMA_30",
    "type": "LAST_EMA_EMI",
    "name": "Last Triggered SMOKING EMA 30 minute ago",
    "values": [
      "1800000"
    ],
    "source": {
      "id": "SMOKING_EMA",
      "type": "EMA"
    }
  },
  {
    "id": "EMI_10",
    "type": "LAST_EMA_EMI",
    "name": "Last Triggered EMI 10 minute ago",
    "values": [
      "600000"
    ],
    "source": {
      "id": "EMI",
      "type": "EMI"
    }
  },
  {
    "id": "EMI_60",
    "type": "LAST_EMA_EMI",
    "name": "Last Triggered EMI 10 minute ago",
    "values": [
      "3600000"
    ],
    "source": {
      "id": "EMI",
      "type": "EMI"
    }
  },
  {
    "id": "VALID_BLOCK_SMOKING_EMA",
    "type": "VALID_BLOCK",
    "name": "No EMA/EMI triggered in this block",
    "values": [
      "1"
    ],
    "source": {
      "id": "SMOKING_EMA",
      "type": "EMA"
    }
  },
  {
    "id": "VALID_BLOCK_RANDOM_EMA",
    "type": "VALID_BLOCK",
    "name": "No EMA/EMI triggered in this block",
    "values": [
      "1"
    ],
    "source": {
      "id": "RANDOM_EMA",
      "type": "EMA"
    }
  },
  {
    "id": "PRIVACY",
    "type": "PRIVACY",
    "name": "Privacy is active",
    "data_source": {
      "type": "PRIVACY"
    }
  }
]
```








# Notification Manager
Config file name and location: `mCerebrum/org.md2k.notificationmanager/`

Notification manager requires `tone.mp3` to be present in this folder and utilizes this file for audible alerts for participants.





# Stream Processor
Config file name and location: `mCerebrum/org.md2k.streamprocessor`

Stream processor requires that SVM model files be present in this directory.



# mCerebrum
Config file name and location: `mCerebrum/org.md2k.study/config.json`

## Base
Defined in main application json file

```JSON
{
    "day_start": {
        "by": "user",
        "base": "wakeup",
        "notify": [
          {
            "type": "button",
            "offset": -30000
          },
          {
            "type": "prompt",
            "offset": 0,
            "parameters": [
              "PHONE_SCREEN",
              "PHONE_MESSAGE_START_DAY"
            ]
          },
          {
            "type": "notification",
            "offset": 30000,
            "parameters": [
              "PHONE_VIBRATE",
              "PHONE_TONE",
              "PHONE_SCREEN",
              "PHONE_MESSAGE_START_DAY"
            ]
          }
        ]
      }
}
```

## Example
```JSON
{
  "config_info": {
    "id": "STU00201566-Test",
    "name": "MD2K Smoking Study (at NW)-Test",
    "version_code": 21,
    "required_files": [
      "org.md2k.autosense/default_config.json",
      "org.md2k.datakit/config.json",
      "org.md2k.datakit/default_config.json",
      "org.md2k.ema/config_ema.json",
      "org.md2k.ema/end_of_day_recording.json",
      "org.md2k.ema/event_contingent_recording.json",
      "org.md2k.ema/random_experience_sampling.json",
      "org.md2k.ema_scheduler/config.json",
      "org.md2k.ema_scheduler/notification.json",
      "org.md2k.ema_scheduler/condition.json",
      "org.md2k.microsoftband/default_config.json",
      "org.md2k.phonesensor/default_config.json",
      "org.md2k.plotter/default_config.json",
      "org.md2k.streamprocessor/model.json",
      "org.md2k.streamprocessor/model_rip.json",
      "org.md2k.notificationmanager/tone.mp3",
      "org.md2k.study/config.json",
      "org.md2k.study/notification.json",
      "org.md2k.study/tutorial.pdf"
    ]
  },
  "study_info": {
    "id": "STU00201566-Test",
    "name": "MD2K Smoking Study (at NW)-Test"
  },
  "apps": [
    {
      "id": "study",
      "name": "Study",
      "enable": true,
      "package_name": "org.md2k.study",
      "download_link": "https://github.com/MD2Korg/mCerebrum-Study/releases"
    },
    {
      "id": "datakit",
      "name": "DataKit",
      "enable": true,
      "package_name": "org.md2k.datakit",
      "config": "config.json",
      "default_config": "default_config.json",
      "service": "org.md2k.datakit.cerebralcortex.ServiceCerebralCortex",
      "download_link": "https://github.com/MD2Korg/mCerebrum-DataKit/releases"
    },
    {
      "id": "phonesensor",
      "name": "PhoneSensor",
      "enable": true,
      "package_name": "org.md2k.phonesensor",
      "service": "org.md2k.phonesensor.ServicePhoneSensor",
      "settings": "org.md2k.phonesensor.ActivityPhoneSensorSettings",
      "config": "config.json",
      "default_config": "default_config.json",
      "download_link": "https://github.com/MD2Korg/mCerebrum-PhoneSensor/releases"
    },
    {
      "id": "autosense",
      "name": "AutoSense",
      "enable": true,
      "package_name": "org.md2k.autosense",
      "service": "org.md2k.autosense.antradio.connection.ServiceAutoSenses",
      "settings": "org.md2k.autosense.ActivityAutoSenseSettings",
      "config": "config.json",
      "default_config": "default_config.json",
      "download_link": "https://github.com/MD2Korg/mCerebrum-AutoSense/releases"
    },
    {
      "id": "microsofthealth",
      "name": "MicrosoftHealth",
      "enable": true,
      "package_name": "com.microsoft.kapp",
      "download_link": "market://details?id=com.microsoft.kapp"
    },
    {
      "id": "microsoftband",
      "name": "MicrosoftBand",
      "enable": true,
      "package_name": "org.md2k.microsoftband",
      "service": "org.md2k.microsoftband.ServiceMicrosoftBands",
      "settings": "org.md2k.microsoftband.ActivityMicrosoftBandSettings",
      "config": "config.json",
      "default_config": "default_config.json",
      "download_link": "https://github.com/MD2Korg/mCerebrum-MicrosoftBand/releases"
    },
    {
      "id": "streamprocessor",
      "name": "StreamProcessor",
      "enable": true,
      "package_name": "org.md2k.streamprocessor",
      "service": "org.md2k.streamprocessor.ServiceStreamProcessor",
      "download_link": "https://github.com/MD2Korg/mCerebrum-StreamProcessor/releases"
    },
    {
      "id": "ema_scheduler",
      "name": "EMAScheduler",
      "enable": true,
      "package_name": "org.md2k.ema_scheduler",
      "service": "org.md2k.ema_scheduler.ServiceEMAScheduler",
      "config": "config.json",
      "download_link": "https://github.com/MD2Korg/mCerebrum-EMAScheduler/releases"
    },
    {
      "id": "notificationmanager",
      "name": "NotificationManager",
      "enable": true,
      "package_name": "org.md2k.notificationmanager",
      "service": "org.md2k.notificationmanager.ServiceNotificationManager",
      "download_link": "https://github.com/MD2Korg/mCerebrum-NotificationManager/releases"
    },
    {
      "id": "ema",
      "name": "EMA",
      "enable": true,
      "package_name": "org.md2k.ema",
      "download_link": "https://github.com/MD2Korg/mCerebrum-EMA/releases"
    },
    {
      "id": "moodsurfing",
      "name": "MoodSurfing",
      "enable": true,
      "package_name": "org.md2k.moodsurfing",
      "download_link": "https://github.com/MD2Korg/mCerebrum-MoodSurfing/releases"
    },
    {
      "id": "thoughtshakeup",
      "name": "ThoughtShakeup",
      "enable": true,
      "package_name": "org.md2k.thoughtshakeup",
      "download_link": "https://github.com/MD2Korg/mCerebrum-ThoughtShakeup/releases"
    },
    {
      "id": "headspace",
      "name": "HeadSpace",
      "enable": true,
      "package_name": "com.getsomeheadspace.android",
      "download_link": "market://details?id=com.getsomeheadspace.android"
    },
    {
      "id": "plotter",
      "name": "Plotter",
      "enable": true,
      "package_name": "org.md2k.plotter",
      "default_config": "default_config.json",
      "download_link": "https://github.com/MD2Korg/mCerebrum-Plotter/releases"
    },
    {
      "id": "adobe_acrobat_reader",
      "name": "Adobe Acrobat Reader",
      "enable": true,
      "package_name": "com.adobe.reader",
      "download_link": "market://details?id=com.adobe.reader"
    }
  ],
  "actions": [
    {
      "id": "config_info",
      "type": "setup",
      "name": "Configuration Info",
      "enable": true,
      "rank": 7
    },
    {
      "id": "clear_config",
      "type": "reset",
      "name": "Clear Configuration",
      "enable": true,
      "rank": 7,
      "icon": "ic_delete_blue_48dp",
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.clear_config.ActivityClearConfig"
    },
    {
      "id": "config_download",
      "type": "reset",
      "name": "Download New Configuration",
      "enable": true,
      "rank": 7,
      "package_name": "org.md2k.study",
      "icon": "ic_download_teal_48dp",
      "class_name": "org.md2k.study.model_view.config_info.ActivityConfigDownload"
    },
    {
      "id": "app_install",
      "type": "setup",
      "name": "Applications",
      "enable": true,
      "rank": 6,
      "icon": "ic_install_teal_48dp",
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.app_install.ActivityInstallApp"
    },
    {
      "id": "app_settings",
      "type": "setup",
      "name": "Settings",
      "enable": true,
      "rank": 6,
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.app_settings.ActivityAppSettings",
      "icon": "ic_settings_teal_48dp"
    },
    {
      "id": "datakit_connect",
      "type": "setup",
      "name": "DataKit Connection",
      "enable": true,
      "rank": 5
    },
    {
      "id": "study_info",
      "type": "setup",
      "enable": true,
      "rank": 4,
      "name": "Study"
    },
    {
      "id": "user_info",
      "type": "setup",
      "name": "User ID",
      "enable": true,
      "rank": 4,
      "icon": "ic_user_teal_48dp",
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.user_info.ActivityUserInfo"
    },
    {
      "id": "wakeup_info",
      "type": "setup",
      "name": "Wakeup Time",
      "rank": 4,
      "enable": true,
      "icon": "ic_wakeup_teal_48dp",
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.wakeup_info.ActivityWakeUp"
    },
    {
      "id": "sleep_info",
      "type": "setup",
      "name": "Sleep Time",
      "rank": 4,
      "enable": true,
      "icon": "ic_sleep_teal_48dp",
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.sleep_info.ActivitySleep"
    },
    {
      "id": "day_type",
      "type": "setup",
      "name": "Pre/Post Quit Day",
      "rank": 4,
      "enable": true,
      "icon": "ic_sleep_teal_48dp",
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.day_type.ActivityDayType"
    },
    {
      "id": "clear_database",
      "type": "reset",
      "name": "Clear All Data",
      "icon": "ic_delete_indigo_48dp",
      "enable": true,
      "rank": 4,
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.clear_data.ActivityClearData"
    },
    {
      "id": "app_service",
      "type": "setup",
      "enable": true,
      "name": "Running Apps",
      "rank": 3,
      "icon": "ic_apps_teal_48dp",
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.app_service.ActivityService"
    },
    {
      "id": "data_quality",
      "rank": 2,
      "enable": true,
      "name": "Sensor Data Quality"
    },
    {
      "id": "day_start_end",
      "type": "setup",
      "rank": 2,
      "enable": true,
      "name": "Day Start/Day End"
    },
    {
      "id": "privacy",
      "name": "Privacy",
      "icon": "ic_unlock_teal_48dp",
      "enable": true,
      "package_name": "org.md2k.datakit",
      "rank": 2,
      "class_name": "org.md2k.datakit.ActivityPrivacy"
    },
    {
      "id": "user_status",
      "name": "user_status",
      "icon": "ic_unlock_teal_48dp",
      "enable": true,
      "rank": 2
    },
    {
      "id": "intervention",
      "name": "Intervention",
      "icon": "ic_intervention_48dp",
      "package_name": "org.md2k.study",
      "enable": true,
      "rank": 2,
      "class_name": "org.md2k.study.model_view.intervention.ActivityInterventionApp"
    },
    {
      "id": "smoking_self_report",
      "name": "Report Smoking",
      "icon": "ic_smoking_teal_48dp",
      "enable": true,
      "package_name": "org.md2k.study",
      "rank": 2,
      "class_name": "org.md2k.study.model_view.selfreport.ActivitySelfReport"
    },
    {
      "id": "plotter",
      "name": "Plotter",
      "enable": true,
      "icon": "ic_plot_teal_48dp",
      "rank": 2,
      "package_name": "org.md2k.plotter"
    },
    {
      "id": "user_app",
      "name": "User Application",
      "icon": "ic_unlock_teal_48dp",
      "enable": true,
      "rank": 2
    },
    {
      "id": "EMA_test",
      "type": "App Controller",
      "name": "Survey/EMI Test",
      "enable": true,
      "icon": "ic_notification_teal_48dp",
      "rank": 2,
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.EMA_test.ActivityEMA_test"
    },
    {
      "id": "app_reset",
      "name": "Reset App",
      "icon": "ic_refresh_teal_48dp",
      "enable": true,
      "rank": 2,
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.app_reset.ActivityAppReset"
    },
    {
      "id": "app_start",
      "name": "Start Data Collection",
      "icon": "ic_play_teal_48dp",
      "enable": true,
      "rank": 2,
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.app_start.ActivityAppStart"
    },
    {
      "id": "app_stop",
      "name": "Stop & Close Application",
      "icon": "ic_error_red_50dp",
      "enable": true,
      "rank": 2,
      "package_name": "org.md2k.study",
      "class_name": "org.md2k.study.model_view.app_stop.ActivityAppStop"
    }
  ],
  "admin_view": {
    "password": "1234",
    "view_contents": [
      {
        "id": "key_configure_app",
        "name": "Configure Applications",
        "enable": true,
        "values": [
          "config_info",
          "app_install",
          "app_settings",
          "config_download",
          "clear_config"
        ]
      },
      {
        "id": "key_configure_study",
        "name": "Configure Study",
        "enable": true,
        "values": [
          "config_info",
          "study_info",
          "user_info",
          "day_type",
          "wakeup_info",
          "sleep_info",
          "clear_database"
        ]
      },
      {
        "id": "key_start_study",
        "name": "Start Study",
        "enable": true
      },
      {
        "id": "key_stop_study",
        "name": "Stop Study",
        "enable": true
      },
      {
        "id": "key_other",
        "name": "Others",
        "enable": true,
        "values": [
          "app_service",
          "EMA_test"
        ]
      }
    ]
  },
  "user_view": {
    "view_contents": [
      {
        "id": "data_quality",
        "enable": true
      },
      {
        "id": "day_start_end",
        "enable": true
      },
      {
        "id": "privacy",
        "enable": true
      },
      {
        "id": "user_app",
        "enable": true,
        "values": [
          "smoking_self_report",
          "intervention",
          "app_reset"
        ]
      }
    ]
  },
  "data_quality": [
    {
      "platform": {
        "type": "AUTOSENSE_CHEST"
      },
      "type": "DATA_QUALITY",
      "id": "RESPIRATION"
    },
    {
      "platform": {
        "type": "AUTOSENSE_CHEST"
      },
      "type": "DATA_QUALITY",
      "id": "ECG"
    },
    {
      "platform": {
        "id": "LEFT_WRIST"
      },
      "type": "DATA_QUALITY"
    },
    {
      "platform": {
        "id": "RIGHT_WRIST"
      },
      "type": "DATA_QUALITY"
    }
  ],
  "data_quality_view": [
    {
      "name": "Breathing",
      "plotter": {
        "enable": true,
        "datasource": {
          "platform": {
            "type": "AUTOSENSE_CHEST"
          },
          "type": "RESPIRATION"
        }
      },
      "video": {
        "enable": true,
        "link": "2bxc8kONPSs"
      },
      "message": {
        "enable": true,
        "text": "1) Tighten the chest band so it fits snugly under the armpits.\n\n2) Make sure all cable connections are secure.\n\n3) Reset the application, wait 15 seconds and check again.\n\n4) Restart the phone, wait one minute and check again.\n\n5) Make sure the chest sensor is charged and powered ON."
      }
    },
    {
      "name": "Heart Rate",
      "plotter": {
        "enable": true,
        "datasource": {
          "platform": {
            "type": "AUTOSENSE_CHEST"
          },
          "type": "ECG"
        }
      },
      "video": {
        "enable": true,
        "link": "toiopB7ltc8"
      },
      "message": {
        "enable": true,
        "text": "1) Adjust the position of the electrodes on the body.\n\n2) Make sure all cable connections are secure.\n\n3) Reset the application, wait 15 seconds and check again.\n\n4) Restart the phone, wait one minute and check again.\n\n5) Make sure the chest sensor is charged and powered ON."
      }
    },
    {
      "name": "Left Wrist(A)",
      "plotter": {
        "enable": true,
        "datasource": {
          "platform": {
            "type": "AUTOSENSE_WRIST",
            "id": "LEFT_WRIST"
          },
          "type": "ACCELEROMETER_X"
        }
      },
      "video": {
        "enable": true,
        "link": "MbHUvM6C1GE"
      },
      "message": {
        "enable": true,
        "text": "1) Reset the application, wait 15 seconds and check again.\n\n2) Restart the phone, wait one minute and check again.\n\n3) Make sure the wrist sensor power switch is ON.\n\n4) Make sure the wrist sensor is charged."
      }
    },
    {
      "name": "Right Wrist(A)",
      "plotter": {
        "enable": true,
        "datasource": {
          "platform": {
            "type": "AUTOSENSE_WRIST",
            "id": "RIGHT_WRIST"
          },
          "type": "ACCELEROMETER_X"
        }
      },
      "video": {
        "enable": true,
        "link": "MbHUvM6C1GE"
      },
      "message": {
        "enable": true,
        "text": "1) Reset the application, wait 15 seconds and check again.\n\n2) Restart the phone, wait one minute and check again.\n\n3) Make sure the wrist sensor power switch is ON.\n\n4) Make sure the wrist sensor is charged."
      }
    },
    {
      "name": "Left Wrist(M)",
      "plotter": {
        "enable": true,
        "datasource": {
          "platform": {
            "type": "MICROSOFT_BAND",
            "id": "LEFT_WRIST"
          },
          "type": "ACCELEROMETER"
        }
      },
      "video": {
        "enable": true,
        "link": "QYQJISCLCdg"
      },
      "message": {
        "enable": true,
        "text": "1) Make sure the clasp on the Band is securely locked around the wrist.\n\n2) Reset the application, wait 15 seconds and check again.\n\n3) Restart the phone, wait one minute and check again.\n\n4) Make sure the Band is charged and powered ON."
      }
    },
    {
      "name": "Right Wrist(M)",
      "plotter": {
        "enable": true,
        "datasource": {
          "platform": {
            "type": "MICROSOFT_BAND",
            "id": "RIGHT_WRIST"
          },
          "type": "ACCELEROMETER"
        }
      },
      "video": {
        "enable": true,
        "link": "QYQJISCLCdg"
      },
      "message": {
        "enable": true,
        "text": "1) Make sure the clasp on the Band is securely locked around the wrist.\n\n2) Reset the application, wait 15 seconds and check again.\n\n3) Restart the phone, wait one minute and check again.\n\n4) Make sure the Band is charged and powered ON."
      }
    }
  ],
  "day_start": {
    "by": "user",
    "base": "wakeup",
    "notify": [
      {
        "type": "button",
        "offset": -30000
      },
      {
        "type": "prompt",
        "offset": 0,
        "parameters": [
          "PHONE_SCREEN",
          "PHONE_MESSAGE_START_DAY"
        ]
      },
      {
        "type": "notification",
        "offset": 30000,
        "parameters": [
          "PHONE_VIBRATE",
          "PHONE_TONE",
          "PHONE_SCREEN",
          "PHONE_MESSAGE_START_DAY"
        ]
      }
    ]
  },
  "day_end": {
    "by": "user",
    "base": "day_start",
    "notify": [
      {
        "type": "button",
        "offset": 30000
      }
    ]
  }
}
```
