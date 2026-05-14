-- ==========================================================
-- SCRULI HUB BRO GIVE ME MY SOURCE BACK             
--                                   
-- ==========================================================

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local LocalPlayer = Players.LocalPlayer


local networkDir = ReplicatedStorage:WaitForChild("Shared"):WaitForChild("Packages"):WaitForChild("Network")
local kickEvent = networkDir:WaitForChild("rev_KickEvent")
local strengthEvent = networkDir:WaitForChild("rev_TaviMishkal")
local speedUpgradeEvent = networkDir:WaitForChild("rev_SPEED_UPGRADE")
local rebirthEvent = networkDir:WaitForChild("rev_RebirthRequest")
local stealEvent = networkDir:WaitForChild("rev_S_Steal")
local kickCollectEvent = networkDir:FindFirstChild("rev_KickCollect")
local bonusCollectEvent = networkDir:FindFirstChild("rev_B_Collect")

local _G = {
    AutoKick = false,
    AutoCollect = false,
    AutoStrength = false,
    AutoSpeed = false,
    AutoRebirth = false,
    AutoSteal = false,
    DodgeEnabled = false,
    ESP = false,
    SpeedBoost = false,
    Orbit = false,
    Blind = false,
    Annoy = false,
    FlingAll = false,
    FakeLag = false,
    ChatSpam = false
}


function LoadRayfield() 
    local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

    local Window = Rayfield:CreateWindow({
        Name = "scruli hub | Developed fort_guys123",
        LoadingTitle = "loading the  Hub...",
        LoadingSubtitle = "Connecting to the server",
        ConfigurationSaving = { Enabled = false },
        Discord = { 
            Enabled = true, 
            Invite = "bFJmhqcUXG", 
            RememberJoins = true 
        },
        KeySystem = false 
    })

 
    local FarmTab = Window:CreateTab("Auto Farm", 4483362458)
    local PlayerTab = Window:CreateTab("player/visual", 4483362458)
    local TrollTab = Window:CreateTab("Troll ", 4483362458)

-- ==========================================
--FARM
-- ==========================================
FarmTab:CreateSection("FARM")


local function getKickReadyPart()
    for _, v in pairs(Workspace:GetDescendants()) do
        if string.lower(v.Name) == "kickready" and v:IsA("BasePart") then
            return v
        end
    end
    return nil
end

FarmTab:CreateButton({
    Name = "AUTO KICK PERFECT (CLICK 2 TIME)",
    Callback = function()
        local char = LocalPlayer.Character
        local hrp = char and char:FindFirstChild("HumanoidRootPart")
        
      
        if hrp then
            local readyPart = getKickReadyPart()
            if readyPart then
                hrp.CFrame = readyPart.CFrame * CFrame.new(0, 3, 0)
            end
        end
        
      
        local args = { [1] = 1, [2] = 1 }
        pcall(function() 
            if kickEvent then
                kickEvent:FireServer(unpack(args)) 
            end
        end)
    end,
})

FarmTab:CreateToggle({
    Name = "Auto Collect (monney)",
    CurrentValue = false,
    Flag = "ToggleCollect",
    Callback = function(Value)
        _G.AutoCollect = Value
        while _G.AutoCollect do
            pcall(function() 
                if kickCollectEvent then kickCollectEvent:FireServer() end
                if bonusCollectEvent then 
                  
                    for i = 1, 100 do
                        bonusCollectEvent:FireServer(i)
                    end
                end
            end)
            task.wait(0.5)
        end
    end,
})

FarmTab:CreateToggle({
    Name = "AUTO TRAINING",
    CurrentValue = false,
    Flag = "ToggleStrength",
    Callback = function(Value)
        _G.AutoStrength = Value
        while _G.AutoStrength do
            pcall(function() strengthEvent:FireServer() end)
            task.wait(0.1)
        end
    end,
})

FarmTab:CreateSection("upgrade")

FarmTab:CreateToggle({
    Name = "AUTO BUY SPEED",
    CurrentValue = false,
    Flag = "ToggleSpeed",
    Callback = function(Value)
        _G.AutoSpeed = Value
        while _G.AutoSpeed do
            pcall(function() speedUpgradeEvent:FireServer(1) end)
            task.wait(0.5)
        end
    end,
})

FarmTab:CreateToggle({
    Name = "Auto Rebirth",
    CurrentValue = false,
    Flag = "ToggleRebirth",
    Callback = function(Value)
        _G.AutoRebirth = Value
        while _G.AutoRebirth do
            pcall(function() rebirthEvent:FireServer() end)
            task.wait(1)
        end
    end,
})

