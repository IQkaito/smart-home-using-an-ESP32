# ⌂ ESP32 Smart Home System

A complete, locally-hosted smart home environment monitor running entirely on an ESP32. This system monitors temperature, humidity, gas levels, and proximity across three separate rooms, serving a real-time responsive web dashboard directly from the microcontroller.

It features a dual-alarm system: a physical hardware buzzer and an API-triggered Web Audio siren that bypasses browser autoplay restrictions to alert you on your phone or laptop during an emergency.

## ✨ Features
*   **Live Web Dashboard:** A sleek, dark-mode compatible UI built with HTML/CSS/JS, hosted directly on the ESP32 (no cloud required).
*   **Dual-Siren Alert System:** Triggers a loud physical buzzer and a flashing web-audio siren if safety thresholds are breached.
*   **Threshold Monitoring:** Alerts trigger if temperature exceeds 47°C, proximity drops below 15cm, or dangerous gas levels are detected.
*   **Room Isolation:** Independent alert toggling and monitoring for the Living Room, Bedroom, and Kitchen.
*   **Central Lighting:** One-touch web control for indicator LEDs across all rooms.
*   **Offline Fallback:** The dashboard includes a demo-mode script if the Wi-Fi connection drops.

## 🛠️ Hardware Requirements
*   1x ESP32 Development Board (e.g., ESP32-D0WD)
*   3x DHT22 Temperature & Humidity Sensors
*   3x HC-SR04 Ultrasonic Distance Sensors
*   1x MQ2 Gas Sensor
*   3x White LEDs (for room lighting simulation)
*   1x Active Buzzer
*   Breadboard and jumper wires

## 🔌 Wiring Guide
*⚠️ **CRITICAL NOTE:** Do not use Pin 12 for the Ultrasonic sensor. Pin 12 is a strapping pin that controls the flash memory voltage. Using it will cause an `0xffffffff` boot error. Use Pin 21 instead.*

| Component | Room | ESP32 Pin |
| :--- | :--- | :--- |
| **DHT22 (Data)** | Living Room | `GPIO 4` |
| | Bedroom | `GPIO 5` |
| | Kitchen | `GPIO 18` |
| **HC-SR04 (Trig / Echo)** | Living Room | `GPIO 21` / `GPIO 14` |
| | Bedroom | `GPIO 27` / `GPIO 35` |
| | Kitchen | `GPIO 25` / `GPIO 33` |
| **MQ2 Gas Sensor (Analog)**| Kitchen | `GPIO 34` |
| **Indicator LEDs** | Living Room | `GPIO 19` |
| | Bedroom | `GPIO 23` |
| | Kitchen | `GPIO 15` |
| **Hardware Buzzer** | Global | `GPIO 26` |

## 🚀 Installation & Flashing
Because the MQ2 sensor draws significant current and the ESP32 is sensitive to strapping pin interference during upload, you must perform a "Bench Flash".

1.  **Remove the ESP32** completely from the breadboard circuit.
2.  Connect the ESP32 directly to your computer via a high-quality data USB cable (avoid hubs).
3.  Open the `.ino` file in the Arduino IDE.
4.  Ensure your upload speed is set to `115200 baud`.
5.  Click **Upload**. *(Note: If you get a packet error, press and hold the physical `BOOT` button on the board until the percentage counter begins).*
6.  Once flashing is 100% complete, disconnect the USB, place the ESP32 back into the fully wired breadboard, and supply power.
7.  Press the **EN** (Reset) button once.

## 📱 Usage
1.  Open your device's Wi-Fi settings.
2.  Connect to the Access Point:
    *   **SSID:** `ESP32-SmartHome`
    *   **Password:** `Password123`
3.  Open a web browser and navigate to `[http://192.168.4.1](http://192.168.4.1)`.
4.  **Important:** Click anywhere on the webpage once to unlock the browser's Web Audio API for the siren functionality.

## 📝 License
This project is [GPL-3.0 license](LICENSE).

*** 

How does that look for your repository?
