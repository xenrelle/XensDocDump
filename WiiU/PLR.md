# Wii U Terraria .PLR file (Player)

> NOTE: This is only for `.plr` files generated in Terraria Wii U [1.08](https://terraria.wiki.gg/wiki/Console_version_history#1.08) (UPFI-20160803).

placeholder

## Player File

> NOTE: The values are in big-endian.

| Value             | Length    | Type                     | Description                                                                                                                                                              |
| ----------------- | --------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Player Version    | 0x2       | Short                    | Defines what version the player file is. 1.08 should be `0x15 (21)`.                                                                                                     |
| Player Name       | *Varies*  | String                   | The first byte defines how long the string is. The next X bytes (defined in the length) store the string in UTF-8.                                                       |
| Difficulty        | 0x1       | Byte                     | The difficulty the player is set as. 0 is Classic, 1 is Mediumcore, and 2 is Hardcore.                                                                                   |
| Hair              | 0x1       | Byte                     | Defines the player's hairstyle ID (zero-based). See all hairstyles and IDs [here](https://terraria.wiki.gg/wiki/Hairstyles).<br>`(HINT: Wii U only has hairstyles 1-51)` |
| Unknown           | 0x3       | Byte Array               | Unknown.                                                                                                                                                                 |
| Current Health    | 0x2       | Short                    | How much health the player currently has.                                                                                                                                |
| Max Health        | 0x2       | Short                    | The maximum amount of health the player has. Increases with Life Crystals or Life Fruit.                                                                                 |
| Current Mana      | 0x2       | Short                    | How much mana the player currently has.                                                                                                                                  |
| Max Mana          | 0x2       | Short                    | The maximum amount of mana the player has. Increases with Mana Crystals.                                                                                                 |
| Hair Colour       | 0x3       | RGB Byte Array           | Colour of the player's hair, 3 bytes make up an RGB value.                                                                                                               |
| Skin Colour       | 0x3       | RGB Byte Array           | Colour of the player's skin, 3 bytes make up an RGB value.                                                                                                               |
| Eye Colour        | 0x3       | RGB Byte Array           | Colour of the player's eyes, 3 bytes make up an RGB value.                                                                                                               |
| Shirt Colour      | 0x3       | RGB Byte Array           | Colour of the player's shirt, 3 bytes make up an RGB value.                                                                                                              |
| Undershirt Colour | 0x3       | RGB Byte Array           | Colour of the player's undershirt, 3 bytes make up an RGB value.                                                                                                         |
| Pants Colour      | 0x3       | RGB Byte Array           | Colour of the player's pants, 3 bytes make up an RGB value.                                                                                                              |
| Shoe Colour       | 0x3       | RGB Byte Array           | Colour of the player's shoes, 3 bytes make up an RGB value.                                                                                                              |
| Unknown           | 0x31 (49) | Byte Array               | Unknown.                                                                                                                                                                 |
| Inventory         | *Varies*  | [Item](#Item-Data) Array | Items in the inventory. There are 44 total items, the first 40 being the player's inventory, and the last 4 being the player's coins.                                    |

## Item Data

| Value         | Length | Type  | Description                                                                                                                                                      |
| ------------- | ------ | ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Item ID       | 0x2    | Short | The ID of the item. See all item IDs [here](https://terraria-archive.fandom.com/wiki/Data_IDs). If the ID is 0, then the "amount" and "modifier" are not stored. |
| Item Amount   | 0x2    | Short | The amount of items in the stack.                                                                                                                                |
| Item Modifier | 0x1    | Byte  | The item's prefix/modifier. See all modifier IDs [here](https://terraria.wiki.gg/wiki/Prefix_IDs).                                                               |
