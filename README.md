humanoid:MoveTo(fruit.PrimaryPart.Position) -- Move para a Fruta
    if (getCharacter().PrimaryPart.Position - fruit.PrimaryPart.Position).Magnitude <= 5 then
         getMouse():Click(0) -- Interage com a fruta (pegar)
    end
  end
end

local function autoCollectFruits()
    local fruit = findNearestFruit()
    if fruit then
        collectFruit(fruit)
    end
end

-- Loop Principal

while true do
    task.wait()
  if AUTO_FARM_LEVEL then
    autoFarmLevel()
  end
  if AUTO_COLLECT_FRUITS then
      autoCollectFruits()
  end
end

-- Interface (BÃ¡sica)

--[[
   Para criar uma interface, vocÃª precisarÃ¡ usar elementos de GUI do Roblox.
   Este Ã© um exemplo bem simples e nÃ£o funcional, apenas para dar uma ideia:
   (Este cÃ³digo precisaria ser executado em outro contexto, como um LocalScript)
   
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.Players.LocalPlayer.PlayerGui
local autoFarmButton = Instance.new("TextButton")
autoFarmButton.Parent = ScreenGui
autoFarmButton.Text = "Auto Farm (OFF)"
autoFarmButton.Size = UDim2.new(0, 100, 0, 30)
autoFarmButton.Position = UDim2.new(0, 10, 0, 10)
autoFarmButton.MouseButton1Click:Connect(function()
  AUTO_FARM_LEVEL = not AUTO_FARM_LEVEL
  autoFarmButton.Text = "Auto Farm (" .. (AUTO_FARM_LEVEL and "ON" or "OFF") .. ")"
end)
