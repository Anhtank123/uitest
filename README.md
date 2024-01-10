local Rayfield = loadstring(game:HttpGet('https://raw.githubusercontent.com/Anhtank123/menu/main/README.md'))() -- loadstring(game:HttpGet('https://raw.githubusercontent.com/Anhtank123/uitest/main/README.md'))()

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
 local Tab = Window:CreateTab("Tab Example", 4483362458) -- Title, Image 
 local Section = Tab:CreateSection("Section Example")

 local Button = Tab:CreateButton({
    Name = "Refresh",
    Callback = function()
      function activatefly()
         local mouse=game.Players.LocalPlayer:GetMouse''
         localplayer=game.Players.LocalPlayer
         game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart")
         local torso = game.Players.LocalPlayer.Character.HumanoidRootPart
         local speedSET=25
         local keys={a=false,d=false,w=false,s=false}
         local e1
         local e2
         local function start()
            local pos = Instance.new("BodyPosition",torso)
            local gyro = Instance.new("BodyGyro",torso)
            pos.Name="EPIXPOS"
            pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
            pos.position = torso.Position
            gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
            gyro.cframe = torso.CFrame
            repeat
               wait()
               localplayer.Character.Humanoid.PlatformStand=true
               local new=gyro.cframe - gyro.cframe.p + pos.position
               if not keys.w and not keys.s and not keys.a and not keys.d then
                  speed=1
               end
               if keys.w then
                  new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                  speed=speed+speedSET
               end
               if keys.s then
                  new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                  speed=speed+speedSET
               end
               if keys.d then
                  new = new * CFrame.new(speed,0,0)
                  speed=speed+speedSET
               end
               if keys.a then
                  new = new * CFrame.new(-speed,0,0)
                  speed=speed+speedSET
               end
               if speed>speedSET then
                  speed=speedSET
               end
               pos.position=new.p
               if keys.w then
                  gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(-math.rad(speed*90),0,0)
               elseif keys.s then
                  gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(math.rad(speed*90),0,0)
               else
                  gyro.cframe = workspace.CurrentCamera.CoordinateFrame
               end
            until not Fly
            if gyro then 
               gyro:Destroy() 
            end
            if pos then 
               pos:Destroy() 
            end
            flying=false
            localplayer.Character.Humanoid.PlatformStand=false
            speed=0
         end
         e1=mouse.KeyDown:connect(function(key)
            if not torso or not torso.Parent then 
               flying=false e1:disconnect() e2:disconnect() return 
            end
            if key=="w" then
               keys.w=true
            elseif key=="s" then
               keys.s=true
            elseif key=="a" then
               keys.a=true
            elseif key=="d" then
               keys.d=true
            end
         end)
         e2=mouse.KeyUp:connect(function(key)
            if key=="w" then
               keys.w=false
            elseif key=="s" then
               keys.s=false
            elseif key=="a" then
               keys.a=false
            elseif key=="d" then
               keys.d=false
            end
         end)
         start()
      end
      page12:Toggle("Fly",false,function(Value)
         Fly = Value
         activatefly()
      end)
      page11:Toggle("No Clip",false,function(value)
         NoClip = value
      end)
      game:GetService("RunService").Heartbeat:Connect(
      function()
         if NoClip or _G.Observation then
            game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)
         end
      end
      )
    end,
 })
 Button:Set("Button Example")
