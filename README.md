<div align="center">

# 🐍 ESP32 Retro Snake Game Console

### A pro-level, animated Snake game running on an ESP32 and a 0.96" OLED display, played with 4 push switches.

![Platform](https://img.shields.io/badge/Platform-ESP32-blue?style=for-the-badge&logo=espressif)
![Framework](https://img.shields.io/badge/Framework-Arduino-00979D?style=for-the-badge&logo=arduino)
![Display](https://img.shields.io/badge/Display-SSD1306_OLED-black?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**Built by TechTadka360**

[![YouTube](https://img.shields.io/badge/YouTube-TechTadka360-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@techtadka360official)
[![Instagram](https://img.shields.io/badge/Instagram-TechTadka360-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](ADD_YOUR_INSTAGRAM_LINK)
[![Facebook](https://img.shields.io/badge/Facebook-TechTadka360-1877F2?style=for-the-badge&logo=facebook&logoColor=white)](ADD_YOUR_FACEBOOK_LINK)
[![GitHub](https://img.shields.io/badge/GitHub-Mr--soumik-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Mr-soumik)

[Watch the Build Video](#-demo) · [Circuit Diagram](#-circuit-diagram) · [Wiring](#-wiring) · [Installation](#-installation) · [How to Play](#-how-to-play)

</div>

---

## 📸 Demo

<div align="center">

![ESP32 Snake Game Demo](images/demo.jpg)

</div>

### 🎥 Watch the full build on every platform

| Platform | Link |
|---|---|
| ▶️ YouTube | https://youtube.com/shorts/x55ezZsaaZk?si=Ih16VS9O-Yb81-Wr
| 📸 Instagram | [Watch the Snake game reel](ADD_INSTAGRAM_VIDEO_LINK) |
| 📘 Facebook | [Watch the Snake game video](ADD_FACEBOOK_VIDEO_LINK) |

### 🔌 Circuit Diagram

<div align="center">

![Circuit Diagram](circuit_diagram.svg)

</div>

---

## 📖 About the Project

This project turns an ESP32 and a tiny 128x64 OLED into a portable retro game console. It is not just a basic Snake clone: it includes a smooth animated interface, a realistic snake with eyes and a flicking tongue, three difficulty levels, bonus food, sound effects, and high scores that are saved even after the power is turned off.

Everything runs from a single Arduino sketch with no extra game engine, and it needs only a handful of cheap parts.

---

## ✨ Features

| Feature | Details |
|---|---|
| 🎬 **Animated splash screen** | A snake slithers across the screen under the game title |
| 🎮 **Menu system** | Choose Easy, Normal or Hard with Left and Right, start with Up or Down |
| 🐍 **Realistic snake** | Rounded head with direction-aware eyes, a flicking tongue, a scaled body and a tapered tail |
| 🍎 **Animated food** | Pulsing apple with a shine effect |
| ⭐ **Bonus star** | Appears after every 5 apples with a countdown bar, worth 50 points |
| ⚡ **Dynamic speed** | The game speeds up as you eat |
| 🔁 **Smart input buffer** | Quick turns are queued, so tight corners feel smooth and the snake can never reverse into itself |
| 💾 **Saved high scores** | A separate best score for each difficulty, stored in flash memory |
| 🔊 **Sound effects** | Optional buzzer for eating, bonus, countdown and game over |
| ⏱️ **3-2-1 countdown** | Get ready before each round |
| 🏆 **Game over screen** | Shows score, best score and a flashing NEW HIGH SCORE message |

---

## 🧰 Hardware Required

| Component | Quantity | Notes |
|---|---|---|
| ESP32 Dev Module | 1 | Any 30-pin or 38-pin ESP32 board |
| 0.96" SSD1306 OLED (I2C) | 1 | 128x64, address `0x3C` |
| Push switches | 4 | Up, Down, Left, Right |
| Active buzzer | 1 | Optional, for sound effects |
| Breadboard or perfboard | 1 | |
| Jumper wires | As needed | |

---

## 🔌 Wiring

### OLED display (I2C)

| OLED Pin | ESP32 Pin |
|---|---|
| VCC | 3V3 |
| GND | GND |
| SDA | GPIO 21 |
| SCL | GPIO 22 |

### Push switches

Connect one leg of each switch to the ESP32 pin and the other leg to GND. No external resistors are needed because the code uses the internal pull-up resistors.

| Button | ESP32 Pin |
|---|---|
| UP | GPIO 18 |
| DOWN | GPIO 5 |
| LEFT | GPIO 4 |
| RIGHT | GPIO 15 |

### Buzzer (optional)

| Buzzer Pin | ESP32 Pin |
|---|---|
| + | GPIO 2 |
| − | GND |

> **Note:** GPIO 2 and GPIO 15 are boot-strapping pins on the ESP32. If code upload fails, disconnect the buzzer from GPIO 2 while flashing, then reconnect it.

### Connection overview

```
                +-----------------+
                |      ESP32      |
                |                 |
   OLED SDA ----| GPIO21          |
   OLED SCL ----| GPIO22          |
   OLED VCC ----| 3V3             |
   OLED GND ----| GND             |
                |                 |
   UP     ------| GPIO18          |
   DOWN   ------| GPIO5           |
   LEFT   ------| GPIO4           |
   RIGHT  ------| GPIO15          |
   (other leg of every button to GND)
                |                 |
   BUZZER + ----| GPIO2           |
   BUZZER - ----| GND             |
                +-----------------+
```

---

## 💻 Installation

### 1. Install the Arduino IDE and ESP32 board support

1. Install the [Arduino IDE](https://www.arduino.cc/en/software).
2. Open **File → Preferences** and add this URL to *Additional Boards Manager URLs*:
   ```
   https://espressif.github.io/arduino-esp32/package_esp32_index.json
   ```
3. Open **Tools → Board → Boards Manager**, search for **esp32** and install it.

### 2. Install the libraries

Open **Sketch → Include Library → Manage Libraries** and install:

- `Adafruit SSD1306`
- `Adafruit GFX Library`

`Wire` and `Preferences` come with the ESP32 package.

### 3. Upload the code

1. Clone or download this repository:
   ```bash
   git clone https://github.com/Mr-soumik/ESP32-Snake-Game.git
   ```
2. Open `Snake_Pro.ino` in the Arduino IDE.
3. Select **Tools → Board → ESP32 Dev Module**.
4. Select the correct COM port.
5. Click **Upload**. If it gets stuck on "Connecting...", hold the **BOOT** button on the ESP32 until upload starts.

---

## 🎮 How to Play

### Controls

| Button | Menu | In game |
|---|---|---|
| ⬆️ UP | Start game | Move up |
| ⬇️ DOWN | Start game | Move down |
| ⬅️ LEFT | Previous difficulty | Move left |
| ➡️ RIGHT | Next difficulty | Move right |

### Rules

- Eat the **apple** to grow and earn **10 points**.
- After every **5 apples**, a blinking **bonus star** appears for 6 seconds. Eat it for **50 points** before the timer bar runs out.
- Do not run into your own body.
- On **Normal** and **Hard**, hitting a wall ends the game.
- The snake gets faster as you eat more apples.

### Difficulty levels

| Level | Starting speed | Maximum speed | Walls |
|---|---|---|---|
| Easy | Slow | Moderate | Snake wraps around to the other side |
| Normal | Medium | Fast | Deadly |
| Hard | Fast | Very fast | Deadly |

---

## ⚙️ Customization

All tuning values are at the top of `Snake_Pro.ino`.

**Change the game speed** (a larger number means a slower snake, in milliseconds per move):

```cpp
const int baseMs[3] = {250, 195, 145};
const int minMs[3]  = {160, 120, 85};
```

**Change the button pins:**

```cpp
const uint8_t BTN[4] = {18, 5, 4, 15};
const uint8_t PIN_BUZZ = 2;
```

**Change the bonus star duration:**

```cpp
const int BONUS_MS = 6000;
```

**Use an SH1106 display** instead of SSD1306: replace the Adafruit SSD1306 driver with an SH1106-compatible library and keep the same drawing code.

---

## 🛠️ How It Works

- **Display:** The game draws on a 31 x 13 grid with 4-pixel cells inside a bordered play area, with a score bar on top.
- **Input:** Buttons are read with debouncing. Direction changes go into a small queue and are checked so the snake can never reverse directly.
- **Movement:** The snake body is stored in coordinate arrays and shifted every tick, with collision checks against the body and walls.
- **Saving scores:** The high score for each level is stored with the ESP32 `Preferences` library, so it survives power loss.
- **Sound:** The buzzer is switched off by a non-blocking timer, so beeps never freeze the game.

---

## 🧯 Troubleshooting

| Problem | Fix |
|---|---|
| Blank OLED | Check SDA to GPIO21 and SCL to GPIO22, and confirm the address is `0x3C` |
| Upload fails | Hold the BOOT button while uploading, and unplug the buzzer from GPIO2 |
| Button does nothing | Check that the other leg of the switch goes to GND |
| Wrong or mirrored display | Check that your OLED is a 128x64 SSD1306 |
| Game feels too fast or slow | Adjust `baseMs` and `minMs` in the code |
| Reset saved high scores | Erase the ESP32 flash from the Arduino IDE (Tools → Erase All Flash) and re-upload |

---

## 🚀 Future Ideas

- [ ] Pause button
- [ ] Obstacles and maze levels
- [ ] Two-player mode
- [ ] Battery power with a 3D-printed case
- [ ] More retro games in the same console (Pong, Tetris, Breakout)

---

## 🤝 Contributing

Contributions, ideas and bug reports are welcome. Fork the repo, create a branch, and open a pull request.

---

## 📜 License

This project is released under the **MIT License**. You are free to use, modify and share it. Please give credit to **TechTadka360** if you use it in a video.

---

## 👤 Author

**Soumik (TechTadka360)**

- GitHub: [@Mr-soumik](https://github.com/Mr-soumik)
- YouTube: [TechTadka360](https://www.youtube.com/@techtadka360official)
- Instagram: [TechTadka360](ADD_YOUR_INSTAGRAM_LINK)
- Facebook: [TechTadka360](ADD_YOUR_FACEBOOK_LINK)

<div align="center">

### ⭐ If you like this project, give the repo a star and subscribe to TechTadka360 for more ESP32 and Arduino builds!

</div>