FarmTab:CreateToggle({
    Name = "Auto Steal (Walk to Zone)",
    CurrentValue = false,
    Flag = "ToggleSteal",
    Callback = function(Value)
        _G.AutoSteal = Value
        while _G.AutoSteal do
            
            pcall(function() transformEvent:FireServer() end)
            
            local char = LocalPlayer.Character
            local hrp = char and char:FindFirstChild("HumanoidRootPart")
            local hum = char and char:FindFirstChildOfClass("Humanoid")
            
            
            local readyPart = getKickReadyPart() 
            
            if hrp and hum and readyPart then

                local lookAtPos = Vector3.new(readyPart.Position.X, hrp.Position.Y, readyPart.Position.Z)
                hrp.CFrame = CFrame.lookAt(hrp.Position, lookAtPos)
                
                
                hum:MoveTo(readyPart.Position)
            end
            
            task.wait(0.1) 
        end
        
        
        if not _G.AutoSteal then
            local char = LocalPlayer.Character
            local hum = char and char:FindFirstChildOfClass("Humanoid")
            local hrp = char and char:FindFirstChild("HumanoidRootPart")
            if hum and hrp then
                hum:MoveTo(hrp.Position)
            end
        end
    end,
})


PlayerTab:CreateSection("Capacités de Combat")

PlayerTab:CreateToggle({
    Name = "BOOST (q keybind)",
    CurrentValue = false,
    Flag = "ToggleDodge",
    Callback = function(Value)
        _G.DodgeEnabled = Value
    end,
})

local function PerformGroundDodge()
    local char = LocalPlayer.Character
    local hrp = char and char:FindFirstChild("HumanoidRootPart")
    local humanoid = char and char:FindFirstChildOfClass("Humanoid")
    

    if humanoid and hrp and humanoid.MoveDirection.Magnitude > 0 then
        local velocity = Instance.new("BodyVelocity")
        velocity.MaxForce = Vector3.new(100000, 0, 100000) 
        velocity.Velocity = humanoid.MoveDirection * 150
        velocity.Parent = hrp
        game:GetService("Debris"):AddItem(velocity, 0.18)
    end
end

UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if not gameProcessed and _G.DodgeEnabled and input.KeyCode == Enum.KeyCode.Q then
        PerformGroundDodge()
    end
end)


PlayerTab:CreateSection("VISUAL")

PlayerTab:CreateToggle({
    Name = "ESP PLAYER",
    CurrentValue = false,
    Flag = "ToggleESP",
    Callback = function(Value)
        _G.ESP = Value
        while _G.ESP do
            for _, player in pairs(Players:GetPlayers()) do
                if player ~= LocalPlayer and player.Character then
                    if not player.Character:FindFirstChild("RayfieldESP") then
                        local highlight = Instance.new("Highlight")
                        highlight.Name = "RayfieldESP"
                        highlight.FillColor = Color3.fromRGB(255, 0, 0)
                        highlight.OutlineColor = Color3.fromRGB(255, 255, 255)
                        highlight.FillTransparency = 0.5
                        highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                        highlight.Parent = player.Character
                    end
                end
            end
            task.wait(1)
        end
        if not _G.ESP then
            for _, player in pairs(Players:GetPlayers()) do
                if player.Character and player.Character:FindFirstChild("RayfieldESP") then
                    player.Character.RayfieldESP:Destroy()
                end
            end
        end
    end,
})

PlayerTab:CreateSection("MISC")

local infJumpConnection
PlayerTab:CreateToggle({
    Name = "Infinity Jump ",
    CurrentValue = false,
    Flag = "ToggleInfJump",
    Callback = function(Value)
        _G.InfJump = Value
        if _G.InfJump then
            
            infJumpConnection = UserInputService.JumpRequest:Connect(function()
                local char = LocalPlayer.Character
                local hum = char and char:FindFirstChildOfClass("Humanoid")
                if hum then
                    hum:ChangeState(Enum.HumanoidStateType.Jumping)
                end
            end)
        else
            if infJumpConnection then infJumpConnection:Disconnect() end
        end
    end,
})

local floatForce
PlayerTab:CreateToggle({
    Name = "Float ",
    CurrentValue = false,
    Flag = "ToggleFloat",
    Callback = function(Value)
        _G.Float = Value
        local char = LocalPlayer.Character
        local hrp = char and char:FindFirstChild("HumanoidRootPart")

        if _G.Float and hrp then
            floatForce = Instance.new("BodyVelocity")
            floatForce.Name = "FloatVelocity"
            -- Bloque uniquement la gravité (Axe Y) pour te faire flotter sans t'empêcher d'avancer
            floatForce.MaxForce = Vector3.new(0, 100000, 0) 
            floatForce.Velocity = Vector3.new(0, 0, 0)
            floatForce.Parent = hrp
        else
            if hrp and hrp:FindFirstChild("FloatVelocity") then
                hrp.FloatVelocity:Destroy()
            end
        end
    end,
})

