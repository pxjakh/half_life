# PCB

Create the KiCad project in **this folder** (name it `Starbie`), so the project files sit next to `libs/`.

## Installing the libraries

In KiCad, add these from `libs/` as project-specific libraries:

- **Preferences → Manage Symbol Libraries → Project Specific Libraries →** add `libs/Seeed_Studio_XIAO_Series.kicad_sym`.
- **Preferences → Manage Footprint Libraries → Project Specific Libraries →** add the `libs/Imported Parts.pretty` folder.

Use a path like `${KIPRJMOD}/libs/...` so the project still works when cloned on another computer.

## Schematic checklist

| Ref | Symbol | Footprint |
| --- | --- | --- |
| U1 | Seeed_Studio_XIAO_Series:XIAO-ESP32-C3-SMD | Imported Parts:XIAO-ESP32-C6-DIP |
| SW1, SW2 | Switch:SW_Push | Button_Switch_Keyboard:SW_Cherry_MX_1.00u_PCB |
| J1 | Connector:Conn_01x04_Pin (OLED) | Imported Parts:Display_128x64_096_I2C |
| J2 | Connector:Conn_01x08_Pin (MPU6050) | Connector_PinHeader_2.54mm:PinHeader_1x08_P2.54mm_Vertical |
| U2 | Sensor:DHT11 | Sensor:Aosong_DHT11_5.5x12.0_P2.54mm |
| R1 | Device:R, 10k (DHT11 pull-up) | Resistor_THT:R_Axial_DIN0204_L3.6mm_D1.6mm_P7.62mm_Horizontal |

### Nets

| Net | Connects |
| --- | --- |
| `+5V` | XIAO 5V |
| `+3.3V` | XIAO 3V3, OLED VCC, MPU6050 VCC, DHT11 VDD, R1 pin 1 |
| `GND` | XIAO GND, OLED GND, MPU6050 GND, DHT11 GND, SW1 pin 2, SW2 pin 2 |
| `SDA` | XIAO D4, OLED SDA, MPU6050 SDA |
| `SCL` | XIAO D5, OLED SCL, MPU6050 SCL |
| `DHT` | XIAO D1, DHT11 DATA, R1 pin 2 |
| `BTN1` | XIAO D2, SW1 pin 1 |
| `BTN2` | XIAO D3, SW2 pin 1 |

MPU6050 pins XDA, XCL, AD0 and INT stay unconnected. Add a "no connect" flag (press Q) to each. The buttons need no resistors because the firmware uses the ESP32's internal pull-ups.

**Check the OLED pin order on your actual module** (GND-VCC-SCL-SDA vs. VCC-GND-SCL-SDA). Clones differ, and getting it wrong swaps power and ground.

## Before you submit

- [ ] DRC shows no errors, apart from the two the guide says to ignore
- [ ] Some art added with the Image Converter
- [ ] Gerbers + drill files exported, zipped, and saved in `/Gerbers`
- [ ] A screenshot of the schematic, the PCB and the 3D view added to the repo
