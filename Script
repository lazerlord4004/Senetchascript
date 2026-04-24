-- Senetcha Menu | Lock Hood Edition
-- LocalScript in StarterPlayerScripts

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")

local player = Players.LocalPlayer
local camera = workspace.CurrentCamera
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local rootPart = character:WaitForChild("HumanoidRootPart")

-- =====================
-- SCREEN GUI
-- =====================

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "SenetchaMenu"
screenGui.ResetOnSpawn = false
screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
screenGui.Parent = player.PlayerGui

local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 340, 0, 540)
mainFrame.Position = UDim2.new(0.5, -170, 0.5, -270)
mainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 20)
mainFrame.BorderSizePixel = 0
mainFrame.Visible = false
mainFrame.Parent = screenGui
Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 12)

local gradient = Instance.new("UIGradient")
gradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(15, 15, 35)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(5, 5, 15))
})
gradient.Rotation = 135
gradient.Parent = mainFrame

local mainStroke = Instance.new("UIStroke")
mainStroke.Color = Color3.fromRGB(100, 60, 200)
mainStroke.Thickness = 1.5
mainStroke.Parent = mainFrame

-- Title Bar
local titleBar = Instance.new("Frame")
titleBar.Size = UDim2.new(1, 0, 0, 50)
titleBar.BackgroundColor3 = Color3.fromRGB(75, 35, 155)
titleBar.BorderSizePixel = 0
titleBar.Parent = mainFrame
Instance.new("UICorner", titleBar).CornerRadius = UDim.new(0, 12)

local titleFix = Instance.new("Frame")
titleFix.Size = UDim2.new(1, 0, 0.5, 0)
titleFix.Position = UDim2.new(0, 0, 0.5, 0)
titleFix.BackgroundColor3 = Color3.fromRGB(75, 35, 155)
titleFix.BorderSizePixel = 0
titleFix.Parent = titleBar

local titleLabel = Instance.new("TextLabel")
titleLabel.Text = "⚡ SENETCHA"
titleLabel.Size = UDim2.new(1, -50, 0, 26)
titleLabel.Position = UDim2.new(0, 14, 0, 6)
titleLabel.BackgroundTransparency = 1
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.TextSize = 18
titleLabel.Font = Enum.Font.GothamBold
titleLabel.TextXAlignment = Enum.TextXAlignment.Left
titleLabel.Parent = titleBar

local subLabel = Instance.new("TextLabel")
subLabel.Text = "Lock Hood Edition"
subLabel.Size = UDim2.new(1, -50, 0, 14)
subLabel.Position = UDim2.new(0, 14, 0, 32)
subLabel.BackgroundTransparency = 1
subLabel.TextColor3 = Color3.fromRGB(180, 140, 255)
subLabel.TextSize = 11
subLabel.Font = Enum.Font.Gotham
subLabel.TextXAlignment = Enum.TextXAlignment.Left
subLabel.Parent = titleBar

local closeBtn = Instance.new("TextButton")
closeBtn.Text = "✕"
closeBtn.Size = UDim2.new(0, 28, 0, 28)
closeBtn.Position = UDim2.new(1, -36, 0, 11)
closeBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 80)
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.TextSize = 13
closeBtn.Font = Enum.Font.GothamBold
closeBtn.BorderSizePixel = 0
closeBtn.Parent = titleBar
Instance.new("UICorner", closeBtn).CornerRadius = UDim.new(0, 6)
closeBtn.MouseButton1Click:Connect(function() mainFrame.Visible = false end)

-- Scroll Frame
local scrollFrame = Instance.new("ScrollingFrame")
scrollFrame.Size = UDim2.new(1, -10, 1, -60)
scrollFrame.Position = UDim2.new(0, 5, 0, 58)
scrollFrame.BackgroundTransparency = 1
scrollFrame.BorderSizePixel = 0
scrollFrame.ScrollBarThickness = 3
scrollFrame.ScrollBarImageColor3 = Color3.fromRGB(100, 60, 200)
scrollFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
scrollFrame.AutomaticCanvasSize = Enum.AutomaticSize.Y
scrollFrame.Parent = mainFrame

local listLayout = Instance.new("UIListLayout")
listLayout.Padding = UDim.new(0, 5)
listLayout.Parent = scrollFrame

local padUI = Instance.new("UIPadding")
padUI.PaddingLeft = UDim.new(0, 8)
padUI.PaddingRight = UDim.new(0, 8)
padUI.PaddingTop = UDim.new(0, 8)
padUI.Parent = scrollFrame

-- Sidebar toggle button
local sideBtn = Instance.new("TextButton")
sideBtn.Text = "⚡"
sideBtn.Size = UDim2.new(0, 45, 0, 45)
sideBtn.Position = UDim2.new(0, 10, 0.5, -22)
sideBtn.BackgroundColor3 = Color3.fromRGB(75, 35, 155)
sideBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
sideBtn.TextSize = 22
sideBtn.Font = Enum.Font.GothamBold
sideBtn.BorderSizePixel = 0
sideBtn.Parent = screenGui
Instance.new("UICorner", sideBtn).CornerRadius = UDim.new(0, 10)
sideBtn.MouseButton1Click:Connect(function() mainFrame.Visible = not mainFrame.Visible end)