PlayerTab:CreateToggle({
    Name = "Noclip ",
    CurrentValue = false,
    Flag = "ToggleNoclip",
    Callback = function(Value)
        _G.Noclip = Value
        if _G.Noclip then
            _G.NoclipConnection = RunService.Stepped:Connect(function()
                local char = LocalPlayer.Character
                if char then
                    for _, part in pairs(char:GetDescendants()) do
                        if part:IsA("BasePart") and part.CanCollide == true then
                            part.CanCollide = false
                        end
                    end
                end
            end)
        else
            if _G.NoclipConnection then _G.NoclipConnection:Disconnect() end
        end
    end,
})

PlayerTab:CreateSection("EXTRA")

PlayerTab:CreateToggle({
    Name = "Fullbright ",
    CurrentValue = false,
    Flag = "ToggleFullbright",
    Callback = function(Value)
        if Value then
            game.Lighting.Ambient = Color3.new(1, 1, 1)
            game.Lighting.OutdoorAmbient = Color3.new(1, 1, 1)
        else
            game.Lighting.Ambient = Color3.fromRGB(128, 128, 128)
            game.Lighting.OutdoorAmbient = Color3.fromRGB(128, 128, 128)
        end
    end,
})


-- ==========================================
-- ONGLET 3 : TROLL & CHAOS
-- ==========================================
TrollTab:CreateSection("BULLY")

local function GetClosestPlayer()
    local closest = nil
    local shortestDist = math.huge
    local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
    if hrp then
        for _, p in pairs(Players:GetPlayers()) do
            if p ~= LocalPlayer and p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
                local dist = (p.Character.HumanoidRootPart.Position - hrp.Position).Magnitude
                if dist < shortestDist then
                    shortestDist = dist
                    closest = p
                end
            end
        end
    end
    return closest
end

TrollTab:CreateToggle({
    Name = "Orbit",
    CurrentValue = false,
    Flag = "ToggleOrbit",
    Callback = function(Value)
        _G.Orbit = Value
        while _G.Orbit do
            local target = GetClosestPlayer()
            local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            if target and hrp then
                local targetHrp = target.Character.HumanoidRootPart
                hrp.CFrame = targetHrp.CFrame * CFrame.Angles(0, tick() * 10, 0) * CFrame.new(0, 0, 5)
            end
            task.wait()
        end
    end,
})

TrollTab:CreateToggle({
    Name = "Blind ",
    CurrentValue = false,
    Flag = "ToggleBlind",
    Callback = function(Value)
        _G.Blind = Value
        while _G.Blind do
            local target = GetClosestPlayer()
            local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            if target and hrp then
                hrp.CFrame = target.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0.5, -1.5)
            end
            task.wait()
        end
    end,
})

TrollTab:CreateToggle({
    Name = "Annoy )",
    CurrentValue = false,
    Flag = "ToggleAnnoy",
    Callback = function(Value)
        _G.Annoy = Value
        while _G.Annoy do
            local target = GetClosestPlayer()
            local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            if target and hrp then
                hrp.CFrame = target.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, 3)
            end
            task.wait()
        end
    end,
})

TrollTab:CreateSection("GLOBAL")

TrollTab:CreateToggle({
    Name = "Fling All ",
    CurrentValue = false,
    Flag = "ToggleFling",
    Callback = function(Value)
        _G.FlingAll = Value
        local char = LocalPlayer.Character
        local hrp = char and char:FindFirstChild("HumanoidRootPart")
        local hum = char and char:FindFirstChildOfClass("Humanoid")

        if _G.FlingAll and hrp and hum then
            hum.PlatformStand = true
            local spinForce = Instance.new("BodyAngularVelocity")
            spinForce.Name = "TrollSpin"
            spinForce.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
            spinForce.AngularVelocity = Vector3.new(0, 50000, 0)
            spinForce.Parent = hrp

            task.spawn(function()
                while _G.FlingAll do
                    for _, targetPlayer in pairs(Players:GetPlayers()) do
                        if targetPlayer ~= LocalPlayer and _G.FlingAll then
                            local targetChar = targetPlayer.Character
                            local targetHrp = targetChar and targetChar:FindFirstChild("HumanoidRootPart")
                            if targetHrp then
                                local timer = tick()
                                while _G.FlingAll and tick() - timer < 0.2 and targetHrp.Parent do
                                    hrp.CFrame = targetHrp.CFrame
                                    hrp.Velocity = Vector3.new(math.random(-5000, 5000), 5000, math.random(-5000, 5000))
                                    task.wait(0.01)
                                end
                            end
                        end
                    end
                    task.wait()
                end
                if hrp:FindFirstChild("TrollSpin") then hrp.TrollSpin:Destroy() end
                hrp.Velocity = Vector3.new(0,0,0)
                hum.PlatformStand = false 
            end)
        end
    end,
})

