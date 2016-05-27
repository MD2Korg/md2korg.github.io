# Introduction
The MD2K software platform includes mobile phone software platform called mCerebrum and a cloud counterpart called Cerebral Cortex. mCerebrum is a configurable software platform for mobile and wearable sensors. It provides support for reliable data collection from mobile and wearable sensors, and real-time processing of these data for sensor triggered just-in-time adaptive interventions.

Cerebral Cortex is the big data companion of mCerebrum designed to support population-scale data analysis, visualization, model development, and intervention design for mobile sensor data. It provides the ability to do machine learning model development on population scale data sets and provides interoperable interfaces for aggregation of diverse data sources.

## Limitations of Existing mHealth Platforms
Several software platforms have recently emerged for collecting mobile health data. For example, Apple and Google each provide a set of APIs and tools for mobile mHeath data collection. But, Apple HealthKit and Google Fit APIs are primarily designed for low frequency data collection of digital biomarkers including: blood pressure, weight, or physical activity. Both of these platforms have limited expressiveness for time series data streams.

## Uniqueness of MD2K
The [MD2K](https://www.github.com/MD2Korg/) platform , on the other hand, is designed from the ground up as a high-frequency data stream processing toolchain that provides flexible data types and custom object storage. It can collect and analyze data from tens of wearable sensors via a wide array of wireless radios (ANT, Bluetooth, Bluetooth LE, etc.). It also provides native support for triggering notifications, self-report prompts, and interventions based on real-time values of digital biomarkers derived from sensor data.

## Background
mCerebrum is backed by 9 years of software development on the [Fieldstream](http://www.fieldstream.org/) and [AutoSense](https://sites.google.com/site/autosenseproject/) projects which yielded in excess of 20,000 hours of wearable sensor data from a variety of lab and field studies with hundreds of participants. Over 27 research articles (with over 400 citations) have been published using analysis of these data (see list of articles below; go here for citations). mCerebrum is based on these extensive experiences with real-life high-frequency sensor data and its analysis for both technology and health research.

The signal processing for Fieldstream and AutoSense were on a Matlab batch-processing codebase that operates on data after a participant has returned the data collection device to the lab. Therefore, no real-time sensor-triggered notifications or interventions were possible with the existing framework and furthermore, the codebase does not lend itself well to distributed processing for scalable application performance.

## Novelty of MD2K
mCerebrum, on the other hand, is designed to be compatible with mobile platforms so as to support real-time signal processing of high-frequency data streams in excess of 800 hertz, while meeting quality of service requirements for the mobile platform. In addition, mCerebrum is designed as an open-source project so that it can be easily used by the community and modified to suit specific research needs.

Cerebral Cortex is the big data companion to mCerebrum designed to support population-scale analytics, model development, and data visualizations. One of the primary capabilities of Cerebral Cortex is its ability to support scalable big data machine learning model development and iterative data analysis and model generation across population-scale data sets. Models learned on population-scale data can be sent back to a smartphone in the field to improve detection and classification accuracy.