-- =====================
-- KEYBIND PICKER POPUP
-- =====================

local keybindPopup = Instance.new("Frame")
keybindPopup.Size = UDim2.new(0, 230, 0, 215)
keybindPopup.Position = UDim2.new(0.5, -115, 0.5, -107)
keybindPopup.BackgroundColor3 = Color3.fromRGB(14, 12, 28)
keybindPopup.BorderSizePixel = 0
keybindPopup.Visible = false
keybindPopup.ZIndex = 20
keybindPopup.Parent = screenGui
Instance.new("UICorner", keybindPopup).CornerRadius = UDim.new(0, 10)

local popupStroke = Instance.new("UIStroke")
popupStroke.Color = Color3.fromRGB(120, 70, 220)
popupStroke.Thickness = 1.5
popupStroke.Parent = keybindPopup

local popupTitle = Instance.new("TextLabel")
popupTitle.Text = "Choose Keybind"
popupTitle.Size = UDim2.new(1, 0, 0, 30)
popupTitle.BackgroundTransparency = 1
popupTitle.TextColor3 = Color3.fromRGB(200, 160, 255)
popupTitle.TextSize = 14
popupTitle.Font = Enum.Font.GothamBold
popupTitle.ZIndex = 21
popupTitle.Parent = keybindPopup

local popupSub = Instance.new("TextLabel")
popupSub.Text = "for: ?"
popupSub.Size = UDim2.new(1, 0, 0, 18)
popupSub.Position = UDim2.new(0, 0, 0, 28)
popupSub.BackgroundTransparency = 1
popupSub.TextColor3 = Color3.fromRGB(150, 120, 200)
popupSub.TextSize = 11
popupSub.Font = Enum.Font.Gotham
popupSub.ZIndex = 21
popupSub.Parent = keybindPopup

local KEYBIND_OPTIONS = {
    {label="Q",   key=Enum.KeyCode.Q},
    {label="E",   key=Enum.KeyCode.E},
    {label="R",   key=Enum.KeyCode.R},
    {label="F",   key=Enum.KeyCode.F},
    {label="G",   key=Enum.KeyCode.G},
    {label="Z",   key=Enum.KeyCode.Z},
    {label="X",   key=Enum.KeyCode.X},
    {label="C",   key=Enum.KeyCode.C},
    {label="V",   key=Enum.KeyCode.V},
    {label="RMB", key=Enum.UserInputType.MouseButton2},
}

local keyGrid = Instance.new("Frame")
keyGrid.Size = UDim2.new(1, -20, 0, 135)
keyGrid.Position = UDim2.new(0, 10, 0, 52)
keyGrid.BackgroundTransparency = 1
keyGrid.ZIndex = 21
keyGrid.Parent = keybindPopup

local gridLayout = Instance.new("UIGridLayout")
gridLayout.CellSize = UDim2.new(0, 50, 0, 30)
gridLayout.CellPadding = UDim2.new(0, 5, 0, 5)
gridLayout.Parent = keyGrid

local popupCancel = Instance.new("TextButton")
popupCancel.Text = "Cancel"
popupCancel.Size = UDim2.new(1, -20, 0, 24)
popupCancel.Position = UDim2.new(0, 10, 1, -30)
popupCancel.BackgroundColor3 = Color3.fromRGB(160, 40, 60)
popupCancel.TextColor3 = Color3.fromRGB(255, 255, 255)
popupCancel.TextSize = 12
popupCancel.Font = Enum.Font.GothamBold
popupCancel.BorderSizePixel = 0
popupCancel.ZIndex = 22
popupCancel.Parent = keybindPopup
Instance.new("UICorner", popupCancel).CornerRadius = UDim.new(0, 6)
popupCancel.MouseButton1Click:Connect(function() keybindPopup.Visible = false end)

local popupCallback = nil
local function openKeybindPicker(featureName, callback)
    popupSub.Text = "for: " .. featureName
    popupCallback = callback
    keybindPopup.Visible = true
end

for _, opt in ipairs(KEYBIND_OPTIONS) do
    local kb = Instance.new("TextButton")
    kb.Text = opt.label
    kb.Size = UDim2.new(0, 50, 0, 30)
    kb.BackgroundColor3 = Color3.fromRGB(40, 30, 70)
    kb.TextColor3 = Color3.fromRGB(220, 200, 255)
    kb.TextSize = 12
    kb.Font = Enum.Font.GothamBold
    kb.BorderSizePixel = 0
    kb.ZIndex = 22
    kb.Parent = keyGrid
    Instance.new("UICorner", kb).CornerRadius = UDim.new(0, 6)
    kb.MouseButton1Click:Connect(function()
        if popupCallback then popupCallback(opt.key, opt.label) popupCallback = nil end
        keybindPopup.Visible = false
    end)
end

-- =====================
-- STATE
-- =====================

local espActive         = false
local aimbotActive      = false
local aimbotSticky      = false
local aimbotLocked      = false
local silentAimActive   = false
local silentAimSticky   = false
local silentAimLocked   = false

local aimbotTarget      = nil
local silentAimTarget   = nil

