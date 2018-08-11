#Not Quite Vanilla Minecraft Server
The files here are the necessary files for a personal minecraft server that is not quite vanilla. There are no mods installed that change blocks in or add blocks to the game. The mods that are installed are for exploration and building purposes only.

##Config


##Libraries


##Logs


##Mods
#####[Sponge](https://www.spongepowered.org/)
Sponge is a plugin API that allows for modifications that do not add content to the game and instead only use ingame items and blocks.

#####[Forge](https://files.minecraftforge.net/)
Forge is a modding API that allows for more complex mods to be installed. Currently this is not really in use, but it is installed for potential future use.

#####[VoxelSniper](https://forums.spongepowered.org/t/voxelsniper-long-range-terrain-editing-v8-0-0-1-8-9-1-10-2/10695)
VoxelSniper is a long range terrain editing and building tool. It allows for the use of various "brushes" in game much like 3D modeling software.

#####[Open Terrain Generator](https://minecraft.curseforge.com/projects/open-terrain-generator) (OTG)
This is an open source Minecraft terrrain customization API. It allows for complete control over the Minecraft generator settings. Presets can be downloaded from various places.

#####[Biome Bundle](https://minecraft.curseforge.com/projects/biome-bundle)
A generator preset for OTG that adds a lot of very beautiful biomes using only vanilla Minecraft blocks.


##World


##Banned-ips.json


##Banned-players.json


##Eula.txt
A file to confirm you agree to the MC server EULA.


##Forge_1.12.2_launcher.jar
Main executable for a Minecraft server with Forge installed. Can be run directly with any sort of jar launcher, or from the command line which allows for various JVM args to be applied.


##Minecraft_server.1.12.2.jar
Main executable for a vanilla Minecraft server. Can be run directly with any sort of jar launcher, or from the command line which allows for various JVM args to be applied.


##Ops.json
List of players with admin level permissions ON the server. Different from someone with access to server files and other "admin" privileges. These users are simply allowed to execute in game commands reserved for high level users.


##Server.properties
The main configuration file for the server. Has a list of values that determine all aspects of the server. Has a few changes in order to properly use the mods that are installed, but it is a largely vanilla file.


##Start_server.command
A short bash command for starting the server with the proper amount of RAM allocated based on the system we are using. Change the 3 in "-Xmx3G" to the desired number of GB of RAM.


##Usercache.json


##Usernamecache.json


##Whitelist.json
Formatted list of player names and UDIDs used to only allow listed players onto the server.