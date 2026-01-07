local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")

local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()

-- [ 1. CLEANUP ]
if CoreGui:FindFirstChild("PKRI_Universal_UI") then
	CoreGui.PKRI_Universal_UI:Destroy()
end

-- [ 2. MAIN GUI SETUP ]
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PKRI_Universal_UI"
ScreenGui.Parent = CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

-- [ MAIN WINDOW ]
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15) -- Dark Background
MainFrame.Position = UDim2.new(0.5, -300, 0.5, -200)
MainFrame.Size = UDim2.new(0, 600, 0, 400)
MainFrame.BorderSizePixel = 0

local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0, 10)
MainCorner.Parent = MainFrame

-- [ HEADER ]
local Header = Instance.new("Frame")
Header.Name = "Header"
Header.Parent = MainFrame
Header.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Header.BackgroundTransparency = 1
Header.Size = UDim2.new(1, 0, 0, 40)

local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.Parent = Header
Title.BackgroundTransparency = 1
Title.Position = UDim2.new(0, 20, 0, 10)
Title.Size = UDim2.new(0, 200, 0, 20)
Title.Font = Enum.Font.GothamBold
Title.Text = "PKRI HUB V3"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 16
Title.TextXAlignment = Enum.TextXAlignment.Left

local SubTitle = Instance.new("TextLabel")
SubTitle.Name = "SubTitle"
SubTitle.Parent = Header
SubTitle.BackgroundTransparency = 1
SubTitle.Position = UDim2.new(0, 20, 0, 25)
SubTitle.Size = UDim2.new(0, 200, 0, 15)
SubTitle.Font = Enum.Font.Gotham
SubTitle.Text = "UNIVERSAL SCRIPT"
SubTitle.TextColor3 = Color3.fromRGB(150, 150, 150)
SubTitle.TextSize = 10
SubTitle.TextXAlignment = Enum.TextXAlignment.Left

local CloseBtn = Instance.new("TextButton")
CloseBtn.Name = "CloseBtn"
CloseBtn.Parent = Header
CloseBtn.BackgroundTransparency = 1
CloseBtn.Position = UDim2.new(1, -40, 0, 0)
CloseBtn.Size = UDim2.new(0, 40, 0, 40)
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
CloseBtn.TextSize = 14
CloseBtn.MouseButton1Click:Connect(function()
	ScreenGui:Destroy()
end)

-- [ SIDEBAR ]
local Sidebar = Instance.new("Frame")
Sidebar.Name = "Sidebar"
Sidebar.Parent = MainFrame
Sidebar.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
Sidebar.Position = UDim2.new(0, 0, 0, 50)
Sidebar.Size = UDim2.new(0, 160, 1, -50)
Sidebar.BorderSizePixel = 0

local SidebarCorner = Instance.new("UICorner")
SidebarCorner.CornerRadius = UDim.new(0, 10)
SidebarCorner.Parent = Sidebar

local SidebarFix = Instance.new("Frame")
SidebarFix.Parent = Sidebar
SidebarFix.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
SidebarFix.BorderSizePixel = 0
SidebarFix.Position = UDim2.new(1, -5, 0, 0)
SidebarFix.Size = UDim2.new(0, 5, 1, 0)

-- [ PROFILE SECTION ]
local ProfileFrame = Instance.new("Frame")
ProfileFrame.Name = "ProfileFrame"
ProfileFrame.Parent = Sidebar
ProfileFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
ProfileFrame.BorderSizePixel = 0
ProfileFrame.Position = UDim2.new(0, 10, 1, -60)
ProfileFrame.Size = UDim2.new(1, -20, 0, 50)

local ProfileCorner = Instance.new("UICorner")
ProfileCorner.CornerRadius = UDim.new(0, 8)
ProfileCorner.Parent = ProfileFrame

