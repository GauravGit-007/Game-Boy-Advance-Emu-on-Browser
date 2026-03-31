# 🎮 PokePlay — Browser GBA Emulator

A visually stunning, portfolio-grade Game Boy Advance emulator that runs entirely in the browser. Built with vanilla HTML/CSS/JS + GBA.js (MIT licensed).

---

## ✨ Features

- 🕹️ Full GBA emulation via GBA.js (MIT)
- 📁 Load any `.gba` ROM via file picker or drag-and-drop
- 💾 3 save slots persisted in `localStorage`
- ⌨️ Full keyboard mapping
- 📱 On-screen touch controls (mobile friendly)
- ⚡ Speed toggle: 1×, 2×, 4×
- ⛶ Fullscreen mode
- 🎨 Retro GBA shell UI with scanlines, CRT glow

---

## 🚀 Setup (5 minutes)

### Step 1 — Get GBA.js

```bash
git clone https://github.com/endrift/gbajs.git
```

Copy these two files into your project:
```
gbajs/resources/gba.js  →  pokeplay/gba/gba.js
gbajs/resources/audio.js →  pokeplay/gba/audio.js
```

### Step 2 — Enable GBA.js in index.html

Uncomment these two lines near the bottom of `index.html`:

```html
<script src="gba/audio.js"></script>
<script src="gba/gba.js"></script>
```

### Step 3 — Serve locally

> ⚠️ Must be served via HTTP (not `file://`) for FileReader + AudioWorklet to work.

```bash
# Python
python3 -m http.server 8080

# Node
npx serve .

# VS Code
# Use the "Live Server" extension
```

Open `http://localhost:8080` in Chrome or Firefox.

### Step 4 — Load a ROM

- Click the ROM zone or drag-and-drop a `.gba` file
- Click **▶ START GAME**

---

## ⌨️ Keyboard Controls

| GBA Button | Key |
|---|---|
| A | `Z` |
| B | `X` |
| Start | `Enter` |
| Select | `Backspace` |
| L | `A` |
| R | `S` |
| D-Pad | Arrow Keys |

---

## 💾 Save States

- 3 save slots, persisted across page refreshes via `localStorage`
- Key format: `pokeplay_save_slot_{1|2|3}`
- Each slot stores: timestamp + base64-encoded GBA state JSON

---

## ⚖️ Legal

- **GBA.js** is MIT licensed — free to use in any project
- **ROM files** carry Nintendo's copyright — this project does NOT bundle any ROMs
- Users load their own ROM files locally; no ROM data is ever sent to any server
- This is a portfolio/showcase project — not sold or monetized

---

## 🗂️ File Structure

```
pokeplay/
├── index.html        # Full app (UI + logic)
├── gba/
│   ├── gba.js        # GBA.js core (add manually)
│   └── audio.js      # GBA.js audio (add manually)
└── README.md
```

---

## 🔮 Future Enhancements

- [ ] Cheat code support (GameShark/Action Replay)
- [ ] Shader post-processing (LCD grid, CRT curve)
- [ ] ROM library management (IndexedDB)
- [ ] Cloud save sync

---

*Built by Gaurav — portfolio project*
