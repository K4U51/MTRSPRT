This board includes built-in LiPo battery charging, 3.3V logic, and USB-C, which eliminates the need for a separate charger and voltage regulator.

⸻

🧰 FoxLAP GPS Lap Timer - Simplified BOM

Optimized for Efficiency, Performance, and Assembly
(Now using Feather ESP32 V2 with built-in battery charging)

Qty	Component	Description	Product Link
1	ESP32 Board	Adafruit Feather ESP32 V2 with USB-C & LiPo charging	Adafruit 5400
1	GNSS Module	Ultimate GPS Breakout – 66 channel / 10 Hz	Adafruit 746
1	OLED Display	2.42” 128x64 SPI Monochrome OLED	Adafruit 2719
1	MicroSD Breakout	SPI MicroSD breakout for data logging	Adafruit 254

🔋 Battery + Charging (Simplified)

Qty	Component	Description	Product Link
1	Li-Ion Battery	3.7V 2200mAh Lithium Polymer Battery	Adafruit 1781
1	Slide Switch	Inline power control (connected to EN pin or battery line)	Adafruit 805

Note: Charging is handled automatically by the Feather ESP32 V2 over USB-C. Just plug in to charge and run.

⏺ Input Controls

Qty	Component	Description	Product Link
4	Tactile Push Buttons	6mm momentary switches (x4)	Adafruit 367
2	10KΩ Resistors	Pull-up resistors for buttons	Adafruit 2784
4	1KΩ Resistors	Series resistors or debouncing	Adafruit 2782

🧱 Enclosure + Assembly

Qty	Component	Description	Source
1	3D Printed Case	STL for main housing	FoxLAP Case STL
1	3D Printed Mount	STL for mounting system	FoxLAP Mount STL
-	Wires / Jumpers	22–26 AWG flexible hookup wire	Adafruit / Amazon
-	Heat Shrink / Screws	Optional for cable cleanup and mounting	Hardware store

✅ Benefits of the Feather ESP32 V2 Upgrade:
	•	USB-C with built-in LiPo charging and protection
	•	3.3V regulated power rail onboard
	•	One board = fewer wires, fewer connections, and less assembly time
	•	More space in enclosure and cleaner cable routing
	•	Easy firmware upload and serial monitor with built-in USB-C

🔌 2. Assemble the Hardware

Wiring Overview:
	•	GPS Module:
	•	Connect GPS TX to ESP32 RX (e.g., GPIO16).
	•	Connect GPS RX to ESP32 TX (e.g., GPIO17).
	•	Power the GPS module with 3.3V and GND.
	•	OLED Display (SPI):
	•	Connect SCK to ESP32 SCK (e.g., GPIO18).
	•	Connect MOSI to ESP32 MOSI (e.g., GPIO23).
	•	Connect DC, CS, and RST to available GPIOs (e.g., GPIO27, GPIO5, GPIO33).
	•	Power the display with 3.3V and GND.
	•	MicroSD Card Breakout (SPI):
	•	Share SCK and MOSI lines with the OLED display.
	•	Connect CS to a separate GPIO (e.g., GPIO32).
	•	Power the SD card breakout with 3.3V and GND.
	•	Buttons:
	•	Connect one side of each button to a GPIO (e.g., GPIO12–GPIO15).
	•	Connect the other side to GND.
	•	Use 10KΩ pull-up resistors between each GPIO and 3.3V.
	•	Optionally, add 1KΩ series resistors for debouncing.
	•	Power System:
	•	Connect the LiPo battery to the Feather’s JST connector.
	•	Optionally, wire the slide switch between the EN pin and GND for power control.

Assembly Tips:
	•	Use heat shrink tubing to insulate exposed wires.
	•	Secure components inside the 3D printed case using screws or adhesive.
	•	Ensure all connections are solid to withstand vibrations during use.

💻 3. Set Up the Software Environment

Install Arduino IDE:
	1.	Download and install the Arduino IDE.

Configure ESP32 Board Support:
	1.	Open Arduino IDE.
	2.	Go to File > Preferences.
	3.	In the “Additional Board Manager URLs” field, add:

	https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

4.	Click “OK”.

Install ESP32 Board Package:
	1.	Go to Tools > Board > Boards Manager.
	2.	Search for “esp32” and install the latest version.

Select the Board and Port:
	1.	Go to Tools > Board and select “Adafruit Feather ESP32 V2”.
	2.	Connect your Feather ESP32 V2 via USB-C.
	3.	Go to Tools > Port and select the appropriate COM port.

🧠 4. Program the Device

Install Required Libraries:
	1.	Go to Sketch > Include Library > Manage Libraries.
	2.	Install the following libraries:
	•	Adafruit GPS Library
	•	Adafruit SSD1306
	•	Adafruit GFX Library
	•	SD
	•	SPI

Upload Sample Code:
	1.	Open a new sketch in Arduino IDE.
	2.	Copy and paste the following sample code:

