# 🌌 Allusive UI Library

A sleek and customizable **Roblox UI library** designed to help you create intuitive, stylish, and feature-rich interfaces for your Roblox projects.

> ✨ Modular tabs, responsive components, persistent settings, and dynamic notifications — all in one robust package.

---

## 📚 Table of Contents

* [Overview](#overview)
* [Getting Started](#getting-started)
* [Core Structure](#core-structure)
* [UI Elements](#ui-elements)

  * [Tabs](#tabs)
  * [Modules](#modules)
  * [Dropdown](#dropdown)
  * [Slider](#slider)
  * [Checkbox](#checkbox)
  * [Divider](#divider)
  * [Paragraph](#paragraph)
  * [Textbox](#textbox)
  * [Feature](#feature)
* [Notifications](#notifications)
* [Custom Example](#custom-example)
* [Best Practices](#best-practices)
* [License](#license)

---

## 🌟 Overview

The **Allusive UI Library** simplifies the creation of complex UIs in Roblox by offering:

* **Modular Design**: Organize UI elements into tabs and modules.
* **Customizable Elements**: Includes dropdowns, sliders, checkboxes, and more.
* **Configuration Management**: Save/load user preferences effortlessly.
* **Built-In Notifications**: Display user-friendly alerts.
* **Responsive UI**: Scales automatically based on device and screen size.

---

## 🚀 Getting Started

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/MarchHubOnTopFr/Allusive-UI/refs/heads/main/Source.lua"))()
local main = Library.new()
main:load()
```

---

## 🧠 Core Structure

### 🔧 `Library`

| Function                                   | Description                            | Parameters                         | Returns         |
| ------------------------------------------ | -------------------------------------- | ---------------------------------- | --------------- |
| `Library.new()`                            | Creates the main UI instance           | None                               | `main` instance |
| `main:load()`                              | Loads the UI and its config            | None                               | None            |
| `Library:get_screen_scale()`               | Gets UI scale factor                   | None                               | `number`        |
| `Library:get_device()`                     | Detects device type (e.g., PC, Mobile) | None                               | `string`        |
| `Library:SendNotification(settings)`       | Sends a notification                   | `{title, text, duration}`          | None            |
| `Library:removed(callback)`                | Registers a cleanup callback           | `function`                         | None            |
| `Library:flag_type(flag, type)`            | Sets flag type                         | `flag`, `type`                     | None            |
| `Library:remove_table_value(table, value)` | Removes value from table               | `table`, `string`                  | None            |
| `Library:create_ui()`                      | Manually creates the UI                | None                               | None            |
| `Library:UIVisiblity()`                    | Toggles visibility                     | None                               | None            |
| `Library:change_visiblity(state)`          | Sets visibility                        | `boolean`                          | None            |
| `Library:update_tabs(tab)`                 | Updates tab appearance                 | `TextButton`                       | None            |
| `Library:update_sections(left, right)`     | Updates module sections                | `ScrollingFrame`, `ScrollingFrame` | None            |

---

## 💾 Config

| Function                  | Description            | Parameters        | Returns |
| ------------------------- | ---------------------- | ----------------- | ------- |
| `Config:save(name, data)` | Saves config to file   | `string`, `table` | None    |
| `Config:load(name, data)` | Loads config from file | `string`, `table` | `table` |

---

## 🧩 UI Elements

### 📁 Tabs

```lua
local tab = main:create_tab("Combat", "rbxassetid://123456789")
```

### 📦 Modules

```lua
local module = tab:create_module({
    title = "Auto Attack",
    flag = "Auto_Attack",
    description = "Automatically attacks enemies",
    section = "left",
    callback = function(value) print("Auto Attack:", value) end
})
```

---

### 🔽 Dropdown

```lua
local dropdown = module:create_dropdown({
    title = "Attack Type",
    flag = "Attack_Type",
    options = {"Melee", "Ranged", "Magic"},
    multi_dropdown = false,
    maximum_options = 1,
    callback = function(value) print("Selected:", value) end
})
```

---

### 🎚️ Slider

```lua
local slider = module:create_slider({
    title = "Attack Speed",
    flag = "Attack_Speed",
    maximum_value = 100,
    minimum_value = 10,
    value = 50,
    round_number = true,
    callback = function(value) print("Speed:", value) end
})
```

---

### ☑️ Checkbox

```lua
module:create_checkbox({
    title = "Enable Critical Hits",
    flag = "Critical_Hits",
    callback = function(value) print("Critical Hits:", value) end
})
```

---

### ➖ Divider

```lua
module:create_divider({})
```

---

### 📝 Paragraph

```lua
module:create_paragraph({
    title = "Warning",
    text = "This feature may affect gameplay balance."
})
```

---

### ⌨️ Textbox

```lua
local textbox = module:create_textbox({
    title = "Player Name",
    placeholder = "Enter name...",
    flag = "Player_Name",
    callback = function(text) print("Name:", text) end
})
```

---

### 🛠️ Feature

```lua
module:create_feature(settings)
-- Custom and advanced component; usage depends on your implementation.
```

---

## 🔔 Notifications

```lua
Library.SendNotification({
    title = "Success",
    text = "Settings saved!",
    duration = 3
})
```

---

## 🧪 Custom Example

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/MarchHubOnTopFr/Allusive-UI/refs/heads/main/Source.lua"))()
local main = Library.new()

-- Tabs
local combat_tab = main:create_tab("Combat", "rbxassetid://76499042599127")
local utility_tab = main:create_tab("Utility", "rbxassetid://126017907477623")

-- Combat Module
local aimbot = combat_tab:create_module({
    title = "Aimbot",
    flag = "Aimbot",
    description = "Locks onto enemies",
    section = "left",
    callback = function(value)
        print("Aimbot enabled:", value)
        Library.SendNotification({
            title = "Aimbot",
            text = value and "Aimbot enabled!" or "Aimbot disabled!",
            duration = 3
        })
    end
})

aimbot:create_dropdown({
    title = "Target Part",
    flag = "Target_Part",
    options = {"Head", "Torso", "Random"},
    multi_dropdown = false,
    maximum_options = 1,
    callback = function(value) print("Targeting:", value) end
})

aimbot:create_slider({
    title = "Aimbot Sensitivity",
    flag = "Aimbot_Sensitivity",
    maximum_value = 100,
    minimum_value = 10,
    value = 50,
    round_number = true,
    callback = function(value) print("Sensitivity:", value) end
})

aimbot:create_checkbox({
    title = "Silent Aim",
    flag = "Silent_Aim",
    callback = function(value) print("Silent Aim:", value) end
})

-- Utility Module
local speedhack = utility_tab:create_module({
    title = "Speed Hack",
    flag = "Speed_Hack",
    description = "Increases player speed",
    section = "right",
    callback = function(value) print("Speed Hack:", value) end
})

speedhack:create_paragraph({
    title = "Info",
    text = "Use responsibly to avoid detection."
})

speedhack:create_textbox({
    title = "Speed Value",
    placeholder = "Enter speed...",
    flag = "Speed_Value",
    callback = function(text) print("Speed set to:", text) end
})

main:load()
```

---

## ✅ Best Practices

* **Modular Layout**: Use tabs and modules to group related functionality.
* **Unique Flags**: Ensure each UI element has a unique `flag` for config management.
* **Responsive Design**: Use `get_screen_scale()` for device compatibility.
* **Test Callbacks**: Handle edge cases and errors in each callback.
* **User Feedback**: Use `SendNotification()` to confirm actions.

---

## 📄 License

**MIT License**
See the [LICENSE](./LICENSE) file for details.
