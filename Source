if game.PlaceId == 155615604 then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("Prison Life", "BloodTheme")
    
    getgenv().godmode = false
    getgenv().noclip = false
    getgenv().alerts = false
    getgenv().changedwalkspeed = false
    getgenv().walkspeed = 0
    getgenv().changedjumppower = false
    getgenv().jumppower = 0
    getgenv().changedhipheight = false
    getgenv().hipheight = 0
    getgenv().onepunch = false
    



    -- Welcome
    local Welcome = Window:NewTab("Welcome")
    local WelcomeSection = Welcome:NewSection("Welcome")

    WelcomeSection:NewButton("Hi!Gay", "Gay", function()
        print("Clicked")
    end)








    -- MAIN
    local Main = Window:NewTab("Main")
    local MainSection = Main:NewSection("Main")

    MainSection:NewButton("No Doors","Removes All Doors",function()
        game.Workspace.Doors:Destroy()
        game.Workspace.Prison_Cellblock.doors:Destroy()
        local Warehouses = game.Workspace.Warehouses
        for i,v in pairs(Warehouses:GetDescendants()) do
            if v.Name == "doors" then
               v:Destroy()
            end
        end
    end)

    MainSection:NewDropdown("Change Team","Changes your team",{"Criminal","Neutral","Gaurd","Inmate"},function(v)
        if v == "Criminal" then
            local weld02 = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-919.958, 95.327, 2138.189)
    		wait(1)
    		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(weld02)
        elseif v == "Inmate" then
            game.Workspace.Remote.TeamEvent:FireServer("Bright orange")
        elseif v == "Gaurd" then
            game.Workspace.Remote.TeamEvent:FireServer("Bright blue")
        elseif v == "Neutral" then
            game.Workspace.Remote.TeamEvent:FireServer("Medium stone grey")
        end
    end)

    MainSection:NewButton("Server Hop","Joins a new server",function()
        local Servers = game.HttpService:JSONDecode(game:HttpGet("https://games.roblox.com/v1/games/"..game.PlaceId.."/servers/Public?sortOrder=Asc&limit=100"))
        for i,v in pairs(Servers.data) do
    		if v.playing ~= v.maxPlayers then
    			game:GetService('TeleportService'):TeleportToPlaceInstance(game.PlaceId, v.id)
    		end
    	end
    end)

    MainSection:NewButton("Rejoin","Rejoins the server", function()
        game:GetService("TeleportService"):Teleport(game.PlaceId)
    end)
    



  

 

 
    -- PLAYER
    local Player = Window:NewTab("Player")
    local PlayerSection = Player:NewSection("Player")
 

 
    
    PlayerSection:NewToggle("Noclip", "Noclip anything", function(state)
        getgenv().noclip = state
    end)

    PlayerSection:NewTextBox("WalkSpeed","Sets your WalkSpeed",function(txt)
        getgenv().changedwalkspeed = true
        if tonumber(txt) then
            getgenv().walkspeed = tonumber(txt)
        end
    end)
    
    PlayerSection:NewTextBox("JumpPower","Sets your JumpPower",function(txt)
        getgenv().changedjumppower = true
        if tonumber(txt) then
            getgenv().jumppower = tonumber(txt)
        end
    end)

    PlayerSection:NewButton("Flight (E)","Allows you to fly",function()
        repeat wait()
        until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Torso") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid")
        local mouse = game.Players.LocalPlayer:GetMouse()
        repeat wait() until mouse
        local plr = game.Players.LocalPlayer
        local torso = plr.Character.Torso
        local deb = true
        local ctrl = {f = 0, b = 0, l = 0, r = 0}
        local lastctrl = {f = 0, b = 0, l = 0, r = 0}
        local maxspeed = 50
        local speed = 0
        
        function Fly()
            local bg = Instance.new("BodyGyro", torso)
            bg.P = 9e4
            bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
            bg.cframe = torso.CFrame
            local bv = Instance.new("BodyVelocity", torso)
            bv.velocity = Vector3.new(0,0.1,0)
            bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
            repeat wait()
            plr.Character.Humanoid.PlatformStand = true
            if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then
            speed = speed+.5+(speed/maxspeed)
            if speed > maxspeed then
            speed = maxspeed
            end
            elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then
            speed = speed-1
            if speed < 0 then
            speed = 0
            end
            end
            if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then
            bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
            lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r}
            elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then
            bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
            else
            bv.velocity = Vector3.new(0,0.1,0)
            end
            bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0)
            until not flying
            ctrl = {f = 0, b = 0, l = 0, r = 0}
            lastctrl = {f = 0, b = 0, l = 0, r = 0}
            speed = 0
            bg:Destroy()
            bv:Destroy()
            plr.Character.Humanoid.PlatformStand = false
            end
            mouse.KeyDown:connect(function(key)
            if key:lower() == "e" then
            if flying then flying = false
            else
            flying = true
            Fly()
            end
            elseif key:lower() == "w" then
            ctrl.f = 1
            elseif key:lower() == "s" then
            ctrl.b = -1
            elseif key:lower() == "a" then
            ctrl.l = -1
            elseif key:lower() == "d" then
            ctrl.r = 1
        end
    end)
        mouse.KeyUp:connect(function(key)
        if key:lower() == "w" then
        ctrl.f = 0
        elseif key:lower() == "s" then
        ctrl.b = 0
        elseif key:lower() == "a" then
        ctrl.l = 0
        elseif key:lower() == "d" then
        ctrl.r = 0
        end
        end)
        Fly()
    end)

    PlayerSection:NewToggle("Inf Respawns","Automatically respawns you",function(state)
        getgenv().godmode = state
   end)

    PlayerSection:NewToggle("Inf Stamina","Infinite Stamina",function(state)
    getgenv().infstamina = state
    if state == false then
        local plr = game:GetService("Players").LocalPlayer
        for i,v in next, getgc() do 
            if type(v) == "function" and getfenv(v).script and getfenv(v).script == plr.Character.ClientInputHandler then 
                for i2,v2 in next, debug.getupvalues(v) do 
                    if type(v2) == "number" then 
                        debug.setupvalue(v, i2, 12)
                    end
                end
            end
        end
    else
        local plr = game:GetService("Players").LocalPlayer
        for i,v in next, getgc() do 
            if type(v) == "function" and getfenv(v).script and getfenv(v).script == plr.Character.ClientInputHandler then 
                for i2,v2 in next, debug.getupvalues(v) do 
                    if type(v2) == "number" then 
                        debug.setupvalue(v, i2, math.huge)
                    end
                end
            end
        end
    end
end)

