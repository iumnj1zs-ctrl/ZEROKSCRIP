-- VOID HUB LOADED
local Player = game:GetService('Players').LocalPlayer
local CoreGui = game:GetService('CoreGui')
local ScreenGui = Instance.new('ScreenGui', CoreGui)
ScreenGui.Name = 'ZEROK_HUB'
ScreenGui.ResetOnSpawn = false

local ScreenGui_1989 = Instance.new('ScreenGui', ScreenGui)
ScreenGui_1989.Name = [[ScreenGui]]
local Frame_4120 = Instance.new('Frame', ScreenGui_1989)
Frame_4120.Name = [[Frame]]
Frame_4120.Size = UDim2.new(0.000000, 632, 0.000000, 432)
Frame_4120.Position = UDim2.new(0.126298, 0, 0.125000, 0)
Frame_4120.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame_4120.BorderSizePixel = 0
Frame_4120.BorderColor3 = Color3.fromRGB(0, 0, 0)
Frame_4120.Rotation = 0
Frame_4120.Visible = false
Frame_4120.ZIndex = 1
Frame_4120.Transparency = 0
-- Script: LocalScript
task.spawn(function()
local script = {Parent = Frame_4120}
local UserInputService = game:GetService("UserInputService")

local gui = script.Parent

local dragging
local dragInput
local dragStart
local startPos

local function update(input)
	local delta = input.Position - dragStart
	-- تحريك القائمة بناءً على إحداثيات الماوس الجديدة
	gui.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end

gui.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		dragging = true
		dragStart = input.Position
		startPos = gui.Position

		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

gui.InputChanged:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
		dragInput = input
	end
end)

