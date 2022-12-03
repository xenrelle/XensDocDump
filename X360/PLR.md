# Xbox 360 Terraria .PLR file (Player)

> NOTE: This is only for `.plr` files generated in Terraria X360 [1.09](https://terraria.wiki.gg/wiki/Console_version_history#1.09) (UPFI-20160803).

placeholder

## Player File

> NOTE: The values are in little-endian.

| Value             | Length   | Type           | Description                                                                                                                                                              |
| ----------------- | -------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Player Version    | 0x4      | Int            | Defines what version the player file is. 1.09 should be `0x15 (21)`.                                                                                                     |
| Unknown           | 0x2      | Byte Array     | Currently unknown, but just seems to be two null bytes.                                                                                                                  |
| Player Name       | *Varies* | String         | The first byte defines how long the string is. The next X bytes (defined in the length) store the string in UTF-8.                                                       |
| Difficulty (?)    | 0x1      | Byte           | The difficulty the player is set as. 0 is Classic, 1 is Mediumcore, and 2 is Hardcore.                                                                                   |
| Hair              | 0x4(?)   | Int(?)         | Defines the player's hairstyle ID (zero-based). See all hairstyles and IDs [here](https://terraria.wiki.gg/wiki/Hairstyles).<br/>`(HINT: X360 only has hairstyles 1-51)` |
| Current Health    | 0x2      | Short          | How much health the player currently has.                                                                                                                                |
| Max Health        | 0x2      | Short          | The maximum amount of health the player has. Increases with Life Crystals or Life Fruit.                                                                                 |
| Current Mana      | 0x2      | Short          | How much mana the player currently has.                                                                                                                                  |
| Max Mana          | 0x2      | Short          | The maximum amount of mana the player has. Increases with Mana Crystals.                                                                                                 |
| Hair Colour       | 0x3      | RGB Byte Array | Colour of the player's hair, 3 bytes make up an RGB value.                                                                                                               |
| Skin Colour       | 0x3      | RGB Byte Array | Colour of the player's skin, 3 bytes make up an RGB value.                                                                                                               |
| Eye Colour        | 0x3      | RGB Byte Array | Colour of the player's eyes, 3 bytes make up an RGB value.                                                                                                               |
| Shirt Colour      | 0x3      | RGB Byte Array | Colour of the player's shirt, 3 bytes make up an RGB value.                                                                                                              |
| Undershirt Colour | 0x3      | RGB Byte Array | Colour of the player's undershirt, 3 bytes make up an RGB value.                                                                                                         |
| Pants Colour      | 0x3      | RGB Byte Array | Colour of the player's pants, 3 bytes make up an RGB value.                                                                                                              |
| Shoe Colour       | 0x3      | RGB Byte Array | Colour of the player's shoes, 3 bytes make up an RGB value.                                                                                                              |
