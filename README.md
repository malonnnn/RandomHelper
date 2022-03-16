How to add monsters

# 1.
Convert decorate to ZScript

# 2.
All monsters get<br>
`MonsterCombo`<br>
`+friendly`<br>
`DamageFactor "Companion", 0`<br>
as well as<br>
`DamageTypes changed to "Companion" in their Melee states`

# 3.
All projectiles get<br>
`Species "Companion"`<br>
`DamageType "Companion"`<br>
as well as<br>
`DamageTypes changed to "Companion" in their Death states`

# 4.
All puffs to be replaced with `"CompanionBulletPuff"`<br>
_This might mean altering the function to explicity add it in!_<br>
Example:<br><br>
`A_Explode (5);`
<br>becomes<br>
`A_Explode (5, -1, 0, false, 0, 0, 10, "CompanionBulletPuff", "Companion")`<br><br>
Where did you get those values after 5 and before `"CompanionBulletPuff"` and what do they mean?<br>
`A_Explode (damage, distance, flags, alert, fulldamagedistance, nails, naildamage, pufftype, damagetype)`<br>
Where I got it:<br>
https://zdoom.org/wiki/A_Explode<br>
Find the rest here:<br>
https://zdoom.org/wiki/Action_functions#Generic_monster_attacks<br>

You will have to replace any functions found in the `Generic Monster Attacks`<br>
(typically you only have to replace 2 or 3).

# 5.
Convert all deprecated functions to modern equivilants
Such as replace `A_PlaySound()` with `A_StartSound()`.<br>
When you first start the mod, open the console and scroll up.
It will tell you if there's any deprecated functions found.

# 6.
Add classes to `CompanionSpawner.zsc`

# 7.
Add their miniature item by copy-pasting an editing an existing one
from `InventoryItems.zsc`

Set their scale size such that they fit in the inventory bar.

When setting the item sprite, use the spawn sprite from the companion.

# 8.
OPTIONAL sometimes sprites don't fit in the hotbar correctly like this<br>
https://i.imgur.com/9FDEc2m.png<br>
This is because of transparent pixels and you must trim them like this:<br>
https://i.imgur.com/XVKktdn.png<br>
Then use the actor property `Inventory.Icon` to set it.<br>
See the companion item AfritItem as an example from `InventoryItems.zsc`

