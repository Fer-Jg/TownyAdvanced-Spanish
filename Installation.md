## Server Preparation
1. Stop your server completely.
2. Download any of the following:
   * Latest development build from the [Official Towny Advanced Discord Server](https://discord.gg/gnpVs5m).
     * Includes **Towny.jar**.
   * Latest release build from the [website](http://towny.palmergames.com/category/towny-download/towny-release-download/).
     * Includes **Towny.jar**, **TownyChat.jar**, and **TownyNameUpdater.jar**.
3. Copy the contents to your _Plugins_ folder.
   * **Towny.jar** is required at all times
   * **TownyChat.jar** is required if you want Towny to modify chatting:
     * Adding prefixes and suffixes from your permissions plugin to chat
     * Adding town/nation/world to chat
     * Adding chat channels
   * **TownyNameUpdater.jar** is required if you want to keep Towny residents' names updated if they change their Minecraft name.
   * [**Vault.jar**](https://www.spigotmc.org/resources/vault.34315/) (separate download) is required if you use an economy plugin other than _[iConomy 5.0.1](http://towny.palmergames.com/iconomy-5-05/)_.
4. Start your server.
5. Stop your server.

## Bypass Craftbukkit Version Check (Optional)

_This step is no longer required for newer versions of Towny._

_If you cannot find this step in your config.yml (which is likely the case), skip this step._

1. Navigate to the newly-created *plugins/Towny/Settings* folder.
   * Open **config.yml**
   * Set `bypass_version_check: true`
   * Save **config.yml**
2. Start your server.
3. Stop your server.

## Configuring Existing Worlds
1. Navigate to the newly-created _plugins/Towny/Data/Worlds_ folder.
2. Open each **worldname.txt**.
3. Edit each file accordingly.
   * This is the place to turn off plots regenerating if a townblock is lost.

## Configuring config.yml
1. Navigate to _plugins/Towny/Settings_
2. Open **config.yml**
3. Carefully edit **config.yml** to your liking, including:
   * Townblock size defaulting at 16x16 (CANNOT BE CHANGED LATER!).
   * Settings for new default worlds (Settings for new **worldname.txt** files).
   * Settings for new towns.
4. Change the economy settings:
   * If you do not use an economy plugin, set `using_economy: false`.
   * If you are using a UUID version of _EssentialsEco_, add _NPC:_ to the beginning of _Town-_ and _Nation-_ in `new_world_settings`:
     * From this:
         ```bash
         town:
         prefix: Town-
         nation:
         prefix: Nation-
         ```
     * To this:
         ```bash
         town:
         prefix: NPC:Town-
         nation:
         prefix: NPC:Nation-
         ```
5. Set the permissions:
  * Set `using_permissions: true` if you have a permissions plugin.
  * Your permissions plugin should be detected.
6. Save **config.yml**.
7. Start your server. You are now ready to begin your own town.

## Configuring townyperms.yml (semi-optional)

1. Navigate to _plugins/Towny/Settings_.
2. Open **townyperms.yml**
3. Carefully read over the default groups/ranks.
4. Add and remove permission nodes as you see fit.
5. Optionally, add your own ranks for mayors to promote (or demote) their residents to.
6. Save **townyperms.yml**.
7. Perform `/ta reload` in-game to see your changes.

## Configuring channels.yml (optional)

_This step is optional if you have **TownyChat.jar**._

1. Navigate to _plugins/Towny/Settings_
2. Open **channels.yml**.
3. Edit **channels.yml** to your liking.
4. Save **channels.yml**.
6. Perform `/ta reload` in-game to see your changes.

## Configuring chatconfig.yml (optional)

_This step is optional if you have **TownyChat.jar**._

1. Navigate to _plugins/Towny/Settings_
2. Open **chatconfig.yml**.
3. Edit **chatconfig.yml** to your liking.
4. Save **chatconfig.yml**.
6. Perform `/ta reload` in-game to see your changes.