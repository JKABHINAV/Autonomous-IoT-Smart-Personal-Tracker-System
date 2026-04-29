# 🚀 IoT-Based Smart Personal Tracker System

An advanced wearable safety solution built on the **ESP32** platform, featuring real-time GPS tracking, automated inactivity monitoring, and emergency SOS alerts with cloud integration.

---

## 🌟 Key Features
- **📍 Real-time GPS Tracking:** High-precision positioning using the SIM28 module.
- **🚨 Emergency SOS Button:** Manual panic button (GPIO 13) to send instant alerts.
- **⌚ Automated Inactivity Monitoring:** Uses the MPU6050 (IMU) to detect medical emergencies or falls automatically.
- **📲 SMS Alerts:** Sends Google Maps location links directly to emergency contacts via SIM900A GSM.
- **☁️ Cloud Data Logging:** Automatically logs movement data to a Google Sheets CSV database every 5 minutes.
- **🌐 Web Dashboard:** Interactive visualization of historical paths using Leaflet.js and a timeline view.

---

## 🛠️ Hardware Architecture
| Component | Function | Interface |
| :--- | :--- | :--- |
| **ESP32** | Central Processing Unit / "The Brain" | - |
| **SIM28 GPS** | Location Positioning | UART1 (GPIO 14/12) |
| **SIM900A GSM** | SMS & GPRS Data Transmission | UART2 (GPIO 16/17) |
| **MPU6050** | Motion & Fall Detection (3-axis Accel/Gyro) | I2C (GPIO 21/22) |
| **Push Button** | Manual SOS Trigger | GPIO 13 |

---

## ⚙️ How It Works
1. **Initialization:** The system sets up UART/I2C communication and syncs with the Cloud API.
2. **Monitoring Phase:** - The **GPS Task** parses NMEA strings to update local coordinates.
   - The **Motion Task** monitors the MPU6050; if motion is detected, the inactivity timer resets.
3. **Emergency Trigger:** If the panic button is pressed OR inactivity exceeds the limit, the system sends an SMS with a Google Maps link.
4. **Data Logging:** Every 5 minutes, coordinates are sent via HTTP request to a Google Apps Script, which appends the data to a Google Sheet.

---

## 📊 Web Dashboard & Visualization
The project includes a public web interface that allows users to:
- **📅 Filter by Date:** Use a date picker to view movements from specific days.
- **🗺️ Interactive Map:** View coordinates plotted on a Leaflet.js map.
- **🛤️ Path Timeline:** A Polyline connects points chronologically to reconstruct the travel path.
- **📑 Activity Summary:** Displays "Total distance travelled" and "Last known location."

---