local aimbotKeybind        = Enum.UserInputType.MouseButton2
local aimbotKeybindLabel   = "RMB"
local silentAimKeybind     = Enum.KeyCode.Q
local silentAimKeybindLabel = "Q"

local aimbotWasHeld    = false
local silentAimWasHeld = false

local currentSpeed      = 60
local currentJumpPower  = 100
local flyActive         = false
local noclipActive      = false
local infiniteJumpActive = false
local bodyVelocity, bodyGyro, flyConn

local AIMBOT_SMOOTHING = 0.15
local AIMBOT_FOV       = 300

local toggleStates = {}
local ESP_OBJECTS  = {}

-- =====================
-- UI HELPERS
-- =====================

local function makeSection(name)
    local lbl = Instance.new("TextLabel")
    lbl.Text = "— " .. name .. " —"
    lbl.Size = UDim2.new(1, 0, 0, 22)
    lbl.BackgroundTransparency = 1
    lbl.TextColor3 = Color3.fromRGB(150, 100, 255)
    lbl.TextSize = 11
    lbl.Font = Enum.Font.GothamBold
    lbl.TextXAlignment = Enum.TextXAlignment.Center
    lbl.Parent = scrollFrame
end

local function makeToggle(name, icon, callback)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(1, 0, 0, 38)
    btn.BackgroundColor3 = Color3.fromRGB(25, 20, 45)
    btn.BorderSizePixel = 0
    btn.Text = ""
    btn.Parent = scrollFrame
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 8)

    local btnStroke = Instance.new("UIStroke")
    btnStroke.Color = Color3.fromRGB(60, 40, 100)
    btnStroke.Thickness = 1
    btnStroke.Parent = btn

    local iconLbl = Instance.new("TextLabel")
    iconLbl.Text = icon
    iconLbl.Size = UDim2.new(0, 30, 1, 0)
    iconLbl.Position = UDim2.new(0, 8, 0, 0)
    iconLbl.BackgroundTransparency = 1
    iconLbl.TextColor3 = Color3.fromRGB(200, 160, 255)
    iconLbl.TextSize = 16
    iconLbl.Font = Enum.Font.Gotham
    iconLbl.Parent = btn

    local nameLbl = Instance.new("TextLabel")
    nameLbl.Text = name
    nameLbl.Size = UDim2.new(1, -80, 1, 0)
    nameLbl.Position = UDim2.new(0, 42, 0, 0)
    nameLbl.BackgroundTransparency = 1
    nameLbl.TextColor3 = Color3.fromRGB(220, 220, 240)
    nameLbl.TextSize = 13
    nameLbl.Font = Enum.Font.Gotham
    nameLbl.TextXAlignment = Enum.TextXAlignment.Left
    nameLbl.Parent = btn

    local dot = Instance.new("Frame")
    dot.Size = UDim2.new(0, 10, 0, 10)
    dot.Position = UDim2.new(1, -20, 0.5, -5)
    dot.BackgroundColor3 = Color3.fromRGB(80, 80, 100)
    dot.BorderSizePixel = 0
    dot.Parent = btn
    Instance.new("UICorner", dot).CornerRadius = UDim.new(1, 0)

    toggleStates[name] = false
    btn.MouseButton1Click:Connect(function()
        toggleStates[name] = not toggleStates[name]
        local on = toggleStates[name]
        dot.BackgroundColor3 = on and Color3.fromRGB(80, 255, 120) or Color3.fromRGB(80, 80, 100)
        btn.BackgroundColor3 = on and Color3.fromRGB(40, 25, 70) or Color3.fromRGB(25, 20, 45)
        btnStroke.Color = on and Color3.fromRGB(100, 60, 200) or Color3.fromRGB(60, 40, 100)
        callback(on)
    end)
end