TrollTab:CreateToggle({
    Name = "Fake Lag ",
    CurrentValue = false,
    Flag = "ToggleLag",
    Callback = function(Value)
        _G.FakeLag = Value
        while _G.FakeLag do
            local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            if hrp then
                hrp.Anchored = true
                task.wait(0.3)
                hrp.Anchored = false
                task.wait(0.5)
            else
                task.wait(0.1)
            end
        end
        local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
        if hrp then hrp.Anchored = false end
    end,
})

TrollTab:CreateToggle({
    Name = "Chat Spammer",
    CurrentValue = false,
    Flag = "ToggleChat",
    Callback = function(Value)
        _G.ChatSpam = Value
        local messages = {"EZ KICK A LUCKY BLOCK!", "SCRULI HUB ON TOP", "Imagine playing legit...", "You are too slow!"}
        while _G.ChatSpam do
            local msg = messages[math.random(1, #messages)]
            pcall(function() game:GetService("TextChatService").TextChannels.RBXGeneral:SendAsync(msg) end)
            pcall(function() game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(msg, "All") end)
            task.wait(2.5)
        end
    end,
})

TrollTab:CreateSection("Troll")




TrollTab:CreateButton({
    Name = "Clone Illusion (put a fake body)",
    Callback = function()
        local char = LocalPlayer.Character
        if char then
            char.Archivable = true
            local clone = char:Clone()
            clone.Parent = Workspace
            
            -- Nettoie les scripts du clone pour ne pas bugger le jeu
            for _, v in pairs(clone:GetDescendants()) do
                if v:IsA("Script") or v:IsA("LocalScript") then
                    v:Destroy()
                end
            end
            
            Rayfield:Notify({
                Title = "Illusion",
                Content = "Clone did!",
                Duration = 3,
                Image = 4483362458,
            })
        end
    end,
})

Rayfield:Notify({
    Title = "Succès",
    Content = "scruli hub loaded!",
    Duration = 5,
    Image = 4483362458,
})
end


local CorrectKey = "SCRULI67" 
local DiscordLink = "https://discord.gg/bFJmhqcUXG" 

local TweenService = game:GetService("TweenService")
local Lighting = game:GetService("Lighting")
local CoreGui = game:GetService("CoreGui")


if CoreGui:FindFirstChild("CyberKeyUI_LO") then CoreGui.CyberKeyUI_LO:Destroy() end
if Lighting:FindFirstChild("CyberBlur_LO") then Lighting.CyberBlur_LO:Destroy() end


local BlurEffect = Instance.new("BlurEffect")
BlurEffect.Name = "CyberBlur_LO"
BlurEffect.Size = 0
BlurEffect.Parent = Lighting
TweenService:Create(BlurEffect, TweenInfo.new(1), {Size = 15}):Play()

local UI = Instance.new("ScreenGui")
UI.Name = "CyberKeyUI_LO"
UI.Parent = CoreGui
UI.ResetOnSpawn = false


local MainFrame = Instance.new("Frame")
MainFrame.Size = UDim2.new(0, 320, 0, 240)
MainFrame.Position = UDim2.new(0.5, -160, 0.5, -120)
MainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 12)
MainFrame.Parent = UI
Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 15)


local Stroke = Instance.new("UIStroke", MainFrame)
Stroke.Color = Color3.fromRGB(0, 160, 255)
Stroke.Thickness = 2
Stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border


local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0, 45)
Title.BackgroundTransparency = 1
Title.Text = "SCRULI HUB"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBlack
Title.TextSize = 22
Title.Parent = MainFrame

local Subtitle = Instance.new("TextLabel")
Subtitle.Size = UDim2.new(1, 0, 0, 15)
Subtitle.Position = UDim2.new(0, 0, 0, 38)
Subtitle.BackgroundTransparency = 1
Subtitle.Text = "AUTHENTICATION SYSTEM"
Subtitle.TextColor3 = Color3.fromRGB(0, 160, 255)
Subtitle.Font = Enum.Font.GothamBold
Subtitle.TextSize = 9
Subtitle.Parent = MainFrame


