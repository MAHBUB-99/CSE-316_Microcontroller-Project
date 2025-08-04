# 👁️ Third Eye for Blind
### A Microcontroller-Based Assistive System for Visually Impaired Individuals

![Arduino](https://img.shields.io/badge/Arduino-Uno-blue?logo=arduino)
![C++](https://img.shields.io/badge/C%2B%2B-Embedded-brightgreen?logo=c%2B%2B)
![Ultrasonic Sensor](https://img.shields.io/badge/Sensors-Ultrasonic-yellow?style=flat-square)
![HMC5883L](https://img.shields.io/badge/Magnetometer-HMC5883L-purple)

---

## 📌 Overview

**Third Eye for Blind** is an **Arduino-powered wearable assistive device** designed to enhance mobility and safety for visually impaired individuals. It provides:

- 🛑 **Real-time obstacle detection** using ultrasonic sensors  
- 📟 **Vibration-based feedback** to intuitively guide users  
- 🧭 **Compass mode** for direction sensing (e.g., facing North)  
- 🚨 **Emergency alert mode** activated through button input  


---

## 🔧 Key Features

| 🧠 Module              | 🚀 Description                                                                 |
|------------------------|--------------------------------------------------------------------------------|
| 🛑 **Obstacle Detection** | Detects objects using 3 ultrasonic sensors (Front, Left, Right).               |
| 🧭 **Compass Mode**       | Utilizes HMC5883L magnetometer to detect direction; vibrates when facing North. |
| 🚨 **Emergency Mode**     | Sends an emergency alert signal after a long button press.                     |
| 📡 **Bluetooth Serial**   | Enables serial communication using SoftwareSerial (pins 0 and 1).              |
| 🔄 **Mode Switching**      | Switches between Sensor, Compass, and Emergency modes via button input.        |
| 📟 **Feedback System**    | Provides tactile feedback using two vibration motors (pins 8 and 9).           |

---

## ⚙️ Hardware Used

| 🧩 Component             | 🔍 Description                                   |
|--------------------------|--------------------------------------------------|
| 🟦 Arduino Uno           | Core microcontroller for logic and control       |
| 📡 3× Ultrasonic Sensors | HC-SR04 sensors for obstacle detection           |
| 🧲 HMC5883L Magnetometer | Provides compass heading via I2C communication   |
| 🔋 Vibration Motors      | Delivers haptic feedback based on sensor data    |
| 🔘 Push Button           | Used to switch between operating modes           |
| 📶 Bluetooth Module      | For wireless serial debugging or data logging    |

---

## 🧠 Core Logic Summary

### 🔍 1️⃣ Sensor Mode
- Uses **three ultrasonic sensors** to detect obstacles: Left, Front, and Right.
- Decision-making based on measured distances:
  - 🚧 **Both sides blocked** → Activate **both motors** (simulate stop or alert).
  - 🔄 **One side clearer** → Turn in that direction by activating only one motor.
  - ✅ **Path clear** → Move forward.
- **Threshold distance:** `MINDISTANCE = 50 cm` *(can be customized)*.

---

### 🧭 2️⃣ Compass Mode
- Reads magnetic field using the **HMC5883L magnetometer** (I2C).
- Converts sensor vector data into **heading angle (in degrees)**.
- 🔔 Triggers **vibration alert** when facing near **North** (within `0° ± 20°`).
- 🕒 After **3 consecutive North detections**, it switches back to **Sensor Mode**.

---

### 🚨 3️⃣ Emergency Mode
- Activated by a **long button press** (after initial short press).
- Sends a **special alert signal** via serial.
- ⏳ Waits for **10 seconds**, then automatically returns to **Sensor Mode**.


---


## 🎥 Demo Video

- 🔗 [Demo Video](https://youtu.be/RtrROTO9bsk?si=J1tAzmDtqypnOe6Z)

---

## 🧰 Tools & Technologies

- **Arduino IDE**
- **C++ for Embedded Systems**
- **Ultrasonic + Compass Integration**
- **Serial Communication**
- **Real-Time Sensor Fusion**

---
## 🙌 Credits

Developed with :

- 🎓 **Ruhul Azgor**  
- 🌟 **Sweekyoching Marma**

