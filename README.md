-- Script para farmar baús automaticamente no Blox Fruits com painel

-- Criar o painel
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")
local Button = Instance.new("TextButton")

-- Configurar o painel
ScreenGui.Parent = game.CoreGui

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Position = UDim2.new(0.5, -100, 0.5, -50)
Frame.Size = UDim2.new(0, 200, 0, 100)

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.Size = UDim2.new(1, 0, 0.3, 0)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "Andreihub"
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextSize = 24

Button.Parent = Frame
Button.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
Button.Position = UDim2.new(0.1, 0, 0.5, 0)
Button.Size = UDim2.new(0.8, 0, 0.4, 0)
Button.Font = Enum.Font.SourceSans
Button.Text = "Ativar Farm de Baús"
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.TextSize = 18

-- Função para farmar baús automaticamente
local function farmBaús()
    while true do
        for _, chest in pairs(game.Workspace:GetChildren()) do
            if chest:IsA("Model") and chest.Name == "Chest" then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = chest.HumanoidRootPart.CFrame
                wait(1) -- Tempo para pegar o baú
            end
        end
        wait(10) -- Tempo de espera antes de procurar novamente
    end
end

-- Função para ativar o farm de baús quando o botão for clicado
Button.MouseButton1Click:Connect(function()
    spawn(farmBaús)
end)
