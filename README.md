local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Function to auto-workout
local function autoWorkout()
    while wait(1) do
        local workoutTool = character:FindFirstChild("WorkoutTool") -- Replace with actual tool name
        if workoutTool and workoutTool:FindFirstChild("Activate") then
            workoutTool.Activate:Fire()
        end
    end
end

-- Start auto-workout when character is ready
if character then
    autoWorkout()
else
    player.CharacterAdded:Connect(function()
        character = player.Character
        autoWorkout()
    end)
end

-- Admin Commands Script
local adminUserId = 12345678 -- Replace with your UserId
local prefix = "!"

game.Players.PlayerAdded:Connect(function(player)
    if player.UserId == adminUserId then
        print(player.Name .. " is recognized as an admin.")
    end
    
    player.Chatted:Connect(function(message)
        if player.UserId == adminUserId and message:sub(1, 1) == prefix then
            local command = message:sub(2):lower()
            
            if command == "fly" then
                local character = player.Character
                if character and character:FindFirstChild("HumanoidRootPart") then
                    local bodyVelocity = Instance.new("BodyVelocity")
                    bodyVelocity.Velocity = Vector3.new(0, 50, 0)
                    bodyVelocity.MaxForce = Vector3.new(1e6, 1e6, 1e6)
                    bodyVelocity.Parent = character.HumanoidRootPart
                    wait(5) -- Time flying
                    bodyVelocity:Destroy()
                end
            elseif command == "speed" then game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        local humanoid = character:WaitForChild("Humanoid")
        humanoid.JumpPower = 100 -- Default is usually 50
    end)
end)
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Button setup
local frame = script.Parent.Parent -- Assume the script is inside a TextButton
local flyButton = frame:WaitForChild("FlyButton") -- A button named FlyButton
local speedButton = frame:WaitForChild("SpeedButton") -- A button named SpeedButton
local resetButton = frame:WaitForChild("ResetButton") -- A button named ResetButton

-- Fly action
flyButton.MouseButton1Click:Connect(function()
    if character and character:FindFirstChild("HumanoidRootPart") then
        local bodyVelocity = Instance.new("BodyVelocity")
        bodyVelocity.Velocity = Vector3.new(0, 50, 0)
        bodyVelocity.MaxForce = Vector3.new(1e6, 1e6, 1e6)
        bodyVelocity.Parent = character.HumanoidRootPart
        wait(5) -- Time flying
        bodyVelocity:Destroy()
    end
end)

-- Speed action
speedButton.MouseButton1Click:Connect(function()
    if character and character:FindFirstChild("Humanoid") then
        character.Humanoid.WalkSpeed = 50 -- Set speed to 50
    end
end)

-- Reset action
resetButton.MouseButton1Click:Connect(function()
    if character and character:FindFirstChild("Humanoid") then
        character.Humanoid.Health = 0 -- Reset the character
    end
end)

              
