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
