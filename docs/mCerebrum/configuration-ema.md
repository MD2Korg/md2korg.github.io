# EMA
Config file name and location: `mCerebrum/org.md2k.ema/config_ema.json`

This JSON array contains a listing of all defined EMA configurations in the system.
Each structure contains:

- `id`: unique EMA identifier
- `name`: string that is displayed to the user describing an EMA
- `file_name`: file name of a json document located in this folder for a specific EMA
- `package_name`: Application reference which handles the specified `file_name`
- `timeout`: Time in milliseconds after which an EMA is considered abandoned

### Example
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
