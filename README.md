# Not Quite Vanilla Minecraft Server
The files here are the necessary files for a personal minecraft server that is not quite vanilla. There are no mods installed that change blocks in or add blocks to the game. The mods that are installed are for exploration and building purposes only. This repo is going to be used to keep files synced and updated on a remote host that will actually be running the server. There wouldn't be much point to just storing a Minecraft server in a repo unless the machine that will be running the server is remote. This could be managed with FTP, but this way I can have a copy of the server folder on my own machine and modify as I see fit then simply push that to the remote host. It also allows me to test a server configuration on my own machine before merging with the master branch, so if I want to add something and see how it plays I don't jeopardize the main world files and configs should something go wrong.


## Config
The folder that contains the majority of the config files for Forge and the installed mods. Most mods make their own folder within this, but some just have loose files.


## Libraries
Various Java libraries needed for vanilla Minecraft.


## Logs
Server log file storage. Keeps separate files for deugging logs and general server logs.


## Mods
This folder contains any changes to the vanilla server and on occasion their configuration folders and files. This folder was created by the Forge install process.

##### [Sponge](https://www.spongepowered.org/)
Sponge is a plugin API that allows for modifications that do not add content to the game and instead only use ingame items and blocks.

##### [Forge](https://files.minecraftforge.net/)
Forge is a modding API that allows for more complex mods to be installed. Currently this is not really in use, but it is installed for potential future use.

##### [VoxelSniper](https://forums.spongepowered.org/t/voxelsniper-long-range-terrain-editing-v8-0-0-1-8-9-1-10-2/10695)
VoxelSniper is a long range terrain editing and building tool. It allows for the use of various "brushes" in game much like 3D modeling software.

##### [Open Terrain Generator](https://minecraft.curseforge.com/projects/open-terrain-generator) (OTG)
This is an open source Minecraft terrrain customization API. It allows for complete control over the Minecraft generator settings. Presets can be downloaded from various places.

##### [Biome Bundle](https://minecraft.curseforge.com/projects/biome-bundle)
A generator preset for OTG that adds a lot of very beautiful biomes using only vanilla Minecraft blocks.


## World
Default folder for save/map data. This is currently a map with completely vanilla terrain and a new folder will be generated once the server is started with the OTG configuration.


## Banned-ips.json
Formatted list of banned IP addresses that will be denied connetion to the server.


## Banned-players.json
Formatted list of banned player names and UUIDs.


## Eula.txt
A file to confirm you agree to the MC server EULA.


## Forge_1.12.2_launcher.jar
Main executable for a Minecraft server with Forge installed. Can be run directly with any sort of jar launcher, or from the command line which allows for various JVM args to be applied.


## Minecraft_server.1.12.2.jar
Main executable for a vanilla Minecraft server. Can be run directly with any sort of jar launcher, or from the command line which allows for various JVM args to be applied.


## Ops.json
List of players with admin level permissions ON the server. Different from someone with access to server files and other "admin" privileges. These users are simply allowed to execute in game commands reserved for high level users.


## Server.properties
The main configuration file for the server. Has a list of values that determine all aspects of the server. Has a few changes in order to properly use the mods that are installed, but it is a largely vanilla file.


## Start_server.command
A short bash command for starting the server with the proper amount of RAM allocated based on the system we are using. Change the 3 in "-Xmx3G" to the desired number of GB of RAM. Other JVM args can be added as needed, but to keep things simple this works well. The file can be executed and the server takes care of the rest.


## Usercache.json
Formatted list of all player usernames and UUIDs that have ever joined the server and when they last joined.


## Usernamecache.json
Formatted list of just player names and UUIDs that have joined the server, does not include date and time last joined.


## Whitelist.json
Formatted list of player names and UUIDs used to only allow listed players onto the server.