# 2026 Summer Projects

What I taught myself in summer 2026, before starting Computer Science & Engineering at UC Irvine.

**Goals:** learn C and C++ for embedded coursework, and build Arduino projects that help my [coil gun](https://github.com/SomeHeresy/Electromagnetic-Accelerator).

---

## What's inside

| Folder | Contents |
|---|---|
| [`C-programmings/`](C-programmings) | C basics: variables, loops, functions, arrays, pointers, and two small programs |
| [`Arduino/Basic/`](Arduino/Basic) | First sketches: an LED, an LCD, and a serial calculator |
| [`Arduino/Advanced/`](Arduino/Advanced) | Sensor readings shown on an OLED screen (see below) |

---

## Highlight: `EMCG Control` OLED display

My coil gun has no display. You fire it and find out what happened afterwards.

This is the first prototype of a control screen for it. The Arduino reads sensors and shows the values on a small OLED over I²C. A future version would show charge voltage, coil status, and faults.

| Sketch | What it shows |
|---|---|
| [`oledInterfaceExample1`](Arduino/Advanced/oledInterfaceExample1) | Temperature and humidity (DHT11) |
| [`oledInterfaceExample2`](Arduino/Advanced/oledInterfaceExample2) | The above, plus distance (HC-SR04) |

### Wiring

| Part | Connection |
|---|---|
| Arduino Uno R3 | — |
| SSD1306 OLED, 128×64 | I²C at `0x3C` (SDA → A4, SCL → A5) |
| DHT11 temperature + humidity | Pin 8 |
| HC-SR04 ultrasonic | TRIG → pin 9, ECHO → pin 10 |

### How it behaves

- The screen refreshes every **100 ms**.
- If the ultrasonic sensor gets no echo within 30 ms, the screen shows `No Echo` instead of a wrong number.

![Full breadboard setup](Arduino/Advanced/assets/picture/full%20setup.png)
*Uno R3, both sensors, and the OLED on one breadboard*

![OLED output](Arduino/Advanced/assets/picture/oled%20display.png)
*Live readings under the `EMCG Control V1.0` header*

**Full write-up:** [someheresy.github.io](https://someheresy.github.io/projects/arduino-sensor-control.html)

---

## Libraries needed

Install these from the Arduino Library Manager to run the Advanced sketches:

- `Adafruit SSD1306`
- `Adafruit GFX Library`
- `DHT sensor library`

---

## Progress

- [x] Learn C and C++ basics
- [x] Learn Git and GitHub properly
- [x] Drive an I²C display from several sensors
- [ ] Learn Python for data analysis
- [ ] Move the control display to STM32 for coil gun V4

---

## Related

- [Electromagnetic-Accelerator](https://github.com/SomeHeresy/Electromagnetic-Accelerator): the coil gun this display is for
- [Portfolio](https://someheresy.github.io/): full project write-ups

---

**Calvin Yang** · Computer Science & Engineering, UC Irvine
[Portfolio](https://someheresy.github.io/) · [LinkedIn](https://www.linkedin.com/in/calvinyang07/) · [Email](mailto:calviny7@uci.edu)
