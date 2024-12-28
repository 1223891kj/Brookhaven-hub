local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local FlyButton = Instance.new("TextButton")
local ESPButton = Instance.new("TextButton")
local PlayerListButton = Instance.new("TextButton")
local UpdateListButton = Instance.new("TextButton")
local PlayerListFrame = Instance.new("Frame")
local PlayerList = Instance.new("TextLabel")
local ToggleButton = Instance.new("TextButton")

ScreenGui.Name = "GGHub"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

Frame.Name = "MainFrame"
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Frame.Position = UDim2.new(0.5, -200, 0.5, -150)
Frame.Size = UDim2.new(0, 400, 0, 300)

Title.Name = "Title"
Title.Parent = Frame
Title.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Title.Size = UDim2.new(0, 400, 0, 50)
Title.Font = Enum.Font.SourceSans
Title.Text = "GG Hub [Beta]"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 24

FlyButton.Name = "FlyButton"
FlyButton.Parent = Frame
FlyButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
FlyButton.Position = UDim2.new(0.5, -50, 0.3, 0)
FlyButton.Size = UDim2.new(0, 100, 0, 30)
FlyButton.Font = Enum.Font.SourceSans
FlyButton.Text = "Fly"
FlyButton.TextColor3 = Color3.fromRGB(255, 255, 255)
FlyButton.TextSize = 20

ESPButton.Name = "ESPButton"
ESPButton.Parent = Frame
ESPButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
ESPButton.Position = UDim2.new(0.5, -50, 0.5, 0)
ESPButton.Size = UDim2.new(0, 100, 0, 30)
ESPButton.Font = Enum.Font.SourceSans
ESPButton.Text = "ESP"
ESPButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ESPButton.TextSize = 20

PlayerListButton.Name = "PlayerListButton"
PlayerListButton.Parent = Frame
PlayerListButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
PlayerListButton.Position = UDim2.new(0.5, -50, 0.7, 0)
PlayerListButton.Size = UDim2.new(0, 100, 0, 30)
PlayerListButton.Font = Enum.Font.SourceSans
PlayerListButton.Text = "Observar Jogadores"
PlayerListButton.TextColor3 = Color3.fromRGB(255, 255, 255)
PlayerListButton.TextSize = 20

UpdateListButton.Name = "UpdateListButton"
UpdateListButton.Parent = Frame
UpdateListButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
UpdateListButton.Position = UDim2.new(0.5, -50, 0.9, 0)
UpdateListButton.Size = UDim2.new(0, 100, 0, 30)
UpdateListButton.Font = Enum.Font.SourceSans
UpdateListButton.Text = "Atualizar Lista"
UpdateListButton.TextColor3 = Color3.fromRGB(255, 255, 255)
UpdateListButton.TextSize = 20

PlayerListFrame.Name = "PlayerListFrame"
PlayerListFrame.Parent = Frame
PlayerListFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
PlayerListFrame.Position = UDim2.new(0.1, 0, 1.1, 0)
PlayerListFrame.Size = UDim2.new(0, 300, 0, 200)
PlayerListFrame.Visible = false

PlayerList.Name = "PlayerList"
PlayerList.Parent = PlayerListFrame
PlayerList.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
PlayerList.Size = UDim2.new(0, 300, 0, 200)
PlayerList.Font = Enum.Font.SourceSans
PlayerList.Text = ""
PlayerList.TextColor3 = Color3.fromRGB(255, 255, 255)
PlayerList.TextSize = 18
PlayerList.TextWrapped = true

ToggleButton.Name = "ToggleButton"
ToggleButton.Parent = ScreenGui
ToggleButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
ToggleButton.Position = UDim2.new(0, 10, 0, 10)
ToggleButton.Size = UDim2.new(0, 50, 0, 50)
ToggleButton.Text = ""
ToggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ToggleButton.TextSize = 14
ToggleButton.BorderSizePixel = 0
ToggleButton.TextTransparency = 1
ToggleButton.BackgroundTransparency = 0
ToggleButton.ClipsDescendants = true
ToggleButton.AutoButtonColor = false
ToggleButton.Style = Enum.ButtonStyle.Custom
ToggleButton.Font = Enum.Font.SourceSans
ToggleButton.TextWrapped = true
ToggleButton.TextScaled = true
ToggleButton.TextStrokeTransparency = 1
ToggleButton.TextXAlignment = Enum.TextXAlignment.Center
ToggleButton.TextYAlignment = Enum.TextYAlignment.Center
ToggleButton.ZIndex = 2
ToggleButton.AnchorPoint = Vector2.new(0.5, 0.5)
ToggleButton.SizeConstraint = Enum.SizeConstraint.RelativeYY
ToggleButton.Size = UDim2.new(0, 50, 0, 50)
ToggleButton.Position = UDim2.new(0, 50, 0, 50)
ToggleButton.Rotation = 0
ToggleButton.Visible = true
ToggleButton.Active = true
ToggleButton.Selectable = true
ToggleButton.Draggable = false

local function updatePlayerList()
    local players = game.Players:GetPlayers()
    local playerNames = ""
    for _, player in ipairs(players) do
        playerNames = playerNames .. player.Name .. "\n"
    end
    PlayerList.Text = playerNames
end

FlyButton.MouseButton1Click:Connect(function()
    local player = game.Players.LocalPlayer
    local character = player.Character
    if character and character:FindFirstChild("HumanoidRootPart") then
        local flying = false
        local flySpeed = 50
        local bodyVelocity = Instance.new("BodyVelocity")
        bodyVelocity.Velocity = Vector3.new(0, 0, 0)
        bodyVelocity.MaxForce = Vector3.new(0, 0, 0)
        bodyVelocity.Parent = character.HumanoidRootPart

        local function fly()
            if flying then
                bodyVelocity.Velocity = Vector3.new(0, flySpeed, 0)
                bodyVelocity.MaxForce = Vector3.new(4000, 4000, 4000)
            else
                bodyVelocity.Velocity = Vector3.new(0, 0, 0)
                bodyVelocity.MaxForce = Vector3.new(0, 0, 0)
            end
        end

        flying = not flying
        fly()
    end
end)

ESPButton.MouseButton1Click:Connect(function()
    for _, player in ipairs(game.Players:GetPlayers()) do
        if player ~= game.Players.LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local highlight = Instance.new("Highlight")
            highlight.Name = "ESP"
            highlight.Adornee = player.Character
            highlight.FillColor = Color3.fromRGB(255, 255, 255)
            highlight.FillTransparency = 0.5
            highlight.OutlineColor = Color3.fromRGB(255, 255, 255)
            highlight.OutlineTransparency = 0
            highlight.Parent = player.Character:FindFirstChild("HumanoidRootPart")
        end
    end
end)

PlayerListButton.MouseButton1Click:Connect(function()
    PlayerListFrame.Visible = not PlayerListFrame.Visible
    updatePlayerList()
end)

UpdateListButton.MouseButton1Click:Connect(function()
    updatePlayerList()
end)

ToggleButton.MouseButton1Click:Connect(function()
    Frame.Visible = not Frame.Visible
end)

game.Players.PlayerAdded:Connect(updatePlayerList)
game.Players.PlayerRemoving:Connect(updatePlayerList)

