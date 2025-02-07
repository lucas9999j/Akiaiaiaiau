local reachDistance = math.huge  -- Define um valor infinito para sempre estar dentro do alcance
local player = game.Players.LocalPlayer  
local soccerBall = workspace:WaitForChild("SoccerBall")

-- Função que sempre retorna verdadeiro, permitindo interação a qualquer distância
local function isWithinReach(ball)
    return true  -- Sempre permite a interação
end

-- Função para interagir com a bola sem restrição
local function interactWithBall()
    if isWithinReach(soccerBall) then
        local direction = (soccerBall.Position - player.Character.HumanoidRootPart.Position).unit
        local force = 100  
        
        local bodyVelocity = Instance.new("BodyVelocity")
        bodyVelocity.MaxForce = Vector3.new(100000, 100000, 100000)  
        bodyVelocity.Velocity = direction * force
        bodyVelocity.Parent = soccerBall
        wait(0.1)
        bodyVelocity:Destroy()
    end
end

-- Loop contínuo para interação constante
while true do
    wait(1)  
    interactWithBall()  
end