local function makeSlider(name, icon, minVal, maxVal, defaultVal, callback)
    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(1, 0, 0, 52)
    frame.BackgroundColor3 = Color3.fromRGB(25, 20, 45)
    frame.BorderSizePixel = 0
    frame.Parent = scrollFrame
    Instance.new("UICorner", frame).CornerRadius = UDim.new(0, 8)

    local fStroke = Instance.new("UIStroke")
    fStroke.Color = Color3.fromRGB(60, 40, 100)
    fStroke.Thickness = 1
    fStroke.Parent = frame

    local iconLbl = Instance.new("TextLabel")
    iconLbl.Text = icon
    iconLbl.Size = UDim2.new(0, 30, 0, 24)
    iconLbl.Position = UDim2.new(0, 8, 0, 4)
    iconLbl.BackgroundTransparency = 1
    iconLbl.TextColor3 = Color3.fromRGB(200, 160, 255)
    iconLbl.TextSize = 15
    iconLbl.Font = Enum.Font.Gotham
    iconLbl.Parent = frame

    local currentVal = defaultVal
    local valLbl = Instance.new("TextLabel")
    valLbl.Text = name .. ": " .. tostring(currentVal)
    valLbl.Size = UDim2.new(1, -50, 0, 24)
    valLbl.Position = UDim2.new(0, 42, 0, 4)
    valLbl.BackgroundTransparency = 1
    valLbl.TextColor3 = Color3.fromRGB(220, 220, 240)
    valLbl.TextSize = 12
    valLbl.Font = Enum.Font.Gotham
    valLbl.TextXAlignment = Enum.TextXAlignment.Left
    valLbl.Parent = frame

    local track = Instance.new("Frame")
    track.Size = UDim2.new(1, -20, 0, 6)
    track.Position = UDim2.new(0, 10, 0, 36)
    track.BackgroundColor3 = Color3.fromRGB(50, 40, 80)
    track.BorderSizePixel = 0
    track.Parent = frame
    Instance.new("UICorner", track).CornerRadius = UDim.new(1, 0)

    local fill = Instance.new("Frame")
    fill.Size = UDim2.new((defaultVal-minVal)/(maxVal-minVal), 0, 1, 0)
    fill.BackgroundColor3 = Color3.fromRGB(120, 70, 220)
    fill.BorderSizePixel = 0
    fill.Parent = track
    Instance.new("UICorner", fill).CornerRadius = UDim.new(1, 0)

    local dragging = false
    track.InputBegan:Connect(function(i)
        if i.UserInputType == Enum.UserInputType.MouseButton1 then dragging = true end
    end)
    track.InputEnded:Connect(function(i)
        if i.UserInputType == Enum.UserInputType.MouseButton1 then dragging = false end
    end)
    RunService.RenderStepped:Connect(function()
        if dragging then
            local mp = UserInputService:GetMouseLocation()
            local ratio = math.clamp((mp.X - track.AbsolutePosition.X) / track.AbsoluteSize.X, 0, 1)
            currentVal = math.floor(minVal + ratio * (maxVal - minVal))
            fill.Size = UDim2.new(ratio, 0, 1, 0)
            valLbl.Text = name .. ": " .. tostring(currentVal)
            callback(currentVal)
        end
    end)
end

--[[
    makeCombatRow
    Builds a row with:
      • left click area  → enable/disable toggle
      • [KEY] pill       → open keybind picker
      • STICKY pill      → toggle sticky mode (green when on)
      • status dot       → green when feature is on
--]]
local function makeCombatRow(name, icon, defaultKeyLabel, onToggle, onKeybindPicked, onStickyChanged)
    local row = Instance.new("Frame")
    row.Size = UDim2.new(1, 0, 0, 38)
    row.BackgroundColor3 = Color3.fromRGB(25, 20, 45)
    row.BorderSizePixel = 0
    row.Parent = scrollFrame
    Instance.new("UICorner", row).CornerRadius = UDim.new(0, 8)

    local rowStroke = Instance.new("UIStroke")
    rowStroke.Color = Color3.fromRGB(60, 40, 100)
    rowStroke.Thickness = 1
    rowStroke.Parent = row

    -- Icon
    local iconLbl = Instance.new("TextLabel")
    iconLbl.Text = icon
    iconLbl.Size = UDim2.new(0, 26, 1, 0)
    iconLbl.Position = UDim2.new(0, 6, 0, 0)
    iconLbl.BackgroundTransparency = 1
    iconLbl.TextColor3 = Color3.fromRGB(200, 160, 255)
    iconLbl.TextSize = 15
    iconLbl.Font = Enum.Font.Gotham
    iconLbl.Parent = row

    -- Name label
    local nameLbl = Instance.new("TextLabel")
    nameLbl.Text = name
    nameLbl.Size = UDim2.new(1, -200, 1, 0)
    nameLbl.Position = UDim2.new(0, 34, 0, 0)
    nameLbl.BackgroundTransparency = 1
    nameLbl.TextColor3 = Color3.fromRGB(220, 220, 240)
    nameLbl.TextSize = 11
    nameLbl.Font = Enum.Font.Gotham
    nameLbl.TextXAlignment = Enum.TextXAlignment.Left
    nameLbl.Parent = row

    -- [KEY] pill
    local keybindBtn = Instance.new("TextButton")
    keybindBtn.Text = "[" .. defaultKeyLabel .. "]"
    keybindBtn.Size = UDim2.new(0, 46, 0, 22)
    keybindBtn.Position = UDim2.new(1, -152, 0.5, -11)
    keybindBtn.BackgroundColor3 = Color3.fromRGB(55, 35, 105)
    keybindBtn.TextColor3 = Color3.fromRGB(200, 170, 255)
    keybindBtn.TextSize = 10
    keybindBtn.Font = Enum.Font.GothamBold
    keybindBtn.BorderSizePixel = 0
    keybindBtn.Parent = row
    Instance.new("UICorner", keybindBtn).CornerRadius = UDim.new(0, 5)

    -- STICKY pill
    local stickyOn = false

    local stickyBtn = Instance.new("TextButton")
    stickyBtn.Text = "STICKY"
    stickyBtn.Size = UDim2.new(0, 50, 0, 22)
    stickyBtn.Position = UDim2.new(1, -100, 0.5, -11)
    stickyBtn.BackgroundColor3 = Color3.fromRGB(38, 28, 58)
    stickyBtn.TextColor3 = Color3.fromRGB(130, 100, 170)
    stickyBtn.TextSize = 9
    stickyBtn.Font = Enum.Font.GothamBold
    stickyBtn.BorderSizePixel = 0
    stickyBtn.Parent = row
    Instance.new("UICorner", stickyBtn).CornerRadius = UDim.new(0, 5)

    local stickyStroke = Instance.new("UIStroke")
    stickyStroke.Color = Color3.fromRGB(70, 45, 120)
    stickyStroke.Thickness = 1
    stickyStroke.Parent = stickyBtn

    -- Feature on/off dot
    local dot = Instance.new("Frame")
    dot.Size = UDim2.new(0, 10, 0, 10)
    dot.Position = UDim2.new(1, -18, 0.5, -5)
    dot.BackgroundColor3 = Color3.fromRGB(80, 80, 100)
    dot.BorderSizePixel = 0
    dot.Parent = row
    Instance.new("UICorner", dot).CornerRadius = UDim.new(1, 0)

    -- Invisible button over the left portion to act as the main toggle
    local toggleArea = Instance.new("TextButton")
    toggleArea.Size = UDim2.new(1, -162, 1, 0)
    toggleArea.BackgroundTransparency = 1
    toggleArea.Text = ""
    toggleArea.Parent = row

    -- Wire up main toggle
    toggleStates[name] = false
    toggleArea.MouseButton1Click:Connect(function()
        toggleStates[name] = not toggleStates[name]
        local on = toggleStates[name]
        dot.BackgroundColor3 = on and Color3.fromRGB(80, 255, 120) or Color3.fromRGB(80, 80, 100)
        row.BackgroundColor3 = on and Color3.fromRGB(40, 25, 70) or Color3.fromRGB(25, 20, 45)
        rowStroke.Color = on and Color3.fromRGB(100, 60, 200) or Color3.fromRGB(60, 40, 100)
        onToggle(on)
    end)

    -- Wire up keybind picker
    keybindBtn.MouseButton1Click:Connect(function()
        openKeybindPicker(name, function(key, label)
            keybindBtn.Text = "[" .. label .. "]"
            onKeybindPicked(key, label)
        end)
    end)

    -- Wire up sticky toggle
    stickyBtn.MouseButton1Click:Connect(function()
        stickyOn = not stickyOn
        if stickyOn then
            stickyBtn.BackgroundColor3 = Color3.fromRGB(50, 170, 80)
            stickyBtn.TextColor3      = Color3.fromRGB(220, 255, 225)
            stickyStroke.Color        = Color3.fromRGB(80, 220, 110)
        else
            stickyBtn.BackgroundColor3 = Color3.fromRGB(38, 28, 58)
            stickyBtn.TextColor3      = Color3.fromRGB(130, 100, 170)
            stickyStroke.Color        = Color3.fromRGB(70, 45, 120)
        end
        onStickyChanged(stickyOn)
    end)
