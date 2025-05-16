🌌 Allusive UI Library

A sleek, customizable, and modular UI framework for Roblox.
Allusive UI brings elegance and power to your game's interface, with intuitive tab and module management, responsive design, and interactive components — all in a visually clean, space-themed format.


---

🚀 Table of Contents

✨ Overview

🛠️ Getting Started

🧠 Core Structure

🎛️ UI Elements

📁 Tabs

📦 Modules

⬇️ Dropdown

🎚️ Slider

☑️ Checkbox

➖ Divider

📜 Paragraph

⌨️ Textbox

🧩 Feature


🔔 Notifications

🧪 Custom Example

📌 Best Practices

📜 License



---

✨ Overview

Allusive UI is a modular and stylish interface library made for Roblox developers who want a clean, responsive, and powerful UI. Built to scale and perform across devices, it supports:

🚀 Tabs & Modules for structured layout

🎨 Customizable UI elements: dropdowns, sliders, checkboxes, and more

💾 Persistent configurations

🔔 In-game notifications

📱 Device- and screen-responsive scaling



---

🛠️ Getting Started

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/MarchHubOnTopFr/Allusive-UI/refs/heads/main/Source.lua"))()
local main = Library.new()
main:load() -- Initialize UI


---

🧠 Core Structure

Function	Description	Params	Returns

Library.new()	Initializes a new UI instance.	None	main instance
Library:load()	Loads and renders the UI.	None	None
Library:get_screen_scale()	Gets current screen scale.	None	number
Library:get_device()	Detects current device.	None	string
Library:SendNotification(settings)	Sends an in-game notification.	{title, text, duration}	None
Library:removed(callback)	Callback on UI destroy.	function	None
Library:flag_type(flag, type)	Sets a flag type.	flag, type	None
Library:remove_table_value(tbl, val)	Removes value from table.	table, value	None
Library:create_ui()	Initializes framework manually.	None	None
Library:UIVisiblity()	Toggles visibility.	None	None
Library:change_visiblity(state)	Sets UI visibility.	boolean	None
Library:update_tabs(tab)	Refreshes a tab.	TextButton	None
Library:update_sections(left, right)	Refreshes section contents.	ScrollingFrame, ScrollingFrame	None



---

🎛️ UI Elements

📁 Tabs

local tab = main:create_tab("Combat", "rbxassetid://123456")

Function	Description

main:create_tab(title, icon)	Creates a new tab.



---

📦 Modules

local mod = tab:create_module({
  title = "Aimbot", flag = "Aimbot", description = "Locks onto targets", section = "left",
  callback = function(enabled) print("Aimbot:", enabled) end
})

Function	Description

Tab:create_module(settings)	Adds a module to tab.



---

⬇️ Dropdown

local dd = mod:create_dropdown({
  title = "Target", flag = "Target_Part",
  options = {"Head", "Torso", "Legs"},
  multi_dropdown = false, maximum_options = 1,
  callback = function(opt) print("Selected:", opt) end
})

Extra Functions

Dropdown:update(option) – Manually updates selected option.
Dropdown:unfold_settings() – Toggles dropdown open/close.
Dropdown:New(value) – Adds a new option.



---

🎚️ Slider

local slider = mod:create_slider({
  title = "Speed", flag = "Speed_Setting", minimum_value = 1,
  maximum_value = 100, value = 50, round_number = true,
  callback = function(v) print("Speed:", v) end
})

Extra Functions

Slider:set_percentage(%) – Set value by percent.
Slider:update() – Refresh UI display.
Slider:input() – Handle user slider interaction.



---

☑️ Checkbox

mod:create_checkbox({
  title = "Enable Crits", flag = "Enable_Crits",
  callback = function(v) print("Criticals:", v) end
})

Simple boolean toggle, no extra functions.


---

➖ Divider

mod:create_divider({})

Purely visual, used to separate elements in modules.


---

📜 Paragraph

mod:create_paragraph({
  title = "Warning", text = "Using this may be risky."
})

Shows static or informational text.


---

⌨️ Textbox

local box = mod:create_textbox({
  title = "Username", placeholder = "Enter name...",
  flag = "User_Input", callback = function(text) print("Name:", text) end
})

Extra Functions

Textbox:update_text(text) – Programmatically change the textbox content.



---

🧩 Feature (Advanced)

mod:create_feature({
  -- Custom implementation here
})

Dynamic features – behavior defined entirely by developer.


---

🔔 Notifications

Library.SendNotification({
  title = "Saved!", text = "Your settings are saved.", duration = 3
})

title: Notification header

text: Message content

duration: Display time (in seconds)



---

🧪 Custom Example

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/MarchHubOnTopFr/Allusive-UI/refs/heads/main/Source.lua"))()
local main = Library.new()

-- Tabs
local combat_tab = main:create_tab("Combat", "rbxassetid://123456")
local utility_tab = main:create_tab("Utility", "rbxassetid://654321")

-- Combat Module
local aimbot = combat_tab:create_module({
  title = "Aimbot", flag = "Aimbot", description = "Lock on enemies",
  section = "left", callback = function(v)
    print("Aimbot:", v)
    Library.SendNotification({title = "Aimbot", text = v and "Enabled" or "Disabled", duration = 2})
  end
})

aimbot:create_dropdown({
  title = "Target", flag = "Target", options = {"Head", "Torso", "Legs"},
  multi_dropdown = false, maximum_options = 1,
  callback = function(value) print("Targeting:", value) end
})

aimbot:create_slider({
  title = "Sensitivity", flag = "Aim_Sens", maximum_value = 100, minimum_value = 1, value = 50,
  round_number = true, callback = function(val) print("Sens:", val) end
})

aimbot:create_checkbox({
  title = "Silent Aim", flag = "Silent_Aim",
  callback = function(v) print("Silent:", v) end
})

-- Utility Module
local speedhack = utility_tab:create_module({
  title = "Speed Hack", flag = "Speed_Hack",
  description = "Increases movement speed", section = "right",
  callback = function(v) print("Speed Hack Enabled:", v) end
})

speedhack:create_paragraph({
  title = "Info", text = "Use responsibly!"
})

speedhack:create_textbox({
  title = "Speed Value", placeholder = "Enter speed...", flag = "Speed_Val",
  callback = function(txt) print("Speed Set To:", txt) end
})

-- Launch
main:load()


---

📌 Best Practices

Structure Smart: Use tabs/modules to categorize features cleanly.

Unique Flags: Every element must have a unique flag to persist values.

Callback Testing: Ensure your logic works across all devices/states.

Scale Responsively: Use Library:get_screen_scale() to adapt layouts.

Notify Users: Give clear feedback through SendNotification.



---

📜 License

MIT License.
Feel free to use, modify, and distribute with credit.
