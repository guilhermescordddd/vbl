-- Script para coletar recompensas de rank (Yen, Lucky Spin, Giros de Habilidade)
-- Coleta automaticamente a cada 3 segundos

local player = game.Players.LocalPlayer
local rewardService = game.ReplicatedStorage.RewardService
local cooldown = 3 -- Segundos entre coletas

while true do
    -- Coleta Yen
    local yenService = rewardService:FindFirstChild("YenService")
    if yenService then
        yenService:FireServer("Collect")
    end
    
    -- Coleta Lucky Spin
    local luckySpinService = rewardService:FindFirstChild("LuckySpinService")
    if luckySpinService then
        luckySpinService:FireServer("Collect")
    end
    
    -- Coleta Giros de Habilidade
    local skillSpinService = rewardService:FindFirstChild("SkillSpinService")
    if skillSpinService then
        skillSpinService:FireServer("Collect")
    end
    
    -- Aguarda antes de tentar novamente
    wait(cooldown)
end
