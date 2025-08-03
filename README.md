# smart-intrusion-detection-system
This project is like a smart security guard for your network. It learns the normal routine and then flags any suspicious behavior. This allows it to detect new, unknown threats that other systems would miss, providing adaptive protection against cyberattacks.


## ESP32 IoT Motion Detection System with ThingSpeak Alerts

This project is a smart IoT security system built with an ESP32, a PIR motion sensor, and the **ThingSpeak** cloud platform. It detects physical movement, provides a local visual alert, logs the event data to the cloud, and sends a real-time notification to a smartphone.

### Scope of the Solution

The primary goal is to create a reliable and responsive motion detection system. The scope covers:

  * **Real-time Detection:** Capturing motion events instantly using a PIR sensor.
  * **Cloud Data Logging:** Sending motion data to the ThingSpeak platform for timestamped storage and analysis.
  * **Instant Notifications:** Configuring ThingSpeak to send an immediate alert to the owner's phone upon detection.
  * **Hardware Simulation:** Providing a virtual, interactive model of the circuit using the Wokwi simulator.


### Required Components

#### Hardware 🔩

  * **ESP32 Development Board**
  * **PIR Motion Sensor** (e.g., HC-SR501)
  * **5mm LED** (Any color)
  * **330Ω Resistor**
  * **Breadboard** and **Jumper Wires**

#### Software 💻

  * **Arduino IDE** or **PlatformIO** (with ESP32 board support)
  * **Wokwi Online Simulator** (for virtual testing)

#### Cloud Environment ☁️

  * **ThingSpeak Account:** A free account for data aggregation and triggering alerts.


### Circuit & Simulation

#### Circuit Diagram



![WhatsApp Image 2025-07-03 at 15 27 31_359e9a3c](https://github.com/user-attachments/assets/047238f0-899d-4daf-8543-9e6207420c83)

The physical components are wired according to the following diagram:


### System Architecture & Flow

#### How It Works

1.  **Motion Detection:** The PIR sensor detects movement and sends a HIGH signal to the ESP32.
2.  **Local Alert:** The ESP32 immediately lights up the LED.
3.  **Cloud Communication:** The ESP32 connects to Wi-Fi and sends the motion data (e.g., a '1') to a ThingSpeak channel.
4.  **Push Notification:** ThingSpeak receives the data and uses its `React` or `ThingHTTP` app to trigger a notification service (like IFTTT), sending an alert to your phone.

- Project Demo Video :
-    

Uploading Project Demo (1).mp4…



#### Flowchart of the Code

This flowchart illustrates the logic programmed into the ESP32.

```
graph TD
    A[Start] --> B{Setup};
    B --> B1[Initialize Pins];
    B1 --> B2[Connect to Wi-Fi];
    B2 --> B3[Connect to ThingSpeak];
    B3 --> C{Loop};
    C --> D[Read PIR Sensor State];
    D --> E{Motion Detected?};
    E -- Yes --> F[Turn LED ON];
    F --> G[Send Data (1) to ThingSpeak];
    G --> C;
    E -- No --> H[Turn LED OFF];
    H --> C;
```

ThingSpeak Integration
ThingSpeak is the cloud backbone of this project. It is used to:

Log Data: Securely store motion events with timestamps using a "Write API Key".

Trigger Alerts: Use the React app to monitor the data channel and send a notification when new data arrives.
