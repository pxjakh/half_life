# Half Life: Starbie

My Starbie: a 2-button digital pet built on a Seeed XIAO ESP32-C3. It has a 0.96" I2C OLED, an MPU6050 motion sensor and a DHT11 temperature/humidity sensor.

Built by following the [Starbie Week 1 guide](https://github.com/SharKingStudios/Starbie) for Hack Club's Half Life.

## Repository layout

| Folder | What's in it |
| --- | --- |
| [`Firmware/Starbie/`](Firmware/Starbie/Starbie.ino) | Arduino sketch, uploaded to the XIAO ESP32-C3 |
| [`PCB/`](PCB/) | KiCad project (schematic + PCB) |
| [`PCB/libs/`](PCB/libs/) | Symbol, footprint and 3D-model libraries from the Week 1 care package |
| [`Gerbers/`](Gerbers/) | Exported Gerber + drill files for fabrication |

## Bill of materials

| Qty | Part |
| --- | --- |
| 1 | Seeed Studio XIAO ESP32-C3 |
| 1 | 0.96" 128x64 SSD1306 I2C OLED (4-pin) |
| 1 | MPU6050 (GY-521) module |
| 1 | DHT11 temperature/humidity sensor |
| 2 | Cherry MX-style switches + keycaps |
| 1 | 10k resistor (DHT11 data pull-up) |

## Wiring

| Part | XIAO pin | ESP32-C3 GPIO |
| --- | --- | --- |
| OLED SDA + MPU6050 SDA | D4 | GPIO6 |
| OLED SCL + MPU6050 SCL | D5 | GPIO7 |
| DHT11 data | D1 | GPIO3 |
| Button 1 (other side to GND) | D2 | GPIO4 |
| Button 2 (other side to GND) | D3 | GPIO5 |

See [PCB/README.md](PCB/README.md) for the full schematic checklist.

## Firmware

Open `Firmware/Starbie/Starbie.ino` in Arduino IDE. Then:

1. Add `https://espressif.github.io/arduino-esp32/package_esp32_index.json` under **File → Preferences → Additional Boards Manager URLs**.
2. Install **esp32 by Espressif Systems**, then select **XIAO_ESP32C3**.
3. Install these libraries: Adafruit GFX, Adafruit SSD1306, Adafruit MPU6050 and DHT sensor library.
4. Click Upload.

### Controls

| Control | What it does |
| --- | --- |
| Button 1 | Open the radial menu; press again to choose the highlighted action |
| Tilt (menu open) | Move the selector toward NAP / PLAY / FEED / PET |
| Button 2 | Show/hide stats (joy, energy, fullness, temperature, humidity) |
| Shake | Shake reaction (also wakes a napping pet) |

### Customizations

- **Sparkle trail:** a small sparkle blinks behind Starbie while it walks.

## Credits

Starter firmware, footprints and guide by Logan Peterson / [SharKingStudios](https://github.com/SharKingStudios/Starbie) (MIT License).
