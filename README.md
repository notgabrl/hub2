local Luna = loadstring(game:HttpGet("https://raw.githubusercontent.com/Nebula-Softworks/Luna-Interface-Suite/refs/heads/main/source.lua", true))()

local Window = Luna:CreateWindow({
	Name = "Idk Hub", -- Este é o título da sua janela
	Subtitle = "by @notgabrl", -- Um subtítulo cinza ao lado do título principal.
	LogoID = "82795327169782", -- O Asset ID do seu logo. Defina como nil se você não tiver um logo para o Luna usar.
	LoadingEnabled = true, -- Se deve habilitar a animação de carregamento. Defina como false se você não quiser a tela de carregamento ou tiver uma personalizada.
	LoadingTitle = "Luna Interface Suite", -- Cabeçalho da tela de carregamento
	LoadingSubtitle = "by Hland", -- Subtítulo da tela de carregamento

	ConfigSettings = {
		RootFolder = nil, -- A pasta raiz é apenas se você tiver um hub com múltiplos scripts de jogos e você pode removê-la. NÃO ADICIONE UMA BARRA
		ConfigFolder = "Big Hub" -- O nome da pasta onde o Luna armazenará as configurações para este script. NÃO ADICIONE UMA BARRA
	},

	KeySystem = false, -- A partir do Beta 6, o Luna implementou oficialmente um sistema de chaves!
	KeySettings = {
		Title = "Idk Example Key",
		Subtitle = "Key System",
		Note = "Just enter discord server to get the key",
		SaveInRoot = false, -- Habilitar salvará a chave na sua RootFolder (VOCÊ DEVE TER UMA ANTES DE HABILITAR ESTA OPÇÃO)
		SaveKey = true, -- A chave do usuário será salva, mas se você mudar a chave, eles não conseguirão usar seu script
		Key = {"idkhub"}, -- Lista de chaves que serão aceitas pelo sistema, por favor use um sistema como Pelican ou Luarmor que fornecem strings de chave baseadas no seu HWID, já que colocar uma string simples é muito fácil de contornar
		SecondAction = {
			Enabled = true, -- Defina como false se você não quiser uma segunda ação,
			Type = "Link", -- Link / Discord.
			Parameter = "" -- Se Type for Discord, então coloque seu link de convite (NÃO COLOQUE DISCORD.GG/). Caso contrário, coloque o link completo do seu sistema de chaves aqui.
		}
	}
})
local Tab = Window:CreateTab({
	Name = "Auto ...",
	Icon = "view_in_ar",
	ImageSource = "Material",
	ShowTitle = true -- Isso determinará se o texto do cabeçalho grande na aba será mostrado
})
Window:CreateHomeTab({
	SupportedExecutors = {}, -- Uma tabela de executores que seu script suporta. Adicione strings dos nomes dos executores para cada executor.
	DiscordInvite = "1234", -- O link de convite do Discord. Não inclua discord.gg/ | Apenas inclua o código.
	Icon = 2, -- Por padrão, o ícone é o ícone Home. Se você quiser mudá-lo para dashboard, substitua o inteiro por 2
})
local Paragraph = Tab:CreateParagraph({
	Title = "info",
	Text = "here you can automatically sell, buy, equip, etc.."
})
local ButtonSellAllNPCs = Tab:CreateButton({
	Name = "Sell All NPCs",
	Description = nil,
    	Callback = function()
         local args = {
         	"sellAllNPCs"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("Sell"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "SellAllNPCs")

local ButtonSellAllPlants = Tab:CreateButton({
	Name = "Sell All Plants",
	Description = nil,
    	Callback = function()
         local args = {
         	"sellAllPlants"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("Sell"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "SellAllPlants")

local ButtonEquipBestNPCs = Tab:CreateButton({
	Name = "Equip Best NPCs - Collect Money",
	Description = nil,
    	Callback = function()
         local args = {
         	"equipBestNPCs"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("EquipBest"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "EquipBestNPCs")

local SectionEquip = Tab:CreateSection("Auto Equip Best NPCs")

local equipLoopActive = false

local ToggleEquipLoop = Tab:CreateToggle({
	Name = "Auto Equip Best NPCs",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         equipLoopActive = Value
         if Value then
         	spawn(function()
         		while equipLoopActive do
         			local args = {
         				"equipBestNPCs"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("EquipBest"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoEquipLoop")

local SectionBuy = Tab:CreateSection("Auto Buy Plants")

local ButtonBuyCactus = Tab:CreateButton({
	Name = "Buy Cactus",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Cactus"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyCactus_1")

local cactusLoopActive = false
local ToggleAutoBuyCactus = Tab:CreateToggle({
	Name = "Auto Buy Cactus",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         cactusLoopActive = Value
         if Value then
         	spawn(function()
         		while cactusLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Cactus"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyCactus_2")

local ButtonBuyStrawberry = Tab:CreateButton({
	Name = "Buy Strawberry",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Strawberry"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyStrawberry")

local strawberryLoopActive = false
local ToggleAutoBuyStrawberry = Tab:CreateToggle({
	Name = "Auto Buy Strawberry",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         strawberryLoopActive = Value
         if Value then
         	spawn(function()
         		while strawberryLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Strawberry"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyStrawberry")

local ButtonBuyPumpkin = Tab:CreateButton({
	Name = "Buy Pumpkin",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Pumpkin"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyPumpkin")

local pumpkinLoopActive = false
local ToggleAutoBuyPumpkin = Tab:CreateToggle({
	Name = "Auto Buy Pumpkin",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         pumpkinLoopActive = Value
         if Value then
         	spawn(function()
         		while pumpkinLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Pumpkin"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyPumpkin")

local ButtonBuySunflower = Tab:CreateButton({
	Name = "Buy Sunflower",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Sunflower"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuySunflower")

local sunflowerLoopActive = false
local ToggleAutoBuySunflower = Tab:CreateToggle({
	Name = "Auto Buy Sunflower",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         sunflowerLoopActive = Value
         if Value then
         	spawn(function()
         		while sunflowerLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Sunflower"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuySunflower")

local ButtonBuyDragonFruit = Tab:CreateButton({
	Name = "Buy Dragon Fruit",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Dragon Fruit"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyDragonFruit")

local dragonFruitLoopActive = false
local ToggleAutoBuyDragonFruit = Tab:CreateToggle({
	Name = "Auto Buy Dragon Fruit",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         dragonFruitLoopActive = Value
         if Value then
         	spawn(function()
         		while dragonFruitLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Dragon Fruit"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyDragonFruit")

local ButtonBuyWatermelon = Tab:CreateButton({
	Name = "Buy Watermelon",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Watermelon"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyWatermelon")

local watermelonLoopActive = false
local ToggleAutoBuyWatermelon = Tab:CreateToggle({
	Name = "Auto Buy Watermelon",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         watermelonLoopActive = Value
         if Value then
         	spawn(function()
         		while watermelonLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Watermelon"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyWatermelon")

local ButtonBuyCocotank = Tab:CreateButton({
	Name = "Buy Cocotank",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Cocotank"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyCocotank")

local cocotankLoopActive = false
local ToggleAutoBuyCocotank = Tab:CreateToggle({
	Name = "Auto Buy Cocotank",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         cocotankLoopActive = Value
         if Value then
         	spawn(function()
         		while cocotankLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Cocotank"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyCocotank")

local ButtonBuyCarnivorousPlant = Tab:CreateButton({
	Name = "Buy Carnivorous Plant",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Carnivorous Plant"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyCarnivorousPlant")

local carnivorousPlantLoopActive = false
local ToggleAutoBuyCarnivorousPlant = Tab:CreateToggle({
	Name = "Auto Buy Carnivorous Plant",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         carnivorousPlantLoopActive = Value
         if Value then
         	spawn(function()
         		while carnivorousPlantLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Carnivorous Plant"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyCarnivorousPlant")

local ButtonBuyMrCarrot = Tab:CreateButton({
	Name = "Buy Mr Carrot",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Mr Carrot"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyMrCarrot")

local mrCarrotLoopActive = false
local ToggleAutoBuyMrCarrot = Tab:CreateToggle({
	Name = "Auto Buy Mr Carrot",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         mrCarrotLoopActive = Value
         if Value then
         	spawn(function()
         		while mrCarrotLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Mr Carrot"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyMrCarrot")

local ButtonBuyChompy = Tab:CreateButton({
	Name = "Buy Chompy",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Chompy"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyChompy")

local chompyLoopActive = false
local ToggleAutoBuyChompy = Tab:CreateToggle({
	Name = "Auto Buy Chompy",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         chompyLoopActive = Value
         if Value then
         	spawn(function()
         		while chompyLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Chompy"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyChompy")

local ButtonBuyPeagris = Tab:CreateButton({
	Name = "Buy Peagris",
	Description = nil,
    	Callback = function()
         local args = {
         	"purchaseSeed",
         	"Peagris"
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "BuyPeagris")

local peagrisLoopActive = false
local ToggleAutoBuyPeagris = Tab:CreateToggle({
	Name = "Auto Buy Peagris",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
         peagrisLoopActive = Value
         if Value then
         	spawn(function()
         		while peagrisLoopActive do
         			local args = {
         				"purchaseSeed",
         				"Peagris"
         			}
         			game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("SeedShop"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
         			wait(5)
         		end
         	end)
         end
    	end
}, "AutoBuyPeagris")

local TabFunctions = Window:CreateTab({
	Name = "Functions",
	Icon = "settings",
	ImageSource = "Material",
	ShowTitle = true
})

local ButtonAntiAfk = TabFunctions:CreateButton({
	Name = "Anti Afk",
	Description = nil,
    	Callback = function()
         wait(0.5)
         local ba = Instance.new("ScreenGui")
         local ca = Instance.new("TextLabel")
         local da = Instance.new("Frame")
         local _b = Instance.new("TextLabel")
         local ab = Instance.new("TextLabel")
         ba.Parent = game.CoreGui
         ba.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
         ca.Parent = ba
         ca.Active = true
         ca.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
         ca.Draggable = true
         ca.Position = UDim2.new(0.698610067, 0, 0.098096624, 0)
         ca.Size = UDim2.new(0, 370, 0, 52)
         ca.Font = Enum.Font.SourceSansSemibold
         ca.Text = "Anti Afk"
         ca.TextColor3 = Color3.new(0, 1, 1)
         ca.TextSize = 22
         da.Parent = ca
         da.BackgroundColor3 = Color3.new(0.196078, 0.196078, 0.196078)
         da.Position = UDim2.new(0, 0, 1.0192306, 0)
         da.Size = UDim2.new(0, 370, 0, 107)
         _b.Parent = da
         _b.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
         _b.Position = UDim2.new(0, 0, 0.800455689, 0)
         _b.Size = UDim2.new(0, 370, 0, 21)
         _b.Font = Enum.Font.Arial
         _b.Text = "Made by luca#5432"
         _b.TextColor3 = Color3.new(0, 1, 1)
         _b.TextSize = 20
         ab.Parent = da
         ab.BackgroundColor3 = Color3.new(0.176471, 0.176471, 0.176471)
         ab.Position = UDim2.new(0, 0, 0.158377, 0)
         ab.Size = UDim2.new(0, 370, 0, 44)
         ab.Font = Enum.Font.ArialBold
         ab.Text = "Status: Active"
         ab.TextColor3 = Color3.new(0, 1, 1)
         ab.TextSize = 20
         local bb = game:service'VirtualUser'
         game:service'Players'.LocalPlayer.Idled:connect(function()
         	bb:CaptureController()
         	bb:ClickButton2(Vector2.new())
         	ab.Text = "Roblox tried kicking you buy I didnt let them!"
         	wait(2)
         	ab.Text = "Status : Active"
         end)
    	end
}, "AntiAfk")
