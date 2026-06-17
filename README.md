# Dark Framework — Clean Dark UI Library

A high-performance, completely procedural dark-themed UI library designed for Roblox scripting. This library removes dependencies on external `rbxassetid://` objects by generating a clean, modern, and sleek interface entirely through code. 

Features smooth animations, zero-lag custom dragging mechanics, a clean minimize-to-tray architecture, and completely responsive canvas scaling.

---

##  Key Features

- ** 100% Procedural Architecture:** No external assets, textures, or Roblox IDs are loaded. Completely independent and bulletproof against asset deletion or tracking errors.
- ** True Dark Aesthetic:** Hand-picked professional color palette utilizing deep charcoal fields (`#18181a`), crisp slate elements (`#26262a`), and electric iOS-style action accents.
- ** Clean Minimize-to-Tray:** Minimizing the UI safely shrinks the main window away using an easing interpolation and opens a compact, styled "Restore UI" floating action tile in the lower-right margin of the screen.
- ** Dynamic Content Canvas:** Automatically measures element layout scales (`UIListLayout` interpolation) and adjusts scroll bounds instantly.
- ** Hardened Drag Dynamics:** Custom physics-less window movement bound to input shifts ensures fluid positioning without administrative delays.

---

## 🛠️ Color Palette Configuration

The user interface uses a centralized, uniform structural theme configuration which can be easily hot-swapped within the source file:

```lua
local Theme = {
    Background = Color3.fromRGB(24, 24, 26),      -- Deep Off-Black Field
    Topbar = Color3.fromRGB(32, 32, 36),          -- Navigation Banner
    Accent = Color3.fromRGB(0, 122, 255),         -- Electric Blue Focus
    Text = Color3.fromRGB(240, 240, 245),         -- High Contrast Text
    TextMuted = Color3.fromRGB(150, 150, 155),    -- Subtle Descriptions/Labels
    ElementBg = Color3.fromRGB(38, 38, 42),       -- Structural Components Background
    ToggleOn = Color3.fromRGB(46, 204, 113),      -- Vibrant State True
    ToggleOff = Color3.fromRGB(231, 76, 60),     -- Vibrant State False
    CornerRadius = UDim.new(0, 8)                -- Crisp Global Curvature
}
```
## Initializing the Window

local MyLib = require(path.to.library) -- Or use loadstring() execution
local Window = MyLib:win("Your Title Here")

----

local Tab = Window:tab("Tab Name")
## Generates a discrete layout list container within the view stack and mounts an interactive index selector on the sidebar column.
Tab:label("Section Header or Text Label")