end

-- =====================
-- ESP SYSTEM
-- =====================

local function getESPColor(p)
    local isTarget = (aimbotActive and aimbotTarget == p)
                  or (silentAimActive and silentAimTarget == p)
    if isTarget then
        return Color3.fromRGB(255, 40, 40), Color3.fromRGB(255, 0, 0), Color3.fromRGB(255, 70, 70)
    end
    return Color3.fromRGB(255,255,255), Color3.fromRGB(200,200,200), Color3.fromRGB(255,255,255)
end

local function createESP(p)
    if not p.Character or ESP_OBJECTS[p] then return end
    local hrp = p.Character:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local hl = Instance.new("Highlight")
    hl.Name = "SenetchaESP"
    hl.FillTransparency = 0.6
    hl.OutlineTransparency = 0
    hl.Parent = p.Character

    local bb = Instance.new("BillboardGui")
    bb.Name = "SenetchaESPBB"
    bb.Size = UDim2.new(0, 140, 0, 34)
    bb.StudsOffset = Vector3.new(0, 3.5, 0)
    bb.AlwaysOnTop = true
    bb.Parent = hrp

    local nameLbl = Instance.new("TextLabel")
    nameLbl.Size = UDim2.new(1, 0, 0.6, 0)
    nameLbl.BackgroundTransparency = 1
    nameLbl.Text = p.Name
    nameLbl.TextColor3 = Color3.fromRGB(255, 255, 255)
    nameLbl.TextSize = 14
    nameLbl.Font = Enum.Font.GothamBold
    nameLbl.TextStrokeTransparency = 0.3
    nameLbl.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    nameLbl.Parent = bb

    local hpLbl = Instance.new("TextLabel")
    hpLbl.Size = UDim2.new(1, 0, 0.4, 0)
    hpLbl.Position = UDim2.new(0, 0, 0.6, 0)
    hpLbl.BackgroundTransparency = 1
    hpLbl.Text = "HP: ?"
    hpLbl.TextColor3 = Color3.fromRGB(100, 255, 120)
    hpLbl.TextSize = 11
    hpLbl.Font = Enum.Font.Gotham
    hpLbl.TextStrokeTransparency = 0.3
    hpLbl.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    hpLbl.Parent = bb

    ESP_OBJECTS[p] = {highlight=hl, billboard=bb, nameLabel=nameLbl, hpLabel=hpLbl}

    local fc, oc, tc = getESPColor(p)
    hl.FillColor = fc; hl.OutlineColor = oc; nameLbl.TextColor3 = tc
