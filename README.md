# Robust Electronic Nose System (Kinetic-ENose)

A real-time atmospheric gas classification system built on the ESP32 platform. This project utilizes a novel **Phase-Space Trajectory Mapping** technique and **Normalized Kinetic Feature Extraction** to decouple gas chemical identity from sensor drift, addressing the common limitations of Metal-Oxide Semiconductor (MOX) sensors.

## 📄 Overview

Traditional MOX sensors suffer from cross-sensitivity and baseline drift due to thermal aging. This system introduces a drift-independent feature—the **Normalized Logarithmic Derivative**—which effectively linearizes the sensor response and separates the "shape" of the reaction from the gas concentration.

By mapping these features into a 2D Phase Space, the system creates unique topological loops for different gases, allowing a K-Nearest Neighbors (KNN) classifier to distinguish between:
- Clean Air
- Butane
- Smoke

## 🚀 Key Features

* **Drift Independence:** Uses a normalized differential metric ($\dot{R}/R$) that is mathematically invariant to baseline resistance shifts ($R_0$).
* **Real-Time Processing:** Optimized $O(1)$ algorithm capable of running on a single-core ESP32 at 100 Hz.
* **Sensor Fusion:** Combines MQ-3 and MQ-136 sensors to resolve "iso-resistive ambiguity" (where different gases produce identical resistance values).
* **High Accuracy:** Achieves **~89-92%** classification accuracy using a KNN ($k=5$) model.

## 🛠️ Hardware Stack

* **Microcontroller:** ESP32 (DOIT DEVKIT V1)
* **Sensors:** * MQ-3 (Alcohol/Ethanol sensitive)
    * MQ-136 (Hydrogen Sulfide sensitive)
* **Power:** 5V Regulated Supply

## 📊 System Architecture

The raw resistance data is transformed through a pipeline to generate a drift-independent feature vector:

`Raw Resistance` -> `Normalization` -> `Logarithmic Derivative` -> `Phase Space Mapping` -> `KNN Classification`

## 👥 Authors

* **Abhishek Srivastava** (Supervisor)
* **Alan Nelson** (Mentor)
* **Bysani Vedavyas**
* **Devshree Vyas**
* **Kushagra Agrawal**
* **Shreyas Agarwal**
* **Srikar Somanchi** (Mentor)

*International Institute of Information Technology, Hyderabad (IIIT-H)*

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.
