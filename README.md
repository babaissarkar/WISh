# WISh

A GUI item inventory system for [War of Legends era](https://github.com/knyghtmare/War_of_Legends) (An addon for [The Battle for Wesnoth](https://www.wesnoth.org/).)

# Usage

```ini
{WISH_ITEM_PICK_UP ID X Y CANNOT_PICKUP_MESSAGE IMAGE_SHOWN_IN_POPUP OBJECT_WML TYPE=weapon TAKE_IT_STRING="Equip" LEAVE_IT_STRING="Leave"}
```
OBJECT is an extended version of the `[object]` from core, namely it supports the following additional keys and tags:
**locked**: boolean, when `true`, the item cannot be unequipped or sold or remove in anyway except by the unit dying.
**lock_msg**: string, the message shown when trying to remove a locked item.
**gold_value**: Cost of the item, i.e., the gold you get when you sell this item.
subtag **[filter]**: Only units satisfying the condition can pickup this `[object]`.

# Inventory
Accessible via **Right click on unit > Inventory** if the unit has an item equipped.
