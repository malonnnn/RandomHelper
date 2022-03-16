How to add monsters<br>
<br>
#1. Convert decorate to ZScript<br>
<br>
#2. All monsters get `MonsterCombo`, `+friendly`, and `DamageFactor "Companion", 0`<br>
&nbsp;&nbsp;&nbsp;&nbsp;as well as `DamageTypes changed to "Companion" in their Melee states`<br>
<br>
#3. All projectiles get `Species "Companion"`, `DamageType "Companion"`<br>
&nbsp;&nbsp;&nbsp;&nbsp;as well as `DamageTypes changed to "Companion" in their Death states`<br>
<br>
#4. All puffs to be replaced with `"CompanionBulletPuff"` in any damaging function where applicable.<br>
&nbsp;&nbsp;&nbsp;&nbsp;`This might mean altering the function to explicity add it in.`
&nbsp;&nbsp;&nbsp;&nbsp;Example:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`A_Explode (5);`<br>
&nbsp;&nbsp;&nbsp;&nbsp;becomes<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`A_Explode (5, -1, 0, false, 0, 0, 10, "CompanionBulletPuff", "Companion")`<br>
&nbsp;&nbsp;&nbsp;&nbsp;Where did you get those values after 5 and before `"CompanionBulletPuff"` and what do they mean?<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`A_Explode (damage, distance, flags, alert, fulldamagedistance, nails, naildamage, pufftype, damagetype)`<br>
&nbsp;&nbsp;&nbsp;&nbsp;Where I got it<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;https://zdoom.org/wiki/A_Explode<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Find the rest here:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;https://zdoom.org/wiki/Action_functions#Generic_monster_attacks<br>
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;You will have to replace any functions found in the `Generic Monster Attacks`<br>
&nbsp;&nbsp;&nbsp;&nbsp;(typically you only have to replace 2 or 3)<br>
<br>
#5. Convert all deprecated functions to modern equivilants<br>
&nbsp;&nbsp;&nbsp;&nbsp;Such as replace A_PlaySound() with A_StartSound().<br>
&nbsp;&nbsp;&nbsp;&nbsp;When you first start the mod, open the console and scroll up.<br>
&nbsp;&nbsp;&nbsp;&nbsp;It will tell you if there's any deprecated functions found.<br>
&nbsp;&nbsp;&nbsp;&nbsp;<br>
#6. Add classes to `CompanionSpawner.zsc`<br>
<br>
#7. Add their miniature item by copy-pasting an editing an existing one<br>
&nbsp;&nbsp;&nbsp;&nbsp;from `InventoryItems.zsc`<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;Set their scale size such that they fit in the inventory bar<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;When setting the item sprite, use the spawn sprite from the companion<br>
<br>
#8. OPTIONAL sometimes sprites don't fit in the hotbar correctly like this<br>
&nbsp;&nbsp;&nbsp;&nbsp;https://i.imgur.com/9FDEc2m.png<br>
&nbsp;&nbsp;&nbsp;&nbsp;This is because of transparent pixels and you must trim them like this:<br>
&nbsp;&nbsp;&nbsp;&nbsp;https://i.imgur.com/XVKktdn.png<br>
&nbsp;&nbsp;&nbsp;&nbsp;Then use the actor property `Inventory.Icon` to set it.<br>
&nbsp;&nbsp;&nbsp;&nbsp;See the companion item AfritItem as an example from `InventoryItems.zsc`<br>

