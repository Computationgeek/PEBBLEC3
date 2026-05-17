# 🍊 FruitWorks PebbleC3

> **Built by makers, for makers.**

![PebbleC3 Board](<img width="1271" height="745" alt="PEBBLEC3FV" src="https://github.com/user-attachments/assets/56a890d8-fbec-438d-8887-76283bf1eec0" />
)

**PebbleC3** is a compact, open-source ESP32-C3 development board designed by [FruitWorks Electronics](https://github.com/fruitworkselectronics). Built as a portfolio and KiCad skill project, it packs native USB, Qwiic/STEMMA QT connectivity, and castellated edges into a small, orange form factor.

---

## ✨ Features

- **ESP32-C3-WROOM-02** — RISC-V single-core @ 160MHz, 4MB Flash, 400KB SRAM, Wi-Fi + BLE 5.0
- **Native USB** — Direct USB-C to ESP32-C3 USB (no CH340 or CP2102), supports CDC/JTAG
- **AP2112K-3.3 LDO** — 600mA, ultra-low dropout (350mV), SOT-23-5
- **Qwiic / STEMMA QT** — JST-SH 4-pin connector for plug-and-play I2C ecosystem
- **Castellated edges** — 8-pin castellated pads on each side, 2.54mm pitch, solderable directly to a carrier board
- **User LED + Power LED** — GPIO-driven user LED (IO3) and always-on power indicator
- **Boot + Reset buttons** — Standard tactile switches for programming and reset
- **Test points** — VOUT and GND test pads for bench probing
- **Open Source Hardware** — Full KiCad project, schematics, and Gerbers available

---

## 📐 Specifications

| Parameter | Value |
|---|---|
| MCU | ESP32-C3-WROOM-02 |
| Clock Speed | 160 MHz |
| Flash | 4MB |
| SRAM | 400KB |
| Connectivity | Wi-Fi 802.11 b/g/n + BLE 5.0 |
| USB | USB-C, Native USB 2.0 (CDC + JTAG) |
| Operating Voltage | 3.3V |
| Input Voltage (VIN) | 3.8V – 6V |
| Input Voltage (USB) | 5V |
| LDO Output Current | 600mA max |
| I2C | IO8 (SDA), IO10 (SCL) |
| PCB Layers | 2 |
| PCB Dimensions | ~52 x 36mm |
| PCB Color | Ember Orange |
| Finish | ENIG |

---

## 📌 Pinout

### Left Edge (J4)

| Pin | Signal | Notes |
|---|---|---|
| 1 | GND | Ground |
| 2 | 3V3 | 3.3V regulated output |
| 3 | IO4 | GPIO / ADC |
| 4 | IO5 | GPIO / ADC |
| 5 | IO6 | GPIO |
| 6 | IO7 | GPIO |
| 7 | IO8/SDA | GPIO / I2C Data |
| 8 | BOOT | GPIO9, Boot button net |

### Right Edge (J3)

| Pin | Signal | Notes |
|---|---|---|
| 1 | VIN | Raw voltage input (3.8–6V) |
| 2 | GND | Ground |
| 3 | IO0 | GPIO / ADC |
| 4 | IO1 | GPIO / ADC |
| 5 | IO2 | GPIO / ADC, strapping pin |
| 6 | IO10/SCL | GPIO / I2C Clock |
| 7 | RXD | UART RX (IO20) |
| 8 | TXD | UART TX (IO21) |

### Qwiic / STEMMA QT (J2)

| Pin | Signal |
|---|---|
| 1 | GND |
| 2 | 3.3V |
| 3 | SDA (IO8) |
| 4 | SCL (IO10) |

---

## 🧩 Bill of Materials

| Reference | Qty | Value | Footprint | Datasheet |
|---|---|---|---|---|
| C1, C2 | 2 | 1µF | C_0805_2012Metric | — |
| C3 | 1 | 100nF | C_0201_0603Metric | — |
| C4 | 1 | 10µF | C_0805_2012Metric | — |
| D1 | 1 | User LED | LED_0805_2012Metric | — |
| D2 | 1 | Power LED | LED_0805_2012Metric | — |
| D4 | 1 | 1N5819 (SOD-123W) | Nexperia_CFP3_SOD-123W | [Datasheet](http://www.vishay.com/docs/88525/1n5817.pdf) |
| J1 | 1 | USB-C 16P Receptacle | USB_C_Receptacle_GCT_USB4110 | [USB Spec](https://www.usb.org) |
| J2 | 1 | Qwiic / STEMMA QT | JST_SH_BM04B-SRSS-TB_1x04-1MP | — |
| J3 | 1 | Right Castellated Edge (8-pin) | PinHeader_1x08_P2.54mm | — |
| J4 | 1 | Left Castellated Edge (8-pin) | PinHeader_1x08_P2.54mm | — |
| R1, R2 | 2 | 5.1kΩ | R_0805_2012Metric | — |
| R3, R6 | 2 | 470Ω | R_0805_2012Metric | — |
| R4, R5 | 2 | 10kΩ | R_0805_2012Metric | — |
| SW1 | 1 | Reset Button | SW_SPST_TS-1088 | — |
| SW2 | 1 | Boot Button | SW_SPST_TS-1088 | — |
| TP1 | 1 | VOUT Test Point | TestPoint_Pad_D1.0mm | — |
| TP2 | 1 | GND Test Point | TestPoint_Pad_D1.0mm | — |
| U1 | 1 | ESP32-C3-WROOM-02 | ESP32-C3-WROOM-02 | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-c3-wroom-02_datasheet_en.pdf) |
| U2 | 1 | AP2112K-3.3 | SOT-23-5 | [Datasheet](https://www.diodes.com/assets/Datasheets/AP2112.pdf) |

---

## ⚡ Power

PebbleC3 can be powered two ways:

**Via USB-C** — 5V from USB → 1N5819 diode → AP2112K-3.3 LDO → 3.3V rail

**Via VIN pad** — 3.8V–6V on VIN castellation → 1N5819 → LDO → 3.3V rail

The 1N5819 Schottky diode provides OR-ing between USB and VIN — whichever is higher wins automatically. Forward drop is ~0.4V.

> ⚠️ Do not exceed 6V on VIN. AP2112K-3.3 absolute maximum input is 6V.

---

## 🔌 USB and Programming

PebbleC3 uses the ESP32-C3's **native USB** peripheral directly — no USB-to-UART bridge chip needed.

**To flash firmware:**

1. Hold **BOOT** button
2. Press and release **RESET**
3. Release **BOOT**
4. Flash using `esptool.py` or Arduino IDE

**Arduino IDE board selection:**
```
Board: ESP32C3 Dev Module
Upload Speed: 921600
USB CDC On Boot: Enabled
```
---


## 🏭 Manufacturing

Designed for JLCPCB 2-layer standard process.

| Setting | Value |
|---|---|
| Layers | 2 |
| Thickness | 1.6mm |
| Surface Finish | ENIG |
| Solder Mask | Orange |
| Silkscreen | White |
| Castellated Holes | Yes |
| Min Hole Size | 0.2mm |
| Min Clearance | 0.1mm |

> When ordering, select **"Castellated holes: Yes"** — without this JLCPCB will route through your castellation pads.

---

## 🔓 License

This project is **Open Source Hardware** licensed under the [CERN-OHL-P v2](https://ohwr.org/cern_ohl_p_v2.txt).

You are free to use, modify, and manufacture this design. Attribution to **FruitWorks Electronics** appreciated.

---

*Built by makers, for makers.*
