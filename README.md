# Latching-switch-digital-and-analog-sensor
(1)Project: On/Off Latching Switch Circuit

Project Concept:

This project is an electronic circuit based on a 555 timer that functions as an on/off latch switch. A single button is used to turn an electrical load (such as a lamp or fan) on and off without the need for a permanent mechanical switch.

When the button is pressed, the 555 timer is activated, generating an on signal. This triggers a transistor that drives a relay, turning the load (in this example, a lamp) on. When pressed again, the signal is turned off and the load is turned off.

⸻

Project Components:
• 555 Timer (NE555)
• Push Button
• Resistors: 10kΩ x2, 100kΩ, 1kΩ, 220Ω
• Capacitor: 100µF
• 1N4007 Diode
• 2N2222A Transistor
• 9V Relay
• Green LED as Indicator
• 9V and 12V Power Supplies
• Electrical Load (12V Lamp)

⸻

Circuit Operation Explanation:
1. When the button connected to pin 2 (TRIG) of the 555 timer is pressed, the voltage is pulled to a low level (LOW).
2. This turns the timer on and activates the output (pin 3), turning it HIGH.
3. The signal from pin 3 activates the 2N2222A transistor, which in turn closes the relay circuit and turns on the load.
4. The load remains on until the circuit is re-energized.
5. The button acts as an on/off switch—each press changes the operating state.

⸻

Why is this project useful?
• Allows electrical loads to be controlled with just one button (on/off).
• Reduces the use of complex mechanical switches.
• Useful in applications such as smart lighting, automation systems, and home automation.
• Easy to install and uses common components.

⸻

Steps to Work:
1. Build the circuit in Proteus as shown in the image:
• Ensure the on/off button is connected between pin 2 and GND.
• Use the correct resistors and values according to the circuit.
• Connect the transistor to the relay to turn on the load.
2. Run the simulation:
• When the button is pressed, the lamp and LED light up.
• When pressed again, it turns off.
3. Performance Test:
• Ensure the LED is working as an output status indicator.
• The relay operates stably when pressed.
——————————————————————-
(2)Project: Design and Programming of Digital and Analog Sensors
https://www.tinkercad.com/things/8SMaZTAXOwe-irldr-sensors-?sharecode=SYKMI4-piLo5tZvxE5VzrxkAf03d6ogkzcIS05hDQWE

Project Overview:

In this project, I designed a system that reads data from two types of sensors:
• Digital sensor
• Analog sensor

I then programmed a microcontroller such as the Arduino uno to read these values, process them, and display them on a screen or use them to activate other devices (such as an LED, fan, alarm, etc.)

1. Project Components:
Arduino uno
Breadboard
IR sensor (digital)
LDR sensor (analog)
Resistor (220Ω, 10kΩ)
LED
Wires
2. Project Outputs:
• When the system is powered on,
• The digital sensor is read (for example, detecting the presence of an object or reading a ready temperature).
• The analog sensor is read (for example, measuring the light intensity or the analog temperature).
• Values are displayed on the screen or on a serial port.

3. Project Applications:
• Security systems (motion detector + light sensor)
• Smart home projects (lighting control based on external lighting)
• Robotics (obstacle detection and environmental analysis)
• Environmental monitoring (temperature, humidity, light)

⸻

4. Educational Benefits:
• I learned the difference between digital and analog sensors.
• I learned how to connect and program each type.
• I understood how to handle and analyze different signals.
• I connected electronics to programming to fully control the surrounding environment.

5.code:

const int digitalPin = 2;    // IR sensor
const int analogPin = A0;    // LDR
const int ledPin = 8;

void setup() {
  Serial.begin(9600);
  pinMode(digitalPin, INPUT);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  int irValue = digitalRead(digitalPin);
  int ldrValue = analogRead(analogPin);

  Serial.print("IR Sensor: ");
  Serial.println(irValue);

  Serial.print("LDR Value: ");
  Serial.println(ldrValue);

  // Example condition: Turn on LED if both are triggered
  if (irValue == 1 && ldrValue < 500) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }
  delay(500);
  }
