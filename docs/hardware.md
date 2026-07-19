## Hardware

## Overview

Mimi DeskBot is built around an ESP32 DevKit V1, which serves as the central controller for the robot. The ESP32 manages the OLED display, motor driver, movement logic, and Wi-Fi web server.

The robot uses a two-wheel differential drive system powered by two N20 geared DC motors. A castor wheel provides additional support and stability.

The system is powered by a 2S 18650 Li-ion battery pack. An LM2596 buck converter regulates the battery voltage to provide suitable power for the robot's electronics.

| Component | Specification | Qty | Purpose |
|-----------|---------------|:---:|---------|
| ESP32  | ESP32 DevKit V1 | 1 | Main microcontroller responsible for motor control, OLED animations, and hosting the Wi-Fi web interface. |
| OLED Display | SSD1306, 0.96", 128×64, I2C | 1 | Displays expressive facial animations and robot status. |
| Motor Driver | DRV8833 Dual H-Bridge | 1 | Controls the speed and direction of both DC motors. |
| DC Gear Motors | N20 Metal Gear Motors, 100 RPM, 6V | 2 | Provide differential drive for robot movement. |
| Wheels | Compatible with N20 motors | 2 | Enable locomotion and traction. |
| Castor Wheel | Free-rotating swivel wheel | 1 | Supports the robot and provides balance during movement. |
| Battery Pack | 2S 18650 Li-ion (7.4V) | 1 | Primary rechargeable power source for the robot. |
| Buck Converter | LM2596 Adjustable DC-DC Converter | 1 | Steps down the battery voltage to a stable supply for the electronics. |
| Power Switch | SPDT Slide Switch | 1 | Safely turns the robot on and off. |

---
## Hardware Subsystems

### Control System

The ESP32 acts as the central processing unit of Mimi DeskBot. It is responsible for:

- Processing movement commands
- Controlling the motor driver
- Managing OLED facial animations
- Running the Wi-Fi access point
- Hosting the web-based control dashboard

### Drive System

The robot uses two N20 geared DC motors arranged in a differential-drive configuration.

Independent control of the left and right motors allows the robot to:

- Move forward
- Move backward
- Turn left
- Turn right
- Rotate in place

### Display System

The SSD1306 OLED display provides the robot with an expressive face.

It is used to display:

- Facial expressions
- Eye movement
- Blinking animations
- Robot status information

### Wireless Control

The ESP32 creates a Wi-Fi network and hosts a web server. A user can connect to the robot using a phone or computer and control its movement through the web dashboard.

### Power System

The 2S Li-ion battery pack serves as the primary power source. The LM2596 buck converter regulates the battery voltage to provide the required voltage for the electronics.

## Hardware Connections


                    ┌──────────────────────────┐
                    │    2S Li-ion Battery     │
                    │           7.4V           │
                    └────────────┬─────────────┘
                                 │
                          Power Switch
                                 │                      
                   |─── ── ── ── ─── ── ──|
                   |                      │
      ┌────────────▼────────────┐         │
      │ LM2596 Buck Converter   │         │
      └───────────────────┬─────┘         │ 
                          │               │ 
                          │               │
                          │               │
                    ┌─────▼─────┐─────────▼──────────────────────────┐
                    │   ESP32   │           DRV8833                  │
                    │           │                                    │
                    │           │                                    │
                    │  GPIO 25  │  --->   IN1      OUT1  ---> Motor1 │
                    │  GPIO 26  │  --->   IN2      OUT2  ---> Motor1 │
                    │  GPIO 27  │  --->   IN1      OUT3  ---> Motor1 │
                    │  GPIO 14  │  --->   IN2      OUT4  ---> Motor1 │
                    │           │────────────────────────────────────┘
                    │           │───────────────────┐                   
                    │  GPIO 21  │  --->  OLED (SCA) │
                    │  GPIO 22  │  --->  OLED (SDA) │
                    │  GND      │  --->  OLED GND   │
                    │  3V3      │  --->  OLED VCC   │
                    └───────────┘───────────────────┘

