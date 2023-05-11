
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

# Hunter macro
mouseover serpent

```
/script if UnitCanAttack("player","mouseover") then TargetUnit("mouseover");CastSpellByName('Serpent Sting');TargetUnit("playertarget");end
/cast Serpent Sting
```


# Druid macro
Feral/pvp macro



required supermacro addon


bear, charge
```
/script SpellStopCasting()
/script bI, bN, bIA = GetShapeshiftFormInfo(1); if bIA then CastSpellByName"Feral Charge" else CastShapeshiftForm(1) end
/script cI, cN, cIA = GetShapeshiftFormInfo(3); if cIA then CastShapeshiftForm(3) end
```
Claw, if 5cp Ferocious Bite
```
/script if not IsCurrentAction(1) then AttackTarget() end;
/script if GetComboPoints()==5 then CastSpellByName("Ferocious Bite") else CastSpellByName("Claw");end
```
ff in all form in one button
```
/script i=1;m=0;while(UnitBuff("player",i)~=nil) do if(strfind(UnitBuff("player",i),"Form")~=nil) then m=1; end;i=i+1;end; c=CastSpellByName; if(m==1) then c("Faerie Fire (Feral)()");else c("Faerie Fire(Rank 4)");end;
```
Autoattack on, if enough rage - maul, autoattack must be in 1st slot on you pannel, or you must change number in your macro
```
/script if not IsCurrentAction(1) then AttackTarget() end;
/cast Maul(Rank 7)
```
Rake, if stealthed - pounce
```
/script i=1;m=0;while(UnitBuff("player",i)~=nil) do if(strfind(UnitBuff("player",i),"Ability_Ambush")~=nil) then m=1; end;i=i+1;end; c=CastSpellByName; if(m==1) then c("Pounce");else c("Rake");end;
```
Shred, if stealthed - ravage
```
/script i=1;m=0;while(UnitBuff("player",i)~=nil) do if(strfind(UnitBuff("player",i),"Ability_Ambush")~=nil) then m=1; end;i=i+1;end; c=CastSpellByName; if(m==1) then c("Ravage");else c("Shred");end;
```
Inner on self, without targeting
```
/script TargetUnit("player")
/cast Innervate
/script TargetLastTarget()
```
Abolish on self, without targeting
```
/script SpellStopCasting()
/script TargetUnit("player")
/cast Abolish Poison
/script TargetLastTarget()
```
Shift bear, stun
```
/script SpellStopCasting()
/script bI, bN, bIA = GetShapeshiftFormInfo(1); if bIA then CastSpellByName"Bash" else CastShapeshiftForm(1) end
/script cI, cN, cIA = GetShapeshiftFormInfo(3); if cIA then CastShapeshiftForm(3) end
```
Use tigerfury, if tigerfury on than ravage
```

/script i=1;m=0;while(UnitBuff("player",i)~=nil) do if(strfind(UnitBuff("player",i),"Ability_Mount_JungleTiger")~=nil) then m=1; end;i=i+1;end; c=CastSpellByName; if(m==1) then c("Ravage");else c("Tiger's Fury");end;
```
travel/aqua form + enable max camera range
```
/script CastSpellByName("Aquatic Form()")
/script CastSpellByName("Travel Form()")
/console CameraDistanceMaxFactor 5
```
cat+stealth
```
/script i=1;m=0;while(UnitBuff("player",i)~=nil) do if(strfind(UnitBuff("player",i),"Ability_Druid_CatForm")~=nil) then m=1; end;i=i+1;end; c=CastSpellByName; if(m==1) then c("Prowl(Rank 3)");else c("Cat Form(Shapeshift)");end;
```
shred, if stealthed than cast tigerfury, if tigerfury on and energy more than 99 cast ravage
```
/script if not buffed("prowl") then cast("shred")end;
/script if buffed("prowl") then if not buffed("Tiger's Fury") then cast("Tiger's Fury")end;end;
/script if buffed("Tiger's Fury") and UnitMana("Player")>99 then cast ("Ravage");end;
```
Powershift claw+rake pve dps rotation

But you must always put on target rip and rake, bcz it most damaging feral spells
```
/script if not buffed("Cat Form", 'player') then cast("Cat Form(Shapeshift)")end;
/script if not IsCurrentAction(1) then AttackTarget() end;
/script if buffed("Clearcasting", 'player') then cast("Shred")end;
/script if GetComboPoints()==5 then CastSpellByName("Ferocious Bite") else CastSpellByName("Claw");end
/script if buffed("Cat Form", 'player') and UnitMana("Player")<30 then cast ("Cat Form(Shapeshift)");end;
```
macro for heals

rjv, if rjv on target than use swiftmend
```
/script i=1;m=0;while(UnitBuff("target",i)~=nil) do if(strfind(UnitBuff("Target",i),"Spell_Nature_Rejuvenation")~=nil) then m=1; end;i=i+1;end; c=CastSpellByName; if(m==1) then c("Swiftmend");else c("Rejuvenation(Rank 10)");end;
```
Rankning, but it better for flash heals, bcz drood heals have to long casttime need editing, depend of your gear, spec and preferences
```

/run if ((UnitHealthMax"target")-(UnitHealth"target")>loosehealth) then CastSpellByName("spell that healing amount of loose healt(Rank off spell)"); end
/run if ((UnitHealthMax"target")-(UnitHealth"target")>200) then CastSpellByName("Heal(Rank 3)"); end
/run if ((UnitHealthMax"target")-(UnitHealth"target")>300) then CastSpellByName("Heal(Rank 4)"); end
/run if ((UnitHealthMax"target")-(UnitHealth"target")>400) then CastSpellByName("Heal(Rank 5)"); end
```
For precast healing, gut for tank healing, if hp of your target more than 95% then stopcast, also you can edit previous macro for add stopcast support, or ranking or what you want.
```
/script CastSpellByName("Healing Touch(Rank 6)"); if (UnitHealth('target')/UnitHealthMax('target')>0.95) then SpellStopCasting() end
```
but when i was heal i just use clique and grid
