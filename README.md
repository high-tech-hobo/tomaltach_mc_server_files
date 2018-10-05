# Not Quite Vanilla Minecraft Server
The files here are the necessary files for a personal minecraft server that is not quite vanilla. There are no mods installed that change blocks in or add blocks to the game. The mods that are installed are for exploration and building purposes only. This repo is going to be used to keep files synced and updated on a remote host that will actually be running the server. There wouldn't be much point to just storing a Minecraft server in a repo unless the machine that will be running the server is remote. This could be managed with FTP, but this way I can have a copy of the server folder on my own machine and modify as I see fit then simply push that to the remote host. It also allows me to test a server configuration on my own machine before merging with the master branch, so if I want to add something and see how it plays I don't jeopardize the main world files and configs should something go wrong.

<br>
<br>
 

## Top Level Files and Folders

### Config 
The folder that contains the majority of the config files for Forge and the installed mods. Most mods make their own folder within this, but some just have loose files.

<br>

### Libraries
Various Java libraries needed for vanilla Minecraft.

<br>

### Logs
Server log file storage. Keeps separate files for debugging logs and general server logs.

<br>


### Mods
This folder contains any changes to the vanilla server and on occasion their configuration folders and files. This folder was created by the Forge install process.

##### [Sponge](https://www.spongepowered.org/)
Sponge is a plugin API that allows for modifications that do not add content to the game and instead only use ingame items and blocks.

##### [Forge](https://files.minecraftforge.net/)
Forge is a modding API that allows for more complex mods to be installed. Currently this is not really in use, but it is installed for potential future use.

##### [VoxelSniper](https://forums.spongepowered.org/t/voxelsniper-long-range-terrain-editing-v8-0-0-1-8-9-1-10-2/10695)
VoxelSniper is a long range terrain editing and building tool. It allows for the use of various "brushes" in game much like 3D modeling software.

##### [Open Terrain Generator](https://minecraft.curseforge.com/projects/open-terrain-generator) (OTG)
This is an open source Minecraft terrain customization API. It allows for complete control over the Minecraft generator settings. Presets can be downloaded from various places.

##### [Biome Bundle](https://minecraft.curseforge.com/projects/biome-bundle)
A generator preset for OTG that adds a lot of very beautiful biomes using only vanilla Minecraft blocks.

<br>

### World
Default folder for save/map data. This is currently a map with completely vanilla terrain and a new folder will be generated once the server is started with the OTG configuration.

<br>

### Banned-ips.json
Formatted list of banned IP addresses that will be denied connection to the server.

<br>

### Banned-players.json
Formatted list of banned player names and UUIDs.

<br>

### Eula.txt
A file to confirm you agree to the MC server EULA.

<br>

### Forge_1.12.2_launcher.jar
Main executable for a Minecraft server with Forge installed. Can be run directly with any sort of jar launcher, or from the command line which allows for various JVM args to be applied.

<br>

### Minecraft_server.1.12.2.jar
Main executable for a vanilla Minecraft server. Can be run directly with any sort of jar launcher, or from the command line which allows for various JVM args to be applied.

<br>

### Ops.json
List of players with admin level permissions ON the server. Different from someone with access to server files and other "admin" privileges. These users are simply allowed to execute in game commands reserved for high level users.

<br>

### Server.properties
The main configuration file for the server. Has a list of values that determine all aspects of the server. Has a few changes in order to properly use the mods that are installed, but it is a largely vanilla file.

<br>

### Start_server.command
A short bash command for starting the server with the proper amount of RAM allocated based on the system we are using. Change the 3 in "-Xmx3G" to the desired number of GB of RAM. Other JVM args can be added as needed, but to keep things simple this works well. The file can be executed and the server takes care of the rest.

<br>

### Usercache.json
Formatted list of all player usernames and UUIDs that have ever joined the server and when they last joined.

<br>

### Usernamecache.json
Formatted list of just player names and UUIDs that have joined the server, does not include date and time last joined.

<br>

### Whitelist.json
Formatted list of player names and UUIDs used to only allow listed players onto the server.

<br>

<br>

## Detailed File Structure

