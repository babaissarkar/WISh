# WISh

A GUI item inventory system for [War of Legends era](https://github.com/knyghtmare/War_of_Legends) (An addon for [The Battle for Wesnoth](https://www.wesnoth.org/)).

# Usage

## Campaign Files

In `_main.cfg`, at the very beginning of this file, add:

```ini
#ifhave ~add-ons/WISh/_main.cfg
    {~add-ons/WISh/utils}
#endif
```

**What does this do?**

It loads the WISh resource in the top-level so that the `[campaign]` tag can recognise it.

Next step is loading the resource:

```ini
[campaign]
    # load inventory items
    # load WISH
    [load_resource]
        id=wish_items
    [/load_resource]
[/campaign]
```

## Scenario Files

```ini
{WISH_ITEM_PICK_UP ID X Y CANNOT_PICKUP_MESSAGE IMAGE_SHOWN_IN_POPUP OBJECT_WML TYPE=weapon TAKE_IT_STRING="Equip" LEAVE_IT_STRING="Leave"}
```

**Example code from Knyghtmare's SotBE rework project**
```ini
{WISH_ITEM_PICK_UP 
        rock_of_frost_resisting 22 17

        (_"This trinket can be equipped by most units except goblins.")

        ("items/rock.png") (
        [object]
            id=rock_of_frost_resisting
            name= _ "Rock of Frost Resistance"
            take_only_once=no
            image="items/rock.png"
            description= _ "Increase cold resistance by 5%."
            [filter]
                side=1
                [not]
                    race=goblin
                [/not]
            [/filter]

            [effect]
                apply_to=resistance
                replace=no
                [resistance]
                    cold=-5
                [/resistance]
            [/effect]
        [/object]
    ) 
    (TYPE=trinket)}
```
* **OBJECT** is an extended version of the `[object]` from core, namely it supports the following additional keys and tags:
    * **locked**: boolean, when `true`, the item cannot be unequipped or sold or remove in anyway except by the unit dying.
    * **lock_msg**: string, the message shown when trying to remove a locked item.
    * **gold_value**: Cost of the item, i.e., the gold you get when you sell this item.
    * subtag **[filter]**: Only units satisfying the condition can pickup this `[object]`.
* **TYPE**: Optional macro argument specifying the type of the equipment. An unit can only have one item of each type at a time. Please note `TYPE` can be any 4 values: `weapon` (default if not specified), `armor`, `trinket`, `amulet`. We have _no further plans_ on expanding the `TYPE=` value list.
* **TAKE_IT_STRING** and **LEAVE_IT_STRING**: Optional macro arguments that specify the caption text to be shown on the `Equip` and `Leave` buttons. Default values are (obviously) `Equip` and `Leave`.

# Inventory
Accessible via **Right click on unit > Inventory** if the unit has an item equipped.

# Screenshots

![Image 1](https://cdn.bsky.app/img/feed_fullsize/plain/did:plc:exlwxcktqkgj7bawgy2muzmg/bafkreiezvh7oixrmbn6ls7gvxoi3z5fdmpaii6j6qrbdtd2qc35233ztdu@jpeg)

![Image 2](https://cdn.bsky.app/img/feed_fullsize/plain/did:plc:exlwxcktqkgj7bawgy2muzmg/bafkreiejyrgxjbj7bmig4sbw6gvzbq4k6k6jk3rrepd5z4yzqr2jxrfmlq@jpeg)

![Image 3](https://cdn.bsky.app/img/feed_fullsize/plain/did:plc:exlwxcktqkgj7bawgy2muzmg/bafkreihalt26ravo7w3nmfpmhcbaiwjwfvbtwvg4xeq3axi73e25r2bgeq@jpeg)
