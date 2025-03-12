-- Função para verificar se o executor está injetado
local function isInjectorInjected()
    return syn and syn.protect_gui and syn.is_syn_user
end

-- Função para injetar o script (se necessário)
local function injectScript()
    if not isInjectorInjected() then
        -- Simulação de injeção (substitua pelo código de injeção real do JJSploit)
        print("Simulando injeção do executor...")
        -- Insira aqui o código de injeção do JJSploit, se necessário
        -- Exemplo (substitua pelo código real):
        -- syn.protect_gui(true)
        -- syn.is_syn_user = true
        task.wait(2) -- Simula um tempo de injeção
        print("Executor injetado com sucesso!")
    end
end

-- Injeta o script se necessário
injectScript()

-- Verifica se o jogador local existe
local player = game.Players.LocalPlayer
if player then
    local playerGui = player:WaitForChild("PlayerGui")
    if playerGui then
        -- Painel personalizado
        local screenGui = Instance.new("ScreenGui")
        screenGui.Parent = playerGui

        local mainFrame = Instance.new("Frame")
        mainFrame.Parent = screenGui
        mainFrame.Size = UDim2.new(0, 300, 0, 400)
        mainFrame.Position = UDim2.new(0, 0, 0, 0) -- Canto esquerdo da tela
        mainFrame.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1) -- Fundo escuro
        mainFrame.BorderColor3 = Color3.new(0.2, 0.2, 0.2)
        mainFrame.BorderSizePixel = 1

        -- Título
        local titleLabel = Instance.new("TextLabel")
        titleLabel.Parent = mainFrame
        titleLabel.Size = UDim2.new(1, 0, 0, 30)
        titleLabel.Position = UDim2.new(0, 0, 0, 0)
        titleLabel.BackgroundTransparency = 1
        titleLabel.Text = "MKHUB" -- Novo título
        titleLabel.TextColor3 = Color3.new(1, 1, 1)
        titleLabel.Font = Enum.Font.SciFi
        titleLabel.TextScaled = true

        -- Estilo dos botões
        local function createStyledButton(parent, position, size, text, connectFunction)
            local button = Instance.new("TextButton")
            button.Parent = parent
            button.Position = position
            button.Size = size
            button.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
            button.TextColor3 = Color3.new(1, 1, 1)
            button.Font = Enum.Font.SciFi
            button.Text = text
            button.TextXAlignment = Enum.TextXAlignment.Left
            button.TextYAlignment = Enum.TextYAlignment.Center
            button.MouseButton1Click:Connect(connectFunction)
            return button
        end

        -- Botões da barra lateral
        local sidebarButtons = {
            { text = "Farm", position = UDim2.new(0, 0, 0.1, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Sea-Farm", position = UDim2.new(0, 0, 0.2, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Combat", position = UDim2.new(0, 0, 0.3, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Visuals", position = UDim2.new(0, 0, 0.4, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Trigger-Bot", position = UDim2.new(0, 0, 0.5, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Status", position = UDim2.new(0, 0, 0.6, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Shop", position = UDim2.new(0, 0, 0.7, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Movement", position = UDim2.new(0, 0, 0.8, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Teleports", position = UDim2.new(0, 0, 0.9, 0), size = UDim2.new(0, 80, 0, 30) },
            { text = "Misc", position = UDim2.new(0, 0, 1, 0), size = UDim2.new(0, 80, 0, 30) }
        }

        for _, buttonData in ipairs(sidebarButtons) do
            createStyledButton(mainFrame, buttonData.position, buttonData.size, buttonData.text, function()
                -- Adicione aqui a lógica para cada botão da barra lateral
                print("Botão " .. buttonData.text .. " clicado.")
            end)
        end

        -- Rótulos e botões principais
        local function createLabel(parent, position, size, text)
            local label = Instance.new("TextLabel")
            label.Parent = parent
            label.Position = position
            label.Size = size
            label.BackgroundTransparency = 1
            label.TextColor3 = Color3.new(1, 1, 1)
            label.Font = Enum.Font.SciFi
            label.Text = text
            label.TextXAlignment = Enum.TextXAlignment.Left
            return label
        end

        local farmLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.1, 0), UDim2.new(0, 150, 0, 30), "Farm")
        local autoFarmLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.2, 0), UDim2.new(0, 150, 0, 30), "Auto Farm")
        local guiButtonLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.3, 0), UDim2.new(0, 150, 0, 30), "GUI Button")
        local levelFarmQuestLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.4, 0), UDim2.new(0, 150, 0, 30), "Level Farm Quest")
        local levelFarmNoQuestLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.5, 0), UDim2.new(0, 150, 0, 30), "Level Farm No Quest")
        local nearestFarmLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.6, 0), UDim2.new(0, 150, 0, 30), "Nearest Farm")
        local selectedFarmLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.7, 0), UDim2.new(0, 150, 0, 30), "Selected Farm")
        local selectMonsterLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.8, 0), UDim2.new(0, 150, 0, 30), "Select Monster")
        local autoFarmSelectMonsterQuestLabel = createLabel(mainFrame, UDim2.new(0.3, 0, 0.9, 0), UDim2.new(0, 250, 0, 30), "Auto Farm Select Monster (
