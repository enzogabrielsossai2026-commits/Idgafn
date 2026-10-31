local ScreenGui = Instance.new("ScreenGui")
local TextButton = Instance.new("TextButton")
local UICorner = Instance.new("UICorner") -- Скруглим углы для красоты

ScreenGui.Parent = game.CoreGui
TextButton.Parent = ScreenGui

-- Настройки внешнего вида
TextButton.Size = UDim2.new(0, 150, 0, 50)
TextButton.Position = UDim2.new(0.1, 0, 0.4, 0)
TextButton.BackgroundColor3 = Color3.fromRGB(200, 50, 50) -- Красный (выключено)
TextButton.Text = "Jump: OFF"
TextButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton.Font = Enum.Font.SourceSansBold
TextButton.TextSize = 20
TextButton.Draggable = true

UICorner.CornerRadius = UDim.new(0, 12)
UICorner.Parent = TextButton

local active = false

-- Логика переключения
TextButton.MouseButton1Click:Connect(function()
    local char = game.Players.LocalPlayer.Character
    if char and char:FindFirstChild("Humanoid") then
        active = not active -- Меняем состояние (вкл/выкл)
        
        if active then
            char.Humanoid.UseJumpPower = true
            char.Humanoid.JumpPower = 900
            TextButton.Text = "Jump: ON"
            TextButton.BackgroundColor3 = Color3.fromRGB(50, 200, 50) -- Зеленый
        else
            char.Humanoid.JumpPower = 50 -- Стандартный прыжок
            TextButton.Text = "Jump: OFF"
            TextButton.BackgroundColor3 = Color3.fromRGB(200, 50, 50) -- Красный
        end
    end
end)
