-- Anti-Kick / Anti-Ban
local mt = getrawmetatable(game)
setreadonly(mt, false)
local namecall = mt.__namecall
mt.__namecall = newcclosure(function(self, ...)
    local method = getnamecallmethod()
    if method == "Kick" or method == "kick" then
        return warn("[ZKHub] Kick attempt blocked.")
    end
    return namecall(self, ...)
end)

-- Load Rayfield UI Library
local Rayfield = loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Rayfield/main/source.lua"))()

local Window = Rayfield:CreateWindow({
	Name = "ZKHub - Streetz War 2",
	LoadingTitle = "ZKHub Loading...",
	LoadingSubtitle = "Silent Aim / Autofarm / ESP",
	ConfigurationSaving = {
		Enabled = true,
		FolderName = "ZKHubSW2",
		FileName = "ZKHubConfig"
	},
	KeySystem = false,
})

-- Get Player Info
local player = game.Players.LocalPlayer
local emoji = "🔥"
local level = "Unknown"
local leaderstats = player:FindFirstChild("leaderstats")
if leaderstats and leaderstats:FindFirstChild("Level") then
	level = leaderstats.Level.Value
end

-- Player Tab
local PlayerTab = Window:CreateTab("Player", 4483362458)
PlayerTab:CreateParagraph({
	Title = "Welcome!",
	Content = "Name: "..player.Name.."\nLevel: "..level.."\nEmoji: "..emoji
})

-- Autofarm Tab
local AutoTab = Window:CreateTab("Autofarm", 4483362458)

local farmingMop = false
AutoTab:CreateToggle({
	Name = "Mop AutoFarm",
	CurrentValue = false,
	Flag = "MopAutoFarm",
	Callback = function(val)
		farmingMop = val
		while farmingMop do
			-- Replace with your mop farming logic
			print("Auto farming mop...")
			task.wait(1)
		end
	end,
})

local farmingBox = false
AutoTab:CreateToggle({
	Name = "Box AutoFarm",
	CurrentValue = false,
	Flag = "BoxAutoFarm",
	Callback = function(val)
		farmingBox = val
		while farmingBox do
			-- Replace with box logic
			print("Auto farming box...")
			task.wait(1)
		end
	end,
})

-- Teleport Tab
local TeleTab = Window:CreateTab("Teleport", 4483362458)

TeleTab:CreateButton({
	Name = "Gun Store",
	Callback = function()
		player.Character:MoveTo(Vector3.new(100, 10, 200)) -- change to real coordinates
	end,
})
TeleTab:CreateButton({
	Name = "Safe Zone",
	Callback = function()
		player.Character:MoveTo(Vector3.new(0, 5, 0))
	end,
})

-- Combat Tab
local CombatTab = Window:CreateTab("Combat", 4483362458)

-- Silent Aim (basic)
getgenv().SilentAim = false
CombatTab:CreateToggle({
	Name = "Silent Aim",
	CurrentValue = false,
	Flag = "SilentAim",
	Callback = function(val)
		getgenv().SilentAim = val
	end,
})

-- Aimbot (basic)
getgenv().Aimbot = false
CombatTab:CreateToggle({
	Name = "Aimbot",
	CurrentValue = false,
	Flag = "Aimbot",
	Callback = function(val)
		getgenv().Aimbot = val
	end,
})

-- ESP
getgenv().ESPEnabled = false
CombatTab:CreateToggle({
	Name = "Player ESP",
	CurrentValue = false,
	Flag = "ESP",
	Callback = function(val)
		getgenv().ESPEnabled = val
		while getgenv().ESPEnabled do
			for _, v in pairs(game.Players:GetPlayers()) do
				if v ~= player and v.Character and not v.Character:FindFirstChild("ESP") then
					local highlight = Instance.new("Highlight", v.Character)
					highlight.Name = "ESP"
					highlight.FillColor = Color3.new(1, 0, 0)
					highlight.OutlineColor = Color3.new(1, 1, 1)
				end
			end
			task.wait(2)
		end
		for _, v in pairs(game.Players:GetPlayers()) do
			if v.Character and v.Character:FindFirstChild("ESP") then
				v.Character.ESP:Destroy()
			end
		end
	end,
})

-- Settings Tab
local SettingsTab = Window:CreateTab("Settings", 4483362458)

SettingsTab:CreateInput({
	Name = "Set Emoji",
	PlaceholderText = "Type your emoji...",
	RemoveTextAfterFocusLost = true,
	Callback = function(txt)
		emoji = txt
		Rayfield:Notify({Title = "Emoji Updated", Content = "Emoji set to "..emoji})
	end,
})

SettingsTab:CreateButton({
	Name = "Destroy GUI",
	Callback = function()
		Rayfield:Destroy()
	end,
})
