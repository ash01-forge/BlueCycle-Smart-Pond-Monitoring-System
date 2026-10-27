# BlueCycle Smart Pond Monitoring and Control System

BlueCycle is an IoT-based smart pond monitoring and control system designed for fish ponds, hatcheries, and commercial aquaculture farms. The system monitors important water quality parameters and performs automatic control actions to keep the pond environment safe for fish.

## Project Idea

Traditional pond monitoring is mostly manual, time-consuming, and sometimes inaccurate. Fish farmers may not detect unsafe water conditions at the right time. Unsafe pH, high temperature, dirty water, or abnormal water level can affect fish health and productivity.

BlueCycle solves this problem by using sensors, microcontrollers, relay-controlled pumps, LCD display, buzzer alert, servo feeding system, and a local WiFi dashboard.

## Main Features

- Real-time pH monitoring
- Temperature monitoring using DS18B20 sensor
- Turbidity detection for water clarity
- Ultrasonic water level monitoring
- Automatic pump control using relay module
- Acid and base dosing pump control
- Oxygen/air pump control
- Water pump control based on water level
- Scheduled fish feeding using servo motor
- Buzzer alert for unsafe conditions
- LCD display for local monitoring
- ESP32 WiFi web dashboard

## Hardware Components

- ESP32
- Arduino UNO
- pH Sensor
- DS18B20 Waterproof Temperature Sensor
- Turbidity Sensor
- Ultrasonic Sensor
- 4 Channel Relay Module
- Servo Motor
- Water Pump
- Acid Dosing Pump
- Base Dosing Pump
- Air/Oxygen Pump
- Buzzer
- 16x2 I2C LCD
- Power Supply
- Wires, Tubes, and Prototype Box

## System Working Principle

The ESP32 works as the main controller and creates a local WiFi dashboard. The Arduino UNO is used as an I2C pH reading unit to provide stable pH data to the ESP32.

The system reads pH, temperature, turbidity, and water level. Based on these readings, the system can automatically activate pumps and buzzer alerts.

For example:

- If pH is too low, the base dosing pump can be activated.
- If pH is too high, the acid dosing pump can be activated.
- If temperature is high, the oxygen pump can be activated.
- If turbidity is high, the system detects dirty water.
- If water level is unsafe, the water pump can be controlled.
- If unsafe condition occurs, the buzzer gives an alert.
- The servo motor is used for scheduled fish feeding.

## Real-Life Application

This project can be used in:

- Fish ponds
- Hatcheries
- Commercial aquaculture farms
- Research water tanks
- Smart aquarium systems
- Small-scale pond management systems

## Innovation and Novelty

BlueCycle is not only a monitoring system. It also takes automatic action. It combines real-time water quality monitoring, automatic pump control, scheduled fish feeding, buzzer alert, LCD display, and WiFi dashboard in one low-cost prototype.

This makes the system useful for smart and sustainable aquaculture.

## Errors Faced and Solutions

| Problem | Reason | Solution |
|---|---|---|
| pH sensor was unstable with ESP32 | ESP32 analog reading was noisy | Arduino UNO was used as pH I2C bridge |
| Turbidity value was showing wrong result | Wrong baseline calibration | Sensor was calibrated in normal pond water |
| Ultrasonic sensor sometimes showed 0 cm | Wiring or echo reading issue | TRIG/ECHO wiring and distance logic were checked |
| Relay ON/OFF confusion | Relay active HIGH/LOW behavior | Relay logic was tested and fixed |
| Servo kept rotating | 360 servo stop value mismatch | Adjustable stop value and timed control were added |
| Pump needed external power | ESP32 cannot drive pump directly | Relay and external supply were used |

## Future Scope

- Mobile app integration
- Cloud data logging
- Solar power support
- Dissolved oxygen sensor
- Ammonia sensor
- TDS sensor
- Waterproof PCB and enclosure
- AI-based fish health risk prediction
- Long-term water quality data graph

## Source Code

This repository contains:

- ESP32 main dashboard and control code
- Arduino UNO pH I2C code
- Project README documentation

## Project Goal

The main goal of BlueCycle is to make pond monitoring easier, faster, and more automated for fish farmers and aquaculture users.

---

## Portfolio and Project Team

**Portfolio maintained by [Adeeb Sharar](https://github.com/ash01-forge).**

BlueCycle is presented in the project showcase as **Group 2, Department of Computer Science and Engineering, United International University**. The team members are Nahid Hasan, Adeeb Sharar, Farhan Labib, Tanvir Rifat, and Sakila Anjum Jinat. See [TEAM.md](TEAM.md) for the team list. Existing team credits and the copyright notice remain in the showcase.

## Files in This Repository

| File | Purpose |
| --- | --- |
| BlueCycle_ESP32_Main_Code.ino | Main ESP32 firmware, local dashboard, sensor processing, and actuator control |
| Arduino_UNO_pH_I2C_Code.ino | Arduino UNO pH sensor and I2C bridge firmware |
| index.html | Standalone project showcase with a simulated dashboard |
| SETUP.md | Preview instructions, library dependencies, board setup, and code pin assignments |
| TEAM.md | Project team credits |

## Preview the Showcase

Download the repository, extract it, and open **index.html** in a browser. The embedded video needs internet access.

The standalone HTML dashboard uses simulated readings. It does not connect to physical sensors. The live local dashboard is embedded in the ESP32 firmware and is accessed through the running board.

## Firmware Setup

Follow [SETUP.md](SETUP.md) to prepare the boards. The two .ino files are separate programs for different boards. Before opening them in Arduino IDE, place each in its own folder matching that file’s name without the .ino extension.

The ESP32 firmware uses WiFi, WebServer, Wire, LiquidCrystal_I2C, OneWire, DallasTemperature, and ESP32Servo. The UNO sketch uses Wire. Board-core libraries and third-party libraries should be installed for the actual hardware configuration.

## Demo Mode and Validation

The supplied ESP32 source starts with demoMode = true. The standalone showcase is a simulation; cloud logging, mobile app integration, and AI-based risk prediction remain future directions.

The firmware files were preserved unchanged during packaging. File integrity and showcase JavaScript syntax were checked. Firmware compilation, flashing, sensor accuracy, and actuator operation were not tested during packaging. Check calibration, signal voltage compatibility, relay polarity, and the actual hardware configuration before operation.
