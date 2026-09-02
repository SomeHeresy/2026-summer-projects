# 2026 Summer Projects

A working log of what I taught myself between high school and starting Computer Science & Engineering at UC Irvine — summer 2026.

The goal was to get comfortable in C and C++ before embedded coursework, and to move my Arduino work past blinking an LED into something that actually serves a project I care about.

---

## What is in here

| Folder | Contents |
|---|---|
| [`C-programmings/`](C-programmings) | C fundamentals — variables, loops, functions, arrays, pointers, plus two small standalone programs |
| [`Arduino/Basic/`](Arduino/Basic) | First Arduino sketches — single LED, LCD output, a serial calculator |
| [`Arduino/Advanced/`](Arduino/Advanced) | Multi-sensor OLED interface over I²C — the control-panel prototype described below |

---

## Highlight — `EMCG Control` OLED interface

The most useful thing in this repository is not a tutorial exercise. It is the first prototype of a control display for my [electromagnetic accelerator](https://github.com/SomeHeresy/Electromagnetic-Accelerator), which currently has no interface at all — you fire it and find out afterwards what happened.

The sketches read live sensor data and render it on a 128×64 SSD1306 OLED over I²C, which is the same output path a real control panel would use for charge voltage, coil status, and fault reporting.

| Sketch | Adds |
|---|---|
| [`oledInterfaceExample1`](Arduino/Advanced/oledInterfaceExample1) | DHT11 temperature and humidity → OLED |
| [`oledInterfaceExample2`](Arduino/Advanced/oledInterfaceExample2) | Adds an HC-SR04 ultrasonic distance reading |

**Hardware**

| Component | Connection |
|---|---|
| Arduino Uno R3 | — |
| SSD1306 OLED, 128×64 | I²C, address `0x3C` (SDA → A4, SCL → A5) |
| DHT11 temperature + humidity | Digital pin 8 |
| HC-SR04 ultrasonic | TRIG → pin 9, ECHO → pin 10 |

Both sketches redraw the full display every **100 ms**. The ultrasonic read uses `pulseIn` with a 30 ms timeout and reports `No Echo` rather than printing a garbage distance when nothing is in range — the display should never show a number it does not actually have.

![Full breadboard setup](Arduino/Advanced/assets/picture/full%20setup.png)
*Uno R3, both sensors, and the OLED on one breadboard*

![OLED output](Arduino/Advanced/assets/picture/oled%20display.png)
*Live readings under the `EMCG Control V1.0` header*

📖 **Write-up → [someheresy.github.io](https://someheresy.github.io/projects/arduino-sensor-control.html)**

---

## Dependencies

The Advanced sketches need these libraries from the Arduino Library Manager:

- `Adafruit SSD1306`
- `Adafruit GFX Library`
- `DHT sensor library`

---

## Learning targets

- [x] Get comfortable with C and C++ ahead of embedded coursework
- [x] Learn Git and GitHub properly, not just as a backup folder
- [x] Drive an I²C display from multiple sensor inputs
- [ ] Python for data analysis
- [ ] Port the control interface to ESP32 for coil gun V4

---

## Related

- 🔗 [Electromagnetic-Accelerator](https://github.com/SomeHeresy/Electromagnetic-Accelerator) — the system this interface is being built for
- 🔗 [Portfolio](https://someheresy.github.io/) — full project write-ups

---

**Calvin Yang** · Computer Science & Engineering, UC Irvine
[Portfolio](https://someheresy.github.io/) · [LinkedIn](https://www.linkedin.com/in/calvinyang07/) · [Email](mailto:calviny7@uci.edu)
