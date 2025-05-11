# InternshipAssessment
ESP32-Based Heater Control System:
This project implements a simple temperature-based heater control system using an NTC thermistor and an ESP32 microcontroller. The system simulates real-world thermal regulation by turning a heater ON or OFF based on temperature thresholds. It also provides live feedback through LED indicators and serial communication.

Features:
Reads temperature from an NTC thermistor connected in a voltage divider circuit.
Uses a state machine to track the heating process through five states: IDLE, HEATING, STABILIZING, TARGET REACHED, and OVERHEAT.
Controls a heater (or relay) through GPIO 25.
Provides visual feedback using an LED connected to GPIO 26.
Triggers an overheat alert using the onboard LED on GPIO 2.
Logs temperature readings and system state over the serial monitor (baud rate: 115200).
Uses non-blocking code with millis() for smooth and responsive behavior.

Hardware Setup:
ESP32 – Microcontroller board.
NTC Thermistor (10kΩ) – Temperature sensor. Connected as part of a voltage divider with a 10kΩ resistor to provide an analog input to GPIO 34.
Heater or Relay Module – Controlled by GPIO 25. Represents the heating element.
LED (Status Indicator) – Connected to GPIO 26 with a 220Ω resistor. Indicates system state (e.g., ON, blinking slow/fast).
Onboard LED (Overheat Alert) – Located on GPIO 2, lights up when overheating is detected.

System Behavior:
When the temperature is below 55°C, the system enters the HEATING state and turns on the heater.
When the temperature reaches 60°C, the system transitions to STABILIZING and turns off the heater.
When the temperature remains within the target range, the system enters the TARGET REACHED state.
If the temperature exceeds 75°C, the system triggers the OVERHEAT state, shuts off the heater, and lights up the overheat LED.
A feedback LED provides visual cues for each state (solid, blinking slow, blinking fast).
All temperature readings and state transitions are printed over the Serial Monitor.

Customization Options:
Temperature thresholds (TEMP_LOW, TEMP_TARGET, TEMP_OVERHEAT) can be adjusted for different use cases.
Additional features such as BLE control, heating profiles, or PID-based temperature regulation can be integrated.
Button inputs and display modules (LCD/OLED) can be added for user interface enhancements.
