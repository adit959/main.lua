-- Adit Premium Hub v1.1 (UI + Toggle + Dragable)
local gui = Instance.new("ScreenGui", game.CoreGui)
gui.Name = "AditPremiumHub"

-- Main Frame
local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 420, 0, 360)
frame.Position = UDim2.new(0.3, 0, 0.2, 0)
frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
frame.BorderSizePixel = 0

local uicorner = Instance.new("UICorner", frame)
uicorner.CornerRadius = UDim.new(0, 10)

-- Title
local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1, 0, 0, 50)
title.Text = "Adit Premium Hub"
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.GothamBold
title.TextSize = 28

-- Dragging logic
local dragging, dragInput, startPos, startInputPos

frame.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = true
		startInputPos = input.Position
		startPos = frame.Position
		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

frame.InputChanged:Connect(function(input)
	if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
		local delta = input.Position - startInputPos
		frame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
	end
end)

-- Toggle state storage
local toggles = {
	AutoCast = false,
	AutoShake = false,
	AutoReel = false,
	AutoSell = false,
	AutoHoldSell = false
}

-- Toggle button creator
local function createToggle(name, posY)
	local button = Instance.new("TextButton", frame)
	button.Size = UDim2.new(0, 300, 0, 40)
	button.Position = UDim2.new(0.5, -150, 0, posY)
	button.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
	button.TextColor3 = Color3.fromRGB(255, 255, 255)
	button.Font = Enum.Font.Gotham
	button.TextSize = 16
	button.Text = name .. ": OFF"

	local corner = Instance.new("UICorner", button)
	corner.CornerRadius = UDim.new(0, 8)

	button.MouseButton1Click:Connect(function()
		toggles[name] = not toggles[name]
		button.Text = name .. ": " .. (toggles[name] and "ON" or "OFF")
		button.BackgroundColor3 = toggles[name] and Color3.fromRGB(0, 170, 85) or Color3.fromRGB(70, 70, 70)
	end)
end

-- Buat tombol toggle
createToggle("AutoCast", 60)
createToggle("AutoShake", 110)
createToggle("AutoReel", 160)
createToggle("AutoSell", 210)
createToggle("AutoHoldSell", 260)

-- Contoh logic loop (bisa lo modif tergantung remotenya)
task.spawn(function()
	while true do
		if toggles.AutoCast then
			print("Casting...")
			-- game:GetService("ReplicatedStorage").Whatever:FireServer("Cast")
		end
		if toggles.AutoShake then
			print("Shaking...")
		end
		if toggles.AutoReel then
			print("Reeling...")
		end
		if toggles.AutoSell then
			print("Selling fish...")
		end
		if toggles.AutoHoldSell then
			print("Hold+Sell...")
		end
		task.wait(2)
	end
end)
