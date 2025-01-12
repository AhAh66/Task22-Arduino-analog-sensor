# **Analog Sensor Example Using Arduino (LDR and LED)**

This example demonstrates how to use an analog sensor with an Arduino. The analog sensor used is an LDR (Light Dependent Resistor) that measures the light intensity. Based on the detected light level, the Arduino controls the LED to turn ON or OFF using a predefined threshold.

---

## **How It Works**

1. The LDR is connected to a voltage divider circuit to produce an analog signal proportional to the light intensity.
2. The analog signal is read by the Arduino via pin `A0`.
3. The program compares the sensor value to a threshold (500):
   - If the light level is below the threshold (low light), the LED turns ON.
   - If the light level is above the threshold (bright light), the LED turns OFF.
4. The sensor readings are printed on the Serial Monitor in real-time for debugging or monitoring.

---

## **Circuit Diagram**

### **Components Needed**
- Arduino board
- LDR (Light Dependent Resistor)
- 10kΩ resistor
- LED
- 220Ω resistor
- Breadboard and jumper wires

### **Connections**
- **LDR Circuit**: One terminal to `5V`, the other to a 10kΩ resistor. The junction between the LDR and resistor connects to `A0` on the Arduino.
- **LED Circuit**: Positive leg (anode) to pin `8` via a 220Ω resistor, negative leg (cathode) to `GND`.

#### **Tinkercad Link**
[Tinkercad Project Link](https://www.tinkercad.com/things/cm2purS069r-analog-sensor/editel?returnTo=%2Fdashboard%2Fdesigns%2Fcircuits&sharecode=KsQrry4k7m5rRoSADLwFb3rqqjC0vzIGVMFp6Oyn88M)

---

## **Code**

```cpp
const int sensorPin = A0;   // LDR connected to analog pin A0
const int ledPin = 8;       // LED connected to digital pin 8
int sensorValue = 0;        // Variable to store the analog reading
const int threshold = 500;  // Threshold for light detection

void setup() {
  pinMode(ledPin, OUTPUT);  // Set the LED pin as OUTPUT
  Serial.begin(9600);       // Start Serial Monitor
}

void loop() {
  sensorValue = analogRead(sensorPin);  // Read analog input
  Serial.println(sensorValue);          // Print value to Serial Monitor

  if (sensorValue < threshold) {
    digitalWrite(ledPin, HIGH);         // Turn LED ON
  } else {
    digitalWrite(ledPin, LOW);          // Turn LED OFF
  }
  
  delay(100);  // Small delay for stability
}


##**Example Demonstration**
	1.	Place the circuit components as per the diagram.
	2.	Upload the code to the Arduino board.
	3.	Open the Serial Monitor (set baud rate to 9600) to observe live readings.
	4.	Test by covering the LDR (to simulate darkness) and observe the LED turning ON.

Project Images
	1.	Circuit Diagram

	2.	Code Overview

Applications
	•	Smart lighting systems.
	•	Light-sensitive devices for energy efficiency.
	•	Real-world examples like automatic streetlights.

