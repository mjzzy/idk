# Clean Dark UI Library

A lightweight, modern Roblox UI library featuring a clean dark theme, smooth animations, draggable windows, tab support, sliders, toggles, textboxes, and automatic minimize/restore functionality.

---

## Preview

### Features

* Modern dark design
* Multi-tab interface
* Draggable window
* Animated UI interactions
* Buttons
* Toggles
* Sliders
* Textboxes
* Labels
* Hidden GUI support (`gethui`)
* Minimize / Restore system
* Close button
* Keyboard toggle (`K`)

---

## Installation

### Using `loadstring`

```lua
local Library = loadstring(game:HttpGet("YOUR_URL_HERE"))()
```

### Using `require`

```lua
local Library = require(path.to.library)
```

---

# Getting Started

## Create a Window

```lua
local Window = Library:win("My Script")
```

### Parameters

| Parameter | Type   | Description  |
| --------- | ------ | ------------ |
| title     | string | Window title |

---

## Create Tabs

```lua
local Main = Window:tab("Main")
local Settings = Window:tab("Settings")
```

### Parameters

| Parameter | Type   |
| --------- | ------ |
| title     | string |

---

# Components

## Label

Displays simple text.

```lua
Main:label("Combat")
```

### Parameters

| Parameter | Type   |
| --------- | ------ |
| text      | string |

---

## Button

Creates a clickable button.

```lua
Main:button("Kill All", function()
    print("Clicked")
end)
```

### Parameters

| Parameter | Type     |
| --------- | -------- |
| text      | string   |
| callback  | function |

---

## Toggle

Creates an animated on/off switch.

```lua
Main:toggle("Auto Farm", false, function(state)
    print(state)
end)
```

### Parameters

| Parameter | Type     |
| --------- | -------- |
| text      | string   |
| default   | boolean  |
| callback  | function |

### Callback

```lua
function(state)
    print(state)
end
```

Returns:

```lua
true
false
```

### Auto Callback

If the default value is `true`, the callback fires automatically once.

```lua
Main:toggle("Enabled", true, function(state)
    print(state)
end)
```

Output:

```lua
true
```

---

## Textbox

Creates a text input field.

```lua
Main:textbox("Player Name", "", function(text)
    print(text)
end)
```

### Parameters

| Parameter | Type     |
| --------- | -------- |
| title     | string   |
| default   | string   |
| callback  | function |

### Notes

* Fires when Enter is pressed.
* Supports default values.
* Automatically calls the callback if a default value is supplied.

```lua
Main:textbox("Username", "Builderman", function(text)
    print(text)
end)
```

---

## Slider

Creates a draggable slider.

```lua
Main:slider("WalkSpeed", 16, 100, 16, function(value)
    print(value)
end)
```

### Parameters

| Parameter | Type     |
| --------- | -------- |
| title     | string   |
| min       | number   |
| max       | number   |
| default   | number   |
| callback  | function |

### Notes

* Rounded to whole numbers.
* Callback fires when dragging ends.
* Supports mouse and touch controls.

---

# Full Example

```lua
-- Execute / Require the Redesigned Dark GUI Module
local DarkLib = loadstring(game:HttpGet("[https://raw.githubusercontent.com/YourRepo/DarkLib/main/lib.lua](https://raw.githubusercontent.com/YourRepo/DarkLib/main/lib.lua)"))()

-- Instantiate Window context
local win = DarkLib:win("Dark Framework v1.0")

-- Define Combat Tab
local combatTab = win:tab("Combat")
combatTab:label("Aura Adjustments")

combatTab:toggle("Active Kill Aura", false, function(enabled)
    _G.KillAura = enabled
    while _G.KillAura do
        task.wait(0.1)
        print("Executing aura sequence...")
    end
end)

combatTab:slider("Target Distance Range", 5, 50, 15, function(rangeValue)
    print("Range target updated: " .. tostring(rangeValue) .. " studs.")
end)

-- Define Settings Tab
local settingsTab = win:tab("Settings")
settingsTab:label("Client Environment")

settingsTab:textbox("Custom Player Tag", "Guest", function(inputtedText)
    print("Custom identity assigned: " .. inputtedText)
end)

settingsTab:button("Unhook Interface Thread", function()
    game:GetService("CoreGui"):FindFirstChild("CleanDarkLib_Gui"):Destroy()
    print("Execution pipeline terminated safely.")
end)
```

---

# Window Controls

## Dragging

Drag the window using the top bar.

---

## Minimize

Click the `-` button or press:

```text
K
```

The window collapses and a floating restore button appears.

---

## Restore

Click:

```text
Restore UI
```

or press:

```text
K
```

---

## Close

Click:

```text
×
```

This completely destroys the UI.

---

# API Reference

## Library

### Create Window

```lua
Library:win(title)
```

Returns:

```lua
Window
```

---

## Window

### Create Tab

```lua
Window:tab(title)
```

Returns:

```lua
Tab
```

---

## Tab

### Label

```lua
Tab:label(text)
```

### Button

```lua
Tab:button(text, callback)
```

### Toggle

```lua
Tab:toggle(text, default, callback)
```

### Textbox

```lua
Tab:textbox(text, default, callback)
```

### Slider

```lua
Tab:slider(text, min, max, default, callback)
```

---

# Theme

Built-in color palette:

```lua
Background = Color3.fromRGB(24, 24, 26)
Topbar = Color3.fromRGB(32, 32, 36)

Accent = Color3.fromRGB(0, 122, 255)

Text = Color3.fromRGB(240, 240, 245)
TextMuted = Color3.fromRGB(150, 150, 155)

ElementBg = Color3.fromRGB(38, 38, 42)

ToggleOn = Color3.fromRGB(46, 204, 113)
ToggleOff = Color3.fromRGB(231, 76, 60)
```

---

# Current Limitations

The current version does not include:

* Dropdowns
* Keybind Components
* Color Pickers
* Notifications
* Paragraphs
* Section Containers
* Configuration Saving
* Theme Customization API

---


# Credits

Created by **mjzzy**

Made for Roblox script hubs, utilities, and executor projects.
