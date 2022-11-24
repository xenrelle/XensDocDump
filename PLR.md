# Terraria .PLR file (Player)  
> NOTE: This is only for `.plr` files generated in Terraria PC 1.4.3.6, 1.4.4.9 will be documented later  
  
Terraria players are stored in `.plr` files, usually located in a "Players" folder in the game's save directory. They contain nearly everything about a player, including inventory, looks, buffs, and certain flags. The only thing that isn't saved in the file are world-specific maps, which are instead stored in a folder based on the player's name.
> • For Windows, the save directory is `%UserProfile%\Documents\My Games\Terraria\Players`  
> • For Linux, the save directory is `~/.local/share/Terraria/Players`  
  
`.plr` files are normally encrypted in AES-128-CBC, the key being `68-00-33-00-79-00-5F-00-67-00-55-00-79-00-5A-00` (or `h3y_gUyZ` in little-endian unicode)  
The key is also available in the root of this repository as `key.bin`

## Header [0x00..0x29+X]
I haven't worked out what the header means quite yet. I do, however, know the name is stored here.  
• At offset `0x18`, the name structure is like this:  
 • The first byte defines how long the name string is. For example, if the byte is `06`, then the name is 6 characters long. We'll refer to this value as X for now.  
 • The following X bytes is the name in UTF-8. It will be as long as X, and it is also null-terminated.

## Player Values [0x2A+X..0x??]
> NOTE: The values seem to be in little-endian from testing, but it could just be a Windows thing.  
  
| Value | Length | Description |
| ----- | ------ | ----------- |
| Clothes | 0x1 | Defines the character's clothing and gender selection. Values 1-4 are male, and 5-8 are female. |
| Current Health | 0x4 | How much health the player currently has. |
| Max Health | 0x4 | The maximum amount of health the player has. Increases with Life Crystals or Life Fruit.<br/>`(Hard-capped at 500.)` |
| Current Mana | 0x4 | How much mana the player currently has.<br/>`(Hard-capped at 400.)` |
| Max Mana | 0x4 | The maximum amount of mana the player has. Increases with Mana Crystals.<br/>`(Hard-capped at 200. Buffs that increase maximum mana don't get stored here, so the current mana could be higher than the max mana.)` |
