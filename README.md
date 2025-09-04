# Temperature Controlled Motor

## Project Overview
This project implements a temperature-controlled DC motor using an 8052 Microcontroller (AT89C52). The system adjusts motor speed based on user-defined temperature thresholds and includes safety features like auto-shutdown and emergency reset.



## Objective
Control a DC motor using an 8052 Microcontroller Development board with three speed stages (low, medium, high) based on temperature. Users define minimum, medium, and maximum temperatures. The motor runs at low speed between minimum and medium, medium speed between medium and maximum, and high speed above maximum. If a critical temperature is exceeded, the motor shuts down with an alert.

## Required Components
| Component Name          | Amount | Price (BDT) |
|-------------------------|--------|-------------|
| Double Shaft DC motor   | 3      | 65*3=195    |
| L298N H-bridge Motor Driver | 1  | 183         |
| Jumper Wires            | -      | -           |
| Battery                 | 1      | -           |
| 8052 board              | 1      | 7000 (apprx)|

## Features
### Mandatory Features
1. **Temperature Sensing**: Reads data from an ADC-connected temperature sensor (e.g., LM35) and converts it to digital readings.
2. **Keypad Input for Thresholds**: Users input TMIN, TMED, TMAX via a 4x4 keypad, stored for speed control.
3. **Motor Speed Control**: Adjusts speed based on temperature:
   - T < TMIN: Motor OFF
   - TMIN < T < TMED: LOW speed
   - TMED < T < TMAX: MEDIUM speed
   - T > TMAX: HIGH speed
4. **Critical Temperature Handling**: Stops motor and displays ALERT if T > TCRIT (80H).
5. **LCD Display**: Shows current temperature, speed (e.g., "LOW SPEED"), and alerts.

### Extra Features
1. **Manual Reset Button (in Proteus)**: Restarts system after critical shutdown.
2. **Auto Shutdown Timer**: Shuts down motor after prolonged operation to save power.

## Working Principle
- **Initialize System**: Configures LCD and ports (P0, P1, P2, P3).
- **Get Temperature Limits**: Users enter Tmin, Tmed, Tmax via keypad, stored at 40H, 41H, 42H.
- **Start Reading Temperature**: ADC converts sensor data to digital.
- **Display Temperature**: Shown on LCD in two-digit format.
- **Compare and Control Motor**: Adjusts speed based on thresholds; stops at TCRIT.
- **Auto-Shutdown**: Timer0 triggers shutdown after delay.
- **Emergency Reset**: Hardware button stops motor.
- **Continuous Monitoring**: Loops to read and adjust.

## Problems Faced
- **Software**: Initial keypad setup stored blank values, causing high-speed operation. Resolved by removing start/equal buttons.
- **Hardware**: ADC on the microcontroller board malfunctioned; LM35 sensor failed to detect temperature.

## Conclusion
Based on simulation and hardware progress, the system successfully controls a DC motor based on temperature.

*(Code and detailed diagrams are in the project report PDF.)*
