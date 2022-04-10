How to add monsters

# 1.
Convert decorate to ZScript

# 2.
Give this to all companions & their companions (if they have any)
```
+FRIENDLY
Species "Companion";
DamageFactor "Companion", 0;
```
as well as<br>
`DamageTypes` changed to `"Companion"` in their Melee + Missile states

# 3.
All projectiles or +Missile actors/w damage set, get the following
```
Species "Companion";
DamageType "Companion";
```
as well as<br>
`DamageTypes` damange functions changed to `"Companion"` in their Death states

# 4.
All puffs to be replaced with `"CompanionBulletPuff"`<br>
<br>
_**This might mean altering the function to explicity add it in!**_<br><br>
Example:<br>
```
A_Explode (5);
```
becomes
```
A_Explode (5, -1, XF_EXPLICITDAMAGETYPE, false, 0, 0, 10, "CompanionBulletPuff", "Companion")
```
<br>
What? Where did you get those values after 5 and before `"CompanionBulletPuff"` and what do they mean?<br>
<br>

Where I got it:<br>
https://zdoom.org/wiki/A_Explode<br>
Find the rest here:<br>
https://zdoom.org/wiki/Action_functions#Generic_monster_attacks<br>

You will have to replace any functions found in the `Generic Monster Attacks`<br>
(typically you only have to replace 2 or 3).

# 5.
Convert all deprecated functions to modern equivilants<br>
Such as replace `A_PlaySound()` with `A_StartSound()`.<br>
<br>
Check the console for deprecated warnings when first loading the mod.<br>
It will tell you if there's any deprecated functions found.

# 6.
Add<br>
```
TNT1 A 0 A_AlertMonsters(0, AMF_TARGETEMITTER);
```
at appropriate locations<br>
Be careful it doesnt interfere with Goto offsets<br>
AKA `Goto+<number>`

# 7
Add new companion to `Globals.zsc`.<br>

# 8.
Add their DeployerGun by copy-pasting an editing an existing one<br>
from `CompanionDeployerGuns.zsc`<br>
`BaseDeployer.price` is price to spawn 1.<br>
`SlotPriority` should be the same as price, this keeps all the monsters ordered
by price from smallest to biggest when scrolling through with mousewheel.<br>

# 9.
Add their Ammo by copy-pasting an editing an existing one<br>
from `CompanionAmmoTypes.zsc`<br>

# 10.
Add their include statment into `Zscript.zsc`<br>