# Smart Car Project

This project simulates a smart car system that integrates light detection and an ultrasonic sensor to monitor the surrounding environment. It uses an LDR (Light Dependent Resistor) to detect ambient light levels and automatically control the high and low beam lights of the car. Additionally, an ultrasonic sensor measures the distance to objects in front of the car, and a buzzer alerts the user when an object is too close.

## Features

- **Light Detection**: The car's high and low beam lights are controlled based on ambient light conditions.
- **Distance Measurement**: The ultrasonic sensor measures the distance to objects in front of the car, with a buzzer warning the user when an object is too close.
- **LCD Display**: Displays real-time data such as light levels and distance on a 16x2 LCD screen.
- **Buzzer Alert**: Activates when the car is too close to an object detected by the ultrasonic sensor.
  
## Components Needed

- **NodeMCU/ESP8266 or compatible microcontroller**
- **16x2 LCD Display with I2C interface**
- **Ultrasonic Sensor (HC-SR04)**
- **LDR (Light Dependent Resistor)**
- **LED (for high and low beam lights)**
- **Buzzer**
- **Resistors for LDR and LEDs**
- **Jumper wires**
- **Breadboard** (optional for testing)

## Circuit Diagram

- **Ultrasonic Sensor (HC-SR04)**: Connect the `Trig` pin to D6 (GPIO12) and the `Echo` pin to D5 (GPIO14) on your microcontroller.
- **LDR**: Connect the LDR to A0 pin for light reading.
- **LEDs**: Connect the high beam LED to D7 and the low beam LED to D8 on the microcontroller.
- **Buzzer**: Connect the buzzer to D1 (or another available pin).
- **Voltage Input Pin**: Connect a digital input pin (D3) for detecting a specific condition (like ignition or a trigger signal).

## Code Overview

### Libraries

```cpp
#include <LiquidCrystal_I2C.h>
```

## How to Use
1. Wire the Components: Follow the wiring diagram to connect the ultrasonic sensor, LDR, LEDs, buzzer, and other components to your microcontroller.
2. Upload the Code: Use the Arduino IDE to upload the provided code to your microcontroller.
3. Test the System: After uploading, the system will begin displaying light levels and distance measurements on the LCD screen. The high or low beam LED will be automatically controlled based on ambient light, and the buzzer will sound when an object is too close to the car.
