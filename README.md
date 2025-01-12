
https://github.com/user-attachments/assets/375d8b54-669e-48fe-a8b2-b2f66e166712

https://github.com/user-attachments/assets/29bf8c2f-1297-4457-8280-c4e90d14c3f6
# **Analog Sensor Example Using Arduino (LDR and LED)**

This example demonstrates how to use an analog sensor with an Arduino. The analog sensor used is an LDR (Light Dependent Resistor) that measures light intensity. Based on the detected light level, the Arduino controls an LED to turn ON or OFF using a predefined threshold.

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
- **LDR Circuit**: One terminal of the LDR is connected to `5V`, the other to a 10kΩ resistor. The junction between the LDR and resistor connects to `A0` on the Arduino.
- **LED Circuit**: The anode (positive leg) of the LED is connected to pin `8` via a 220Ω resistor, and the cathode (negative leg) is connected to `GND`.

#### **Tinkercad Link**
[Tinkercad Project Link](https://www.tinkercad.com/things/cm2purS069r-analog-sensor/editel?returnTo=%2Fdashboard%2Fdesigns%2Fcircuits&sharecode=KsQrry4k7m5rRoSADLwFb3rqqjC0vzIGVMFp6Oyn88M)

---

## **Preview**
Here are some preview images of the circuit design:




*Note: Upload your videos separately or include them as links.*

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
