-- Made by bossorlose13
-- 
 
-- Instances:
 
local ScreenGui = Instance.new("ScreenGui")
local mainframe = Instance.new("Frame")
local Bossorlose13sGUI = Instance.new("TextLabel")
local Noclip = Instance.new("TextButton")
local Fly = Instance.new("TextButton")
 
--Properties:
 
ScreenGui.Parent = game.CoreGui
 
mainframe.Name = "mainframe"
mainframe.Parent = ScreenGui
mainframe.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
mainframe.BorderColor3 = Color3.fromRGB(0, 0, 0)
mainframe.Position = UDim2.new(0.135501355, 0, 0.306020081, 0)
mainframe.Size = UDim2.new(0, 282, 0, 180)
 
Bossorlose13sGUI.Name = "Bossorlose13's GUI"
Bossorlose13sGUI.Parent = mainframe
Bossorlose13sGUI.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Bossorlose13sGUI.Size = UDim2.new(0, 282, 0, 22)
Bossorlose13sGUI.Font = Enum.Font.SourceSans
Bossorlose13sGUI.Text = "Bossorlose13's GUI"
Bossorlose13sGUI.TextColor3 = Color3.fromRGB(255, 0, 0)
Bossorlose13sGUI.TextSize = 14.000
 
Noclip.Name = "Noclip"
Noclip.Parent = mainframe
Noclip.BackgroundColor3 = Color3.fromRGB(85, 0, 255)
Noclip.Position = UDim2.new(0.0283687934, 0, 0.294444442, 0)
Noclip.Size = UDim2.new(0, 77, 0, 22)
Noclip.Font = Enum.Font.SourceSans
Noclip.Text = "Noclip"
Noclip.TextColor3 = Color3.fromRGB(0, 0, 0)
Noclip.TextSize = 14.000
Noclip.MouseButton1Down:connect(function()
	local noclip = true char = game.Players.LocalPlayer.Character while true do if noclip == true then for _,v in pairs(char:children()) do pcall(function() if v.className == "Part" then v.CanCollide = false elseif v.ClassName == "Model" then v.Head.CanCollide = false end end) end end game:service("RunService").Stepped:wait() end
end)
Fly.Name = "Fly"
Fly.Parent = mainframe
Fly.BackgroundColor3 = Color3.fromRGB(85, 0, 255)
Fly.Position = UDim2.new(0.723404229, 0, 0.305555552, 0)
Fly.Size = UDim2.new(0, 48, 0, 20)
Fly.Font = Enum.Font.SourceSans
Fly.Text = "Fly"
Fly.TextColor3 = Color3.fromRGB(0, 0, 0)
Fly.TextSize = 14.000
Fly.MouseButton1Down:connect(function()
	repeat wait()
	until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Torso") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid")
	local mouse = game.Players.LocalPlayer:GetMouse()
	repeat wait() until mouse
	local plr = game.Players.LocalPlayer
	local torso = plr.Character.Torso
	local flying = true
	local deb = true
	local ctrl = {f = 0, b = 0, l = 0, r = 0}
	local lastctrl = {f = 0, b = 0, l = 0, r = 0}
	local maxspeed = 50
	local speed = 0
 
	function Fly()
		local bg = Instance.new("BodyGyro", torso)
		bg.P = 9e4
		bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
		bg.cframe = torso.CFrame
		local bv = Instance.new("BodyVelocity", torso)
		bv.velocity = Vector3.new(0,0.1,0)
		bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
		repeat wait()
			plr.Character.Humanoid.PlatformStand = true
			if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then
				speed = speed+.5+(speed/maxspeed)
				if speed > maxspeed then
					speed = maxspeed
				end
			elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then
				speed = speed-1
				if speed < 0 then
					speed = 0
				end
			end
			if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
				lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r}
			elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
			else
				bv.velocity = Vector3.new(0,0.1,0)
			end
			bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0)
		until not flying
		ctrl = {f = 0, b = 0, l = 0, r = 0}
		lastctrl = {f = 0, b = 0, l = 0, r = 0}
		speed = 0
		bg:Destroy()
		bv:Destroy()
		plr.Character.Humanoid.PlatformStand = false
	end
	mouse.KeyDown:connect(function(key)
		if key:lower() == "e" then
			if flying then flying = false
			else
				flying = true
				Fly()
			end
		elseif key:lower() == "w" then
			ctrl.f = 1
		elseif key:lower() == "s" then
			ctrl.b = -1
		elseif key:lower() == "a" then
			ctrl.l = -1
		elseif key:lower() == "d" then
			ctrl.r = 1
		end
	end)
	mouse.KeyUp:connect(function(key)
		if key:lower() == "w" then
			ctrl.f = 0
		elseif key:lower() == "s" then
			ctrl.b = 0
		elseif key:lower() == "a" then
			ctrl.l = 0
		elseif key:lower() == "d" then
			ctrl.r = 0
		end
	end)
	Fly()
 
end)
-- Scripts:
 
local function JETILC_fake_script() -- mainframe.LocalScript 
	local script = Instance.new('LocalScript', mainframe)
 
	script.parent.Selectable = true
	script.Parent.Active = true
	script.parent.Draggable = true
 
end
coroutine.wrap(JETILC_fake_script)()
