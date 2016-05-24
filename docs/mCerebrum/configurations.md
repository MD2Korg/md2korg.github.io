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
- `id`: ...

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


# EMA
Config file name and location: `mCerebrum/org.md2k.ema/config_ema.json`

This JSON array contains a listing of all defined EMA configurations in the system.
Each structure contains:

- `id`: unique EMA identifier
- `name`: string that is displayed to the user describing an EMA
- `file_name`: file name of a json document located in this folder for a specific EMA
- `package_name`: Application reference which handles the specified `file_name`
- `timeout`: Time in milliseconds after which an EMA is considered abandoned

```JSON
[
  {
    "id": "random_experience_sampling",
    "name": "Random Experience Sampling",
    "file_name": "random_experience_sampling.json",
    "package_name": "org.md2k.ema",
    "timeout": 300000
  },
  {
    "id": "event_contingent_recording",
    "name": "Event Contingent Recording",
    "package_name": "org.md2k.ema",
    "file_name": "event_contingent_recording.json",
    "timeout": 300000
  },
  {
    "id": "end_of_day_recording",
    "name": "End of Day Recording",
    "package_name": "org.md2k.ema",
    "file_name": "end_of_day_recording.json",
    "timeout": 300000
  }
]
```

# EMA Scheduler
Config file name and location: `mCerebrum/org.md2k.ema_scheduler/config.json`

Contains a list of ema/emi objects each which contain the following:

- `id`: unique object identifier string
- `type`: can be one of the following
    - `EMA` for ecological momentary assessment
    - `EMI` for ecological momentary intervention
- `trigger_type`:
    - `RANDOM`: A randomly generated assessment time subject to the criteria of the `blocks` definition
    - `SELF_REPORT`: Participant has generated a self-reported response
    - `EVENT`: Generated by a processing sensor data and computing specific events such as high stress or a smoking puff
- `name`: Description that is provided to a participant through mCerebrum's interface
- `enabled`: `true` or `false` to enable or disable this object
- `application`: Defines where the EMA/EMI is located and which application utilized to execute it
    - `id`: unique EMA identifier
    - `name`: string that is displayed to the user describing an EMA
    - `file_name`: file name of a json document located in this folder for a specific EMA
    - `package_name`: Application reference which handles the specified `file_name`
    - `timeout`: Time in milliseconds after which an EMA is considered abandoned
