# Terraria .MAP file (Player)

> NOTE: This is only for `.map` files generated in Terraria PC 1.4.4.9.

The player's world-specific maps are stored in `.map` files, located in a folder based on the player's name.  

> • For Windows, the save directory is `%UserProfile%\Documents\My Games\Terraria\Players\{PLAYER}`  
> • For Linux, the save directory is `~/.local/share/Terraria/Players/{PLAYER}`  

Unlike `.plr` files, `.map` files are not encrypted and can be read normally in a hex editor.

## Map File

> NOTE: The values are in little-endian.  

| Value         | Length    | Type   | Description                                                                                                                                                                                                                                  |
| ------------- | --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Map Version   | 0x4       | Int    | Defines what version the map file is. 1.4.4.9 should be `0x117 (279)`.                                                                                                                                                                       |
| File Metadata | 0x14 (20) | Struct | The metadata of the map file. See how it's stored [here](FileMetadata.md).                                                                                                                                                                   |
| World Name    | *Varies*  | String | The name of the world this map is based on. The first byte defines how long the string is. The next X bytes (defined in the length) store the string in UTF-8. (max string length is 20, so the Player Name could take up a max of 21 bytes) |
| World ID      | 0x4       | Int    | The ID of the world this map is based on.                                                                                                                                                                                                    |
| Max Tiles X   | 0x4       | Int    | The maximum amount of tiles in the X axis, based on the world's size.<br/>`Small` - 4200<br/>`Medium` - 6400<br/>`Large` - 8400                                                                                                              |
| Max Tiles Y   | 0x4       | Int    | The maximum amount of tiles in the Y axis, based on the world's size.<br/>`Small` - 1200<br/>`Medium` - 1800<br/>`Large` - 2400                                                                                                              |
