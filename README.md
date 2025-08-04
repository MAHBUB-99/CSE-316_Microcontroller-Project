# 👁️ Third Eye for Blind
### A Microcontroller-Based Assistive System for Visually Impaired Individuals

![Arduino](https://img.shields.io/badge/Arduino-Uno-blue?logo=arduino)
![C++](https://img.shields.io/badge/C%2B%2B-Embedded-brightgreen?logo=c%2B%2B)
![Ultrasonic Sensor](https://img.shields.io/badge/Sensors-Ultrasonic-yellow?style=flat-square)
![HMC5883L](https://img.shields.io/badge/Magnetometer-HMC5883L-purple)

---

## 📌 Overview

The **Third Eye for Blind** is an **Arduino-powered wearable assistive device** that helps visually impaired users by:

- Detecting nearby obstacles
- Guiding users via **vibration feedback**
- Providing **compass-based direction sensing**
- Supporting **emergency alert mode**

---

## 🔧 Key Features

| 🧠 Module        | 🚀 Description                                                                 |
|------------------|--------------------------------------------------------------------------------|
| 🛑 **Obstacle Detection** | Detects objects using 3 ultrasonic sensors (Front, Left, Right).               |
| 🧭 **Compass Mode**       | Uses HMC5883L magnetometer to guide direction; triggers alert when facing North. |
| 🚨 **Emergency Mode**     | Sends an emergency signal when a specific condition is triggered.               |
| 📡 **Bluetooth Serial**   | Communication via SoftwareSerial on pins 0 and 1.                              |
| 🎮 **Sensor Switching**   | Modes (Sensor, Compass, Emergency) are switchable via digital input.           |
| 📟 **Feedback System**    | Alerts users through two vibration motors (pins 8 and 9).                      |

---

## ⚙️ Hardware Used

| Component               | Description                                   |
|------------------------|-----------------------------------------------|
| Arduino Uno            | Main microcontroller                          |
| 3x Ultrasonic Sensors  | For obstacle detection (HC-SR04)              |
| HMC5883L Magnetometer  | For compass heading                           |
| Vibration Motors       | For tactile feedback                          |
| Push Button            | Mode switching input                          |
| Bluetooth Module (optional) | For serial debugging/logging             |

---

## 🧠 Core Logic Summary

### 1️⃣ Sensor Mode
- Measures distances from 3 ultrasonic sensors
- Based on thresholds:
  - Both sides blocked → alert both vibrators
  - Clear path → activate only one motor based on direction
  - Distance threshold: `< 50cm` (customizable)

### 2️⃣ Compass Mode
- Reads magnetometer via I2C
- Converts vector data to compass heading
- Alerts user when facing **North** (0° ± 20°)
- After 3 alerts → returns to Sensor Mode

### 3️⃣ Emergency Mode
- Activated after a long button press
- Sends alert signal
- Waits 10 seconds before returning to Sensor Mode

---

## 💻 Code Snippet

```cpp
if (FrontSensor < MINDISTANCE) {
    if (RightSensor < MINDISTANCE && LeftSensor < MINDISTANCE) {
        digitalWrite(8, HIGH); // Vibrate both
    } else if (RightSensor > LeftSensor) {
        digitalWrite(9, HIGH); // Vibrate right
    } else {
        digitalWrite(8, HIGH); // Vibrate left
    }
}
```

---

## 🎥 Demo Video & Repository

- 🔗 [Demo Video](https://youtu.be/RtrROTO9bsk?si=J1tAzmDtqypnOe6Z)
- 🧾 [GitHub Repo](https://github.com/your-username/ThirdEyeForBlind)

---

## 🧰 Tools & Technologies

- **Arduino IDE**
- **C++ for Embedded Systems**
- **Ultrasonic + Compass Integration**
- **Serial Communication**
- **Real-Time Sensor Fusion**

---

## 💡 Future Improvements

- Add **buzzer alerts**
- GPS integration for **location tracking**
- Real-time mobile app integration via Bluetooth
- Rechargeable power unit with battery monitoring

---

## 🤝 Credits

Developed with ❤️ by [Your Name]

---

## 📄 License

This project is licensed under the [MIT License](LICENSE)
