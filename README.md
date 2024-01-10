local Rayfield = loadstring(game:HttpGet('https://raw.githubusercontent.com/Anhtank123/menu/main/README.md'))() -- loadstring(game:HttpGet('https://raw.githubusercontent.com/Anhtank123/uitest/main/README.md'))()
local Keybind = Tab:CreateKeybind({
   Name = "Keybind Example",
   CurrentKeybind = "Q",
   HoldToInteract = false,
   Flag = "Keybind1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Keybind)
   -- The function that takes place when the keybind is pressed
   -- The variable (Keybind) is a boolean for whether the keybind is being held or not (HoldToInteract needs to be true)
   end,
})
Keybind:Set("RightCtrl") -- Keybind (string)

local Window = Rayfield:CreateWindow({
    Name = "Khanh Hub",
    LoadingTitle = "Wellcome to Khanh Hub",
    LoadingSubtitle = "a hub by Khanh",
    ConfigurationSaving = {
       Enabled = true,
       FolderName = nil, -- Create a custom folder for your hub/game
       FileName = "Big Hub"
    },
    Discord = {
       Enabled = false,
       Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ABCD would be ABCD
       RememberJoins = true -- Set this to false to make them join the discord every time they load it up
    },
    KeySystem = false, -- Set this to true to use our key system (de sau)
    KeySettings = {
       Title = "Key System",
       Subtitle = "",
       Note = "KEY = khanh",
       FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
       SaveKey = false, -- The user's key will be saved, but if you change the key, they will be unable to use your script
       GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
       Key = {"khanh"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
    }
 })
 local Tab = Window:CreateTab("Tab Example") -- Title, Image 
 local Section = Tab:CreateSection("Section Example")

 local Button = Tab:CreateButton({
    Name = "Refresh",
    Callback = function()
    -- The function that takes place when the button is pressed
    end,
 })
 Button:Set("Button Example")

 local Toggle = Tab:CreateToggle({
   Name = "Fly",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})
Toggle:Set(false)
