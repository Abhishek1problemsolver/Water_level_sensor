# Water Level Indicator

## Description
The Water Level Indicator is a project that uses a water level sensor and an Arduino Uno to monitor the water level in a tank. When the water level changes, the sensor sends a signal to the Arduino, which then processes the data and indicates the water level.

## Materials Required

### Hardware Requirement
- Arduino Uno
- Water Level Sensor
- 10kΩ Resistors (x3)
- Breadboard
- Jumper wires

### Software
- Arduino IDE

## Theory

### Water Level Sensor
A water level sensor is used to measure the level of water in a tank. It outputs an analog signal proportional to the water level. Below is an image of a water level sensor:

![Water Level Sensor](https://example.com/water-level-sensor.jpg)

### Arduino Uno
The Arduino Uno has several digital and analog pins used for input and output operations. Below is an image of the Arduino pin description:

![Arduino Uno](https://example.com/arduino-uno.jpg)

## Circuit Diagram

### Prototype Image
![Circuit Diagram](https://example.com/circuit-diagram.jpg)

### Real Image from Project
![Real Image](https://example.com/real-image.jpg)

## Working
The Water Level Indicator project utilizes a water level sensor to measure the water level and an Arduino Uno to process the sensor data and indicate the water level. Here’s a detailed explanation of how it works:

### Principle
The water level sensor changes its output voltage based on the water level. The Arduino reads this voltage and converts it into a digital value.

### Setup and Components
- **Water Level Sensor**: Connected in a voltage divider configuration with a fixed resistor (10kΩ). The junction of the sensor and the resistor is connected to an analog input pin (A0) of the Arduino to read the voltage level, which varies with water level.
- **Resistors**: Used to create a voltage divider circuit if necessary.

### Circuit Description
1. **Sensor and Resistor**: The water level sensor and a 10kΩ resistor form a voltage divider. One end of the sensor is connected to 5V, the other end to the analog input pin A0, and the 10kΩ resistor connects this junction to ground (GND).

### Steps
1. **Reading Sensor Value**: The Arduino reads the analog voltage from the sensor using the `analogRead` function.
2. **Processing the Data**: The read value is processed to determine the water level.
3. **Indicating the Water Level**: Based on the processed value, the Arduino can indicate the water level through various means (e.g., serial monitor, LEDs, etc.).

## Arduino IDE Code
```cpp
// Sensor pins
#define sensorPower 7
#define sensorPin A0

// Value for storing water level
int val = 0;

void setup() {
	// Set D7 as an OUTPUT
	pinMode(sensorPower, OUTPUT);
	
	// Set to LOW so no power flows through the sensor
	digitalWrite(sensorPower, LOW);
	
	Serial.begin(9600);
}

void loop() {
	//get the reading from the function below and print it
	int level = readSensor();
	
	Serial.print("Water level: ");
	Serial.println(level);
	
	delay(1000);
}

//This is a function used to get the reading
int readSensor() {
	digitalWrite(sensorPower, HIGH);	// Turn the sensor ON
	delay(10);							// wait 10 milliseconds
	val = analogRead(sensorPin);		// Read the analog value form sensor
	digitalWrite(sensorPower, LOW);		// Turn the sensor OFF
	return val;							// send current reading
}
```
## Applications
- **Water Tank Monitoring:** Automatically monitor and display the water level in household or industrial water tanks.
- **Sump Pumps:** Control sump pumps to prevent overflow or dry running.
- **Aquariums:** Maintain the water level in aquariums to ensure a stable environment for aquatic life.
- **Irrigation Systems:** Automate irrigation systems based on the water level in storage tanks.
- **Flood Detection:** Detect and alert in case of potential flooding scenarios.

## Conclusion
The Water Level Indicator works by continuously monitoring the water level through the sensor. The Arduino processes the sensor data and indicates the water level, providing a simple and effective way to manage water levels in various applications.

## Features
- Monitors water levels accurately
- Indicates water levels through serial monitor or other means
- Simple and easy to build
- Low-cost components

## Uses
- Automating water level monitoring
- Preventing tank overflows
- Maintaining aquarium water levels
- Managing irrigation systems
- Detecting potential flooding
