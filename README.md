-- made by leoarruda

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local savedPosition = nil

-- Create UI
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "TpScriptGui"
screenGui.Parent = player:WaitForChild("PlayerGui")

local caption = Instance.new("TextLabel")
caption.Text = "made by leoarruda"
caption.Size = UDim2.new(0, 200, 0, 50)
caption.Position = UDim2.new(0, 10, 0, 10)
caption.BackgroundTransparency = 1
caption.TextColor3 = Color3.fromRGB(255, 255, 255)
caption.Font = Enum.Font.SourceSansBold
caption.TextSize = 24
caption.Parent = screenGui

local saveButton = Instance.new("TextButton")
saveButton.Text = "salvar posição"
saveButton.Size = UDim2.new(0, 200, 0, 40)
saveButton.Position = UDim2.new(0, 10, 0, 70)
saveButton.BackgroundColor3 = Color3.fromRGB(50, 200, 50)
saveButton.TextColor3 = Color3.fromRGB(255, 255, 255)
saveButton.Font = Enum.Font.SourceSansBold
saveButton.TextSize = 20
saveButton.Parent = screenGui

local tpButton = Instance.new("TextButton")
tpButton.Text = "tp"
tpButton.Size = UDim2.new(0, 200, 0, 40)
tpButton.Position = UDim2.new(0, 10, 0, 120)
tpButton.BackgroundColor3 = Color3.fromRGB(50, 50, 200)
tpButton.TextColor3 = Color3.fromRGB(255, 255, 255)
tpButton.Font = Enum.Font.SourceSansBold
tpButton.TextSize = 20
tpButton.Parent = screenGui

-- Button function: save position
saveButton.MouseButton1Click:Connect(function()
    if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        savedPosition = player.Character.HumanoidRootPart.Position
        saveButton.Text = "posição salva!"
        task.wait(1)
        saveButton.Text = "salvar posição"
    end
end)

-- Button function: teleport to saved position
tpButton.MouseButton1Click:Connect(function()
    if savedPosition and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        player.Character.HumanoidRootPart.CFrame = CFrame.new(savedPosition)
    end
end)
