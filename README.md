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
