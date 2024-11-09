local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Teams = game:GetService("Teams")

local function setRankDisplay(OverheadDisplay, RankDisplay, rank, team)
    local rankText, usernameText
    if team == "The Jedi Order" then
        local rankNames = {
            [1] = "Force Sensitive",
            [2] = "Youngling",
            [3] = "Initiate",
            [4] = "Padawan Learner",
            [5] = "Jedi Knight",
            [11] = "Jedi Instructor",
            [12] = "Temple Guard",
            [13] = "Master",
            [14] = "Jedi Elder",
            [15] = "Jedi Ghost",
            [16] = "Master of the Jedi Council",
            [17] = "Jedi High Council",
            [25] = "Master of the Order",
            [255] = "Grand Master"
        }

        rankText = rankNames[rank] or "Unknown Rank"
        usernameText = (rank <= 5 and rankText .. ", " or "") .. " " .. Players.LocalPlayer.Name
    elseif team == "Temple Guard" then
        local rankNames = {
            [1] = "Candidate",
            [2] = "Pledge",
            [3] = "Trainee",
            [4] = "Guardsman",
            [5] = "Senior Guardsman",
            [6] = "Sentry",
            [7] = "Warden",
            [8] = "Watchman",
            [9] = "Instructor",
            [10] = "Lieutenant",
            [11] = "Captain",
            [12] = "Commander",
            [13] = "Chief of Security",
            [14] = "Jedi High Council",
            [254] = "Master of the Order",
            [255] = "Grandmaster"
        }

        rankText = rankNames[rank] or "Unknown Rank"
        usernameText = "Temple Guard"
    elseif team == "Hostiles" then
        rankText = ""
        usernameText = Players.LocalPlayer.Name
    elseif team == "Visitor" then
        rankText = ""
        usernameText = Players.LocalPlayer.Name
    elseif team == "The Sith Order" then
        local rankNames = {
            [1] = "Hopeful",
            [2] = "Acolyte",
            [3] = "Adept",
            [4] = "Apprentice",
            [5] = "Sith Knight",
            [6] = "Sith Warrior",
            [7] = "Dark Honor Guard",
            [8] = "Sith Elder",
            [9] = "Sith Lord",
            [10] = "Sith Wraith",
            [11] = "Darth",
            [12] = "Dark Council",
            [13] = "Powerbase",
            [14] = "Dark Lord of the Sith",
            [255] = "The Force"
        }

        rankText = rankNames[rank] or "Unknown Rank"
        usernameText = "Sith Order - " .. Players.LocalPlayer.Name
    else
        rankText = ""
        usernameText = Players.LocalPlayer.Name
    end

    OverheadDisplay.Username.Text = usernameText
    RankDisplay.Rank.Text = rankText
end

Players.PlayerAdded:Connect(function(Player)
    Player.CharacterAdded:Connect(function(Character)
        local OverheadDisplay = ReplicatedStorage:WaitForChild("Assets").OverheadDisplay:Clone()
        local RankDisplay = ReplicatedStorage:WaitForChild("Assets").Rank:Clone()

        local function setupDisplays()
            local head = Character:WaitForChild("Head")
            OverheadDisplay.Parent = head
            RankDisplay.Parent = head
            RankDisplay.Rank.Visible = false

            local team = Player.Team.Name
            local rank = Player:GetRankInGroup(34426333)

            if team == "The Jedi Order" then
                OverheadDisplay.TeamIcon.Visible = true
                OverheadDisplay.TeamIcon.Image = "rbxassetid://18957678579"
                OverheadDisplay.TeamIcon.ImageColor3 = Color3.new(0.145098, 0.32549, 0.705882)
                OverheadDisplay.Team.Text = "The Jedi Order"
                OverheadDisplay.Team.TextColor3 = Color3.new(0.145098, 0.32549, 0.705882)
                RankDisplay.Rank.Visible = true
            elseif team == "Temple Guard" then
                OverheadDisplay.TeamIcon.Image = "rbxassetid://18604351517"
                OverheadDisplay.TeamIcon.ImageColor3 = Color3.new(1, 0.847059, 0)
                OverheadDisplay.Team.Text = "Temple Guardian"
                OverheadDisplay.Team.TextColor3 = Color3.new(1, 0.847059, 0)
                RankDisplay.Rank.Visible = true
            elseif team == "The Sith Order" then
                OverheadDisplay.TeamIcon.Image = "rbxassetid://17870293233"
                OverheadDisplay.TeamIcon.ImageColor3 = Color3.new(0.705882, 0, 0)
                OverheadDisplay.Team.Text = "The Sith Order"
                OverheadDisplay.Team.TextColor3 = Color3.new(0.490196, 0.0823529, 0.0862745)
                RankDisplay.Rank.Visible = true
            elseif team == "Hostiles" then
                OverheadDisplay.TeamIcon.Visible = false
                OverheadDisplay.Team.Text = "Hostile"
                OverheadDisplay.Team.TextColor3 = Color3.new(0.705882, 0.180392, 0.188235)
            elseif team == "Visitor" then
                OverheadDisplay.TeamIcon.Visible = false
                OverheadDisplay.Team.Text = "Visitor"
                OverheadDisplay.Team.TextColor3 = Color3.new(0.0784314, 0.560784, 0.0784314)
            end

            setRankDisplay(OverheadDisplay, RankDisplay, rank, team)
        end

        setupDisplays()
        
        Character:WaitForChild("Head").ChildAdded:Connect(function(child)
            if child.Name == "Head" then
                setupDisplays()
            end
        end)
    end)
end)
