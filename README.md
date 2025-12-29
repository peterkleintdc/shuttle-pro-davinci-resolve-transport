# 🎛️ Shuttle Pro v2 – DaVinci Resolve (PK Profile)

This repository contains a **complete Shuttle Pro v2 profile** for **DaVinci Resolve**, including advanced jog/shuttle macros and button mappings. The goal of this setup is to provide **fast, smooth timeline navigation** without spamming frame-by-frame key presses.

> **Disclaimer**
> 
> This is a **highly opinionated workflow** designed around a compact, transport-centric editing style.
> It is not intended to replace all input devices or mimic default mouse/keyboard behavior.
> Expect a short adaptation period — the payoff is speed, precision, and reduced friction once muscle memory sets in.

The jog/shuttle behavior is the core of the setup (the “secret sauce”). Instead of repeatedly sending Left/Right arrow keys, the shuttle dynamically controls **playback direction and speed** using Resolve’s native **J / K / L** transport logic.

---

## ✨ Key Features

- Designed for **left-hand use on the Shuttle Pro** and **right-hand use on a touchpad** (built-in laptop trackpad or external)
- Eliminates the need for a traditional mouse
- Enables a compact, finger-focused workflow ideal for laptops and small desks
- Advanced **jog/shuttle acceleration logic** using J / K / L
- Smooth ramping of playback speed (0.25× → 0.5× → 1× → 2× …)
- Immediate stop when returning to center (K)
- Jog dial used as **mouse wheel / scroll**, perfect for Resolve timeline zoom and navigation
- Clean, predictable behavior without key-repeat lag

---

## 🧠 Jog / Shuttle Logic (The Secret Sauce)

### Basic idea

- **Right side** of the shuttle = forward playback (L)
- **Left side** of the shuttle = reverse playback (J)
- **Returning toward center** gradually slows playback using **Shift + K** (halve speed)
- **Center position** always sends **K** (stop)

This mimics a professional transport wheel rather than a keyboard jog.

### Speed ramping by zone

| Shuttle zone     | Action sent               | Resulting speed            |
| ---------------- | ------------------------- | -------------------------- |
| First step (±1)  | L / J + Shift+K + Shift+K | \~0.25×                    |
| Second step (±2) | L / J + Shift+K           | \~0.5×                     |
| Third step (±3)  | L / J                     | 1×                         |
| Further steps    | L / J                     | 2×, 4×, … (Resolve native) |

Because Resolve treats repeated **L** or **J** presses as speed multipliers, this approach scales naturally and stays responsive.

---

## 🖱️ Jog Dial (Inner Wheel)

- The jog dial itself is configured as **mouse scroll**
- This makes it ideal for:
  - Timeline zoom (Alt + scroll)
  - Horizontal timeline movement (Ctrl + scroll)
  - Track height / vertical navigation (Shift + scroll)

Modifier keys are intentionally left to the keyboard for flexibility.

---

## 🎹 Button Mappings (Resolve Context)

Below is an overview of the button mappings used in this profile.

| Shuttle Button | Mapping           | Purpose                                                          |
| -------------- | ----------------- | ---------------------------------------------------------------- |
| Button 1       | Left Click        | Standard mouse left-click for selection and UI interaction       |
| Button 2       | Left Click (Hold) | Click-and-drag operations (move clips, resize, drag UI elements) |
| Button 3       | Right Click       | Open context menus                                               |
| Button 4       | Ctrl + Z          | Undo                                                             |
| Button 5       | I                 | Mark In                                                          |
| Button 6       | J                 | Play reverse                                                     |
| Button 7       | K                 | Stop                                                             |
| Button 8       | L                 | Play forward                                                     |
| Button 9       | O                 | Mark Out                                                         |
| Button 10      | Ctrl + Up Arrow   | Move clip selection **up one track**                             |
| Button 11      | Ctrl + T          | **Split clip** (PK custom Resolve mapping)                       |
| Button 12      | Ctrl + Down Arrow | Move clip selection **down one track**                           |
| Button 13      | Shift + V         | Select clip under playhead                                       |
| Button 14      | Left Arrow        | Nudge playhead **one frame backward**                            |
| Button 15      | Right Arrow       | Nudge playhead **one frame forward**                             |

---

## 📦 Installation

### Windows

1. Close the **Contour Shuttle** software

2. Locate the configuration file:

   ```
   C:\ProgramData\ContourDesignMediaControllerSoftware\contour_default.json
   ```

3. Back up the existing file

4. Merge or replace it with the provided configuration (see integration notes below)

5. Restart the Shuttle software

6. Launch DaVinci Resolve

---

## 🔧 Integration Notes (IMPORTANT)

This profile is designed to live **inside** an existing `contour_default.json` file.

When integrating manually:

- The **`Macros`** section must be merged into the top-level `"Macros"` array
- The **profile itself** must be added as an entry inside `"ProfilesPreferences"`
- The profile name is:
  ```
  "Name": "PK"
  ```

Make sure you do **not** break the JSON structure (commas, brackets, ordering).

> Tip: Use a code editor with JSON validation (VS Code is perfect for this).

---

## ⚠️ Important Quirks & Gotchas

### 1) Button 2 (Left Click – Hold)

Button 2 is mapped to **Left Click (Hold)** and is intended for drag operations (moving clips, resizing, dragging UI elements).

⚠️ **Important:**

- To reliably *release* the hold state, you should **press Button 1 (Left Click)** after finishing the drag.
- If you do not do this, the system may remain in a "held" mouse state, which can feel confusing or broken.

This is a limitation of how mouse-hold actions are handled by the Shuttle software rather than a Resolve issue.

---

### 2) Button 11 (Split Clip – Ctrl + T)

Button 11 is intended to perform **Split Clip**, but:

- DaVinci Resolve has **no default keyboard shortcut** assigned to Split Clip
- You **must manually assign** `Ctrl + T` (or any preferred shortcut) to *Split Clip* in:

  **DaVinci Resolve → Keyboard Customization**

Alternatively:

- You may remap Button 11 to **any other frequently used command** if you prefer not to modify Resolve’s keymap.

This flexibility is intentional.

---

### 3) Timeline Scroll & Zoom Requires Cursor Focus

For **timeline scrolling and zooming** (via jog dial + modifier keys) to work correctly:

- The **mouse cursor must be positioned over the timeline panel** in DaVinci Resolve
- If the cursor is over another panel (Viewer, Inspector, Media Pool, etc.), scroll and zoom actions will affect that panel instead — or do nothing

This is standard Resolve behavior and not a Shuttle limitation, but it is important to be aware of when navigating quickly.

---

## 🧪 Troubleshooting

- If playback behaves strangely, check that no other key-mapping tools are active
- If Alt-Tab or other global shortcuts break, restart the Shuttle service
- Make sure DaVinci Resolve has focus when testing shuttle behavior

---

## 🔁 Customization

This setup is intentionally modular:

- You can adjust speed ramping by adding/removing **Shift+K** actions
- You can change jog behavior per zone (`DeviceJogWheelTransition_*`)
- You can add additional macros for large jumps or timeline tools

---

## ❤️ Credits & Philosophy

This profile was built to **feel like a real edit controller**, not a keyboard workaround.

If you improve or adapt it, consider sharing your changes back with others — small tweaks can make a big difference in editing speed.

Happy editing 🎬

