# dsdsds
loadstring(game:HttpGet("https://raw.githubusercontent.com/skibiditoiletfan2007/BaldyToSorcerer/main/Latest.lua"))()

local mouse = game.Players.LocalPlayer:GetMouse()
local tool = Instance.new("Tool")
tool.RequiresHandle = false
tool.Name = "Phashing Blue"

local teleportAnimationId = "rbxassetid://15957361339"
local teleportSoundId = "rbxassetid://5066021887"

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local animator = humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", humanoid)

local teleportAnimation = Instance.new("Animation")
teleportAnimation.AnimationId = teleportAnimationId
local teleportTrack = animator:LoadAnimation(teleportAnimation)

local teleportSound = Instance.new("Sound")
teleportSound.SoundId = teleportSoundId
teleportSound.Parent = character.HumanoidRootPart

tool.Activated:Connect(function()
    teleportTrack:Play()
    teleportSound:Play()
    local pos = mouse.Hit + Vector3.new(0, 2.5, 0)
    pos = CFrame.new(pos.X, pos.Y, pos.Z)
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = pos
end)

tool.Parent = game.Players.LocalPlayer.Backpack