```
tomaltach_mc_server_files
├── Biome Bundle/                                      <- world data for OTG preset world
|   ├── data/                                          <- world data not specific to dimensions
|   |   ├── advancements/                              <- player advancement progress files
|   |   |
|   |   ├── functions/                                 <- folder for function files (see apx. 1)
|   |   |
|   |   └── sponge/                                    <- nto sure until it has files
|   |
|   ├── DIM1/                                          <- world data for The End dimension
|   |   ├── data/                                      <- non-player data for End dimension
|   |   |   ├── advancements/                          <- player advancement progress files
|   |   |   |
|   |   |   └── functions/                             <- folder for function files (see apx. 1)
|   |   |
|   |   ├── playerdata/                                <- player info for End dimension
|   |   |
|   |   └── session.lock                               <- last level access info (see apx. 1)
|   |
|   ├── DIM-1/                                         <- world data for Nether dimension
|   |   ├── data/                                      <- non-player data for Nether dimension
|   |   |   ├── advancements/                          <- player advancement progress files
|   |   |   |
|   |   |   └── functions/                             <- folder for function files (see apx. 1)
|   |   |
|   |   ├── playerdata/                                <- player info for the Nether
|   |   |
|   |   └── session.lock                               <- last level access info (see apx. 1)
|   |
|   ├── OpenTerrainGenerator/                          <- OTG info for world gen
|   |   ├── Dimensions.txt                             <- dimension list (not exactly sure based on content)
|   |   |
|   |   └── WorldBorder.txt                            <- generation limit (0,0,0 if no limit)
|   |
|   ├── playerdata/                                    <- player data not specific to dimensions
|   |
|   ├── region/                                        <- chunk files (see apx. 1)
|   |
|   └── session.lock                                   <- last level access info (see apx. 1)
|
├── Config/                                            <- config files for Forge and mods
|   ├── sponge/                                        <- Sponge config files
|   |   ├── worlds/                                    <- multi-world files
|   |   |   └── minecraft/                             <- default minecraft world config
|   |   |       ├── nether/                            <- dimension using Nether config
|   |   |       |   ├── DIM-1/                         <- specific dimension instance folder
|   |   |       |   |   └── world.conf                 <- Nether config
|   |   |       |   |
|   |   |       |   └── dimension.conf                 <- general Nether config
|   |   |       |
|   |   |       ├── overworld/                         <- dimensions using overworld config
|   |   |       |   ├── Biome Bundle/                  <- BB specific config folder
|   |   |       |   |   └── world.conf                 <- world config
|   |   |       |   |
|   |   |       |   ├── world/                         <- default world config folder
|   |   |       |   |   └── world.conf                 <- world config
|   |   |       |   |
|   |   |       |   └── dimension.conf                 <- general overworld config
|   |   |       |
|   |   |       └── the_end/                           <- dimensions using End config
|   |   |           ├── DIM1/                          <- specific dimension instance folder
|   |   |           |   └── world.conf                 <- world config
|   |   |           |
|   |   |           └── dimension.conf                 <- general End config
|   |   |
|   |   ├── custom_data.conf                           <- CHECKED DOCS AND NOT SURE
|   |   |
|   |   ├── global.conf                                <- Sponge global settings (see apx. 1)
|   |   |
|   |   └── tracker.conf                               <- CHECKED DOCS AND NOT SURE
|   |
|   ├── voxelsniper/                                   <- VoxelSniper data folder
|   |   └── voxelsniper.conf                           <- main VoxelSniper config
|   |
|   ├── forge.cfg                                      <- general Forge config
|   |
|   └── forgeChunkLoading.cfg                          <- chunk loading control config
|
├── libraries/                                         <- all the java libraries, not going to break it down
|
├── logs/                                              <- all the server log files, again not worth the detail
|
├── mods/                                              <- folder for all mod files
|   ├── 1.12.2/                                        <- mods for MC version 1.12.2
|   |   └── OTG-Core.jar                               <- OTG secondary jar
|   |
|   ├── OpenTerrainGenerator/                          <- OTG generator files
|   |   ├── GlobalBiomes/                              <- biome files w/o OTG preset
|   |   |
|   |   ├── GlobalObjects/                             <- world object files w/o preset
|   |   |
|   |   └── worlds/                                    <- OTG presets
|   |       ├── Biome Bundle/                          <- OTG preset gen files
|   |       |   ├── WorldBiomes/                       <- biome gen files
|   |       |   |
|   |       |   ├── WorldObjects/                      <- world object gen files
|   |       |   |
|   |       |   └── WorldConfig.ini                    <- OTG preset config
|   |       |
|   |       └── OTG.ini                                <- OTG config file
|   |
|   ├── Biome_Bundle-1.12.2-v6.1.jar                   <- OTG preset file
|   |
|   ├── OpenTerrainGenerator-1.12.2+-+v6.jar           <- main mod file for OTG
|   |
|   ├── spongeforge-1.12.2-2705-7.1.0-BETA-3361.jar    <- main mod file for Sponge on Forge
|   |
|   └── VoxelSniper-8.5.0-SNAPSHOT.jar                 <- main mod file for VoxelSniper
|
├── world/                                             <- structured same as Biome Bundle Folder
|
├── banned-ips.json                                    <- list of banned IP addresses
|
├── banned-players.json                                <- list of banned players and UUIDs
|
├── eula.txt                                           <- user agreement
|
├── forge_1.12.2_launcher.jar                          <- jar to spart server w/ forge
|
├── minecraft_server.1.12.2.jar                        <- main minecraft server jar
|
├── ops.json                                           <- players with op privileges
|
├── README.md                                          <- this file
|
├── server.properties                                  <- main server config
|
├── start_server.command                               <- java command for server start
|
├── usercache.json                                     <- timestamped log-on and log-off data
|
├── usernamecache.json                                 <- log-on and log-off data
|
└── whitelist.json                                     <- list of allowed players and UUIDs

```


## Appendix 1
Function Files  - https://minecraft.gamepedia.com/Function/ <br>
Session Files   - https://minecraft.gamepedia.com/Level_format#session.lock_format (bottom of page) <br>
Chunk/Region Files - https://minecraft.gamepedia.com/Region_file_format <br>
Sponge Global Config File - https://docs.spongepowered.org/stable/en/server/getting-started/configuration/sponge-conf.html