end

local function removeESP(p)
    if ESP_OBJECTS[p] then
        pcall(function() ESP_OBJECTS[p].highlight:Destroy() end)
        pcall(function() ESP_OBJECTS[p].billboard:Destroy() end)
        ESP_OBJECTS[p] = nil
    end
end

local function updateAllESPColors()
    for p, objs in pairs(ESP_OBJECTS) do
        if objs.highlight and objs.highlight.Parent then
            local fc, oc, tc = getESPColor(p)
            objs.highlight.FillColor = fc
            objs.highlight.OutlineColor = oc
            if objs.nameLabel and objs.nameLabel.Parent then
                objs.nameLabel.TextColor3 = tc
            end
        end
    end
end

local function enableESP()
    for _, p in pairs(Players:GetPlayers()) do
        if p ~= player then createESP(p) end
    end
end
local function disableESP()
    for p in pairs(ESP_OBJECTS) do removeESP(p) end
end

-- Live HP update
RunService.Heartbeat:Connect(function()
    for p, objs in pairs(ESP_OBJECTS) do
        if p.Character and objs.hpLabel and objs.hpLabel.Parent then
            local hum = p.Character:FindFirstChildOfClass("Humanoid")
            if hum then
                local hp    = math.floor(hum.Health)
                local maxHp = math.max(1, math.floor(hum.MaxHealth))
                objs.hpLabel.Text = "HP: " .. hp .. "/" .. maxHp
                local ratio = math.clamp(hum.Health / maxHp, 0, 1)
                objs.hpLabel.TextColor3 = Color3.fromRGB(255*(1-ratio), 255*ratio, 60)
            end
        end
    end
end)

Players.PlayerAdded:Connect(function(p)
    p.CharacterAdded:Connect(function()
        task.wait(1)
        if espActive then removeESP(p) createESP(p) end
    end)
end)
Players.PlayerRemoving:Connect(function(p)
    removeESP(p)
    if aimbotTarget == p    then aimbotTarget = nil    aimbotLocked    = false end
    if silentAimTarget == p then silentAimTarget = nil silentAimLocked = false end
    updateAllESPColors()
end)
for _, p in pairs(Players:GetPlayers()) do
    if p ~= player then
        p.CharacterAdded:Connect(function()
            task.wait(1)
            if espActive then removeESP(p) createESP(p) end
        end)
    end
end

-- =====================
-- INPUT HELPERS
-- =====================

local function isKeyHeld(bind)
    if typeof(bind) ~= "EnumItem" then return false end
    if bind.EnumType == Enum.KeyCode then
        return UserInputService:IsKeyDown(bind)
    elseif bind.EnumType == Enum.UserInputType then
        return UserInputService:IsMouseButtonPressed(bind)
    end
    return false
end

local function getNearestEnemy()
    local center = Vector2.new(camera.ViewportSize.X/2, camera.ViewportSize.Y/2)
    local closest, closestDist = nil, AIMBOT_FOV
    for _, p in pairs(Players:GetPlayers()) do
        if p ~= player and p.Character then
            local hum = p.Character:FindFirstChildOfClass("Humanoid")
            if hum and hum.Health > 0 then
                local head = p.Character:FindFirstChild("Head")
                if head then
                    local sp, onScreen = camera:WorldToViewportPoint(head.Position)
                    if onScreen then
                        local dist = (Vector2.new(sp.X, sp.Y) - center).Magnitude
                        if dist < closestDist then closestDist = dist closest = p end
                    end
                end
            end
        end
    end
    return closest
end

local function getHeadWorld(p)
    if not p or not p.Character then return nil end
    local head = p.Character:FindFirstChild("Head")
    return head and head.Position or nil
end

local function targetAlive(p)
    if not p or not p.Character then return false end
    local hum = p.Character:FindFirstChildOfClass("Humanoid")
    return hum ~= nil and hum.Health > 0
end

-- =====================
-- AIMBOT  (camera moves)
-- =====================

RunService.RenderStepped:Connect(function()
    if not aimbotActive then
        if aimbotTarget then aimbotTarget = nil updateAllESPColors() end
        aimbotWasHeld = false
        aimbotLocked  = false
        return
    end

    local held       = isKeyHeld(aimbotKeybind)
    local justPressed = held and not aimbotWasHeld

    if aimbotSticky then
        -- ── STICKY MODE ──────────────────────────────────────────
        -- First press  → lock onto nearest enemy
        -- Second press → release the lock
        if justPressed then
            if aimbotLocked then
                aimbotLocked = false
                aimbotTarget = nil
                updateAllESPColors()
            else
                aimbotTarget = getNearestEnemy()
                aimbotLocked = aimbotTarget ~= nil
                updateAllESPColors()
            end
        end

        -- While locked, track the target every frame
        if aimbotLocked then
            if not targetAlive(aimbotTarget) then
                -- Auto-release if target dies / leaves
                aimbotTarget = nil
                aimbotLocked = false
                updateAllESPColors()
            else
                local hw = getHeadWorld(aimbotTarget)
                if hw then
                    local cf = camera.CFrame
                    camera.CFrame = cf:Lerp(CFrame.lookAt(cf.Position, hw), AIMBOT_SMOOTHING)
                end
            end
        end
    else
        -- ── HOLD MODE ────────────────────────────────────────────
        -- Hold key to aim, release to stop (previous behaviour)
        if held then
            local target = getNearestEnemy()
            if target ~= aimbotTarget then aimbotTarget = target updateAllESPColors() end
            if aimbotTarget then
                local hw = getHeadWorld(aimbotTarget)
                if hw then
                    local cf = camera.CFrame
                    camera.CFrame = cf:Lerp(CFrame.lookAt(cf.Position, hw), AIMBOT_SMOOTHING)
                end
            end
        else
            if aimbotTarget then aimbotTarget = nil updateAllESPColors() end
        end
    end

    aimbotWasHeld = held
end)

