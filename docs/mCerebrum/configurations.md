# Configuration
**mCerebrum** is primarily configured and controlled by a set of JSON configuration files.  This document describes how to utilize and adapt these configurations to your own requirements.

## Data source
A data source uniquely represents a single data stream within mCerebrum.  Subsets of a data source definition can be utilized to query for multiple streams. This example contains all possible fields.  `dataDescriptors` and `metadata` are always optional.

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
Notifications are handled by mCerebrum by sending a notification object to the notification manager application.  This is the definition of the object and certain fields are require depending on the targeted notification device.  Please refer to the device specific documentation.

- `id`: Unique identifier that is utilized by other configuration file to reference this object instance.
- `name`: Short string description of the notification that can be utilized by application user interfaces
- `type`: Must be one of the following:
    - `VIBRATION`: Causes the notification device to vibrate if possible
    - `MESSAGE`: Causes the notification device to display a message if possible
    - `TONE`: Causes the notification device to sound a tone if possible
    - `SCREEN`: Causes the notification device to turn on a screen if possible
- `priority`: Integer priority level, lower is higher priority
- `datasource`: A [data source](#data-source) object
- `format`: Specific format option depending on the notification device
- `repeat`: How many time to repeat this notification
- `duration`: How long in milliseconds to alert for each notification iteration

### Example
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
TODO:

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


### Example
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

## Base
Defined in main application JSON file

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

## Notification Manager
Config file name and location: `mCerebrum/org.md2k.notificationmanager/`

Notification manager requires `tone.mp3` to be present in this folder and utilizes this file for audible alerts for participants.

## Stream Processor
Config file name and location: `mCerebrum/org.md2k.streamprocessor`

Stream processor requires that SVM model files be present in this directory.
