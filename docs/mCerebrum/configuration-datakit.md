# DataKit
Config file name and location: `mCerebrum/org.md2k.datakit/default_config.json`

## Database
The database section designates:

- `enabled`: true or false to designate whether to store data to memory
- `location`: Store the sqlite database on the phone's
    - _INTERNAL_SDCARD_: internal memory, no exceptions
    - _EXTERNAL_SDCARD_: external memory, no exceptions
    - _EXTERNAL_SDCARD_PREFERRED_: external memory is preferred if available, but internal memory will be utilized as a fallback option

### Example
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

### Example
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

### Example
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
- `privacy_type_options`: A list of [privacy types](configurations/#privacy-type-options)

### Example
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


## Complete Example
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
    "url": "https://site-cerebralcortex.site.org/",
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