-- =====================
-- SILENT AIM  (no camera move)
-- =====================

local function hookTool(tool)
    tool.Activated:Connect(function()
        if silentAimActive and silentAimTarget and silentAimTarget.Character then
            local hw = getHeadWorld(silentAimTarget)
            if hw then
                local savedCF = camera.CFrame
                camera.CFrame = CFrame.lookAt(savedCF.Position, hw)
                task.defer(function() camera.CFrame = savedCF end)
            end
        end
    end)
end

local function hookCharacterTools(char)
    char.ChildAdded:Connect(function(child)
        if child:IsA("Tool") then hookTool(child) end
    end)
    for _, child in pairs(char:GetChildren()) do
        if child:IsA("Tool") then hookTool(child) end
    end
end

player.CharacterAdded:Connect(function(char)
    character = char
    humanoid  = char:WaitForChild("Humanoid")
    rootPart  = char:WaitForChild("HumanoidRootPart")
    hookCharacterTools(char)
end)
if player.Character then hookCharacterTools(player.Character) end

RunService.RenderStepped:Connect(function()
    if not silentAimActive then
        if silentAimTarget then silentAimTarget = nil updateAllESPColors() end
        silentAimWasHeld = false
        silentAimLocked  = false
        return
    end

    local held        = isKeyHeld(silentAimKeybind)
    local justPressed = held and not silentAimWasHeld

    if silentAimSticky then
        -- ── STICKY MODE ──────────────────────────────────────────
        if justPressed then
            if silentAimLocked then
                silentAimLocked = false
                silentAimTarget = nil
                updateAllESPColors()
            else
                silentAimTarget = getNearestEnemy()
                silentAimLocked = silentAimTarget ~= nil
                updateAllESPColors()
            end
        end

        -- Auto-release if target dies / leaves
        if silentAimLocked and not targetAlive(silentAimTarget) then
            silentAimTarget = nil
            silentAimLocked = false
            updateAllESPColors()
        end
    else
        -- ── HOLD MODE ────────────────────────────────────────────
        if held then
            local target = getNearestEnemy()
            if target ~= silentAimTarget then silentAimTarget = target updateAllESPColors() end
        else
            if silentAimTarget then silentAimTarget = nil updateAllESPColors() end
        end
    end

    silentAimWasHeld = held
end)

-- =====================
-- BUILD MENU
-- =====================

makeSection("COMBAT")

makeToggle("ESP + Usernames + HP", "👁️", function(on)
    espActive = on
    if on then enableESP() else disableESP() end
end)

makeCombatRow(
    "Aimbot (Camera Lock)", "🎯", aimbotKeybindLabel,
    function(on)                                      -- on toggle
        aimbotActive = on
        if not on then
            aimbotTarget = nil
            aimbotLocked = false
            updateAllESPColors()
        end
    end,
    function(key, label)                              -- on keybind picked
        aimbotKeybind      = key
        aimbotKeybindLabel = label
        -- Clear lock so the new key takes effect cleanly
        aimbotTarget = nil
        aimbotLocked = false
        updateAllESPColors()
    end,
    function(on)                                      -- on sticky toggled
        aimbotSticky = on
        aimbotTarget = nil
        aimbotLocked = false
        updateAllESPColors()
    end
)

makeCombatRow(
    "Silent Aim (No Camera)", "🔫", silentAimKeybindLabel,
    function(on)
        silentAimActive = on
        if not on then
            silentAimTarget = nil
            silentAimLocked = false
            updateAllESPColors()
        end
    end,
    function(key, label)
        silentAimKeybind      = key
        silentAimKeybindLabel = label
        silentAimTarget = nil
        silentAimLocked = false
        updateAllESPColors()
    end,
    function(on)
        silentAimSticky = on
        silentAimTarget = nil
        silentAimLocked = false
        updateAllESPColors()
    end
)

makeToggle("God Mode (Local)", "🛡️", function(on)
    local c = player.Character
    local hum = c and c:FindFirstChildOfClass("Humanoid")
    if hum then hum.MaxHealth = on and math.huge or 100 hum.Health = hum.MaxHealth end
end)

makeSection("MOVEMENT")

