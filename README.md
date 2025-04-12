# MTRSPRT
# 🏁 FoxLAP DIY GPS Lap Timer

Build your own GPS-based lap timer for karting or track racing using an ESP32 and GNSS module. Based on the official [FoxLAP DIY Guide](https://foxlap.com/tutorials/diy-build-your-foxlap-device/).

---

## 📦 Features

- GPS-based lap timing
- SD card data logging
- Wi-Fi firmware updates
- OLED Display
- Data analysis via GPXRender

---

## 🧰 Hardware Requirements

| Quantity | Item                                      | Link |
|----------|-------------------------------------------|------|
| 1 | ESP32 ESP-WROOM-32 Dev Board | [AZ Delivery](https://www.az-delivery.de/en/products/esp32-dev-kit-c-v4) |
| 1 | GNSS Module (SAM-M10Q / Ublox M8N) | [AliExpress](https://www.aliexpress.com/item/10050032748573256.html) |
| 1 | JLX 256×128 COG 5V White SPI Display | [AliExpress](https://www.aliexpress.com/item/10050032748573256.html) |
| 1 | MicroSD Card Module | [AliExpress](https://www.aliexpress.com/item/10050032748573256.html) |
| 1 | Wemos D1 Mini Lithium Battery Charger | [AliExpress](https://www.aliexpress.com/item/10050032748573256.html) |
| 1 | 18650 Li-Ion Battery | [EtronixCenter](https://www.etronixcenter.com/en/18650-li-ion/18650-inr18650-35e-samsung-li-ion-37v-3450mah.html) |
| 1 | Power Switch | [Amazon](https://www.amazon.com/dp/B07P6MZPK3) |
| 4 | Push Buttons (6x6x4mm) | [EverythingPi](https://everythingpi.co.uk/6x6x4mm-tactile-push-button-switch-pack-of-10/) |
| 2 | 10KΩ Resistors | - |
| 4 | 1KΩ Resistors | - |
| - | Wires, Screws, Glue, etc. | - |

---

## 🧩 Assembly

1. Wire the components using the [official wiring diagram](https://foxlap.com/wp-content/uploads/2023/12/FoxLAP.DIY-wiring-1.png)
![image](https://github.com/user-attachments/assets/a5d44ee7-e786-4253-a10a-c4df37811aab)
wires.
![image](https://github.com/user-attachments/assets/70351935-bc68-4ff6-9a51-0b1fdf1f93fd)

2. Download 3D printable [enclosure STL files](https://foxlap.com/wp-content/uploads/2023/12/FoxLAP.DIY-case.STL) and [mount STL](https://foxlap.com/wp-content/uploads/2023/12/FoxLAP.mount.STL)
4. Solder, assemble, and glue per the tutorial images.

---

## 🔄 Flashing Firmware

Download firmware from [FoxLAP DIY Firmware](https://foxlap.com/download/foxlap-diy-firmware/).

### Flash via USB

```bash
esptool.py --chip esp32 --port COM6 --baud 921600 --before default_reset --after hard_reset write_flash -z \
--flash_mode dio --flash_freq 80m --flash_size 4MB \
0x1000 foxlap.DIY.bootloader.bin \
0x8000 foxlap.DIY.partitions.bin \
0xe000 boot_app0.bin \
0x10000 foxlap.DIY.bin
