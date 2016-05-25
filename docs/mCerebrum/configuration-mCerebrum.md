# mCerebrum
Config file name and location: `mCerebrum/org.md2k.study/config.json`


### Structure Overview
This is the general structure of the mCerebrum configuration file.  Please see additional details in the following subsections.
```JSON
{
  "config_info": {
    CONFIG_INFO
  },
  "study_info": {
    STUDY_INFO
  },
  "apps": [
    APP_LIST1,
    APP_LIST2,
    ...
  ],
  "actions": [
    ACTION_1,
    ACTION_2,
    ...
  ],
  "admin_view": {
    ADMININISTRATION_VIEW
  },
  "user_view": {
    USER_VIEW
  },
  "data_quality": [
    DATA_QUALITY_1,
    DATA_QUALITY_2,
    ...
  ],
  "data_quality_view": [
    DATA_QUALITY_VIEW_1,
    DATA_QUALITY_VIEW_2,
    ...
  ],
  "day_start": {
    DAY_START
  },
  "day_end": {
    DAY_END
  }
}
```


## Config Info
The config info key specifies several required pieces of information and defines which resources are required.

- `id`: Unique study identifier.  E.g. ProtocolNumber TODO: Why is this here?
- `name`: Human readable study description.  This identifies a specific study. TODO: Why is this here?
- `version_code`: The version of this file that is utilized by mCerebrum to determine if it can utilize this configuration
- `required_files`: List of files required to be present in the configuration folder before allowing the system to be configured.

### Example
```JSON
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
}
```

## Study Info
This object defines the specific study for the the configuration.

- `id`: Unique study identifier.  E.g. ProtocolNumber
- `name`: Human readable study description.  This identifies a specific study.

### Example
```JSON
{
  "id": "STU00201566-Test",
  "name": "MD2K Smoking Study (at NW)-Test"
}
```

## Application List


### Application object
```JSON
{
  "id": "datakit",
  "name": "DataKit",
  "enable": true,
  "package_name": "org.md2k.datakit",
  "config": "config.json",
  "default_config": "default_config.json",
  "service": "org.md2k.datakit.cerebralcortex.ServiceCerebralCortex",
  "download_link": "https://github.com/MD2Korg/mCerebrum-DataKit/releases"
}
```

### Application List Example
```JSON
[
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
]
```

## Action List
```JSON
[
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
]
```

## Administration View
```JSON
{
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
}
```

## User View
```JSON
{
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
}
```

## Data Quality List
```JSON
[
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
]
```
## Data Quality View List
```JSON
[
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
]
```

## Day Start
```JSON
{
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
```

## Day End
```JSON
{
  "by": "user",
  "base": "day_start",
  "notify": [
    {
      "type": "button",
      "offset": 30000
    }
  ]
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
