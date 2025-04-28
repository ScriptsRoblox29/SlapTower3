local StarterGui = game:GetService("StarterGui")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

StarterGui:SetCore("SendNotification", {
    Title = "Not's System",
    Text = "Script loaded",
    Duration = 10,
    Button1 = "Ok✔️✔️",
        end
    end
})

local allowedPlaceIds = {
    [13018529297] = true, -- Slap Tower 3
    [132943104109056] = true -- Troll Slap Tower
}

if not allowedPlaceIds[game.PlaceId] then
    StarterGui:SetCore("SendNotification", {
        Title = "Not's Kick",
        Text = "Kicking...",
        Duration = 60
    })
    task.wait(1.5)
    LocalPlayer:Kick("This game is not supported, Please join games called Slap tower troll or Slap tower 3.")
    return
end

task.spawn(function()
    while task.wait(0.1) do
        local character = LocalPlayer.Character
        local humanoid = character and character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            if humanoid:FindFirstChildOfClass("Tool") == nil or humanoid:FindFirstChild("Default") == nil then
                local backpack = LocalPlayer:FindFirstChildOfClass("Backpack")
                if backpack then
                    local tool = backpack:FindFirstChild("Default")
                    if tool then
                        humanoid:EquipTool(tool)
                        task.wait(0.2)
                    end
                end
            end

            for _, player in ipairs(Players:GetPlayers()) do
                if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                    local args = {
                        [1] = "slash",
                        [2] = player.Character,
                        [3] = player.Character.HumanoidRootPart.Position
                    }

                    if game.PlaceId == 13018529297 then
                        LocalPlayer.Character.Default.Event:FireServer(unpack(args))
                    elseif game.PlaceId == 132943104109056 then
                        LocalPlayer.Character.Slap.Event:FireServer(unpack(args))
                    end
                end
            end
        end
    end
end)
