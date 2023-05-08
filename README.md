
# General macro

### Mob dps on you *supermacro
extended lua code*
```
/run unitdpsonyou()
```

```
function unitdpsonyou()
local
function round(number,decimals)
power=10^decimals
return math.floor(number*power)/power
end
L,H=UnitDamage("target")
S=UnitAttackSpeed("target")
A=UnitArmor("target")
AP=UnitArmor("player")
AL=UnitLevel("target")
DR=AP/(AP+400+85*AL)
ADL=(1-DR)*L
ADH=(1-DR)*H
DPS=(ADH+ADL)/2/S
DEFAULT_CHAT_FRAME:AddMessage("Dps On Player:"..round(DPS,2))
DEFAULT_CHAT_FRAME:AddMessage("Damage On Player:"..round(ADL,2).."-"..round(ADH,2))
DEFAULT_CHAT_FRAME:AddMessage("Damage:"..round(L,2).."-"..round(H,2))
end
```

### lfm hardcore *supermacro
extended lua code*

```
/run lfm()
```

```
function lfm()
local
lf=("QUEST, DUNGEON, OTHER THINGS WRITE HERE")
pn=4-GetNumPartyMembers()
pl=UnitLevel("Player")
p1=UnitLevel("Party1")
if p1==0 then p1=pl
end
p2=UnitLevel("Party2")
if p2==0 then p2=pl
end
p3=UnitLevel("Party3")
if p3==0 then p3=pl
end
p4=UnitLevel("Party4")
if p4==0 then p4=pl
end
maxlvl=math.max(p1,p2,p3,p4,pl)
minlvl=math.min(p1,p2,p3,p4,pl)
maxlvlannounce=minlvl+5
minlvlannounce=maxlvl-5
z=("LF"..pn.."M "..lf.." lvl "..minlvlannounce.."-"..maxlvlannounce.." HardCore")
c=SendChatMessage
c(z,GUILD,nil,Guild)
c(z,"Channel",nil,1)
--c(z,"SAY",nil,1)
end
```

# hunter macro
## mouseover serpent

```
/script if UnitCanAttack("player","mouseover") then TargetUnit("mouseover");CastSpellByName('Serpent Sting');TargetUnit("playertarget");end
/cast Serpent Sting
```