UserInputService.InputChanged:Connect(function(input)
	if input == dragInput and dragging then
		update(input)
	end
end)
end)
local UICorner_6757 = Instance.new('UICorner', Frame_4120)
UICorner_6757.Name = [[UICorner]]
UICorner_6757.CornerRadius = UDim.new(0.000000, 8)
local ZEROK_5046 = Instance.new('TextLabel', Frame_4120)
ZEROK_5046.Name = [[ZEROK]]
ZEROK_5046.Size = UDim2.new(0.000000, 632, 0.000000, 70)
ZEROK_5046.Position = UDim2.new(0.000000, 0, 0.000000, 0)
ZEROK_5046.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ZEROK_5046.BorderSizePixel = 0
ZEROK_5046.BorderColor3 = Color3.fromRGB(0, 0, 0)
ZEROK_5046.Rotation = 0
ZEROK_5046.Visible = true
ZEROK_5046.ZIndex = 1
ZEROK_5046.Transparency = 1
ZEROK_5046.Text = 'Welcome: ' .. Player.Name
ZEROK_5046.TextColor3 = Color3.fromRGB(0, 0, 0)
ZEROK_5046.TextSize = 14
ZEROK_5046.Font = Enum.Font.Unknown
ZEROK_5046.TextScaled = true
ZEROK_5046.FontFace = Font.new([[rbxasset://fonts/families/Creepster.json]], Enum.FontWeight.Bold, Enum.FontStyle.Italic)
ZEROK_5046.ZIndex = 10
local UIGradient_3779 = Instance.new('UIGradient', Frame_4120)
UIGradient_3779.Name = [[UIGradient]]
UIGradient_3779.Rotation = 0
UIGradient_3779.Color = ColorSequence.new({ColorSequenceKeypoint.new(0.000000, Color3.fromRGB(19, 35, 255)), ColorSequenceKeypoint.new(1.000000, Color3.fromRGB(44, 209, 255))})
UIGradient_3779.Rotation = 0
local Fly_5009 = Instance.new('TextButton', Frame_4120)
Fly_5009.Name = [[Fly]]
Fly_5009.Size = UDim2.new(0.000000, 173, 0.000000, 50)
Fly_5009.Position = UDim2.new(0.053797, 0, 0.187500, 0)
Fly_5009.BackgroundColor3 = Color3.fromRGB(0, 0, 127)
Fly_5009.BorderSizePixel = 0
Fly_5009.BorderColor3 = Color3.fromRGB(0, 0, 0)
Fly_5009.Rotation = 0
Fly_5009.Visible = true
Fly_5009.ZIndex = 1
Fly_5009.Transparency = 0
Fly_5009.Text = [[Fly]]
Fly_5009.TextColor3 = Color3.fromRGB(0, 0, 0)
Fly_5009.TextSize = 14
Fly_5009.Font = Enum.Font.Unknown
Fly_5009.TextScaled = true
Fly_5009.FontFace = Font.new([[rbxasset://fonts/families/FredokaOne.json]], Enum.FontWeight.Bold, Enum.FontStyle.Italic)
local UICorner_8954 = Instance.new('UICorner', Fly_5009)
UICorner_8954.Name = [[UICorner]]
UICorner_8954.CornerRadius = UDim.new(0.000000, 8)
-- Script: LocalScript
task.spawn(function()
local script = {Parent = Fly_5009}
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local hrp = character:WaitForChild("HumanoidRootPart")
local button = script.Parent
local UIS = game:GetService("UserInputService")

local flying = false
local speed = 70
local bv, bg

button.MouseButton1Click:Connect(function()
	flying = not flying

	if flying then
		-- تغيير مظهر الزر عند التفعيل
		button.Text = "FLYING: ON"
		button.TextColor3 = Color3.fromRGB(0, 255, 150) -- لون أخضر نيون

		-- إيقاف الأنميشن (تجميد الشخصية في وضع السكون)
		humanoid.PlatformStand = true 

		-- إضافة قوى الطيران
		bv = Instance.new("BodyVelocity")
		bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
		bv.Velocity = Vector3.new(0, 0, 0)
		bv.Parent = hrp

		bg = Instance.new("BodyGyro")
		bg.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
		bg.CFrame = hrp.CFrame
		bg.Parent = hrp

		-- حلقة التحكم بالتحرك
		task.spawn(function()
			while flying do
				local cam = workspace.CurrentCamera
				local dir = Vector3.new(0,0,0)

				if UIS:IsKeyDown(Enum.KeyCode.W) then dir = dir + cam.CFrame.LookVector end
				if UIS:IsKeyDown(Enum.KeyCode.S) then dir = dir - cam.CFrame.LookVector end
				if UIS:IsKeyDown(Enum.KeyCode.A) then dir = dir - cam.CFrame.RightVector end
				if UIS:IsKeyDown(Enum.KeyCode.D) then dir = dir + cam.CFrame.RightVector end

				bv.Velocity = dir * speed
				bg.CFrame = cam.CFrame
				task.wait()
			end
		end)
	else
		-- العودة للحالة الطبيعية عند الإيقاف
		button.Text = "FLYING: OFF"
		button.TextColor3 = Color3.fromRGB(255, 255, 255)

		humanoid.PlatformStand = false -- إعادة الأنميشن
		if bv then bv:Destroy() end
		if bg then bg:Destroy() end
	end
end)
end)
local EMOTEBROOM_8414 = Instance.new('TextButton', Frame_4120)
EMOTEBROOM_8414.Name = [[EMOTE BROOM]]
EMOTEBROOM_8414.Size = UDim2.new(0.000000, 173, 0.000000, 50)
EMOTEBROOM_8414.Position = UDim2.new(0.053797, 0, 0.442130, 0)
EMOTEBROOM_8414.BackgroundColor3 = Color3.fromRGB(0, 0, 127)
EMOTEBROOM_8414.BorderSizePixel = 0
EMOTEBROOM_8414.BorderColor3 = Color3.fromRGB(0, 0, 0)
EMOTEBROOM_8414.Rotation = 0
EMOTEBROOM_8414.Visible = true
EMOTEBROOM_8414.ZIndex = 1
EMOTEBROOM_8414.Transparency = 0
EMOTEBROOM_8414.Text = [[Head = Broom]]
EMOTEBROOM_8414.TextColor3 = Color3.fromRGB(0, 0, 0)
EMOTEBROOM_8414.TextSize = 14
EMOTEBROOM_8414.Font = Enum.Font.Unknown
EMOTEBROOM_8414.TextScaled = true
EMOTEBROOM_8414.FontFace = Font.new([[rbxasset://fonts/families/FredokaOne.json]], Enum.FontWeight.Bold, Enum.FontStyle.Italic)
local UICorner_9129 = Instance.new('UICorner', EMOTEBROOM_8414)
UICorner_9129.Name = [[UICorner]]
UICorner_9129.CornerRadius = UDim.new(0.000000, 8)
-- Script: LocalScript
task.spawn(function()
local script = {Parent = EMOTEBROOM_8414}
local button = script.Parent
local replicatedStorage = game:GetService("ReplicatedStorage")

button.MouseButton1Click:Connect(function()
	-- التحقق من وجود الأداة قبل تغيير الاسم لتجنب الأخطاء
	local item = replicatedStorage:FindFirstChild("Items") and replicatedStorage.Items:FindFirstChild("Broom")

	if item then
		item.Name = "HeadlessBaller"
		button.Text = "Done!"
		button.TextColor3 = Color3.fromRGB(0, 255, 0) -- تغيير لون النص للأخضر للتأكيد
		print("Success: Name changed to HeadlessBaller")
	else
		warn("Error: Item 'Broom' not found in ReplicatedStorage.Items")
		button.Text = "Not Found!"
		button.TextColor3 = Color3.fromRGB(255, 0, 0) -- لون أحمر في حال الفشل
	end
end)
end)
local EMOTEHoveringCrystal_2804 = Instance.new('TextButton', Frame_4120)
EMOTEHoveringCrystal_2804.Name = [[EMOTE HoveringCrystal]]
EMOTEHoveringCrystal_2804.Size = UDim2.new(0.000000, 173, 0.000000, 50)
EMOTEHoveringCrystal_2804.Position = UDim2.new(0.053797, 0, 0.671296, 0)
EMOTEHoveringCrystal_2804.BackgroundColor3 = Color3.fromRGB(0, 0, 127)
EMOTEHoveringCrystal_2804.BorderSizePixel = 0
EMOTEHoveringCrystal_2804.BorderColor3 = Color3.fromRGB(0, 0, 0)
EMOTEHoveringCrystal_2804.Rotation = 0
EMOTEHoveringCrystal_2804.Visible = true
EMOTEHoveringCrystal_2804.ZIndex = 1
EMOTEHoveringCrystal_2804.Transparency = 0
EMOTEHoveringCrystal_2804.Text = [[FrostDrake = HoveringCrystal]]
EMOTEHoveringCrystal_2804.TextColor3 = Color3.fromRGB(0, 0, 0)
EMOTEHoveringCrystal_2804.TextSize = 14
EMOTEHoveringCrystal_2804.Font = Enum.Font.Unknown
EMOTEHoveringCrystal_2804.TextScaled = true
EMOTEHoveringCrystal_2804.FontFace = Font.new([[rbxasset://fonts/families/FredokaOne.json]], Enum.FontWeight.Bold, Enum.FontStyle.Italic)
local UICorner_7465 = Instance.new('UICorner', EMOTEHoveringCrystal_2804)
UICorner_7465.Name = [[UICorner]]
UICorner_7465.CornerRadius = UDim.new(0.000000, 8)
-- Script: LocalScript
task.spawn(function()
local script = {Parent = EMOTEHoveringCrystal_2804}
local button = script.Parent
local replicatedStorage = game:GetService("ReplicatedStorage")

button.MouseButton1Click:Connect(function()
	-- الوصول إلى المسار المطلوب
	local items = replicatedStorage:FindFirstChild("Items")
	if items then
		local emotes = items:FindFirstChild("Emotes")
		if emotes then
			local targetItem = emotes:FindFirstChild("HoveringCrystal")

			if targetItem then
				targetItem.Name = "FrostDrake"

				-- تأثير بصري بسيط للزر عند النجاح
				button.Text = "Name Changed!"
				button.TextColor3 = Color3.fromRGB(0, 255, 255) -- لون سماوي (Cyan) يناسب اسم Frost
				print("Success: HoveringCrystal renamed to FrostDrake")
			else
				warn("Item 'HoveringCrystal' not found!")
				button.Text = "Not Found!"
			end
		else
			warn("'Emotes' folder not found!")
		end
	else
		warn("'Items' folder not found!")
	end
end)
end)
local EMOTERocket_5101 = Instance.new('TextButton', Frame_4120)
EMOTERocket_5101.Name = [[EMOTE Rocket]]
EMOTERocket_5101.Size = UDim2.new(0.000000, 173, 0.000000, 50)
EMOTERocket_5101.Position = UDim2.new(0.693038, 0, 0.671296, 0)
EMOTERocket_5101.BackgroundColor3 = Color3.fromRGB(37, 162, 255)
EMOTERocket_5101.BorderSizePixel = 0
EMOTERocket_5101.BorderColor3 = Color3.fromRGB(0, 0, 0)
EMOTERocket_5101.Rotation = 0
EMOTERocket_5101.Visible = true
EMOTERocket_5101.ZIndex = 1
EMOTERocket_5101.Transparency = 0
EMOTERocket_5101.Text = [[HeadlessHorseman = Rocket]]
EMOTERocket_5101.TextColor3 = Color3.fromRGB(0, 0, 0)
EMOTERocket_5101.TextSize = 14
EMOTERocket_5101.Font = Enum.Font.Unknown
EMOTERocket_5101.TextScaled = true
EMOTERocket_5101.FontFace = Font.new([[rbxasset://fonts/families/FredokaOne.json]], Enum.FontWeight.Bold, Enum.FontStyle.Italic)
local UICorner_8377 = Instance.new('UICorner', EMOTERocket_5101)
UICorner_8377.Name = [[UICorner]]
UICorner_8377.CornerRadius = UDim.new(0.000000, 8)
-- Script: LocalScript
task.spawn(function()
local script = {Parent = EMOTERocket_5101}
local button = script.Parent
local replicatedStorage = game:GetService("ReplicatedStorage")

button.MouseButton1Click:Connect(function()
	-- الوصول للمسار: Items -> Emotes -> Rocket
	local items = replicatedStorage:FindFirstChild("Items")
	if items then
		local emotes = items:FindFirstChild("Emotes")
		if emotes then
			local rocket = emotes:FindFirstChild("Rocket")

			if rocket then
				rocket.Name = "HeadlessHorseman"

				-- تغيير شكل الزر للتأكيد
				button.Text = "Rocket -> Headless"
				button.TextColor3 = Color3.fromRGB(255, 170, 0) -- لون برتقالي/ذهبي احترافي
				print("Success: Rocket renamed to HeadlessHorseman")
			else
				button.Text = "Rocket Not Found"
				warn("Rocket object not found in Emotes")
			end
		else
			warn("Emotes folder not found")
		end
	else
		warn("Items folder not found")
	end
end)
end)
local Open_1963 = Instance.new('TextButton', ScreenGui_1989)
Open_1963.Name = [[Open]]
Open_1963.Size = UDim2.new(0.000000, 43, 0.000000, 43)
Open_1963.Position = UDim2.new(0.010623, 0, 0.574653, 0)
Open_1963.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Open_1963.BorderSizePixel = 0
Open_1963.BorderColor3 = Color3.fromRGB(0, 0, 0)
Open_1963.Rotation = 0
Open_1963.Visible = true
Open_1963.ZIndex = 1
Open_1963.Transparency = 0
Open_1963.Text = [[Open]]
Open_1963.TextColor3 = Color3.fromRGB(255, 255, 255)
Open_1963.TextSize = 17
Open_1963.Font = Enum.Font.Unknown
Open_1963.TextScaled = false
Open_1963.FontFace = Font.new([[rbxasset://fonts/families/FredokaOne.json]], Enum.FontWeight.Bold, Enum.FontStyle.Italic)
local UICorner_7357 = Instance.new('UICorner', Open_1963)
UICorner_7357.Name = [[UICorner]]
UICorner_7357.CornerRadius = UDim.new(0.000000, 8)
local UIGradient_2200 = Instance.new('UIGradient', Open_1963)
UIGradient_2200.Name = [[UIGradient]]
UIGradient_2200.Rotation = 0
UIGradient_2200.Color = ColorSequence.new({ColorSequenceKeypoint.new(0.000000, Color3.fromRGB(17, 255, 0)), ColorSequenceKeypoint.new(1.000000, Color3.fromRGB(70, 70, 70))})
UIGradient_2200.Rotation = 0
-- Script: LocalScript
task.spawn(function()
local script = {Parent = Open_1963}
local button = script.Parent -- الزر الذي تضغط عليه
local frame = button.Parent:FindFirstChild("Frame") -- استبدل "Frame" باسم القائمة لديك

button.MouseButton1Click:Connect(function()
	if frame then
		frame.Visible = not frame.Visible
	else
		warn("القائمة (Frame) غير موجودة، تأكد من مطابقة الاسم!")
	end
end)
end)
