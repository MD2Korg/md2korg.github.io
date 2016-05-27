# Sensor Interface configurations

## Phone Sensor
Config file name and location: `mCerebrum/org.md2k.phonesensor/default_config.json`

The phone sensor configuration is a list of [data sources](configurations/#data-source) with a `FREQUENCY` specific to the sensor specified. The absence of a configuration file will allow the system to allow the configuration of all possible data sources.

Frequency can be one of the following:

- Sample rate in hertz: e.g. "1.0 Hz"
- SENSOR_DELAY_NORMAL
- SENSOR_DELAY_UI
- SENSOR_DELAY_GAME
- SENSOR_DELAY_FASTEST
- ON_CHANGE for `PROXIMITY` only


### Complete Example
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
      "FREQUENCY": "SENSOR_DELAY_UI"
    },
    "type": "COMPASS"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "SENSOR_DELAY_UI"
    },
    "type": "AMBIENT_LIGHT"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "6.0 Hz"
    },
    "type": "PRESSURE"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "1.0 Hz"
    },
    "type": "AMBIENT_TEMPERATURE"
  },
  {
    "platform": {
      "type": "PHONE"
    },
    "metadata": {
      "FREQUENCY": "ON_CHANGE"
    },
    "type": "PROXIMITY"
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


## Autosense
Config file name and location: `mCerebrum/org.md2k.autosense/default_config.json`

AutoSense [data sources](configurations/#data-source) are associated with hardware sensors and are expected to be explicitly listed to enable.  The following example illustrates all possible sensors and data streams.  Remove entries to disable the UI for specific sensors. The absence of a configuration file will allow the system to allow the configuration of all possible data sources.

### Complete Example
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


## Microsoft Band
Config file name and location: `mCerebrum/org.md2k.microsoftband/default_config.json`

Microsoft Band [data sources](configurations/#data-source) are associated with hardware and software sensors and are expected to be explicitly listed to enable.  The following example illustrates all possible sensors and data streams.  Remove entries to disable the UI for specific sensors.  The absence of a configuration file will allow the system to allow the configuration of all possible data sources.


`ACCELEROMETER` and `GYROSCOPE` sensors must have their frequency configured to one of the following:

- 8Hz
- 31Hz
- 62Hz

### Complete Example
```JSON
[
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "DATA_QUALITY"
  },
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
    "metadata": {
      "FREQUENCY": "???"
    },
    "type": "AIR_PRESSSURE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "AMBIENT_LIGHT"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "AMBIENT_TEMPERATURE"
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
    "type": "CALORY_BURN"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "DISTANCE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "GALVANIC_SKIN_RESPONSE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "HEART_RATE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "MOTION_TYPE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "PACE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "RR_INTERVAL"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "SKIN_TEMPERATURE"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "SPEED"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "STEP_COUNT"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "ULTRA_VIOLET_RADIATION"
  },
  {
    "platform": {
      "type": "MICROSOFT_BAND"
    },
    "type": "ALTIMETER"
  }
]
```
