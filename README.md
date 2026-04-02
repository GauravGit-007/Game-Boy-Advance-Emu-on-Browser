# 🕹️ PokePlay Arcade: The Ultimate Browser GBA Experience

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![GBA Engine](https://img.shields.io/badge/Engine-Handheld_GBA-red.svg)
![Optimized for Mobile](https://img.shields.io/badge/Optimization-Mobile_Ready-green.svg)

A visually stunning, portfolio-grade Game Boy Advance emulator designed for the modern web. PokePlay Arcade combines nostalgic 32-bit gaming with a premium "Glassmorphism" interface, providing a clean, distraction-free experience across Desktop, Tablet, and Mobile.

---

## ✨ Features that "Wow"

### 🎨 Visual Excellence
- **Cinematic UI**: A sleek, dark-themed dashboard with glassmorphic effects and fluid transitions.
- **Dynamic GBA Shell**: An interactive 3D-breathing model for keybindings and controls.
- **Retro-Modern Fusion**: Beautiful typography (Inter/Roboto) paired with classic pixel-art accents.

### 🎮 Superior Emulation
- **Pixel-Perfect Scaling**: Auto-adjusting canvas with hardware-accelerated GPU scaling.
- **Zero-Latency Audio**: Optimized for mobile browsers with high-stability buffering.
- **Save State Engine**: 3 dedicated safe-slots persisted instantly to `localStorage`.
- **Advanced Core**: Multi-speed support (1×, 2×, 4×) and high-accuracy cycle timing.

### 📱 Handheld Engine (Mobile/Tablet)
- **Fluid Layout**: Seamless transition between Portrait and Landscape modes.
- **Responsive Controls**: Tactile, oversized touch buttons designed for thumbs.
- **Auto-Fullscreen**: Native immersive mode triggered on game launch for a true handheld feel.
- **Performance Mode**: Intelligently disables heavy CSS effects during gameplay to maximize FPS on mobile GPUs.

---

## 🚀 Getting Started

PokePlay is built with zero dependencies, requiring only a simple local server to handle file reading and audio processing.

### 1. Serving Locally
```bash
# Using Node/NPM (Recommended)
npx serve .

# Using Python
python -m http.server 8080

# Or use "Live Server" extension in VS Code
```

### 2. Loading Your Cartridge
1. Navigate to the **Advance** tab or the **Library**.
2. Drag and drop your `.gba` file or click the ROM upload zone.
3. Click **▶ START GAME** and dive in!

---

## ⌨️ Pro Controls

### Desktop Mapping
| Action | Key |
| :--- | :--- |
| **D-Pad** | `Arrow Keys` |
| **A / B** | `Z` / `X` |
| **L / R** | `A` / `S` |
| **START** | `Enter` |
| **SELECT** | `Backspace` |
| **FULLSCREEN** | `F` |

> [!TIP]
> **PRO TIP**: Master your control keys, hit **[F]** for Fullscreen, and dive into the uncompromised Arcade Experience!

---

## 🛠️ Technology Stack

- **Core Logic**: Vanilla JavaScript (GBA.js Core)
- **Styling**: Modern CSS3 (Grid, Flexbox, Variable Tokens)
- **Storage**: Web Storage API (localStorage)
- **Audio**: Web Audio API (AudioContext)
- **Graphics**: HTML5 Canvas (2D Context)

---

## ⚖️ Legal & Copyright

PokePlay Arcade is an open-source educational project.

- **Emulator Core**: Based on the MIT Licensed GBA.js by `endrift`.
- **Legal Notice**: This project does **not** bundle any ROM files. Users must provide their own legally obtained ROMs.
- **Usage**: No data is ever uploaded to a server; all processing happens locally on the user's machine.

---

*Crafted with 🕹️ by Gaurav — [Portfolio Project]*