- `blocks`: A list of `block` object each designating:
    - `total`: Total number of times this object should be shown to a participant
    - `base`: A reference from which to start the offsets: [base](#base)
    - `start_offset`: Offset time in milliseconds from the value defined in `base`
    - `end_offset`: Offset time in milliseconds from the value defined in `base`
- `scheduler_rules`: List of schedule objects each designating:
    - `type`:
        - `RANDOM`
        - `IMMEDIATE`
    - `start_time`:
    - `end_time`:
    - `divide`: TODO: What does this mean?
    - `conditions`: A list from a a set of [conditions](#conditions), all which are required to be met for a notification to be delivered
- `notifications`: A list of notification objects, each of which include:
    - `time`: Milliseconds after the object generation time when to deliver the specified notification(s)
    - `types`: A list of [notificaiton types](#notification-types)
- `incentive_rules`: A list of [incentive](#incentive) objects to apply
    - `intentive`: Payment in dollars
    - `messages`: List of strings to be shown to the participant
    - `conditions`: A set of [conditions](#conditions) that must be met to receive this incentive.

```JSON
[
  {
    "id": "RANDOM_EMA",
    "type": "EMA",
    "trigger_type": "RANDOM",
    "name": "Random Experience Sampling",
    "enable": true,
    "application": {
      "id": "random_experience_sampling",
      "name": "Random Experience Sampling",
      "file_name": "random_experience_sampling.json",
      "package_name": "org.md2k.ema",
      "timeout": 600000
    },
    "blocks": [
      {
        "total": 1,
        "base": "DAY_START",
        "start_offset": 0,
        "end_offset": 14400000
      },
      {
        "total": 1,
        "base": "DAY_START",
        "start_offset": 14400000,
        "end_offset": 28800000
      },
      {
        "total": 1,
        "base": "DAY_START",
        "start_offset": 28800000,
        "end_offset": 43200000
      }
    ],
    "scheduler_rules": [
      {
        "type": "RANDOM",
        "start_time": "BLOCK_START",
        "end_time": "BLOCK_END",
        "divide": 2,
        "conditions": [
          "PRIVACY",
          "VALID_BLOCK_RANDOM_EMA",
          "RANDOM_EMA_60",
          "SMOKING_EMA_10",
          "EMI_10",
          "DATA_QUALITY_5",
          "NOT_DRIVING_5",
          "PHONE_BATTERY_10"
        ]
      },
      {
        "type": "RANDOM",
        "start_time": "LAST_SCHEDULE",
        "end_time": "BLOCK_END",
        "divide": 2,
        "conditions": [
          "PRIVACY",
          "VALID_BLOCK_RANDOM_EMA",
          "RANDOM_EMA_60",
          "SMOKING_EMA_10",
          "EMI_10",
          "DATA_QUALITY_5",
          "NOT_DRIVING_5",
          "PHONE_BATTERY_10"
        ]
      },
      {
        "type": "IMMEDIATE",
        "conditions": [
          "PRIVACY",
          "VALID_BLOCK_RANDOM_EMA",
          "RANDOM_EMA_60",
          "SMOKING_EMA_10",
          "EMI_10"
        ]
      }
    ],
    "notifications": [
      {
        "time": 0,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "MICROSOFT_BAND_MESSAGE_EMA",
          "PHONE_VIBRATE_3",
          "PHONE_MESSAGE_DELAY_EMA",
          "PHONE_SCREEN"
        ]
      },
      {
        "time": 120000,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "PHONE_VIBRATE_3"
        ]
      },
      {
        "time": 240000,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "PHONE_VIBRATE_3"
        ]
      }
    ],
    "incentive_rules": [
      {
        "incentive": 0.75,
        "messages": [
          "Thank you. You will be paid $0.75 for taking the survey within 5 minutes and wearing the sensors for more than 60% of the time since day started.",
          "You will be paid $0.75",
          "Total Earning: $"
        ],
        "conditions": [
          "DATA_QUALITY_DAY_START",
          "EMA_ANSWER_5"
        ]
      },
      {
        "incentive": 0.5,
        "messages": [
          "Thank you. You will be paid $0.50 for taking the survey and wearing the sensors for more than 60% of the time since day started. But you missed $0.25 bonus for not answering the survey within 5 minutes.",
          "You will be paid $0.50",
          "Total Earning: $"
        ],
        "conditions": [
          "DATA_QUALITY_DAY_START"
        ]
      },
      {
        "incentive": 0,
        "messages": [
          "Thank you. Unfortunately, you will be paid $0.00 because you have not worn sensors for at least 60% of the time since day started.",
          "You will be paid $0.50",
          "Total Earning: $"
        ],
        "conditions": []
      }
    ]
  },
  {
    "id": "SMOKING_EMA",
    "type": "EMA",
    "trigger_type": "SELF_REPORT",
    "name": "Event Contingent EMA",
    "enable": true,
    "application": {
      "id": "event_contingent_recording",
      "name": "Event Contingent Recording",
      "package_name": "org.md2k.ema",
      "file_name": "event_contingent_recording.json",
      "timeout": 600000
    },
    "blocks": [
      {
        "total": 1,
        "base": "DAY_START",
        "start_offset": 0,
        "end_offset": 14400000
      },
      {
        "total": 1,
        "base": "DAY_START",
        "start_offset": 14400000,
        "end_offset": 28800000
      },
      {
        "total": 1,
        "base": "DAY_START",
        "start_offset": 28800000,
        "end_offset": 43200000
      }
    ],
    "scheduler_rules": [
      {
        "type": "IMMEDIATE",
        "data_source": {
          "type": "EVENT"
        },
        "parameters": [
          "SMOKING"
        ],
        "conditions": [
          "PRIVACY",
          "VALID_BLOCK_SMOKING_EMA",
          "RANDOM_EMA_10",
          "SMOKING_EMA_30",
          "EMI_10",
          "DATA_QUALITY_5",
          "NOT_DRIVING_5",
          "PHONE_BATTERY_10"
        ]
      }
    ],
    "notifications": [
      {
        "time": 0,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "MICROSOFT_BAND_MESSAGE_EMA",
          "PHONE_VIBRATE_3",
          "PHONE_MESSAGE_DELAY_EMA",
          "PHONE_SCREEN"
        ]
      },
      {
        "time": 120000,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "PHONE_VIBRATE_3"
        ]
      },
      {
        "time": 240000,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "PHONE_VIBRATE_3"
        ]
      }
    ],
    "incentive_rules": [
      {
        "incentive": 0.75,
        "messages": [
          "Thank you. You will be paid $0.75 for taking the survey within 5 minutes and wearing the sensors for more than 60% of the time since day started.",
          "You will be paid $0.75",
          "Total Earning: $"
        ],
        "conditions": [
          "DATA_QUALITY_DAY_START",
          "EMA_ANSWER_5"
        ]
      },
      {
        "incentive": 0.5,
        "messages": [
          "Thank you. You will be paid $0.50 for taking the survey and wearing the sensors for more than 60% of the time since day started. But you missed $0.25 bonus for not answering the survey within 5 minutes.",
          "You will be paid $0.50",
          "Total Earning: $"
        ],
        "conditions": [
          "DATA_QUALITY_DAY_START"
        ]
      },
      {
        "incentive": 0,
        "messages": [
          "Thank you. Unfortunately, you will be paid $0.00 because you have not worn sensors for at least 60% of the time since day started.",
          "You will be paid $0.50",
          "Total Earning: $"
        ],
        "conditions": []
      }
    ]
  },
  {
    "id": "END_OF_DAY_EMA",
    "type": "EMA",
    "trigger_type": "SELF_REPORT",
    "name": "End of day EMA",
    "enable": true,
    "application": {
      "id": "end_of_day_recording",
      "name": "End of Day Recording",
      "package_name": "org.md2k.ema",
      "file_name": "end_of_day_recording.json",
      "timeout": 600000
    },
    "scheduler_rules": [
      {
        "type": "IMMEDIATE",
        "data_source": {
          "type": "DAY_END"
        }
      }
    ],
    "notifications": [
      {
        "time": 0,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "MICROSOFT_BAND_MESSAGE_EMA",
          "PHONE_VIBRATE_3",
          "PHONE_MESSAGE_DELAY_EMA_15_30_60_120",
          "PHONE_SCREEN"
        ]
      },
      {
        "time": 120000,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "PHONE_VIBRATE_3"
        ]
      },
      {
        "time": 240000,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "PHONE_VIBRATE_3"
        ]
      }
    ],
    "incentive_rules": [
      {
        "incentive": 1,
        "messages": [
          "Thank you. You will be paid $1.00 for taking the End of Day survey.",
          "You will be paid $1.00",
          "Total Earning: $"
        ],
        "conditions": []
      }
    ]
  },
  {
    "id": "EMI",
    "type": "EMI",
    "trigger_type": "EVENT",
    "name": "Intervention",
    "enable": true,
    "scheduler_rules": [
      {
        "type": "IMMEDIATE",
        "data_source": {
          "type": "ORG_MD2K_CSTRESS_STRESS_EPISODE_CLASSIFICATION"
        },
        "parameters": [
          "0",
          "2"
        ],
        "conditions": [
          "PRIVACY",
          "RANDOM_EMA_10",
          "SMOKING_EMA_10",
          "EMI_60",
          "DATA_QUALITY_5",
          "NOT_DRIVING_5",
          "PHONE_BATTERY_10"
        ]
      }
    ],
    "incentive_rules": [
      {
        "incentive": 1,
        "conditions": []
      }
    ]
  },
  {
    "id": "MOODSURFING",
    "type": "EMI",
    "name": "MoodSurfing",
    "trigger_type": "EVENT",
    "enable": false,
    "application": {
      "id": "moodsurfing",
      "name": "MoodSurfing",
      "package_name": "org.md2k.moodsurfing",
      "timeout": 600000
    },
    "notifications": [
      {
        "time": 0,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "MICROSOFT_BAND_MESSAGE_MOODSURFING",
          "PHONE_VIBRATE_3",
          "PHONE_MESSAGE_MOODSURFING"
        ]
      }
    ]
  },
  {
    "id": "THOUGHT_SHAKEUP",
    "type": "EMI",
    "name": "Thought Shakeup",
    "trigger_type": "EVENT",
    "enable": false,
    "application": {
      "id": "thought_shakeup",
      "name": "Thought Shakeup",
      "package_name": "org.md2k.thoughtshakeup",
      "timeout": 600000
    },
    "notifications": [
      {
        "time": 0,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "MICROSOFT_BAND_MESSAGE_THOUGHTSHAKEUP",
          "PHONE_VIBRATE_3",
          "PHONE_MESSAGE_THOUGHTSHAKEUP"
        ]
      }
    ]
  },
  {
    "id": "HEADSPACE",
    "type": "EMI",
    "name": "HeadSpace",
    "trigger_type": "EVENT",
    "enable": false,
    "application": {
      "id": "head_space",
      "name": "HeadSpace",
      "package_name": "com.getsomeheadspace.android",
      "timeout": 1000
    },
    "notifications": [
      {
        "time": 0,
        "types": [
          "MICROSOFT_BAND_VIBRATE_3",
          "MICROSOFT_BAND_MESSAGE_HEADSPACE",
          "PHONE_VIBRATE_3",
          "PHONE_MESSAGE_HEADSPACE"
        ]
      }
    ]
  }
]
```

# Microsoft Band
Config file name and location: `mCerebrum/org.md2k.microsoftband/default_config.json`

TODO: Need complete listing of all MS Band sensors

```JSON
[
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "metadata": {
      "FREQUENCY": "31 Hz"
    },
    "type": "ACCELEROMETER"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "metadata": {
      "FREQUENCY": "31 Hz"
    },
    "type": "GYROSCOPE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "BAND_CONTACT"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "DATA_QUALITY"
  }
]
```

# Notification Manager
Config file name and location: `mCerebrum/org.md2k.notificationmanager/`

Notification manager requires `tone.mp3` to be present in this folder and utilizes this file for audible alerts for participants.

# Phone Sensor
Config file name and location: `mCerebrum/org.md2k.phonesensor/default_config.json`

TODO: Need complete listing of all MS Band sensors

```JSON
[
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "1.0 Hz"
    },
    "type": "BATTERY"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "SENSOR_DELAY_UI"
    },
    "type": "LOCATION"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "SENSOR_DELAY_UI"
    },
    "type": "ACCELEROMETER"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "SENSOR_DELAY_UI"
    },
    "type": "GYROSCOPE"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "1.0 Hz"
    },
    "type": "CPU"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "1.0 Hz"
    },
    "type": "MEMORY"
  }
]
```

# Plotter
Config file name and location: `mCerebrum/org.md2k.plotter/default_config.json`

This JSON array should contain the data sources that should be made available to the plotting tool.  The absence of this
configuration file will show all datastream in the user interface


Example:
```JSON
[
  {
    "platform": {
      "type": "PHONE"
    },
    "type": "ACCELEROMETER"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "type": "GYROSCOPE"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "RESPIRATION"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "ECG"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "ACCELEROMETER_X"
  },
  {
    "platform": {
      "type": "AUTOSENSE_WRIST"
    },
    "type": "ACCELEROMETER_X"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "ACCELEROMETER"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "GYROSCOPE"
  }
]
```

# Stream Processor
Config file name and location: `mCerebrum/org.md2k.streamprocessor`

Stream processor requires that SVM model files be present in this directory.

# Autosense
Config file name and location: `mCerebrum/org.md2k.autosense/default_config.json`

AutoSense [data sources](#data-source) are associated with hardware sensors and are expected to be explicitly listed to enable.  The following example illustrates all possible sensors and data streams.  Remove entries to disable the UI for specific sensors.

```JSON
[
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "RESPIRATION"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "ECG"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "ACCELEROMETER_X"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "ACCELEROMETER_Y"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "ACCELEROMETER_Z"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "GALVANIC_SKIN_RESPONSE"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "BATTERY"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "SKIN_TEMPERATURE"
  },
  {
    "platform": {
      "type": "AUTOSENSE_CHEST",
      "id": "CHEST"
    },
    "type": "AMBIENT_TEMPERATURE"
  },
  {
    "platform": {
      "type": "AUTOSENSE_WRIST"
    },
    "type": "ACCELEROMETER_X"
  },
  {
    "platform": {
      "type": "AUTOSENSE_WRIST"
    },
    "type": "ACCELEROMETER_Y"
  },
  {
    "platform": {
      "type": "AUTOSENSE_WRIST"
    },
    "type": "ACCELEROMETER_Z"
  },
  {
    "platform": {
      "type": "AUTOSENSE_WRIST"
    },
    "type": "GYROSCOPE_X"
  },
  {
    "platform": {
      "type": "AUTOSENSE_WRIST"
    },
    "type": "GYROSCOPE_Y"
  },
  {
    "platform": {
      "type": "AUTOSENSE_WRIST"
    },
    "type": "GYROSCOPE_Z"
  }
]
```

# DataKit
Config file name and location: `mCerebrum/org.md2k.datakit/default_config.json`

## Database
The database section designates:

- `enabled`: true or false to designate whether to store data to memory
- `location`: Store the sqlite database on the phone's
    - _INTERNAL_SDCARD_: internal memory, no exceptions
    - _EXTERNAL_SDCARD_: external memory, no exceptions
    - _EXTERNAL_SDCARD_PREFERRED_: external memory is preferred if available, but internal memory will be utilized as a fallback option

```JSON
"database": {
  "enabled": true,
  "location": "INTERNAL_SDCARD"
}
```

## Archive
This section configures the archive options for DataKit:

- `enabled`: true or false to designate whether to archive records to flash storage
- `location`: Store the archive files on:
    - _INTERNAL_SDCARD_: internal memory, no exceptions
    - _EXTERNAL_SDCARD_: external memory, no exceptions
    - _EXTERNAL_SDCARD_PREFERRED_: external memory is preferred if available, but internal memory will be utilized as a fallback option
- `interval`: Delay in milliseconds from when a datapoint is logged in the system and when it is eligible for archiving

```JSON
"archive": {
  "enabled": true,
  "location": "EXTERNAL_SDCARD_PREFERRED",
  "interval": 86400000
}
```

## Upload
This section configures the upload to Cerebral Cortex options for DataKit:

- `enabled`: true or false to designate whether to upload data to mCerebrum's cloud component, Cerebral Cortex
- `interval`: Delay in milliseconds between upload iterations
- `url`: Cerebral Cortex API URL: e.g. https://cerebralcortex.SITE.ORG/
- `restricted_datasource`: List of [datastreams](#data-streams) eligible for upload restrictions

```JSON
"upload": {
  "enabled": true,
  "interval": 900000,
  "url": "https://cerebralcortex.SITE.ORG/",
  "restricted_datasource": [
    {
      "platform": {
        "type": "PHONE"
      },
      "type": "LOCATION"
    }
  ]
}
```

## Privacy
This section configures the privacy controller for DataKit:

- `duration_options`: a list of options where each contains the following:
    - `id`: TODO: What does this mean?
    - `title`: Text to be shown in the user interface
    - `value`: Time in milliseconds
- `privacy_type_options`: A list of [privacy types](#privacy-type-options)


```JSON
"privacy": {
  "duration_options": [
    {
      "id": "300000",
      "title": "5 Minutes",
      "value": 300000
    },
    {
      "id": "600000",
      "title": "10 Minutes",
      "value": 600000
    },
    {
      "id": "900000",
      "title": "15 Minutes",
      "value": 900000
    },
    {
      "id": "1800000",
      "title": "30 Minutes",
      "value": 1800000
    }
  ],
  "privacy_type_options": [
    {
      "id": "location",
      "title": "Location",
      "summary": "",
      "source": [
        {
          "datasource_type": "LOCATION"
        }
      ]
    },
    {
      "id": "activity",
      "title": "Activity",
      "summary": "",
      "source": [
        {
          "datasource_type": "LOCATION"
        },
        {
          "datasource_type": "ACCELEROMETER"
        },
        {
          "datasource_type": "GYROSCOPE"
        },
        {
          "datasource_type": "ACCELEROMETER_X"
        },
        {
          "datasource_type": "ACCELEROMETER_Y"
        },
        {
          "datasource_type": "ACCELEROMETER_Z"
        },
        {
          "datasource_type": "GYROSCOPE_X"
        },
        {
          "datasource_type": "GYROSCOPE_Y"
        },
        {
          "datasource_type": "GYROSCOPE_Z"
        }
      ]
    },
    {
      "id": "chest_sensor",
      "title": "Chest Sensor",
      "summary": "",
      "source": [
        {
          "platform_type": "AUTOSENSE_CHEST"
        }
      ]
    },
    {
      "id": "wrist_sensor",
      "title": "Wrist Sensors",
      "summary": "",
      "source": [
        {
          "platform_type": "AUTOSENSE_WRIST"
        }
      ]
    },
    {
      "id": "ema_intervention",
      "title": "Surveys",
      "summary": "",
      "source": [
        {
          "datasource_type": "SURVEY"
        }
      ]
    }
  ]
}
```


## Example
```JSON
{
  "database": {
    "enabled": true,
    "location": "INTERNAL_SDCARD"
  },
  "archive": {
    "enabled": true,
    "location": "EXTERNAL_SDCARD_PREFERRED",
    "interval": 86400000
  },
  "upload": {
    "enabled": true,
    "interval": 900000,
    "url": "https://northwestern-cerebralcortex.md2k.org/",
    "restricted_datasource": [
      {
        "platform": {
          "type": "PHONE"
        },
        "type": "LOCATION"
      }
    ]
  },
  "privacy": {
    "duration_options": [
      {
        "id": "300000",
        "title": "5 Minutes",
        "value": 300000
      },
      {
        "id": "600000",
        "title": "10 Minutes",
        "value": 600000
      },
      {
        "id": "900000",
        "title": "15 Minutes",
        "value": 900000
      },
      {
        "id": "1800000",
        "title": "30 Minutes",
        "value": 1800000
      }
    ],
    "privacy_type_options": [
      {
        "id": "location",
        "title": "Location",
        "summary": "",
        "source": [
          {
            "datasource_type": "LOCATION"
          }
        ]
      },
      {
        "id": "activity",
        "title": "Activity",
        "summary": "",
        "source": [
          {
            "datasource_type": "LOCATION"
          },
          {
            "datasource_type": "ACCELEROMETER"
          },
          {
            "datasource_type": "GYROSCOPE"
          },
          {
            "datasource_type": "ACCELEROMETER_X"
          },
          {
            "datasource_type": "ACCELEROMETER_Y"
          },
          {
            "datasource_type": "ACCELEROMETER_Z"
          },
          {
            "datasource_type": "GYROSCOPE_X"
          },
          {
            "datasource_type": "GYROSCOPE_Y"
          },
          {
            "datasource_type": "GYROSCOPE_Z"
          }
        ]
      },
      {
        "id": "chest_sensor",
        "title": "Chest Sensor",
        "summary": "",
        "source": [
          {
            "platform_type": "AUTOSENSE_CHEST"
          }
        ]
      },
      {
        "id": "wrist_sensor",
        "title": "Wrist Sensors",
        "summary": "",
        "source": [
          {
            "platform_type": "AUTOSENSE_WRIST"
          }
        ]
      },
      {
        "id": "ema_intervention",
        "title": "Surveys",
        "summary": "",
        "source": [
          {
            "datasource_type": "SURVEY"
          }
        ]
      }
    ]
  }
}
```

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
