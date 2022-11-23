# Terraria .PLR file (Player)  
Terraria players are stored in `.plr` files, usually located in a "Players" folder in the game's save directory. They contain nearly everything about a player, including inventory, looks, buffs, and certain flags. The only thing that isn't saved in the file are world-specific maps, which are instead stored in a folder based on the player's name.
> • For Windows, the save directory is `%UserProfile%\Documents\My Games\Terraria\Players`  
> • For Linux, the save directory is `~/.local/share/Terraria/Players`  
  
`.plr` files are normally encrypted in AES-128-CBC, the key being `68-00-33-00-79-00-5F-00-67-00-55-00-79-00-5A-00` (or `h3y_gUyZ` in little-endian unicode)  
The key is also available in the root of this repository as `key.bin`