local KeyInput = Instance.new("TextBox")
KeyInput.Size = UDim2.new(0, 260, 0, 40)
KeyInput.Position = UDim2.new(0.5, -130, 0, 75)
KeyInput.BackgroundColor3 = Color3.fromRGB(18, 18, 22)
KeyInput.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyInput.PlaceholderText = "••••••••••••"
KeyInput.PlaceholderColor3 = Color3.fromRGB(60, 60, 70)
KeyInput.Font = Enum.Font.GothamSemibold
KeyInput.TextSize = 14
KeyInput.Parent = MainFrame
Instance.new("UICorner", KeyInput).CornerRadius = UDim.new(0, 8)
local InputStroke = Instance.new("UIStroke", KeyInput)
InputStroke.Color = Color3.fromRGB(30, 30, 35)


local SubmitBtn = Instance.new("TextButton")
SubmitBtn.Size = UDim2.new(0, 260, 0, 40)
SubmitBtn.Position = UDim2.new(0.5, -130, 0, 130)
SubmitBtn.BackgroundColor3 = Color3.fromRGB(0, 160, 255)
SubmitBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
SubmitBtn.Text = "LOGIN"
SubmitBtn.Font = Enum.Font.GothamBlack
SubmitBtn.TextSize = 14
SubmitBtn.AutoButtonColor = false
SubmitBtn.Parent = MainFrame
Instance.new("UICorner", SubmitBtn).CornerRadius = UDim.new(0, 8)


local DiscordBtn = Instance.new("TextButton")
DiscordBtn.Size = UDim2.new(0, 260, 0, 35)
DiscordBtn.Position = UDim2.new(0.5, -130, 0, 180)
DiscordBtn.BackgroundColor3 = Color3.fromRGB(25, 25, 28)
DiscordBtn.TextColor3 = Color3.fromRGB(180, 180, 190)
DiscordBtn.Text = "JOIN DISCORD FOR KEY"
DiscordBtn.Font = Enum.Font.GothamBold
DiscordBtn.TextSize = 12
DiscordBtn.Parent = MainFrame
Instance.new("UICorner", DiscordBtn).CornerRadius = UDim.new(0, 8)


local function Animate(obj, prop, val)
    TweenService:Create(obj, TweenInfo.new(0.3, Enum.EasingStyle.Quint), {[prop] = val}):Play()
end

SubmitBtn.MouseEnter:Connect(function() Animate(SubmitBtn, "BackgroundColor3", Color3.fromRGB(0, 190, 255)) end)
SubmitBtn.MouseLeave:Connect(function() Animate(SubmitBtn, "BackgroundColor3", Color3.fromRGB(0, 160, 255)) end)

DiscordBtn.MouseButton1Click:Connect(function()
    pcall(function() setclipboard(DiscordLink) end)
    DiscordBtn.Text = "LINK COPIED!"
    Animate(DiscordBtn, "TextColor3", Color3.fromRGB(0, 160, 255))
    task.wait(1.5)
    DiscordBtn.Text = "JOIN DISCORD FOR KEY"
    Animate(DiscordBtn, "TextColor3", Color3.fromRGB(180, 180, 190))
end)

SubmitBtn.MouseButton1Click:Connect(function()
    if KeyInput.Text == CorrectKey then
        Animate(SubmitBtn, "BackgroundColor3", Color3.fromRGB(0, 255, 120))
        SubmitBtn.Text = "SUCCESS"
        task.wait(0.5)
        
        -- Animation de sortie
        Animate(BlurEffect, "Size", 0)
        Animate(MainFrame, "BackgroundTransparency", 1)
        Animate(Stroke, "Transparency", 1)
        for _, v in pairs(MainFrame:GetChildren()) do
            if v:IsA("TextLabel") or v:IsA("TextBox") or v:IsA("TextButton") then
                Animate(v, "TextTransparency", 1)
                if not v:IsA("TextLabel") then Animate(v, "BackgroundTransparency", 1) end
            end
        end
        
        task.wait(0.4)
        UI:Destroy()
        BlurEffect:Destroy()
        LoadRayfield() 
    else
        SubmitBtn.Text = "INVALID KEY"
        Animate(SubmitBtn, "BackgroundColor3", Color3.fromRGB(255, 50, 70))
        task.wait(1)
        SubmitBtn.Text = "LOGIN"
        Animate(SubmitBtn, "BackgroundColor3", Color3.fromRGB(0, 160, 255))
    end
end)
