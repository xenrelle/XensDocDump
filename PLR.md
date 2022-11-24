# Terraria .PLR file (Player)  
> NOTE: This is only for `.plr` files generated in Terraria PC 1.4.3.6, 1.4.4.9 will be documented later  
  
Terraria players are stored in `.plr` files, usually located in a "Players" folder in the game's save directory. They contain nearly everything about a player, including inventory, looks, buffs, and certain flags. The only thing that isn't saved in the file are world-specific maps, which are instead stored in a folder based on the player's name.
> • For Windows, the save directory is `%UserProfile%\Documents\My Games\Terraria\Players`  
> • For Linux, the save directory is `~/.local/share/Terraria/Players`  
  
`.plr` files are normally encrypted in AES-128-CBC, the key (and IV) being `68-00-33-00-79-00-5F-00-67-00-55-00-79-00-5A-00` (or `h3y_gUyZ` in little-endian unicode)  
The key is also available in the root of this repository as `key.bin`

## Player Values [0x00..0x??]
> NOTE: The values seem to be in little-endian from testing, but it could just be a Windows thing.  
  
| Value | Length | Description |
| ----- | ------ | ----------- |
| Player Version | 0x1 | Defines what version the player file is. 1.4.3.6 should be `F0` |
| Unknown | 0x17 | Unknown. |
| Player Name | Varies | The first byte defines how long the string is. The next X bytes (defined in the length) store the string in UTF-8. (max string length is 20, so the Player Name could take up a max of 21 bytes) |\
| Difficulty | 0x1 | The difficulty the player is set as. 0 is Classic, 1 is Expert, 2 is Master, and 3 is Journey. |
| Play Time Ticks | 0x4 | The character's play time in ticks `(HINT: 1 millisecond = 10000 ticks)` |
| Hair | 0x4 | Defines the player's hairstyle. |
| Hair Dye | 0x1 | Defines the player's hair dye. |
| Unknown | 0x7 | Unknown. |
| Clothes/Gender | 0x1 | Defines the character's clothing and gender selection. Values 0-4 are male, and 5-9 are female. |
| Current Health | 0x4 | How much health the player currently has. |
| Max Health | 0x4 | The maximum amount of health the player has. Increases with Life Crystals or Life Fruit.<br/>`(Hard-capped at 500.)` |
| Current Mana | 0x4 | How much mana the player currently has.<br/>`(Hard-capped at 400.)` |
| Max Mana | 0x4 | The maximum amount of mana the player has. Increases with Mana Crystals.<br/>`(Hard-capped at 200. Buffs that increase maximum mana don't get stored here, so the current mana could be higher than the max mana.)` |
| Has Extra Accessory | 0x1(bool) | If a player has used a Demon Heart, increasing their maximum accessory slots by 1. |
| Unlocked Biome Torches | 0x1(bool) | If a player has unlocked biome torches by surviving the Torch God event. |
| Is Using Biome Torches | 0x1(bool) | If a player has biome torches toggled or not. |
| Can use DD2 Sentries | 0x1(bool) | If the player is allowed to use DD2 sentries outside of the event, set to true when the event has been successfully cleared. |
| Tax Money | 0x4 | The amount of money the Tax Collector has saved up for the player (in copper coins). |
| Hair Colour | 0x3 | Colour of the player's hair, 3 bytes make up an RGB value. |
| Skin Colour | 0x3 | Colour of the player's skin, 3 bytes make up an RGB value. |
| Eye Colour | 0x3 | Colour of the player's eyes, 3 bytes make up an RGB value. |
| Shirt Colour | 0x3 | Colour of the player's shirt, 3 bytes make up an RGB value. |
| Undershirt Colour | 0x3 | Colour of the player's undershirt, 3 bytes make up an RGB value. |
| Pants Colour | 0x3 | Colour of the player's pants, 3 bytes make up an RGB value. |
| Shoe Colour | 0x3 | Colour of the player's shoes, 3 bytes make up an RGB value. |
