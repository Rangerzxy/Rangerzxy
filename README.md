
`lua
local player = game.Players.LocalPlayer
local replicatedStorage = game:GetService("ReplicatedStorage")
local fruitSpawnedEvent = replicatedStorage:WaitForChild("FruitSpawned")
local fruits = {} 

local function onFruitSpawned(fruitName)
    table.insert(fruits, fruitName)
    print("Fruta spawnada: " .. fruitName)
    
end


fruitSpawnedEvent.OnClientEvent:Connect(onFruitSpawned)

-- Função para verificar e listar as frutas spawnadas
local function listFruits()
    while true do
        wait(5) 
        if #fruits > 0 then
            print("Frutas encontradas:")
            for _, fruit in ipairs(fruits) do
                print("- " .. fruit)
            end
        else
            print("Nenhuma fruta encontrada.")
        end
    end
end


listFruits()
```