makeSlider("Speed",      "🏃", 16, 300, 60,  function(val) currentSpeed      = val end)
makeSlider("Jump Power", "🦘", 50, 500, 100, function(val) currentJumpPower  = val end)

makeToggle("Infinite Jump", "♾️", function(on) infiniteJumpActive = on end)

makeToggle("Fly (WASD + Space/Ctrl)", "🦅", function(on)
    flyActive = on
    character = player.Character
    if not character then return end
    rootPart  = character:FindFirstChild("HumanoidRootPart")
    if on then
        bodyVelocity = Instance.new("BodyVelocity")
        bodyVelocity.Velocity  = Vector3.zero
        bodyVelocity.MaxForce  = Vector3.new(1e5,1e5,1e5)
        bodyVelocity.Parent    = rootPart
        bodyGyro = Instance.new("BodyGyro")
        bodyGyro.MaxTorque = Vector3.new(1e5,1e5,1e5)
        bodyGyro.P         = 1e4
        bodyGyro.Parent    = rootPart
        flyConn = RunService.RenderStepped:Connect(function()
            if not flyActive then return end
            local cam = workspace.CurrentCamera
            local dir = Vector3.zero
            if UserInputService:IsKeyDown(Enum.KeyCode.W)           then dir += cam.CFrame.LookVector  end
            if UserInputService:IsKeyDown(Enum.KeyCode.S)           then dir -= cam.CFrame.LookVector  end
            if UserInputService:IsKeyDown(Enum.KeyCode.A)           then dir -= cam.CFrame.RightVector end
            if UserInputService:IsKeyDown(Enum.KeyCode.D)           then dir += cam.CFrame.RightVector end
            if UserInputService:IsKeyDown(Enum.KeyCode.Space)       then dir += Vector3.new(0,1,0)     end
            if UserInputService:IsKeyDown(Enum.KeyCode.LeftControl) then dir -= Vector3.new(0,1,0)     end
            bodyVelocity.Velocity = dir.Magnitude > 0 and dir.Unit*65 or Vector3.zero
            bodyGyro.CFrame = cam.CFrame
        end)
    else
        if flyConn      then flyConn:Disconnect()        flyConn      = nil end
        if bodyVelocity then bodyVelocity:Destroy()      bodyVelocity = nil end
        if bodyGyro     then bodyGyro:Destroy()          bodyGyro     = nil end
    end
end)

makeToggle("Noclip", "👻", function(on) noclipActive = on end)

makeSection("VISUAL")

makeToggle("Fullbright", "🌟", function(on)
    local L = game:GetService("Lighting")
    L.Brightness = on and 10 or 1
    L.Ambient    = on and Color3.fromRGB(255,255,255) or Color3.fromRGB(70,70,70)
end)

makeToggle("Rainbow Character", "🌈", function(on)
    if on then
        task.spawn(function()
            while toggleStates["Rainbow Character"] do
                local c = player.Character
                if c then
                    for _, part in pairs(c:GetDescendants()) do
                        if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                            part.Color = Color3.fromHSV(tick()%5/5, 1, 1)
                        end
                    end
                end
                task.wait(0.05)
            end
        end)
    end
end)

makeSection("MISC")

makeToggle("Anti-AFK", "💤", function(on)
    if on then
        task.spawn(function()
            while toggleStates["Anti-AFK"] do
                task.wait(55)
                pcall(function()
                    game:GetService("VirtualInputManager"):SendKeyEvent(true,"LeftShift",false,game)
                end)
            end
        end)
    end
end)

-- =====================
-- RUNTIME LOOPS
-- =====================

RunService.Stepped:Connect(function()
    if noclipActive then
        local c = player.Character
        if c then
            for _, part in pairs(c:GetDescendants()) do
                if part:IsA("BasePart") then part.CanCollide = false end
            end
        end
    end
end)

RunService.RenderStepped:Connect(function()
    local c = player.Character
    if c then
        local hum = c:FindFirstChildOfClass("Humanoid")
        if hum then hum.WalkSpeed = currentSpeed hum.JumpPower = currentJumpPower end
    end
end)

UserInputService.JumpRequest:Connect(function()
    if infiniteJumpActive then
        local c   = player.Character
        local hum = c and c:FindFirstChildOfClass("Humanoid")
        if hum then hum:ChangeState(Enum.HumanoidStateType.Jumping) end
    end
end)

-- Draggable window
local dragging, dragStart, startPos
titleBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging  = true
        dragStart = input.Position
        startPos  = mainFrame.Position
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then dragging = false end
        end)
    end
end)
UserInputService.InputChanged:Connect(function(input)
    if dragging and input.UserInputType == Enum.UserInputType.MouseMove then
        local d = input.Position - dragStart
        mainFrame.Position = UDim2.new(
            startPos.X.Scale, startPos.X.Offset + d.X,
            startPos.Y.Scale, startPos.Y.Offset + d.Y
        )
    end
end)

-- Insert key opens/closes menu
UserInputService.InputBegan:Connect(function(input, gpe)
    if not gpe and input.KeyCode == Enum.KeyCode.Insert then
        mainFrame.Visible = not mainFrame.Visible
    end
end)

print("✅ Senetcha loaded | Lock Hood Edition")
