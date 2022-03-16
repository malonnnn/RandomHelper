How to add monsters

#1. Convert decorate to ZScript

#2. All monsters get `MonsterCombo`, `+friendly`, and `DamageFactor "Companion", 0`
    as well as **DamageTypes changed to `"Companion"` in their Melee states**

#3. All projectiles get `Species "Companion"`, `DamageType "Companion"`
    as well as **DamageTypes changed to `"Companion"` in their Death states**

#4. All puffs to be replaced with `"CompanionBulletPuff"` in any damaging function where applicable.
    
    **This might mean altering the function to explicity add it in.**

    Example:

      `A_Explode (5);`

    becomes

      `A_Explode (5, -1, 0, false, 0, 0, 10, "CompanionBulletPuff", "Companion")`

    Where did you get those values after 5 and before `"CompanionBulletPuff"` and what do they mean?
      `A_Explode (damage, distance, flags, alert, fulldamagedistance, nails, naildamage, pufftype, damagetype)`

    Where I got it
      https://zdoom.org/wiki/A_Explode
        Find the rest here:
        https://zdoom.org/wiki/Action_functions#Generic_monster_attacks
    
    You will have to replace any functions found in the `Generic Monster Attacks`
    (typically you only have to replace 2 or 3)

#5. Convert all deprecated functions to modern equivilants
    Such as replace A_PlaySound() with A_StartSound().
    When you first start the mod, open the console and scroll up.
    It will tell you if there's any deprecated functions found.
    
#6. Add classes to `CompanionSpawner.zsc`

#7. Add their miniature item by copy-pasting an editing an existing one
    from `InventoryItems.zsc`

    Set their scale size such that they fit in the inventory bar

    When setting the item sprite, use the spawn sprite from the companion

#8. OPTIONAL sometimes sprites don't fit in the hotbar correctly like this
    https://i.imgur.com/9FDEc2m.png
    This is because of transparent pixels and you must trim them like this:
    https://i.imgur.com/XVKktdn.png
    Then use the actor property `Inventory.Icon` to set it.
    See the companion item AfritItem as an example from `InventoryItems.zsc`

