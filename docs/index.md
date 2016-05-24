# Introduction
The MD2K software platform includes mobile phone software platform called mCerebrum and a cloud counterpart called Cerebral Cortex. mCerebrum is a configurable software platform for mobile and wearable sensors. It provides support for reliable data collection from mobile and wearable sensors, and real-time processing of these data for sensor triggered just-in-time adaptive interventions.

Cerebral Cortex is the big data companion of mCerebrum designed to support population-scale data analysis, visualization, model development, and intervention design for mobile sensor data. It provides the ability to do machine learning model development on population scale data sets and provides interoperable interfaces for aggregation of diverse data sources.

## Limitations of Existing mHealth Platforms
Several software platforms have recently emerged for collecting mobile health data. For example, Apple and Google each provide a set of APIs and tools for mobile mHeath data collection. But, Apple Healthkit and Google Fit APIs are primarily designed for low frequency data collection of digital biomarkers including: blood pressure, weight, or physical activity. Both of these platforms have limited expressiveness for time series data streams.

## Uniqueness of MD2K
The MD2K platform (https://www.github.com/MD2Korg/), on the other hand, is designed from the ground up as a high-frequency data stream processing toolchain that provides flexible data types and custom object storage. It can collect and analyze data from tens of wearable sensors via a wide array of wireless radios (ANT, Bluetooth, Bluetooth LE, etc.). It also provides native support for triggering notifications, self-report prompts, and interventions based on real-time values of digital biomarkers derived from sensor data.

## Background
mCerebrum is backed by 9 years of software development on the Fieldstream (http://www.fieldstream.org/) and AutoSense (https://sites.google.com/site/autosenseproject/) projects which yielded in excess of 20,000 hours of wearable sensor data from a variety of lab and field studies with hundreds of participants. Over 27 research articles (with over 400 citations) have been published using analysis of these data (see list of articles below; go here for citations). mCerebrum is based on these extensive experiences with real-life high-frequency sensor data and its analysis for both technology and health research.

The signal processing for Fieldstream and AutoSense were on a Matlab batch-processing codebase that operates on data after a participant has returned the data collection device to the lab. Therefore, no real-time sensor-triggered notifications or interventions were possible with the existing framework and furthermore, the codebase does not lend itself well to distributed processing for scalable application performance.

## Novelty of MD2K
mCerebrum, on the other hand, is designed to be compatible with mobile platforms so as to support real-time signal processing of high-frequency data streams in excess of 800 hertz, while meeting quality of service requirements for the mobile platform. In addition, mCerebrum is designed as an open-source project so that it can be easily used by the community and modified to suit specific research needs.

Cerebral Cortex is the big data companion to mCerebrum designed to support population-scale analytics, model development, and data visualizations. One of the primary capabilities of Cerebral Cortex is its ability to support scalable big data machine learning model development and iterative data analysis and model generation across population-scale data sets. Models learned on population-scale data can be sent back to a smartphone in the field to improve detection and classification accuracy.


# Software Release Information

## Schedule
MD2K software is released based on a monthly development and testing cycle.  Typically, we allocate **3 1-week sprints** for development activities followed by a **single 1-week sprint** dedicated towards testing.  

- Major `X.0.0` software updates will occur approximately every year
- Minor/Feature `1.X.0` updates will occur each month on the 3rd Wednesday
- Critical bug fixes `1.2.X` will be released immediately

| Year |    Month   | Release Day       |
|------|------------|-------------------|
| 2016 | June       | 2016/06/15  (Wed) |
| 2016 | July       | 2016/07/13  (Wed) |
| 2016 | August     | 2016/08/17  (Wed) |
| 2016 | September  | 2016/09/14  (Wed) |
| 2016 | October    | 2016/10/19  (Wed) |
| 2016 | November   | 2016/11/16  (Wed) |
| 2016 | December   | 2016/12/21  (Wed) |
| 2017 | January    | 2017/01/18  (Wed) |
| 2017 | February   | 2017/02/15  (Wed) |
| 2017 | March      | 2017/03/15  (Wed) |
| 2017 | April      | 2017/04/19  (Wed) |
| 2017 | May        | 2017/05/17  (Wed) |

All feature requests should be submitted prior to the scheduled release day of the prior month.  For example, for a feature request to be considered for the September 2016 release, it should be submitted to the [JIRA](feedback) tracker before the August release day `2016/08/17`.  This will allow the software engineers sufficient time to plan and execute the upcoming activities.

## Download

### mCerebrum instructions
mCerebrum is a suite of several Android applications that are combined with a
set of configuration files.  These instructions will guide you in downloading,
installing, and configuring the mCerebrum software suite.  All source code is
available in the [MD2K's GitHub organization](https://github.com/MD2Korg).

1. Download the latest version of mCerebrum ([latest release](https://github.com/MD2Korg/mCerebrum-Study/releases/latest) ) and install the APK file on and Android 5.0+ device.
1. mCerebrum will run and the `Settings` button will be highlighted in red, press it.
1. A prompt will be shown asking you to enter a filename of a configuration file to download, enter `default` and press `OK`.
1. Once a configuration file is successfully downloaded and installed, you will be prompted with an Admin password screen.  The default password is `1234`.
1. Congratulations, you have successfully installed the main mCerebrum application.  Please follow the instructions [here](https://md2k.org/wp-content/uploads/2016/05/M0003.pdf) for configuring the platform


### List of mCerebrum Apps

| Applications                                                                          | Download                                                                                   |
|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| [AutoSense](https://github.com/MD2Korg/mCerebrum-AutoSense)                           | [latest release](https://github.com/MD2Korg/mCerebrum-AutoSense/releases/latest) |
| [Microsoft Band](https://github.com/MD2Korg/mCerebrum-MicrosoftBand)                  | [latest release](https://github.com/MD2Korg/mCerebrum-MicrosoftBand/releases/latest) |
| [Phone Sensor](https://github.com/MD2Korg/mCerebrum-PhoneSensor)                      | [latest release](https://github.com/MD2Korg/mCerebrum-PhoneSensor/releases/latest) |
| [Stream Processor](https://github.com/MD2Korg/mCerebrum-StreamProcessor)              | [latest release](https://github.com/MD2Korg/mCerebrum-StreamProcessor/releases/latest) |
| [Mood Surfing](https://github.com/MD2Korg/mCerebrum-MoodSurfing)                      | [latest release](https://github.com/MD2Korg/mCerebrum-MoodSurfing/releases/latest) |
| [Thought Shakeup](https://github.com/MD2Korg/mCerebrum-ThoughtShakeup)                | [latest release](https://github.com/MD2Korg/mCerebrum-ThoughtShakeup/releases/latest) |
| [Ecological Momentary Assessment (EMA)](https://github.com/MD2Korg/mCerebrum-EMA)     | [latest release](https://github.com/MD2Korg/mCerebrum-EMA/releases/latest) |
| [EMA Scheduler](https://github.com/MD2Korg/mCerebrum-EMAScheduler)                    | [latest release](https://github.com/MD2Korg/mCerebrum-EMAScheduler/releases/latest) |
| [Notification Manager](https://github.com/MD2Korg/mCerebrum-NotificationManager)      | [latest release](https://github.com/MD2Korg/mCerebrum-NotificationManager/releases/latest) |
| [Data stream plotter](https://github.com/MD2Korg/mCerebrum-Plotter)                   | [latest release](https://github.com/MD2Korg/mCerebrum-Plotter/releases/latest) |
| [DataKit](https://github.com/MD2Korg/mCerebrum-DataKit)                               | [latest release](https://github.com/MD2Korg/mCerebrum-DataKit/releases/latest) |
| [mCerebrum (Study)](https://github.com/MD2Korg/mCerebrum-Study)                       | [latest release](https://github.com/MD2Korg/mCerebrum-Study/releases/latest) |
