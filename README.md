local StarterGui = game:GetService("StarterGui")

StarterGui:SetCore("SendNotification", {
    Title = "Not's Hub",
    Text = "made by Not and Check our Server for more Scripts: https://discord.gg/zbQhavwkAR",
    Duration = 7
})

task.spawn(function()
    while task.wait(0.05) do
        local character = game.Players.LocalPlayer.Character
        local humanoid = character and character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            if humanoid:FindFirstChildOfClass("Tool") == nil or humanoid:FindFirstChild("Default") == nil then
                local backpack = game.Players.LocalPlayer:FindFirstChildOfClass("Backpack")
                if backpack then
                    local tool = backpack:FindFirstChild("Default")
                    if tool then
                        humanoid:EquipTool(tool)
                        task.wait(0.04)
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
