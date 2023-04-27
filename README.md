
# General macro

### lfm hardcore supermacro
extendet lua code*

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
