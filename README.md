-- LocalScript: StarterPlayerScripts/SpeedClient.lua
local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local player = Players.LocalPlayer

local normalSpeed =89 
local sprintSpeed =89

local function getHumanoid()
	local character = player.Character or player.CharacterAdded:Wait()
	return character:WaitForChild("Humanoid")
end

local humanoid = getHumanoid()

UserInputService.InputBegan:Connect(function(input, gameProcessed)
	if gameProcessed then return end
	if input.KeyCode == Enum.KeyCode.LeftShift then
		humanoid.WalkSpeed = sprintSpeed
	end
end)

UserInputService.InputEnded:Connect(function(input, gameProcessed)
	if input.KeyCode == Enum.KeyCode.LeftShift then
		humanoid.WalkSpeed = normalSpeed
	end
end)

player.CharacterAdded:Connect(function()
	humanoid = getHumanoid()
	humanoid.WalkSpeed = normalSpeed
end)
