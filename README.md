game.ReplicatedStorage:WaitForChild("KillAll").OnServerEvent:Connect(function(player)
    for _, target in pairs(game.Players:GetPlayers()) do
        if target ~= player and target.Character then
            local humanoid = target.Character:FindFirstChild("Humanoid")
            if humanoid then
                humanoid.Health = 0
            end
        end
    end
end)
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local KillAll = ReplicatedStorage:WaitForChild("KillAll")

local function onChat(msg)
    if msg == "!killall" then
        KillAll:FireServer()
    end
end

game.Players.LocalPlayer.Chatted:Connect(onChat)
