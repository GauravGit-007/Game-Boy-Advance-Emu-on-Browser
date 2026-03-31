# 📋 PRD — PokePlay: Browser GBA Emulator
**Version:** 1.0.0  
**Author:** Gaurav  
**Reviewer:** Tech Reviewer  
**Status:** Ready for Implementation  

---

## 1. Overview

### 1.1 Product Summary
PokePlay is a browser-based Game Boy Advance (GBA) emulator built entirely in vanilla HTML/CSS/JavaScript. It uses the **GBA.js** open-source emulator core to run GBA ROMs directly in the browser with zero server-side logic. The primary showcase game is a custom/open-source compatible ROM (e.g., a Pokemon fan-made or public domain GBA ROM).

### 1.2 Goals
- Run GBA ROMs entirely client-side (no backend, no server)
- Deliver a visually stunning, retro-futuristic UI
- Support save states persisted in `localStorage`
- Support keyboard and on-screen touch controls
- Be showcaseable as a portfolio/demo project

### 1.3 Non-Goals
- No ROM hosting or distribution of copyrighted ROMs
- No multiplayer / link cable emulation
- No mobile app (web only, responsive)
- No server-side processing of any kind

---

## 2. Legal & Ethical Stance

| Concern | Decision |
|---|---|
| ROM Distribution | ❌ NOT distributed — user loads their own ROM via file picker |
| Copyrighted ROMs | ❌ Not bundled — showcase uses open-source/fan ROMs only |
| Emulator Code (GBA.js) | ✅ MIT Licensed — free to use |
| Commercial Use | ❌ This is a portfolio/showcase project, not sold |

> **Note:** GBA.js is MIT licensed. The emulator itself is fully legal to use. Only ROM files carry copyright. Since no ROM is bundled and the user loads their own file locally (never uploaded to any server), this is legally safe as a showcase.

---

## 3. Architecture

```
┌─────────────────────────────────────────────┐
│              Browser (Client Only)           │
│                                              │
│  ┌──────────┐    ┌──────────┐   ┌────────┐  │
│  │  index   │───▶│  GBA.js  │──▶│Canvas  │  │
│  │  .html   │    │  Core    │   │Render  │  │
│  └──────────┘    └──────────┘   └────────┘  │
│       │                │                    │
│  ┌────▼──────┐   ┌─────▼──────┐             │
│  │  UI Layer │   │localStorage│             │
│  │ Controls  │   │ Save States│             │
│  └───────────┘   └────────────┘             │
└─────────────────────────────────────────────┘
```

### 3.1 Key Components

| Component | Responsibility |
|---|---|
| `index.html` | Entry point, full UI shell |
| `style.css` | All visual styling, animations, retro theme |
| `main.js` | ROM loading, GBA.js wiring, controls, save state logic |
| `gba.js` | Third-party GBA emulator core (MIT) |
| `audio.js` | GBA.js audio worklet (bundled with GBA.js) |

---

## 4. Features

### 4.1 Core Features (MVP)

#### F1 — ROM Loading
- User clicks "Load ROM" button → triggers `<input type="file" accept=".gba">`
- File is read as `ArrayBuffer` via `FileReader`
- Passed directly to `gba.setRom(buffer)`
- ROM never leaves the browser

#### F2 — Game Rendering
- GBA renders to an HTML5 `<canvas>` element (240×160 native resolution)
- Canvas is CSS-scaled to fit the screen beautifully
- Aspect ratio is locked at 3:2

#### F3 — Keyboard Controls

| GBA Button | Keyboard Key |
|---|---|
| A | `Z` |
| B | `X` |
| Start | `Enter` |
| Select | `Backspace` |
| L | `A` |
| R | `S` |
| D-Pad Up | `Arrow Up` |
| D-Pad Down | `Arrow Down` |
| D-Pad Left | `Arrow Left` |
| D-Pad Right | `Arrow Right` |

#### F4 — On-Screen Controls
- Touch-friendly D-pad (left side)
- A, B, Start, Select buttons (right side)
- Works on mobile browsers
- Each button fires `keydown`/`keyup` equivalents via GBA.js input API

#### F5 — Save States
- Up to 3 save slots
- Each slot stores serialized GBA state in `localStorage`
- Key format: `pokeplay_save_slot_{n}`
- UI shows slot thumbnail label + timestamp
- Save / Load buttons per slot

#### F6 — Game Controls Bar
- Play / Pause toggle
- Reset game
- Fullscreen toggle (Fullscreen API)
- Speed toggle: 1× / 2× / 4×

### 4.2 Visual Features

#### F7 — Retro GBA Shell UI
- The canvas is embedded inside a visual GBA hardware shell (pure CSS)
- Pixel-art inspired design language
- Animated scanlines overlay on the screen
- Glowing screen effect

#### F8 — Theming
- Dark retro theme: deep navy + electric red + amber accents
- Custom pixel-art font (Press Start 2P via Google Fonts)
- Subtle CRT/grain texture overlay

---

## 5. Data Model

### 5.1 localStorage Schema

```json
{
  "pokeplay_save_slot_1": {
    "timestamp": "2024-01-15T10:30:00Z",
    "label": "Slot 1",
    "state": "<base64-encoded GBA state blob>"
  },
  "pokeplay_save_slot_2": null,
  "pokeplay_save_slot_3": null
}
```

---

## 6. Non-Functional Requirements

| Requirement | Target |
|---|---|
| Performance | 60 FPS on modern desktop Chrome/Firefox |
| Compatibility | Chrome 90+, Firefox 88+, Safari 15+, Edge 90+ |
| Mobile | Responsive layout, touch controls functional |
| Load Time | < 2s first paint (all assets local or CDN) |
| Accessibility | Keyboard navigable UI, ARIA labels on buttons |

---

## 7. File Structure

```
pokeplay/
├── index.html         # Main entry point
├── style.css          # All styles
├── main.js            # App logic
├── gba/
│   ├── gba.js         # GBA.js core (MIT)
│   └── audio.js       # GBA.js audio worklet
└── README.md
```

---

## 8. Out of Scope / Future Enhancements

- [ ] Cheats / GameShark code support
- [ ] Link cable / multiplayer
- [ ] Cloud save sync
- [ ] ROM library management
- [ ] Shader post-processing (LCD grid, CRT curve)

---

## 9. Success Criteria

- [ ] ROM loads and game runs at full speed
- [ ] Save/load states work correctly across page refreshes
- [ ] On-screen controls functional on mobile
- [ ] UI is visually impressive as a portfolio piece
- [ ] No ROM files are bundled or served from any server

---

*End of PRD*
