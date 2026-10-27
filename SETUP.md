# BlueCycle setup

## 1. View the project showcase

Open `index.html` in a browser. Its dashboard is a simulation and makes no sensor API requests. It is separate from the live dashboard embedded in the ESP32 firmware. Opening this HTML page does not flash or run either microcontroller program.

## 2. Prepare the two Arduino sketches

The upload package keeps all files together to make browser uploads simple. For Arduino IDE use, copy the firmware files into two separate folders:

```text
BlueCycle_ESP32_Main_Code/
  BlueCycle_ESP32_Main_Code.ino

Arduino_UNO_pH_I2C_Code/
  Arduino_UNO_pH_I2C_Code.ino
```

Open each sketch separately. Do not place both `.ino` files in one sketch folder: they target different boards and each defines its own program. The folder must match the primary `.ino` filename; see the [Arduino sketch specification](https://docs.arduino.cc/arduino-cli/sketch-specification/).

## 3. Install board support and libraries

In Arduino IDE, install board support appropriate to the physical ESP32 board and Arduino UNO. Select the matching board and serial port before each upload.

The ESP32 source includes these external library headers:

- `LiquidCrystal_I2C.h`
- `OneWire.h`
- `DallasTemperature.h`
- `ESP32Servo.h`

`WiFi.h`, `WebServer.h`, and `Wire.h` are supplied with the relevant board core. The UNO sketch uses `Wire.h`. Exact third-party library versions were not recorded in the supplied source, so compilation should be checked with the versions installed for the actual build.

## 4. Check the hardware configuration

The following assignments are read from the supplied ESP32 source. They are code settings, not a verified wiring schematic.

| Function | ESP32 GPIO |
| --- | --- |
| DS18B20 data | 4 |
| Turbidity analog input | 35 |
| Ultrasonic trigger / echo | 18 / 34 |
| Buzzer | 23 |
| Servo | 13 |
| Servo home / target switches | 16 / 17 |
| Acid / oxygen relays | 25 / 26 |
| Base / water relays | 27 / 14 |
| LCD I2C SDA / SCL | 21 / 22 |
| UNO pH bridge I2C SDA / SCL | 32 / 33 |

The UNO source uses analog input A0 for pH and I2C address 8. Review the source and actual wiring, including signal voltage levels, power, grounds, relay behavior, and calibration, before connecting actuators. The ESP32 defines `PH_PIN` as 34 as well; the active pH bridge configuration and ultrasonic use should be reviewed rather than treating that define as an additional wiring instruction.

## 5. Demo and local dashboard

The ESP32 source starts with `demoMode = true`. The configured demo access point is `BlueCycle_Demo`, with example password `12345678`. These are demonstration settings in the source.

After flashing and starting the board, join its access point and open the board’s AP IP address in a browser. Confirm the address from the running board instead of assuming the standalone `index.html` provides live hardware access.

## Verification status

The two firmware files are unchanged in this upload package. File integrity and showcase JavaScript syntax were checked. Firmware compilation, flashing, sensor measurements, and actuator operation were not tested during packaging.
