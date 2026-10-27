# BlueCycle — Smart Pond Monitoring System

An IoT and robotics prototype for monitoring pond water conditions and coordinating pumps, alerts, and fish feeding. Developed as a university project at United International University (UIU), Department of Computer Science and Engineering.

**Portfolio maintained by [Adeeb Sharar](https://github.com/ash01-forge).** Project team credits are listed in [TEAM.md](TEAM.md) and in the showcase page.

## Overview

BlueCycle combines an ESP32 main controller with an Arduino UNO pH interface. The firmware includes water-quality monitoring, a local Wi-Fi control dashboard, relay-based pump control, a servo feeding mechanism, a buzzer, and a 16×2 I2C LCD.

The repository also includes a standalone HTML showcase with simulated readings. Opening that page does not connect it to physical sensors.

## Features in the firmware

- pH readings supplied by an Arduino UNO over I2C.
- DS18B20 temperature readings, turbidity detection, and ultrasonic water-level measurement.
- Relay control for acid dosing, base dosing, aeration, and water pumping.
- Servo-based feeding with limit-switch inputs.
- LCD status display and buzzer alerts.
- ESP32 access-point mode and an embedded local web dashboard.
- A demo mode for presenting the prototype.

## Repository contents

| File | Purpose |
| --- | --- |
| `BlueCycle_ESP32_Main_Code.ino` | Main ESP32 firmware and embedded dashboard |
| `Arduino_UNO_pH_I2C_Code.ino` | Arduino UNO pH sensor and I2C interface |
| `index.html` | Standalone project showcase and simulated dashboard |
| `SETUP.md` | Preview, dependencies, and board setup notes |
| `TEAM.md` | University project team credits |

## Preview the showcase

Download the repository, extract it, and open **index.html** in a browser. The showcase can be viewed without connecting a board. The embedded video requires internet access.

To operate the hardware, follow [SETUP.md](SETUP.md). Each `.ino` file is a separate program for a different board.

## Technology

**Hardware:** ESP32, Arduino UNO, pH sensor, DS18B20, turbidity sensor, ultrasonic sensor, relay module, pumps, servo, limit switches, buzzer, and I2C LCD.

**Software:** Arduino C++, I2C, ESP32 Wi-Fi/WebServer, HTML, CSS, and JavaScript.

## Prototype status

The firmware is supplied as a prototype. The current ESP32 source starts with `demoMode = true`. Sensor calibration, voltage compatibility, relay polarity, and actuator behavior need to be checked against the actual build before hardware operation. Packaging verification does not establish sensor accuracy or deployment readiness.

## Future directions

Cloud logging, historical graphs, additional water-quality sensors, and AI-assisted risk prediction are potential extensions; they are not presented here as completed features.
