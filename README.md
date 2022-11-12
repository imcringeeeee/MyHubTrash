# MyHubTrash

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("KameanHub", "Midnight")
local Tab = Window:NewTab("General")
local Section = Tab:NewSection("Auto Equip")

local Weaponlist = {}

for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
end

Section:NewDropdown("Weapon", "DropdownInf", Weaponlist, function(currentOption)
    Weapon = currentOption
end)

Section:NewToggle("AutoEquip", "ToggleInfo", function(a)
AutoEquiped = a
end)

spawn(function()
Weapon = "Combat"

while wait() do
if AutoEquiped then
pcall(function()
game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(Weapon))
end)
end
end
end)
