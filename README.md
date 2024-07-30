# Water Level Indicator Interfacing with Arduino

## Overview
This project involves interfacing a water level sensor with an Arduino to create a simple water level indicator system. This can be used for applications such as water tanks, sump pumps, and similar systems.

## Components Required
- Arduino Uno
- Water Level Sensor
- 10KΩ Resistors (x3)
- Connecting wires
- Breadboard

## Schematic Diagram
Refer to the schematic diagram included in the repository for the wiring setup.

## Connection Instructions
1. **Water Level Sensor to Arduino:**
   - Connect the VCC pin of the sensor to the 5V pin on the Arduino.
   - Connect the GND pin of the sensor to the GND pin on the Arduino.
   - Connect the sensor output pin to the analog input pin (A0) on the Arduino.

2. **Resistors Setup:**
   - Use the 10KΩ resistors to create a voltage divider circuit if necessary, depending on the specific sensor used.

## Arduino Code
Upload the following code to your Arduino:

```cpp
const int sensorPin = A0; // Pin connected to the sensor
int sensorValue = 0; // Variable to store the sensor value

void setup() {
  Serial.begin(9600); // Initialize serial communication
  pinMode(sensorPin, INPUT); // Set the sensor pin as input
}

void loop() {
  sensorValue = analogRead(sensorPin); // Read the value from the sensor
  Serial.print("Water Level: ");
  Serial.println(sensorValue); // Print the sensor value to the serial monitor
  delay(1000); // Wait for a second before reading again
}
