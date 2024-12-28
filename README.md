# Smart Car Project

This project is a Smart Car System that integrates light and distance sensors, an LCD display, and a buzzer to enhance the functionality of a car. The system uses a **LiquidCrystal I2C** display to show real-time data and controls the high and low beam lights based on ambient light conditions. It also uses an ultrasonic sensor to detect distance and activates the buzzer if an object is detected within a specified range.

## Features

- **Light Detection:**
  - Switches between **High Beam** and **Low Beam** based on ambient light using an LDR (Light Dependent Resistor).
  - Displays the light intensity and beam status on an LCD.

- **Distance Measurement:**
  - Uses an **Ultrasonic Sensor** (HC-SR04) to measure the distance to objects in front of the car.
  - Activates a **Buzzer** if an object is detected within 50 cm.

- **LCD Display:**
  - Displays the **light intensity** and **distance** readings in real-time.
  - Shows the current light status: High Beam (`H`), Low Beam (`L`), or No Light (`No`).

## Hardware Components

- **ESP8266/ESP32 Board** (e.g., NodeMCU or Wemos D1 mini)
- **LDR (Light Dependent Resistor)** for light sensing
- **HC-SR04 Ultrasonic Sensor** for distance measurement
- **16x2 LCD Display** with I2C interface
- **Buzzer** for object proximity alerts
- **LEDs** (for High Beam and Low Beam simulation)
- **Digital Pin** for voltage reading (optional)

## Circuit Diagram

- **LDR (Light Sensor):** Connected to analog pin A0.
- **Ultrasonic Sensor:**
  - `TrigPin` connected to D6 (GPIO12).
  - `EchoPin` connected to D5 (GPIO14).
- **LEDs:**
  - High Beam LED connected to D7.
  - Low Beam LED connected to D8.
- **Buzzer:** Connected to D0.
- **Voltage Sensor (Optional):** Connected to D3 for voltage monitoring.
  
## Software Requirements

- **Arduino IDE**
- **LiquidCrystal_I2C Library** for controlling the LCD display
- **Ultrasonic Library** (optional, for easier handling of the ultrasonic sensor)

### Install Libraries

1. Go to **Sketch > Include Library > Manage Libraries** in Arduino IDE.
2. Search and install the following libraries:
   - **LiquidCrystal_I2C** (for LCD control)

## Setup

1. Open the Arduino IDE and select the correct **Board** and **Port** for your ESP8266/ESP32.
2. Upload the code to your board after ensuring the wiring is correct.
3. Monitor the output using the **Serial Monitor** for debugging.

## Code Explanation

### Key Components:

- **Light Detection:** 
  - The **LDR** detects the ambient light and switches between high and low beams based on the light level:
    - **Low Beam (L):** When light is between 50 and 150.
    - **High Beam (H):** When light is less than 50.
    - **No Light:** If no significant light is detected.
  
- **Distance Measurement:**
  - The **HC-SR04** ultrasonic sensor measures the distance to the nearest object.
  - If the distance is less than 50 cm, a buzzer sounds for a duration proportional to the distance.
  
- **LCD Display:**
  - Displays the **light level** and **distance** data. It also shows the current light beam status.

- **Buzzer Feedback:**
  - The buzzer is activated when an object is detected within a 50 cm range.

### Functions:

- **Light Detection Logic:**
  - Reads the light sensor and updates the LCD with the light intensity and the corresponding beam status.
  
- **Ultrasonic Distance Measurement:**
  - Uses `pulseIn()` to measure the time taken by the sound waves to travel and calculates the distance.
  - If the object is detected within 50 cm, it triggers the buzzer for a short duration based on the detected distance.

### Code Flow:
1. The program continuously reads the light intensity and updates the LCD with the value.
2. Based on the light intensity, it controls the high and low beams (LEDs).
3. It also reads the distance from the ultrasonic sensor and triggers the buzzer when the distance is below 50 cm.
4. Serial output provides debugging information about light intensity and distance.

## Troubleshooting

- **LCD not displaying properly:**
  - Ensure the I2C address of your LCD is correct (default is `0x27`).
  - Check the connections and ensure the LCD's backlight is working.

- **Buzzer not sounding:**
  - Ensure the ultrasonic sensor is correctly wired.
  - If the distance is too large, ensure there are objects within 50 cm range to activate the buzzer.

- **High/Low Beam not switching:**
  - Ensure the **LDR** is working and properly connected to analog pin A0.
  - Adjust the light thresholds if needed.

## License

This project is open-source and can be freely modified for personal or educational purposes.
