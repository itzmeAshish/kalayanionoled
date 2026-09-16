# Kalayani Song OLED Animation — Arduino SSD1306

![Arduino](https://img.shields.io/badge/Arduino-IDE-00979D?logo=arduino&logoColor=white)
![OLED](https://img.shields.io/badge/Display-SSD1306%20128x64-111827)
![Library](https://img.shields.io/badge/Library-Adafruit%20SSD1306-orange)
![License](https://img.shields.io/badge/code-free%20to%20use-brightgreen)

Play the **Kalayani song** as a looping animation on a **0.96" SSD1306 OLED** (128×64).  
This repo contains a ready-to-upload Arduino sketch with **148 PROGMEM bitmap frames**.

**Repo:** [https://github.com/itzmeAshish/kalayanionoled](https://github.com/itzmeAshish/kalayanionoled)  
**Full tutorial (SEO blog):** [Kalayani Song OLED Animation Guide](https://www.oledanimationmaker.com/blog/kalayani-song-oled-animation-arduino-ssd1306.html)  
**Made with:** [OLED Animation Maker](https://www.oledanimationmaker.com/)

---

## Keywords / SEO

`kalayani song oled` · `arduino oled animation` · `ssd1306 frame animation` · `progmem bitmap` · `gif to oled` · `0.96 oled arduino` · `esp8266 oled song` · `adafruit ssd1306 animation`

---

## Features

- 148 frames × 128×64 mono bitmaps in `PROGMEM`
- Frame delay ≈ **318 ms** (~3 fps) — easy to change
- Adafruit SSD1306 + Adafruit GFX
- I2C address **0x3C**
- Auto-loop in `loop()`

---

## Requirements

| Item | Notes |
|------|--------|
| Board | **ESP8266 / ESP32 / Mega recommended** |
| OLED | 0.96" SSD1306 I2C 128×64 |
| IDE | Arduino IDE 1.8+ or 2.x |
| Libraries | Adafruit SSD1306, Adafruit GFX |

> **Flash size warning:** 148 frames ≈ **148 KB** of bitmap data. Classic **Arduino Uno (32 KB)** cannot fit this sketch. Use ESP8266, ESP32, or Mega — or regenerate fewer frames in [OLED Animation Maker](https://www.oledanimationmaker.com/).

---

## Connection / Wiring

### Arduino Uno / Nano (for smaller projects)

| OLED | Board |
|------|--------|
| VCC | 5V (or 3.3V if required by module) |
| GND | GND |
| SDA | **A4** |
| SCL | **A5** |

### ESP8266 NodeMCU / Wemos D1 Mini (recommended)

| OLED | Board | GPIO |
|------|--------|------|
| VCC | **3.3V** | — |
| GND | GND | — |
| SDA | **D2** | GPIO4 |
| SCL | **D1** | GPIO5 |

If needed, add before `display.begin()`:

```cpp
Wire.begin(4, 5);  // SDA, SCL on ESP8266
```

### ESP32

| OLED | Board |
|------|--------|
| VCC | 3.3V |
| GND | GND |
| SDA | GPIO21 (common) |
| SCL | GPIO22 (common) |

```cpp
Wire.begin(21, 22);
```

---

## Install & upload

1. **Download** this repo  
   - ZIP: GitHub → **Code → Download ZIP**  
   - or `git clone https://github.com/itzmeAshish/kalayanionoled.git`
2. Open `code.ino` in Arduino IDE
3. Install libraries: **Adafruit SSD1306** + **Adafruit GFX**
4. Select board + COM port  
   - Example: *NodeMCU 1.0* or *ESP32 Dev Module*
5. Click **Upload**
6. Watch the Kalayani animation loop on the OLED

Serial baud: **115200**. If you see `SSD1306 allocation failed`, check power, wiring, and try address `0x3D`.

---

## Speed control

In `loop()`, change the delay:

```cpp
if (millis() - lastMs >= 318) {  // lower = faster
```

| Value | Approx FPS |
|------:|-----------:|
| 318 | ~3 |
| 100 | ~10 |
| 66 | ~15 |

---

## How this was made

1. Open [oledanimationmaker.com](https://www.oledanimationmaker.com/)
2. **Import** a short GIF / video of the Kalayani visual
3. Tune FPS and frame count for your board flash
4. **Get the Code** → Adafruit SSD1306 Arduino
5. Upload to GitHub (this repo)

Tutorial walkthrough:  
https://www.oledanimationmaker.com/blog/kalayani-song-oled-animation-arduino-ssd1306.html

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Blank screen | 3.3V on ESP, swap SDA/SCL check, try `0x3D` |
| Sketch too big | Use ESP8266/ESP32; reduce frames |
| Laggy playback | Increase frame delay; solid USB power |
| Compile errors | Install both Adafruit libraries |

More help: [OLED blank screen guide](https://www.oledanimationmaker.com/blog/arduino-oled-blank-screen-fix-ssd1306.html)

---

## Links

- **Code download:** https://github.com/itzmeAshish/kalayanionoled
- **Blog tutorial:** https://www.oledanimationmaker.com/blog/kalayani-song-oled-animation-arduino-ssd1306.html
- **Free tool:** https://www.oledanimationmaker.com/
- **Author:** [itzmeAshish](https://github.com/itzmeAshish)

---

## License

Free to use for learning, demos, and personal projects.  
Credit appreciated: link back to this repo and [oledanimationmaker.com](https://www.oledanimationmaker.com/).
