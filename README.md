local StarterGui = game:GetService("StarterGui")

if game.PlaceId ~= 13018529297 then
    StarterGui:SetCore("SendNotification", {
        Title = "Not's System",
        Text = "wrong game, blud🥀💔",
        Duration = 5
    })
    return
end

StarterGui:SetCore("SendNotification", {
    Title = "Not's System",
    Text = "Our server: https://discord.gg/zbQhavwkAR",
    Duration = 10
})

task.spawn(function()
    while task.wait(0) do
        local character = game.Players.LocalPlayer.Character
        local humanoid = character and character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            if humanoid:FindFirstChildOfClass("Tool") == nil or humanoid:FindFirstChild("Default") == nil then
                local backpack = game.Players.LocalPlayer:FindFirstChildOfClass("Backpack")
                if backpack then
                    local tool = backpack:FindFirstChild("Default")
                    if tool then
                        humanoid:EquipTool(tool)
                        task.wait(0)
                    end
                end
            end

            for _, player in ipairs(game.Players:GetPlayers()) do
                if player ~= game.Players.LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                    local args = {
                        [1] = "slash",
                        [2] = player.Character,
                        [3] = player.Character.HumanoidRootPart.Position
                    }
                    game.Players.LocalPlayer.Character.Default.Event:FireServer(unpack(args))
                end
            end
        end
    end
end)
