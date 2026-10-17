# Starbie - ESP32-C3 Virtual Pet PCB

**Starbie** is a star-shaped interactive desktop companion PCB powered by the Seeed Studio XIAO ESP32C3 microcontroller. Featuring an OLED display, motion/tilt control via an IMU, environmental tracking, and custom tactile buttons, Starbie functions as an animated virtual pet with responsive behaviors and radial menu controls.

---

## Project Structure

```text
starbie/
├── Hardware/        # KiCad PCB design, schematic, and artwork assets
├── Fabrication/     # Gerber & drill files prepared for PCB manufacturing
└── Firmware/        # Arduino firmware (Starbie/Starbie.ino)
```

---

## Hardware Specifications & Bill of Materials

* **Microcontroller:** Seeed Studio XIAO ESP32C3
* **Display:** 0.96" I2C Monochrome OLED Display ($128 \times 64$ resolution, SSD1306)
* **Motion Sensor:** MPU6050 6-Axis Gyroscope & Accelerometer
* **Environmental Sensor:** DHT11 Temperature & Humidity Sensor
* **Input Controls:** 2x Tactile Pushbuttons
* **Pull-up Resistor:** $10\text{k}\Omega$ (0805 or Through-Hole)
* **Form Factor:** Star-shaped PCB outline with custom silkscreen artwork

### Pin Mapping

| Component Net | XIAO Label | ESP32-C3 GPIO | Description |
| :--- | :--- | :--- | :--- |
| **I2C SDA** | `D4` | `GPIO6` | OLED & MPU6050 Data Line |
| **I2C SCL** | `D5` | `GPIO7` | OLED & MPU6050 Clock Line |
| **DHT11 Data** | `D1` | `GPIO3` | Temperature / Humidity Signal |
| **Button 1** | `D2` | `GPIO4` | Menu Trigger / Select |
| **Button 2** | `D3` | `GPIO5` | Stats Screen Toggle |

---

## Software & Flashing Guide

### 1. Requirements & Board Support
1. Download and install [Arduino IDE](https://www.arduino.cc/en/software).
2. Go to **File > Preferences** and add the Espressif Board Manager URL:
   ```text
   https://espressif.github.io/arduino-esp32/package_esp32_index.json
   ```
3. Open **Tools > Board > Boards Manager**, search for `esp32`, and install **esp32 by Espressif Systems**.
4. Set board target under **Tools > Board > esp32 > XIAO_ESP32C3**.

### 2. Required Libraries
Open **Sketch > Include Library > Manage Libraries** and install:
* `Adafruit GFX Library`
* `Adafruit SSD1306`
* `Adafruit MPU6050`
* `DHT sensor library`

*(Select "Install All" if prompted for dependencies).*

### 3. Compiling & Uploading
1. Open `Firmware/Starbie/Starbie.ino` in Arduino IDE.
2. Connect your XIAO ESP32C3 via USB-C and select its COM port under **Tools > Port**.
3. Click **Upload** (`Ctrl + U`).

---

## Controls & Features

* **Button 1 (First Press):** Opens the 4-direction radial menu.
* **Tilt (IMU):** Move the star to direct the selector ball in the radial menu.
* **Button 1 (Second Press):** Confirms the selected action (**NAP**, **PLAY**, **FEED**, **PET**).
* **Button 2:** Toggles the background stats screen (Temperature & Humidity).
* **Shake:** Triggers Starbie's interactive shake reaction.

---

## Customization

You can personalize Starbie's behaviors under the `BEGINNER SETTINGS` block at the top of `Starbie.ino`:
* **Menu Items:** Edit names and stat changes in `MENU_ITEMS[]`.
* **Custom Artwork:** Replace `PET_SPRITE[]` with custom 1-bit byte array bitmaps converted via [image2cpp](https://javl.github.io/image2cpp/).

---

## Bill of Materials (BOM)

| Part | Description / Function | Qty | Unit Price (USD) | Total Price (USD) | Vendor |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Seeed Studio XIAO ESP32-C3** | Main microcontroller running the code | 1 | $7.74 | $7.74 | [robu.in](https://robu.in/product/seeed-studio-xiao-esp32c3-tiny-mcu-board-with-wi-fi-and-ble-battery-charge-supported-power-efficiency-and-rich-interface/) |
| **0.96" OLED Screen (128x64 I2C)** | Displays text and project data | 1 | $1.93 | $1.93 | [thingbits.in](https://www.thingbits.in/products/0-96-inch-oled-128x64-display-board-with-i2c) |
| **DHT11 Sensor** | Measures temperature and relative humidity | 1 | $1.54 | $1.54 | [robu.in](https://robu.in/product/dht-11-digital-temperature-and-humidity-sensor/) |
| **Mechanical Keyboard Switches** | User input and button presses | 1 | $9.26 | $9.26 | [amazon.in](https://www.amazon.in/piercing-Mechanical-Keyboard-Switches-Universal/dp/B0G39H2G4H/) |
| **10 kΩ Resistor Pack** | Pulls up the data line | 1 | $0.12 | $0.12 | [amazon.in](https://www.amazon.in/Electronic-Spices-Tolerance-Through-Resistors/dp/B0BDV2T3PX/) |
| **GY-521 MPU6050** | Detects motion and board orientation | 1 | $2.77 | $2.77 | [amazon.in](https://www.amazon.in/Robocraze-MPU-6050-Gyroscope-Accelerometer-Arduino/dp/B07H3XH1TB/) |
| **1x40 Female Header Strip** | Socket connectors for plug-in modules | 1 | $0.13 | $0.13 | [robu.in](https://robu.in/product/1-40-pin-2-54m-straight-long-female-berg-strip-connector-pack-of-5/) |
| **1x40 Male Header Strip (3 Pack)** | Pin connectors for module wiring | 1 | $0.18 | $0.18 | [robu.in](https://robu.in/product/2-54mm-1x40-pin-male-single-row-straight-long-header-strip-pack-of-3/) |
| **Tax & Shipping** | Estimated shipping and handling for order | — | — | $1.86 | — |
| **TOTAL** | | | | **$25.53** | |

---

## Starbie PCB Photos

![Starbie PCB Render](Hardware/Assets/starbie_render.png)
![Starbie PCB Schematic](Hardware/Assets/starbie_schematic.png)
![Starbie PCB Design](Hardware/Assets/starbie_pcb_design.png)