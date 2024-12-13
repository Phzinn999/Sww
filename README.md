-- Script Completo para "Carrossel - Escola Mundial"

local teleportLocations = {
    ["Casa da Maria J."] = Vector3.new(10, 0, 10),
    ["Casa da Valéria"] = Vector3.new(20, 0, 20),
    ["Casa do Paulo"] = Vector3.new(30, 0, 30),
    ["Casa do Cirilo"] = Vector3.new(40, 0, 40)
}

local premiumItems = {"Interfone", "Skate", "Estilingue", "Giz arco-íris"}

local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui", player.PlayerGui)

-- Função para criar botões de teleporte
local function createTeleportButtons()
    for name, position in pairs(teleportLocations) do
        local button = Instance.new("TextButton", screenGui)
        button.Size = UDim2.new(0, 200, 0, 50)
        button.Position = UDim2.new(0, 0, 0, #screenGui:GetChildren() * 60)
        button.Text = "Teleportar para " .. name

        button.MouseButton1Click:Connect(function()
            player.Character:SetPrimaryPartCFrame(CFrame.new(position))
        end)
    end
end

-- Função para criar botão de itens premium
local function createPremiumButton()
    local button = Instance.new("TextButton", screenGui)
    button.Size = UDim2.new(0, 200, 0, 50)
    button.Position = UDim2.new(0, 0, 0, #screenGui:GetChildren() * 60)
    button.Text = "Obter Itens Premium"

    button.MouseButton1Click:Connect(function()
        for _, itemName in ipairs(premiumItems) do
            local item = Instance.new("Tool")
            item.Name = itemName
            item.Parent = player.Backpack
        end
    end)
end

-- Criar todos os botões
createTeleportButtons()
createPremiumButton()
