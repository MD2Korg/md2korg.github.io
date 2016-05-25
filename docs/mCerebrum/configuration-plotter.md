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
