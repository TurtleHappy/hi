shared.infammo = false;
shared.norecoil = false;
shared.nospread = false;
shared.auto = false;

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/forumsLib/main/source.lua"))()
local Forums = Library.new("Arsenal Gun Modification")

local Section = Forums:NewSection('Features')

Section:NewToggle('Infinite Ammo', function(state)
    shared.infammo = state 
end)

Section:NewToggle('No Recoil', function(state)
    shared.norecoil = state 
end)

Section:NewToggle('No Spread', function(state)
    shared.nospread = state 
end)

Section:NewToggle('Automatic Gun', function(state)
    shared.auto = state 
end)

local func;
for i,v in next, getgc(true) do
    if typeof(v) == "table" and rawget(v, 'countammo') then
        func = v
    end
end

local mt = getrawmetatable(game);
setreadonly(mt,false)
local newindex = mt.__newindex

mt.__newindex = newcclosure(function(Instance, Property, Value)
    if tostring(Instance) == 'Clip' and Instance:IsA('TextLabel') and tostring(Instance.Parent) == 'Ammo' then
        if Property == 'Text' then
            if shared.infammo then
                func.ammocount = 999
            end
            if shared.norecoil then
                func.recoil = 0
            end
            if shared.nospread then
                func.spreadmodifier = 0
                func.currentspread = 0 
            end
            if shared.auto then
                func.mode = 'automatic'
            end
        end
    end
    
    return newindex(Instance, Property, Value)
end)
