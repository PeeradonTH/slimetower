local library = loadstring(game:HttpGet(('https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/wall%20v3')))()
local w = library:CreateWindow("Slime Tower Tycoon")
local b = w:CreateFolder("Auto Farm")
local a = require(game.ReplicatedStorage.Modules.SharedUtility)
getgenv().Plot = a.GetPlayerTycoon(game.Players.LocalPlayer)
getgenv().DropFarm = false
getgenv().Merge = false
getgenv().DropSpeed = false
getgenv().DropDeposit = false
getgenv().SlimeOneF = false
getgenv().BuyThousandSlime = false


function CollectDrops()
	for i,v in pairs(Workspace.Drops:GetChildren()) do
		v.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
	end
end
function DepositDrops()
game:GetService("ReplicatedStorage").GTycoonClient.Remotes.DepositDrops:FireServer()
end

function BuyOneSlime()
	local SPlot = tostring(Plot)
	local PL = game:GetService("Workspace").Plots[SPlot].Buttons.BuyDropper.Button.BillboardGui.DropperCost.Text
	local apb = string.gsub(PL, "%D","")

	if game:GetService("Players").LocalPlayer.leaderstats.Coins.Value >= tonumber(apb) then
game:GetService("ReplicatedStorage").GTycoonClient.Remotes.BuyDropper:FireServer(1)
	else
	end
end
function BuyHundredSlime()
	local SPlot = tostring(Plot)
	local PL = game:GetService("Workspace").Plots[SPlot].Buttons.BuyDropper.Button.BillboardGui.DropperCost.Text
	local apb = string.gsub(PL, "%D","")

	if game:GetService("Players").LocalPlayer.leaderstats.Coins.Value >= tonumber(apb) then
game:GetService("ReplicatedStorage").GTycoonClient.Remotes.BuyDropper:FireServer(100)
	else
	end
end
function AMerge()
game:GetService("ReplicatedStorage").GTycoonClient.Remotes.MergeDroppers:FireServer()
end
function ADropSpeed()
game:GetService("ReplicatedStorage").GTycoonClient.Remotes.BuySpeed:FireServer(1)
end
function Autoobby()
local playerselect = game.Players.LocalPlayer.Character.HumanoidRootPart
local obbycheckpoint = game:GetService("Workspace").ObbyCheckpoints
local obbybutton = game:GetService("Workspace").ObbyButton2

while wait(0.75) do
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint1, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint1, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint2, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint2, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint3, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint3, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint4, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint4, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint5, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint5, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint6, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint6, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint7, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint7, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint8, 0)
            firetouchinterest(playerselect, obbycheckpoint.ObbyCheckpoint8, 1)
            wait(0.5)
            firetouchinterest(playerselect, obbybutton.Button, 0)
            firetouchinterest(playerselect, obbybutton.Button, 1)
end
end


b:Toggle("Auto Collect Drops",function(bool)
    DropFarm = bool
end)
b:Toggle("Auto Deposit Drops",function(bool)
	DropDeposit = bool
end)
b:Toggle("Auto Buy Slimes",function(bool)
	SlimeOneF = bool
end)
b:Toggle("Auto Buy 100 Slimes",function(bool)
    HundredSlime = bool
end)
b:Toggle("Auto Obby",function(bool)
    Aobby = bool
end)
b:Toggle("Auto Merge",function(bool)
	Merge = bool
end)
b:Toggle("Auto Buy Drop Rate",function(bool)
	DropSpeed = bool
end)


coroutine.wrap(function()
    while wait() do
        if DropFarm == true and task.wait(0.5) then
            pcall(function()
				CollectDrops()
            end)
        end
    end
end)()
coroutine.wrap(function()
    while wait() do
        if Aobby == true and task.wait(0.5) then
            pcall(function()
				Autoobby()
            end)
        end
    end
end)()
coroutine.wrap(function()
    while wait() do
        if DropSpeed == true and task.wait(0.5) then
            pcall(function()
				ADropSpeed()
            end)
        end
    end
end)()

coroutine.wrap(function()
    while wait() do
        if Merge == true and task.wait(0.5) then
            pcall(function()
				AMerge()
            end)
        end
    end
end)()

coroutine.wrap(function()
    while wait() do
        if SlimeOneF == true and task.wait(0.01) then
            pcall(function()
				BuyOneSlime()
            end)
        end
    end
end)()

coroutine.wrap(function()
    while wait() do
        if HundredSlime == true and task.wait(0.01) then
            pcall(function()
				BuyHundredSlime()
            end)
        end
    end
end)()
coroutine.wrap(function()
    while wait() do
        if DropDeposit == true and task.wait(0.5) then
            pcall(function()
				DepositDrops()
            end)
        end
    end
end)()

game.StarterGui:SetCore("SendNotification", {
	Title = "Credits";
	Text = "Free source code";
	Icon = "rbxassetid://2541869220";
	Duration = 5;
})