// Sample code to initialize GPS, OLED, and SD card
// Replace with actual implementation as needed

	#include <Adafruit_GPS.h>
	#include <Adafruit_SSD1306.h>
	#include <SD.h>
	#include <SPI.h>

	// Define pins and initialize peripherals here

	void setup() {
	  // Initialize Serial, GPS, OLED, SD card
	}
	
	void loop() {
	  // Read GPS data
	  // Display on OLED
	  // Log to SD card
	}

3.	Customize the code to implement lap timing functionality.
	4.	Click the “Upload” button to program the ESP32.

🔋 5. Power and Test the Device

Charging the Battery:
	•	Connect the Feather ESP32 V2 to a USB-C power source.
	•	The onboard charger will handle battery charging automatically.

Testing:
	1.	Disconnect USB-C and power the device using the LiPo battery.
	2.	Ensure the OLED displays GPS data.
	3.	Verify that lap times are being logged to the SD card.
	4.	Test button functionality for user inputs.

🏁 6. Deploy and Use
	•	Mount the device securely on your vehicle using the 3D printed mount.
	•	Ensure the GPS module has a clear view of the sky for accurate positioning.
	•	Start recording lap times and analyze the data post-session.

# 🏁 FoxLAP DIY - ESP32 Feather V2 Edition

A DIY GPS lap timer and data logger built using the Adafruit Feather ESP32 V2. Designed for karting, motorbikes, and racing telemetry. This project replicates the original FoxLAP firmware wiring but swaps in all-Adafruit hardware for a compact, well-documented build.

---

## 📦 Parts List (All from [Adafruit](https://www.adafruit.com))

### 🧠 Core Components

| Component | Purpose | Part # | Qty |
|----------|---------|--------|-----|
| [Feather ESP32 V2](https://www.adafruit.com/product/5400) | Main MCU | 5400 | 1 |
| [LiPo Battery (1200mAh)](https://www.adafruit.com/product/1578) | Portable power | 1578 | 1 |
| [USB Cable A to C](https://www.adafruit.com/product/4474) | Power + programming | 4474 | 1 |

### 📡 Modules & Sensors

| Component | Purpose | Part # | Qty |
|----------|---------|--------|-----|
| [Ultimate GPS Module](https://www.adafruit.com/product/746) | GNSS | 746 | 1 |
| [1.8" TFT SPI Display (ST7735)](https://www.adafruit.com/product/358) | Screen | 358 | 1 |
| [MicroSD Breakout (SPI)](https://www.adafruit.com/product/254) | Logging | 254 | 1 |
| [Tactile Buttons (x4)](https://www.adafruit.com/product/367) | Input | 367 | 4 |

### 🧵 Wires, Tools, and Prototyping

| Component | Purpose | Part # |
|----------|---------|--------|
| [Jumper Wires (M-F)](https://www.adafruit.com/product/1956) | Wiring modules | 1956 |
| [Jumper Wires (M-M)](https://www.adafruit.com/product/759) | Breadboarding | 759 |
| [Solderless Breadboard](https://www.adafruit.com/product/64) *(optional)* | Testing | 64 |
| [Feather Header Kit](https://www.adafruit.com/product/2886) | Soldering | 2886 |

### 🔌 Optional Add-ons

| Component | Purpose | Part # |
|----------|---------|--------|
| [Feather OLED Wing](https://www.adafruit.com/product/5517) | Debug display | 5517 |
| [FeatherWing Tripler](https://www.adafruit.com/product/3500) | Feather stacking | 3500 |

---

## 🔌 Wiring Reference

| Feather GPIO | Function | Connects To |
|--------------|----------|-------------|
| GPIO18 | SPI CLK | Display SCK |
| GPIO19 | SPI MISO | SD MISO |
| GPIO23 | SPI MOSI | Display & SD MOSI |
| GPIO5  | Display CS | Display |
| GPIO22 | Display DC | Display |
| GPIO21 | Display RST | Display |
| GPIO17 | GPS RX | GPS TX |
| GPIO16 | GPS TX | GPS RX |
| GPIO13 | SD CS | SD Card |
| GPIO14 | SD CLK | SD Card |
| GPIO15 | SD MOSI | SD Card |
| GPIO2  | SD MISO | SD Card *(Safe at boot)* |
| GPIO25/26/27 | Buttons | Up / Down / OK |

---

## ⚙️ Flashing the Firmware

> **⚠️ License Note:** FoxLAP firmware is closed-source and may prohibit modification or redistribution. Ensure you're legally allowed to flash it.

1. Install [esptool](https://github.com/espressif/esptool):
	   ```bash
   pip install esptool

	Flash with the following command:
		esptool.py --chip esp32 write_flash -z \
		  0x1000   foxlap.DIY.bootloader.bin \
		  0x8000   foxlap.DIY.partitions.bin \
		  0xe000   boot_app0.bin \
		  0x10000  foxlap.DIY.bin