local Avatar = Instance.new("ImageLabel")
Avatar.Parent = ProfileFrame
Avatar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Avatar.BackgroundTransparency = 1
Avatar.Position = UDim2.new(0, 5, 0.5, -17)
Avatar.Size = UDim2.new(0, 34, 0, 34)
Avatar.Image = Players:GetUserThumbnailAsync(LocalPlayer.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size420x420)

local AvatarCorner = Instance.new("UICorner")
AvatarCorner.CornerRadius = UDim.new(1, 0)
AvatarCorner.Parent = Avatar

local DisplayName = Instance.new("TextLabel")
DisplayName.Parent = ProfileFrame
DisplayName.BackgroundTransparency = 1
DisplayName.Position = UDim2.new(0, 45, 0, 8)
DisplayName.Size = UDim2.new(1, -50, 0, 15)
DisplayName.Font = Enum.Font.GothamBold
DisplayName.Text = LocalPlayer.DisplayName
DisplayName.TextColor3 = Color3.fromRGB(255, 255, 255)
DisplayName.TextSize = 12
DisplayName.TextXAlignment = Enum.TextXAlignment.Left

local UserName = Instance.new("TextLabel")
UserName.Parent = ProfileFrame
UserName.BackgroundTransparency = 1
UserName.Position = UDim2.new(0, 45, 0, 25)
UserName.Size = UDim2.new(1, -50, 0, 15)
UserName.Font = Enum.Font.Gotham
UserName.Text = "@" .. LocalPlayer.Name
UserName.TextColor3 = Color3.fromRGB(150, 150, 150)
UserName.TextSize = 10
UserName.TextXAlignment = Enum.TextXAlignment.Left

-- [ CONTENT AREA ]
local ContentArea = Instance.new("Frame")
ContentArea.Name = "ContentArea"
ContentArea.Parent = MainFrame
ContentArea.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
ContentArea.BackgroundTransparency = 1
ContentArea.Position = UDim2.new(0, 170, 0, 50)
ContentArea.Size = UDim2.new(1, -180, 1, -60)

-- [ TAB SYSTEM ]
local TabContainer = Instance.new("Frame")
TabContainer.Parent = Sidebar
TabContainer.BackgroundTransparency = 1
TabContainer.Position = UDim2.new(0, 0, 0, 10)
TabContainer.Size = UDim2.new(1, 0, 1, -80)

local TabLayout = Instance.new("UIListLayout")
TabLayout.Parent = TabContainer
TabLayout.SortOrder = Enum.SortOrder.LayoutOrder
TabLayout.Padding = UDim.new(0, 5)

local function CreateTab(name)
	local Page = Instance.new("ScrollingFrame")
	Page.Name = name .. "Page"
	Page.Parent = ContentArea
	Page.Size = UDim2.new(1, 0, 1, 0)
	Page.BackgroundTransparency = 1
	Page.ScrollBarThickness = 2
	Page.Visible = false
	
	local PageLayout = Instance.new("UIListLayout")
	PageLayout.Parent = Page
	PageLayout.Padding = UDim.new(0, 5)
	
	local Button = Instance.new("TextButton")
	Button.Name = name .. "Btn"
	Button.Parent = TabContainer
	Button.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Button.BackgroundTransparency = 1
	Button.Size = UDim2.new(1, 0, 0, 35)
	Button.Font = Enum.Font.GothamMedium
	Button.Text = "       " .. name
	Button.TextColor3 = Color3.fromRGB(100, 100, 100)
	Button.TextSize = 13
	Button.TextXAlignment = Enum.TextXAlignment.Left
	
	local Indicator = Instance.new("Frame")
	Indicator.Parent = Button
	Indicator.BackgroundColor3 = Color3.fromRGB(0, 120, 255)
	Indicator.BorderSizePixel = 0
	Indicator.Position = UDim2.new(0, 0, 0, 5)
	Indicator.Size = UDim2.new(0, 3, 0, 25)
	Indicator.Visible = false

	Button.MouseButton1Click:Connect(function()
		for _, child in pairs(TabContainer:GetChildren()) do
			if child:IsA("TextButton") then
				child.TextColor3 = Color3.fromRGB(100, 100, 100)
				child:FindFirstChild("Frame").Visible = false
			end
		end
		for _, child in pairs(ContentArea:GetChildren()) do
			child.Visible = false
		end
		Button.TextColor3 = Color3.fromRGB(255, 255, 255)
		Indicator.Visible = true
		Page.Visible = true
	end)
	return Page
