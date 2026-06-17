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
-- Load Library
local DarkLib = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/YourRepo/DarkLib/main/lib.lua"
))()

-- Create Window
local Window = DarkLib:win("Dark Framework v1.0")

--------------------------------------------------
-- MAIN TAB
--------------------------------------------------

local Main = Window:tab("Main")

Main:label("Framework Demonstration")

Main:button("Print Hello", function()
    print("Hello from Dark Framework!")
end)

Main:textbox("Username", "Guest", function(text)
    print("Username:", text)
end)

Main:slider("WalkSpeed", 16, 100, 16, function(value)
    print("WalkSpeed set to:", value)
end)

--------------------------------------------------
-- COMBAT TAB
--------------------------------------------------

local Combat = Window:tab("Combat")

Combat:label("Combat Features")

local KillAura = false

Combat:toggle("Kill Aura", false, function(state)
    KillAura = state

    if state then
        task.spawn(function()
            while KillAura do
                print("Searching for targets...")
                task.wait(1)
            end
        end)
    end
end)

Combat:slider("Aura Range", 5, 100, 25, function(value)
    print("Aura Range:", value)
end)

Combat:button("Attack Closest Target", function()
    print("Attacking nearest enemy...")
end)

--------------------------------------------------
-- MOVEMENT TAB
--------------------------------------------------

local Movement = Window:tab("Movement")

Movement:label("Movement Controls")

Movement:toggle("Infinite Jump", false, function(state)
    print("Infinite Jump:", state)
end)

Movement:toggle("No Clip", false, function(state)
    print("No Clip:", state)
end)

Movement:slider("Jump Power", 50, 200, 50, function(value)
    print("Jump Power:", value)
end)

--------------------------------------------------
-- VISUALS TAB
--------------------------------------------------

local Visuals = Window:tab("Visuals")

Visuals:label("ESP Settings")

Visuals:toggle("Player ESP", false, function(state)
    print("ESP:", state)
end)

Visuals:toggle("Tracers", false, function(state)
    print("Tracers:", state)
end)

Visuals:toggle("Boxes", false, function(state)
    print("Boxes:", state)
end)

--------------------------------------------------
-- SETTINGS TAB
--------------------------------------------------

local Settings = Window:tab("Settings")

Settings:label("Client Settings")

Settings:textbox("Custom Tag", "DarkUser", function(text)
    print("Tag Updated:", text)
end)

Settings:button("Rejoin Server", function()
    print("Rejoin clicked")
end)

Settings:button("Copy Discord Invite", function()
    print("Discord copied")
end)

Settings:button("Unload UI", function()
    local gui = game:GetService("CoreGui"):FindFirstChild("CleanDarkLib_Gui")

    if gui then
        gui:Destroy()
    end

    print("UI unloaded")
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
