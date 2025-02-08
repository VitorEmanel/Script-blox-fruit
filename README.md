-- Defina os jogadores
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Camera = game:GetService("Workspace").CurrentCamera

-- Função para criar ESP
function CreateESP(Player)
    local Highlight = Instance.new("Highlight")
    Highlight.Parent = Player.Character
    Highlight.FillColor = Color3.new(1, 0, 0) -- Cor vermelha
    Highlight.OutlineColor = Color3.new(1, 1, 1) -- Cor branca
end

-- Função para remover ESP
function RemoveESP(Player)
    for _, v in pairs(Player.Character:GetChildren()) do
        if v:IsA("Highlight") then
            v:Destroy()
        end
    end
end

-- Função para ativar/desativar ESP
local ESPEnabled = false
function ToggleESP()
    ESPEnabled = not ESPEnabled
    for _, Player in pairs(Players:GetPlayers()) do
        if Player ~= LocalPlayer then
            if ESPEnabled then
                CreateESP(Player)
            else
                RemoveESP(Player)
            end
        end
    end
end

-- Criar botão na interface do usuário
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local ToggleButton = Instance.new("TextButton")
ToggleButton.Size = UDim2.new(0, 200, 0, 50)
ToggleButton.Position = UDim2.new(0.5, -100, 0, 50)
ToggleButton.Text = "Toggle ESP"
ToggleButton.Parent = ScreenGui

ToggleButton.MouseButton1Click:Connect(ToggleESP)# Script-blox-fruit
O melhor de todos 
