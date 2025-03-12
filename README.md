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
        mainFrame.Position = UDim2.new(0.05, 0, 0.05, 0)
        mainFrame.BackgroundColor3 = Color3.new(0, 0, 0)
        mainFrame.BorderColor3 = Color3.new(1, 0, 0)
        mainFrame.BorderSizePixel = 2

        -- Imagem de fundo neon vermelha
        local backgroundImage = Instance.new("ImageLabel")
        backgroundImage.Parent = mainFrame
        backgroundImage.Size = UDim2.new(1, 0, 1, 0)
        backgroundImage.BackgroundTransparency = 1
        backgroundImage.Image = "rbxassetid://YOUR_NEON_RED_IMAGE_ID_HERE" -- Substitua pelo seu ID de imagem
        backgroundImage.ZIndex = 0

        -- Título
        local titleLabel = Instance.new("TextLabel")
        titleLabel.Parent = mainFrame
        titleLabel.Size = UDim2.new(1, 0, 0, 30)
        titleLabel.Position = UDim2.new(0, 0, 0, 0)
        titleLabel.BackgroundTransparency = 1
        titleLabel.Text = "Painel de Hacks"
        titleLabel.TextColor3 = Color3.new(1, 0, 0)
        titleLabel.Font = Enum.Font.SciFi
        titleLabel.TextScaled = true

        -- Variáveis de estado
        local teleportEnabled = false
        local flyEnabled = false
        local autoFarmEnabled = false
        local autoFarmChestEnabled = false
        local autoFarmLevelEnabled = false
        local autoRaidEnabled = false
        local autoFruitEnabled = false

        -- Funções de ativação/desativação
        local function toggleTeleport()
            teleportEnabled = not teleportEnabled
            if teleportButton then
                teleportButton.Text = teleportEnabled and "Teleporte: Ligado (Teleporta para ilha aleatória)" or "Teleporte: Desligado"
            end
        end

        local function toggleFly()
            flyEnabled = not flyEnabled
            if flyButton then
                flyButton.Text = flyEnabled and "Voar: Ligado (Permite voar)" or "Voar: Desligado"
            end
            if flyEnabled then
                enableFlyMode()
            else
                disableFlyMode()
            end
        end

        local function toggleAutoFarm()
            autoFarmEnabled = not autoFarmEnabled
            if autoFarmButton then
                autoFarmButton.Text = autoFarmEnabled and "Auto Farm: Ligado" or "Auto Farm: Desligado"
            end
            if autoFarmEnabled then
                startAutoFarm()
            else
                stopAutoFarm()
            end
        end

        local function toggleAutoFarmChest()
            autoFarmChestEnabled = not autoFarmChestEnabled
            if autoFarmChestButton then
                autoFarmChestButton.Text = autoFarmChestEnabled and "Auto Farm Baú: Ligado" or "Auto Farm Baú: Desligado"
            end
            if autoFarmChestEnabled then
                startAutoFarmChest()
            else
                stopAutoFarmChest()
            end
        end

        local function toggleAutoFarmLevel()
            autoFarmLevelEnabled = not autoFarmLevelEnabled
            if autoFarmLevelButton then
                autoFarmLevelButton.Text = autoFarmLevelEnabled and "Auto Farm Nível: Ligado" or "Auto Farm Nível: Desligado"
            end
            if autoFarmLevelEnabled then
                startAutoFarmLevel()
            else
                stopAutoFarmLevel()
            end
        end

        local function toggleAutoRaid()
            autoRaidEnabled = not autoRaidEnabled
            if autoRaidButton then
                autoRaidButton.Text = autoRaidEnabled and "Auto Raid: Ligado" or "Auto Raid: Desligado"
            end
            if autoRaidEnabled then
                startAutoRaid()
            else
                stopAutoRaid()
            end
        end

        local function toggleAutoFruit()
            autoFruitEnabled = not autoFruitEnabled
            if autoFruitButton then
                autoFruitButton.Text = autoFruitEnabled and "Auto Fruta: Ligado" or "Auto Fruta: Desligado"
            end
            if autoFruitEnabled then
                startAutoFruit()
            else
                stopAutoFruit()
            end
        end

        -- Funções de teletransporte e voo (mantidas do script anterior)
        local function teleportToRandomIsland()
            if teleportEnabled then
                -- ... (código de teletransporte para ilha aleatória)
                print("Teletransportando para ilha aleatória...")
            end
        end

        local function enableFlyMode()
            -- ... (código de voo)
            print("Modo de voo ativado.")
        end

        local function disableFlyMode()
            -- ... (código de não voo)
            print("Modo de voo desativado.")
        end

        -- Funções de autofarm (exemplos básicos)
        local function startAutoFarm()
            -- ... (código para atacar NPCs automaticamente)
            print("Auto farm iniciado.")
        end

        local function stopAutoFarm()
            -- ... (código para parar o autofarm)
            print("Auto farm parado.")
        end

        local function startAutoFarmChest()
            -- ... (código para coletar baús automaticamente)
            print("Auto farm de baú iniciado.")
        end

        local function stopAutoFarmChest()
            -- ... (código para parar o autofarm de baú)
            print("Auto farm de baú parado.")
        end

        local function startAutoFarmLevel()
            -- ... (código para farmar nível automaticamente)
            print("Auto farm de nível iniciado.")
        end

        local function stopAutoFarmLevel()
            -- ... (código para parar o autofarm de nível)
            print("Auto farm de nível parado.")
        end

        local function startAutoRaid()
            -- ... (código para iniciar raids automaticamente)
            print("Auto raid iniciado.")
        end

        local function stopAutoRaid()
            -- ... (código para parar o auto raid)
            print("Auto raid parado.")
        end

        local function startAutoFruit()
            -- ... (código para pegar frutas automaticamente)
            print("Auto fruta iniciado.")
        end

        local function stopAutoFruit()
