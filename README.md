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

local ButtonSellHand = Tab:CreateButton({
	Name = "Sell Hand",
	Description = nil,
    	Callback = function()
         local args = {
         	"sellHoldingItem",
         	Instance.new("Tool", nil)
         }
         game:GetService("ReplicatedStorage"):WaitForChild("Packages"):WaitForChild("Networker"):WaitForChild("leifstout_networker@0.3.0"):WaitForChild("networker"):WaitForChild("_remotes"):WaitForChild("Sell"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    	end
}, "SellHand")
local Dropdown = Tab:CreateDropdown({
	Name = "Dropdown Example",
    	Description = nil,
	Options = {"Option 1","Option 2"},
    	CurrentOption = {"Option 1"},
    	MultipleOptions = false,
    	SpecialType = nil,
    	Callback = function(Options)
     	 -- A função que acontece quando a opção selecionada é alterada
    	 -- Se MultipleOptions for true, então a variável (Options) é uma tabela de strings para as opções selecionadas atualmente. Caso contrário, é uma string da opção atual
	end
}, "Dropdown") -- Uma flag é o identificador para o arquivo de configuração, certifique-se de que cada elemento tenha uma flag diferente se você estiver usando salvamento de configuração para garantir que não haja sobreposições
local Toggle = Tab:CreateToggle({
	Name = "Toggle Example",
	Description = nil,
	CurrentValue = false,
    	Callback = function(Value)
       	 -- A função que acontece quando o toggle é alternado
       	 -- A variável (Value) é um booleano indicando se o toggle está true ou false
    	end
}, "Toggle") -- Uma flag é o identificador para o arquivo de configuração, certifique-se de que cada elemento tenha uma flag diferente se você estiver usando salvamento de configuração para garantir que não haja sobreposições
local Bind = Tab:CreateBind({
	Name = "Bind Example",
	Description = nil,
	CurrentBind = "Q", -- Verifique a documentação do Roblox Studio para nomes de KeyCode
	HoldToInteract = false, -- Quando true, ao invés de alternar, você segura para alcançar o estado ativo do Bind
    	Callback = function(BindState)
     	 -- A função que acontece quando a tecla de atalho é pressionada
     	 -- A variável (BindState) é um booleano indicando se o Bind está sendo segurado ou não (HoldToInteract precisa ser true) OU é se o Bind está ativo
    	end,

	OnChangedCallback = function(Bind)
	 -- A função que acontece quando a tecla vinculada muda
	 -- A variável (Bind) é um Enum.KeyCode para a nova tecla vinculada
	end,
}, "Bind") -- Uma flag é o identificador para o arquivo de configuração, certifique-se de que cada elemento tenha uma flag diferente se você estiver usando salvamento de configuração para garantir que não haja sobreposições
local Label = Tab:CreateLabel({
	Text = "Label Example",
	Style = 2 -- Os Labels do Luna têm 3 estilos: Um Label básico, Um Label de informação verde e Um Label de aviso vermelho. Veja a imagem a seguir para mais detalhes
})