PlayerSection:NewToggle("Super Punch","Kills anyone with one punch",function(state)
    getgenv().onepunch = state
end)

PlayerSection:NewButton("Reset","Resets your character", function()
    game.Workspace.Remote.loadchar:InvokeServer(game.Players.LocalPlayer.Name)
end)

    -- Guns
    local Guns = Window:NewTab("Guns")
    local GunsSection = Guns:NewSection("Guns")

    GunsSection:NewDropdown("Give Gun", "Gives the localplayer a gun", {"M9", "Remington 870", "AK-47"}, function(v)
        local A_1 = game:GetService("Workspace")["Prison_ITEMS"].giver[v].ITEMPICKUP
        local Event = game:GetService("Workspace").Remote.ItemHandler
        Event:InvokeServer(A_1)
    end)
 
    GunsSection:NewDropdown("Gun Mod", "Makes the gun op", {"M9", "Remington 870", "AK-47"}, function(v)
        local module = nil
        if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(v) then
            module = require(game:GetService("Players").LocalPlayer.Backpack[v].GunStates)
        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(v) then
            module = require(game:GetService("Players").LocalPlayer.Character[v].GunStates)
        end
        if module ~= nil then
            module["MaxAmmo"] = math.huge
            module["CurrentAmmo"] = math.huge
            module["StoredAmmo"] = math.huge
            module["FireRate"] = 0.000001
            module["Spread"] = 0
            module["Range"] = math.huge
            module["Bullets"] = 10
            module["ReloadTime"] = 0.000001
            module["AutoFire"] = true
        end
    end)      










    -- Teleport
    local Teleport = Window:NewTab("Teleport")
    local TeleportSection = Teleport:NewSection("Teleport")

    TeleportSection:NewButton("Criminal Base","Teleports to the Criminal Base",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-859.15161132813, 94.476051330566, 2058.5427246094)
    end)
    
    TeleportSection:NewButton("Downtown","Teleports you to down town",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-300.44033813477, 54.175037384033, 1781.2364501953)
    end)
    
    TeleportSection:NewButton("Entrance Gate","Teleports you to the entrance gate",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(491.27182006836, 98.039939880371, 2216.3107910156)
    end)
    
    TeleportSection:NewButton("Entrance","Teleports you to the entrance",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(653.81713867188, 99.990005493164, 2272.083984375)
    end)
    
    TeleportSection:NewButton("Yard","Teleports you to the yard",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(781.6845703125, 97.999946594238, 2462.8779296875)
    end)
    
    TeleportSection:NewButton("Hallway","Teleports you to the hallway",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(860.78448486328, 99.990005493164, 2362.9597167969)
    end)
    
    TeleportSection:NewButton("Cell Block","Teleports you to the cell block",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(918.43115234375, 99.989990234375, 2440.3828125)
    end)
    
    TeleportSection:NewButton("Cafeteria","Teleports you to the cafeteria",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(932.06213378906, 99.989959716797, 2290.4250488281)
    end)
    
    TeleportSection:NewButton("Armory","Teleports you to the armory",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(835.28918457031, 99.990005493164, 2285.4909667969)
    end)
    
    TeleportSection:NewButton("Gaurds Only","Teleports you to the gaurds only room",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(830.04302978516, 99.990005493164, 2327.0859375)
    end)

    -- Misc
    local Misc = Window:NewTab("Misc")
    local MiscSection = Misc:NewSection("Misc")

    MiscSection:NewTextBox("Arrest Player", "Arrest the player", function(txt)
        if txt == "all" then
            for i,v in pairs(game.Teams.Criminals:GetPlayers()) do
                if v ~= game.Players.LocalPlayer then
                    i = 0
                    repeat wait()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Character.HumanoidRootPart.CFrame
                        game.Workspace.Remote.arrest:InvokeServer(v.Character.HumanoidRootPart)
                        i = i + 1
                    until i == 10
                end
            end
        else
        	local plr = findplayer(txt)
            if plr then
                local i = 0
                repeat wait()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = plr.Character.HumanoidRootPart.CFrame
                    game.Workspace.Remote.arrest:InvokeServer(plr.Character.HumanoidRootPart)
                    i = i + 1
                until i == 10
            end
        end
    end)
    
    MiscSection:NewTextBox("To Player", "Teleports to the player", function(txt)
    	local plr = findplayer(txt)
        if plr then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = plr.Character.HumanoidRootPart.CFrame
    	end
    end)

    MiscSection:NewTextBox("Bring Player","Brings a player to you",function(txt)
        game.Workspace.Remote.ItemHandler:InvokeServer(game.Workspace.Prison_ITEMS.giver["Remington 870"].ITEMPICKUP)
            local Target = findplayer(txt).Name
            if Target then
                NOW = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
                game.Players.LocalPlayer.Character.Humanoid.Name = 1
                local l = game.Players.LocalPlayer.Character["1"]:Clone()
                l.Parent = game.Players.LocalPlayer.Character
                l.Name = "Humanoid"
                wait()
                game.Players.LocalPlayer.Character["1"]:Destroy()
                game.Workspace.CurrentCamera.CameraSubject = game.Players.LocalPlayer.Character
                game.Players.LocalPlayer.Character.Animate.Disabled = true
                wait()
                game.Players.LocalPlayer.Character.Animate.Disabled = false
                game.Players.LocalPlayer.Character.Humanoid.DisplayDistanceType = "None"
                game.Players.LocalPlayer.Character.Humanoid:EquipTool(game.Players.LocalPlayer.Backpack["Remington 870"])
                local function tp(player,player2)
                local char1,char2=player.Character,player2.Character
                if char1 and char2 then
                char1.HumanoidRootPart.CFrame = char2.HumanoidRootPart.CFrame
                end
                end
                local function getout(player,player2)
                local char1,char2=player.Character,player2.Character
                if char1 and char2 then
                char1:MoveTo(char2.Head.Position)
                end
                end
                tp(game.Players[Target], game.Players.LocalPlayer)
                wait()
                tp(game.Players[Target], game.Players.LocalPlayer)
                wait()
                getout(game.Players.LocalPlayer, game.Players[Target])
                wait(5)
                game.Workspace.Remote.loadchar:InvokeServer(game.Players.LocalPlayer.Name)
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = NOW
            end
    end)
    
    MiscSection:NewTextBox("Make Criminal","Makes the player a criminal (Takes one or two tries)",function(txt)
        game.Workspace.Remote.ItemHandler:InvokeServer(game.Workspace.Prison_ITEMS.giver["Remington 870"].ITEMPICKUP)
        local Target = findplayer(txt).Name
        if Target then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-919.958, 95.327, 2138.189)
            game.Players.LocalPlayer.Character.Humanoid.Name = 1
            local l = game.Players.LocalPlayer.Character["1"]:Clone()
            l.Parent = game.Players.LocalPlayer.Character
            l.Name = "Humanoid"
            wait()
            game.Players.LocalPlayer.Character["1"]:Destroy()
            game.Workspace.CurrentCamera.CameraSubject = game.Players.LocalPlayer.Character
            game.Players.LocalPlayer.Character.Animate.Disabled = true
            wait()
            game.Players.LocalPlayer.Character.Animate.Disabled = false
            game.Players.LocalPlayer.Character.Humanoid.DisplayDistanceType = "None"
            game.Players.LocalPlayer.Character.Humanoid:EquipTool(game.Players.LocalPlayer.Backpack["Remington 870"])
            local function tp(player,player2)
            local char1,char2=player.Character,player2.Character
            if char1 and char2 then
            char1.HumanoidRootPart.CFrame = char2.HumanoidRootPart.CFrame
            end
            end
            local function getout(player,player2)
            local char1,char2=player.Character,player2.Character
            if char1 and char2 then
            char1:MoveTo(char2.Head.Position)
            end
            end
            tp(game.Players[Target], game.Players.LocalPlayer)
            wait()
            tp(game.Players[Target], game.Players.LocalPlayer)
            wait()
            getout(game.Players.LocalPlayer, game.Players[Target])
            wait(1)
            game.Workspace.Remote.loadchar:InvokeServer(game.Players.LocalPlayer.Name)
        end
    end)

    -- Settings
    local Settings = Window:NewTab("Settings")
    local SettingsSection = Settings:NewSection("Settings")

    SettingsSection:NewKeybind("Keybind to close UI", "Hotkey close UI", Enum.KeyCode.F, function()
        Library:ToggleUI()
    end)


    

end


