--Made By frkfx
--Working Games
--Prison Life
--Ninja Legends
--Sonic Speed Simulator
--More Game Support Soon

-- HUB
if game.PlaceId == 155615604 then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("Prison Life (BETA)", "Synapse")

    -- MAIN
    local Main = Window:NewTab("Guns")
    local MainSection = Main:NewSection("Gun And Mod")

    MainSection:NewDropdown("Gun Grabber", "Grabs The Gun", {"M9", "Remington 870", "AK-47"}, function(v)
        local A_1 = game:GetService("Workspace")["Prison_ITEMS"].giver[v].ITEMPICKUP
        local Event = game:GetService("Workspace").Remote.ItemHandler
        Event:InvokeServer(A_1)
    end)

    MainSection:NewDropdown("Gun Mod", "Mods The Gun", {"M9", "Remington 870", "AK-47"}, function(v)
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

    -- PLAYER
    local Player = Window:NewTab("Player")
    local PlayerSection = Player:NewSection("Player")

    PlayerSection:NewSlider("Walkspeed", "Increases Walkspeed", 250, 16, function(v)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = v
    end)

    PlayerSection:NewSlider("Jump Power", "Increases Jump Power", 250, 50, function(v)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = v
    end)
elseif game.PlaceId == 3956818381 then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("Ninja Legends (TESTING)", "Synapse")

    -- MAIN
    local Main = Window:NewTab("Auto Farm")
    local MainSection = Main:NewSection("Auto Farm")

    MainSection:NewToggle("Auto Swing", "Auto Swings", function(v)
        getgenv().autoswing = v
        while true do
            if not getgenv().autoswing then return end
            for _,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if v:FindFirstChild("ninjitsuGain") then
                    game.Players.LocalPlayer.Character.Humanoid:EquipTool(v)
                    break
                end
            end
            local A_1 = "swingKatana"
            local Event = game:GetService("Players").LocalPlayer.ninjaEvent
            Event:FireServer(A_1)
            wait(0.1)
        end
    end)

    MainSection:NewToggle("Auto Sell", "Sells For You", function(v)
        getgenv().autosell = v
        while true do
            if getgenv().autoswing == false then return end
            game:GetService("Workspace").sellAreaCircles["sellAreaCircle16"].circleInner.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
            wait(0.1)
            game:GetService("Workspace").sellAreaCircles["sellAreaCircle16"].circleInner.CFrame = CFrame.new(0,0,0)
            wait(0.1)
        end
    end)

    MainSection:NewButton("Unlock all islands", "Unlocks all islands", function()
        local oldcframe = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
        for _,v in pairs(game:GetService("Workspace").islandUnlockParts:GetChildren()) do
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
            wait(0.1)
        end
        wait(0.1)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = oldcframe
    end)
    
    MainSection:NewToggle("Auto Buy Swords", "Buys All Affordable Swords", function(v)
        getgenv().buyswords = v
        while true do
            if not getgenv().buyswords then return end
            local A_1 = "buyAllSwords"
            local A_2 = "Inner Peace Island"
            local Event = game:GetService("Players").LocalPlayer.ninjaEvent
            Event:FireServer(A_1, A_2)
            wait(0.5)
        end
    end)

    MainSection:NewToggle("Auto Buy Belts", "Buys All Affordable Belts", function(v)
        getgenv().buybelts = v
        while true do
            if not getgenv().buybelts then return end
            local A_1 = "buyAllBelts"
            local A_2 = "Inner Peace Island"
            local Event = game:GetService("Players").LocalPlayer.ninjaEvent
            Event:FireServer(A_1, A_2)
            wait(0.5)
        end
    end)
end

if game.PlaceId == 9049840490 then
    local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
    local Window = Library.CreateLib("Sonic Speed Simulator (TESTING)", "Synapse")
    local Main = Window:NewTab("Auto Farm")
    local MainSection = Main:NewSection("Made By frkfx")
 
 local Main = Window:NewTab("Vending Machines")
    local MainSection = Main:NewSection("Purchase An Affordable Vending Machine")
   MainSection:NewButton("300", "Purchases Vending Machine", function(v)
local args = {
    [1] = "GreenHill1"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args)) 


    end)

MainSection:NewButton("600", "Purchases Vending Machine", function(v)
local args = {
    [1] = "GreenHill2"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args))

end)

MainSection:NewButton("1000", "Purchases Vending Machine", function(v)
local args = {
    [1] = "GreenHill3"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args))
end)

MainSection:NewButton("1200", "Purchases Vending Machine", function(v)
local args = {
    [1] = "GreenHill4"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args))

end)

MainSection:NewButton("2500", "Purchases Vending Machine", function(v)
local args = {
    [1] = "GreenHill5"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args))

end)

MainSection:NewButton("4000", "Purchases Vending Machine", function(v)
local args = {
    [1] = "SandyHill1"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args))

end)

MainSection:NewButton("8000", "Purchases Vending Machine", function(v)
local args = {
    [1] = "EmeraldHill1"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args))

end)

MainSection:NewButton("40000", "Purchases Vending Machine", function(v)
local args = {
    [1] = "SnowValley1"
}

game:GetService("ReplicatedStorage").Knit.Services.VendorService.RF.EggPurchased:InvokeServer(unpack(args))

end)
local Main = Window:NewTab("Instant Collect")
    local MainSection = Main:NewSection("Collect XP/Rings (Broken)")
MainSection:NewButton("Collect", "Collects XP/Rings", function(v)
  
local args = {
    [1] = "1ac59480-35e7-4e3c-85ea-20d19e46b3d0"
}

game:GetService("ReplicatedStorage").Knit.Services.WorldCurrencyService.RE.PickupCurrency:FireServer(unpack(args))

end)
end
 
