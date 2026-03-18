# Wearable Infant Heart Rate & Oxygen Monitor
**Arduino-based biosensor system for continuous cardiac monitoring in infants with Congenital Heart Disease (CHD)**

> Academic Design Project — Illinois Institute of Technology | BME 100 | Aug – Dec 2024
> 5-person team | 32+ design sessions | 2 circuit iterations | 1 functional prototype

---

## Overview
Infants with congenital heart defects require continuous cardiac monitoring, but existing hospital equipment is bulky and restricts movement. This project designs a lightweight, wearable monitoring system integrated into a baby onesie that tracks ECG and blood oxygen saturation (SpO₂) in real time, alerting caregivers via a local display and BLE smartphone notification when abnormal readings are detected (Next phase).

---

## System Architecture

```
ECG Electrodes       Pulse Oximeter
    │                     │
  AD8232              MAX30102
    │                     │
    └──────────┬──────────┘
               │
      Arduino Nano 33 BLE Sense
               │
       ┌───────┴───────┐
   TFT Display     BLE Alert
  (on-device)   (Smartphone App)
               │
         3.7V LiPo Battery
```

---

## Hardware Components

| Component | Role | Justification |
|---|---|---|
| AD8232 ECG Module | ECG signal acquisition | Medical-grade instrumentation amplifier with high common-mode rejection; optimized for microvolt cardiac signals |
| MAX30102 Pulse Oximeter | SpO₂ + PPG monitoring | Low-power red/IR LEDs for continuous oxygen saturation tracking; critical for detecting CHD decompensation |
| Arduino Nano 33 BLE Sense | Central processor | Compact ARM Cortex-M4, built-in BLE for wireless alerts, capable of simultaneous ECG + PPG processing |
| ILI9341 TFT Display | On-device output | Real-time display of heart rate and SpO₂ for immediate caregiver reference |
| BLE Smartphone Alert | Secondary alert pathway | Sends notifications when abnormal thresholds are detected; supports fast caregiver response |
| 3.7V LiPo Battery | Power supply | Lightweight, rechargeable, suitable for wearable integration |

---

## Key Features
- Dual biosignal monitoring: ECG (electrical cardiac activity) + SpO₂ (oxygen saturation)
- Dual alert system: local TFT display + BLE smartphone notification. BLE alert system designed but not implemented in final prototype — identified as next development phase
- Wearable design: integrated into baby onesie using Velcro and soft fabric — non-restrictive for infant movement
- Designed specifically for infants with CHD, where abnormalities can occur without visible external symptoms

---

## Circuit Design
Full breadboard circuit diagram designed in Fritzing. See [Circuit Diagram](circuit_diagram.jpg)

Communication protocols:
- MAX30102 → Arduino via **I²C**
- TFT Display → Arduino via **SPI**
- Smartphone alerts via **BLE**

---

## Clinical Motivation
Congenital heart defects affect approximately 1% of births globally. Continuous monitoring is critical because cardiac instability in CHD infants can occur suddenly and without visible symptoms. Existing hospital monitors are large and impractical for home use. This device aims to bridge that gap with a low-cost, wearable alternative that keeps infants connected to caregivers.

---

## Tools & Technologies
- Arduino IDE
- Fritzing (circuit design)
- AD8232, MAX30102 sensor libraries
- Bluetooth Low Energy (BLE)

---

## Team
5-person team — Illinois Institute of Technology, BME 100 Design Project

---

## References
- AD8232 Datasheet — Analog Devices
- MAX30102 Datasheet — Analog Devices  
- Arduino Nano 33 BLE Sense Documentation
- CDC Congenital Heart Defects Data (2024)
- WHO Standards for Newborn Care (2020)