end

-- [ DRAGGABLE ]
local dragging, dragInput, dragStart, startPos
local function update(input)
	local delta = input.Position - dragStart
	MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end
MainFrame.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		dragging = true; dragStart = input.Position; startPos = MainFrame.Position
		input.Changed:Connect(function() if input.UserInputState == Enum.UserInputState.End then dragging = false end end)
	end
end)
MainFrame.InputChanged:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
		if dragging then update(input) end
	end
end)

-- [ HELPER FUNCTION: ADD BUTTON ]
local function AddButton(parent, text, callback)
    local Button = Instance.new("TextButton")
    Button.Parent = parent
    Button.BackgroundColor3 = Color3.fromRGB(25, 25, 30)
    Button.Size = UDim2.new(1, -10, 0, 45)
    Button.Font = Enum.Font.GothamMedium
    Button.Text = text
    Button.TextColor3 = Color3.fromRGB(230, 230, 230)
    Button.TextSize = 13
    local Corner = Instance.new("UICorner"); Corner.CornerRadius = UDim.new(0, 6); Corner.Parent = Button
    
    Button.MouseButton1Click:Connect(function()
        Button.Text = "Executing..."
        Button.TextColor3 = Color3.fromRGB(0, 255, 100)
        task.spawn(function()
            pcall(callback)
        end)
        task.wait(1)
        Button.Text = text
        Button.TextColor3 = Color3.fromRGB(230, 230, 230)
    end)
end

-- [ 3. SETUP TABS & SCRIPTS ]
local HomeTab = CreateTab("Home")
local GamesTab = CreateTab("Games Script") -- Ini Tab Buat Script yg lu minta
local MiscTab = CreateTab("Misc")

-- DEFAULT SELECT
local firstBtn = TabContainer:FindFirstChild("HomeBtn")
if firstBtn then
	firstBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
	firstBtn:FindFirstChild("Frame").Visible = true
	ContentArea:FindFirstChild("HomePage").Visible = true
end

-- =========================================================
-- [ REQUESTED SCRIPTS ] -> DI SINI TEMPATNYA
-- =========================================================

-- HOME TAB (Welcome Info)
AddButton(HomeTab, "Welcome to PKRI HUB V3", function() print("Welcome") end)

-- GAMES TAB (List Script Lu)
AddButton(GamesTab, "Fisch | KAN Script (Gunung)", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/KAN-FISCH/tesss/refs/heads/main/gunung/fish.lua"))()
end)

AddButton(GamesTab, "Fisch | Chloe X (Fish It)", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/MajestySkie/Chloe-X/main/Main/ChloeX"))()
end)

AddButton(GamesTab, "Prospecting (GNC)", function()
    loadstring(game:HttpGet("https://gnchub.danzgnc.site/api/scripts/3"))()
end)

AddButton(GamesTab, "Neo Tennis (GNC)", function()
    loadstring(game:HttpGet("https://gnchub.danzgnc.site/api/scripts/4"))()
end)

AddButton(GamesTab, "Shoot A Brainrot (GNC)", function()
    loadstring(game:HttpGet("https://gnchub.danzgnc.site/api/scripts/8"))()
end)

AddButton(GamesTab, "Blox Fruit | BlueX Hub", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Dev-BlueX/BlueX-Hub/refs/heads/main/Main.lua"))()
end)

-- MISC TAB
AddButton(MiscTab, "Infinite Yield", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
end)
