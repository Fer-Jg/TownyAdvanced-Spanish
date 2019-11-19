Use this page to learn how Towny works, how various settings affect the gameplay, what you can do to customize Towny to your liking.

-   [The Hierarchy](#the-hierarchy)
    -   [Nomads](#nomads)
    -   [Residents](#residents)
    -   [Towns](#towns)
    -   [Mayors](#mayors)
    -   [Outlaws](#outlaws)
    -   [Nations](#nations)
    -   [Kings](#kings)
    -   [Configuring Townyperms.yml and the Roles of the Ranks Within](#configuring-townypermsyml-and-the-roles-of-the-ranks-within)
    -   [Configuring Mayor and King Titles, Town and Nation Names](#configuring-mayor-and-king-titles-town-and-nation-names)
-   [How Towns Grow](#how-towns-grow)
    -   [Starting a Town](#starting-a-town)
    -   [Joining Towns](#joining-yowns)
-   [Plot System of Land Ownership](#plot-system-of-land-ownership)
    -   [Town Blocks](#town-blocks)
    -   [Plot Types](#plot-types)
    -   [Outposts](#outposts)
    -   [Selling Land](#selling-land)
    -   [Using the Maps](#using-the-maps)
    -   [Plot Regeneration & Unclaimed Plots](#plot-regeneration--unclaimed-plots)
-   [How Towny Lets Players Protect Their Blocks](#how-towny-lets-players-protect-their-blocks)
    -   [Towny Plot Perms](#towny-plot-perms)
    -   [Protection Additions Found in Towny Advanced](#protection-additions-found-in-towny-advanced)
-   [How Towny Controls PVP Combat](#how-towny-controls-pvp-combat)
    -   [Friendly-fire](#friendly-fire)
    -   [Plot, Town and World PVP Settings](#plot-town-and-world-pvp-settings)
-   [Money](#money)
    -   [Taxes and Upkeep](#taxes-and-upkeep)
    -   [Town and Nation Banks](#town-and-nation-banks)
-   [Chat](#chat)
    -   [PlaceholderAPI Support](#placeholderapi-support)
    -   [Townychat.jar](#townychatjar)
    -   [Chatconfig.yml](#chatconfigyml)
    -   [Chat Channels](#chat_channels)
    -   [Kings' minions' prefixes and suffixes](##kings-minions-prefixes-and-suffixes)
    -   [Spying on chat channels](#spying-on-chat-channels)
-   [Multiworld](#multiworld)
    -   [World Toggles](#world-toggles)
-   [Towny War](#towny-war)
    -   [/ta toggle war (Event War)](#ta-toggle-war-event-war))
    -   [flag-war mode](#flag-war-mode)
-   [Using SQL instead of Flatfile](#using-sql-instead-of-flatfile)
    -   [Configuring SQL](#configuring-sql)
    -   [Converting Flatfile to SQL](#converting-flatfile-to-sql)
    -   [Converting SQL to Flatfile](#converting-sql-to-flatfile)

------------------------------------------------------------------------

[]()The Hierarchy
=================

[]()Nomads
----------

Nomads are simply players who are not part of any town. They are landless and their permission nodes are configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml. Nomads can purchase Embassy plots if they have been given towny.command.plot.claim in the Townyperms.yml

[]()Residents
-------------

Every person who joins your server can become a resident (by default they are given the towny.town.resident permission node in townyperms.yml's nomad section.) Residents have their own [command](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands) `/resident` which used by itself outputs a Resident Screen, displaying Money, Town, Plots owned and Friends. Residents can join towns or choose to start a town of their own. 

Residents can also be put into one town automatically when they join the server for the first time by setting `default_town_name: ''` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). Residents who join towns can claim plots that the Mayor of the town has set for sale. When a resident owns 1 or more plots, they will see a new line on their Resident Screen, showing plots owned and a perm line showing the [plot perms](https://github.com/TownyAdvanced/Towny/wiki/How-Towny-Works#towny-plot-perms) given on all plots that resident owns. Residents have their permission nodes configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml.

[]()Towns
---------

A town is a collection of residents (or just one resident) with one resident as the mayor. A town also has a bank which the mayor can withdraw from. A mayor can also have assistants who have the same powers as him/herself. Towns can have taxes that will be taken at the end of each day interval. 

Towns usually grow outwards from their home block, the townblock the mayor stood in during town creation. Townblocks need to be claimed beside other townblocks, unless the mayor claims an outpost in the wilderness. Towns can be limited to a number of residents using the config option `global_town_settings.max_residents_per_town`, by default this is not limited. All of the towns on a server can be seen in a list using `/town list`.

As of Towny 0.95.1.0 it is possible to store MetaData on a town, see [here](https://github.com/TownyAdvanced/Towny/wiki/Configuring-Metadata-in-Towns-and-Townblocks) for details.

[]()Mayors
----------

Mayors run towns and with the help of their assistants, manage a town and its residents. Mayors have their permission nodes configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml. 

Mayors can decide which ranks their residents fall into, in their town. This can be a Town Assistant or any other custom ranks created by the server admin in the townyperms.yml file. Mayors can see the available ranks using '/town ranklist' command. Players are ranked using `/town rank {add|remove} {playername} {rankname}`. A player can have more than one rank assigned, allowing admins to create diverse town-roles such as bankers, builders, inviters for the mayor to choose for their trusted residents. 

It is not possible to run two towns unless you are also an admin. An admin can do the following to manage two or more towns:

```
Example: Admin Bob
Admin Bob wants to have a server-town, and his own town. Bob would start by creating his Server Town and setting up taxes, plotprices, permissions. This sort of town should not give residents, allies or outsiders permissions in the Server Town.
Bob can give himself more townblocks using the /ta givebonus {townname} {#} command.
When Bob finished making his town the way he wants he uses /townyadmin set mayor {townname} npc to place a fake 'npc' resident as mayor of the Server Town.
Then Bob leaves Server Town and creates his own town. Using the /townyadmin set mayor {townname} npc command Bob can flip back and forth between towns.
Bob doesn't have to leave his town to add players to the Server Town though! He can use /townyadmin town {townname} add {playername}  to add players to the Server Town or set default_town_name: 'Server_Town' in config.yml.
Bob can also add the NPC town into a nation using /ta nation {nation} add {town}.
```

As of Towny 0.95.1.0 mayors have the ability to set titles (prefixes) and surnames (postfixes) to the residents of their town. This is done with:

-   /town set title {name} titlegoeshere
-   /town set surname {name} surnamegoeshere

[]()Outlaws
-----------

As of Towny 0.92.0.0, towns (typically mayors by default, but possibly other town ranks,) can set a list of Outlaws. Outlaws are set using '/town outlaw [add/remove] [name]' and the command requires the towny.command.town.outlaw permission node. Outlaws can be any player and do not have to be in a town or nation. 

If the newly-minted outlaw is a member of your town they will be kicked. Towns that have themselves set to Open-status (anyone can join using the '/town join' command,) can use the outlaw list to prevent these players from joining their town freely. Players cannot spawn to public towns which consider them outlaws.

Players that enter into a town where they are considered to be an outlaw will see a warning-title-message informing them. If a player is online and they are made into an Outlaw they will see a message in chat. 

Outlaws can be jailed if they die in the town where they are considered to be an outlaw. This requires the `jail.is_jailing_attacking_outlaws` option in the Towny config.yml to be set to true. It also requires the person who's done the killing to have the towny.outlaw.jailer permission node. It also requires the town to own at least one jail plot. By default only Mayors, Assistants and Sheriff ranks have the towny.outlaw.jailer permission node. 

A town member can view their town's outlaw list using `/town outlawlist`. Anyone can view any town's outlawlist using `/town outlawlist {townname}>/tt>  `

[]()Nations
-----------

A nation is a collection of towns (or just one town) with one town as the capital. The mayor of that capital is the king. A nation can join the war event, as well as ally other nations. A nation also has it's own bank. It can also tax the towns that belong to it. 

Nations can also have a spawn reached using `/nation spawn` which if the nation is considered 'Public' can be reached by nearly any non-enemy players. The nation spawn can be restricted to the capital in the config.yml at `global_nation_settings.capital_spawn` otherwise the spawn point can be anywhere in the nation. 

Two nations can decide to join in an alliance, which allows them to be protected from friendly fire, help on each others plots (if the plot's perm line allows allies,) and to help each other in war. As of 0.91.0.0, you may restrict nation alliances to be 2-way only. So that Nation A cannot consider Nation B an ally unless the Nation B also considers Nation A an ally. You may turn this setting on in the config: war.disallow_one_way_alliance, which defaults to false. 

Also, as of 0.91.0.0, you may restrict who can create, join and maintain a nation by requiring a minimum number of residents. See the Global Town Settings section of the config.yml. 

As of 0.92.0.0, you may set a maximum distance between the nation capital and towns which are allowed to join the nation. See the Global Town Settings section of the config.yml. 

As of 0.93.0.0, nations can grant a NationZone which surrounds the towns which are members. This is enabled at `global_nation_settings.nationzone.enable` in the config.yml. NationZones are just like normal wilderness except the only players which can modify the area are members of the nation. This can be useful to prevent greifing near to towns who have a nation. NationZones can be increased in size by increasing the population of the nation using the NationLevels in the config.yml, you can optionally make the capital town have a larger NationZone. NationZones can be disabled during war time in the config.yml at `global_nation_settings.nationzone.war_disables`. 

Nations can grant many perks to their towns which can increase as the nation population increases, these include:

-   Bonus townblocks to be claimed.
-   Cheaper town upkeep costs.
-   Larger surrounding NationZones.
-   An increased outpost limit.

[]()Kings
---------

Kings lead Nations and are the mayor of the capital city. Kings have their permission nodes configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml. Kings can decide which ranks their residents fall into, in their nation. This can be a Nation Assistant or any other custom ranks created by the server admin in the townyperms.yml file. Kings can see the available ranks using `/nation ranklist` command. Players are ranked using `/nation rank {add|remove} {playername} {rankname}`. A player can have more than one rank assigned, allowing admins to create diverse nation-roles such as bankers, inviters for the king to choose for their trusted residents. 

Kings have the ability to set titles (prefixes) and surnames (postfixes) to the residents of the towns they have in their nation. This is done with:

-   /nation set title {name} titlegoeshere
-   /nation set surname {name} surnamegoeshere

Typing the commands with nothing after the player's name resets the title or surname to blank.

[]()Configuring Townyperms.yml and the Roles of the Ranks Within
----------------------------------------------------------------

As of Towny 0.82.0.0 Towny has a permission configuration file, [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml, located in the towny\settings\ folder. This system pushes permissions directly to Bukkit and works along side all other perms plugins. It allows you to define sets of permissions based upon a players status (nomad/resident/mayor/king). You can also assign additional permissions based upon any assigned town/nation ranks (assistant/vip etc). This system is not limited to Towny permission nodes. You can assign any permissions for any plugins in its groups. This file allows admins to decide what each player-rank can do. Some ranks are assigned automatically:

-   Players without towns are Nomads.
-   Players in towns are Residents.
-   Owners of towns are Mayors.
-   Owners of nations are Kings.

Some ranks are assigned by Mayors or Kings, and supplement the ranks the players already have:

-   Mayors can make a resident a Town Assistant.
-   Kings can make a resident a Nation Assistant.
-   Mayors and kings can grant admin-created ranks, allowing for diverse customization.
    -   A player can attain many Supplemental ranks from their mayor or king, allowing for diverse nation/town-roles.
    -   Examples of this would be town-builders, town-bankers, nation-bankers, town-inviters, etc.

A resident of a town can see the ranks within their town using `/town ranklist`. A mayor can use `/town rank {add|remove} {playername} {rankname}` to give a player a new rank within their town. A king can use `/nation rank {add|remove} {playername} {rankname}` to give a player a new rank within their nation.

[]()Configuring Mayor and King Titles, Town and Nation Names
------------------------------------------------------------

Towny gives you the ability to customize the naming scheme applied to Mayors, Kings, Towns, Capital Cities and Nations. This is done with two sections in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) town_level:

-   The basic layout of the townLevel lines are as follows:

```
    -   upkeepModifier: 1.0
        namePostfix: ' (Settlement)'
        mayorPrefix: 'Hermit '
        mayorPostfix: ''
        townBlockLimit: 16
        namePrefix: ''
        numresidents: 1
        townOutpostLimit: 1
    -   upkeepModifier: 1.0
        namePostfix: ' (Hamlet)'
        mayorPrefix: 'Chief '
        mayorPostfix: ''
        townBlockLimit: 32
        namePrefix: ''
        numResidents: 2
        townOutpostLimit: 2
```

These are read as follows:

-   upkeepModifier: 1.0 - Use a higher multiplier to increase the upkeep as towns get more residents (unless you use `town_plotbased_upkeep:true` in which case it is based off of plot-count rather than resident-count. Unless you've also got `town_plotbased_upkeep_affected_by_town_level_modifier:true` )
-   namePostfix: ' (Settlement)' - This is added to the end of the town name.
-   mayorPrefix: 'Hermit ' - This is added to the front of the mayor's name.
-   mayorPostfix: '' - This is added to the end of the mayor's name.
-   townBlockLimit: 16 - This decides how many townblocks a town gets, it is only used if town_block_ratio: '0' is set in the config.yml.
-   namePrefix: '' - This is added to the front of the town name.
-   numresidents: 1 - This is how many residents a town needs to have in order to attain the prefixes/postfixes of the townlevel.
-   townOutpostLimit: 1 - This is how many outposts a Town can claim,

-   The two levels above are for towns of 1 and 2 residents. When a town is created the mayor's new town has (Settlement) added to the end of his townname and he is given the prefix of Hermit. When the mayor gets a second resident his town becomes Townname (Hamlet) and he receives the prefix of Chief.

nation_level:

-   The basic layout of the nationLevel lines are as follows:

```
        -   capitalPostfix: ''
            upkeepModifier: 1.0
            namePostfix: ' (Nation)'
            kingPrefix: 'Count '
            townBlockLimitBonus: 10
            namePrefix: 'Federation of '
            numResidents: 10
            capitalPrefix: ''
            kingPostfix: ''
            nationTownUpkeepModifier: 1.0
            nationZonesSize: 1
            nationBonusOutpostLimit: 2
        -   capitalPostfix: ''
            upkeepModifier: 1.0
            namePostfix: ' (Nation)'
            kingPrefix: 'Duke '
            townBlockLimitBonus: 20
            namePrefix: 'Dominion of '
            numResidents: 20
            capitalPrefix: ''
            kingPostfix: ''
            nationTownUpkeepModifier: 1.0
            nationZonesSize: 2
            nationBonusOutpostLimit: 3
```

These are read as follows:

-   capitolPostfix: '' - This is added to the end of the capital city of the nation.
-   upkeepModifier: 1.0 - Use a higher multiplier to increase the upkeep as nations get more residents (unless you use `town_plotbased_upkeep:true` in which case it is based off of plot-count rather than resident-count.)
-   namePostfix: ' (Nation)' - This is added to the end of the nation name.
-   kingPrefix: 'Count ' - This is added to the front of the nation-leader.
-   townBlockLimitBonus: 10 - This is the number of bonus townblocks given to a town when they join a nation.
-   namePrefix: 'Federation of ' - This is added to the front of the nation name.
-   numResidents: 10 - This is how many residents a nation must have to receive the prefixes and postfixes of the nation level.
-   capitalPrefix: '' - This is added to the front of the capital city of the nation.
-   kingPostfix: '' - This is added to the end of the nation-leader's name.
-   nationTownUpkeepModifier: 1.0 - Joining a nation will lower/raise how much town upkeep your town pays. This multiplier is calculated after all other multipliers have their effect on the town upkeep cost. When set at 1.0, there is no change to upkeep.
-   nationZonesSize: 2 - How many plots wide the NationZone is surrounding a town.
-   nationBonusOutpostLimit: 2 - How many outposts more that the town can claim on top of it's usual limit.

------------------------------------------------------------------------

[]()How Towns Grow
==================

[]()Starting a Town
-------------------

Mayors start towns using the command /town new {townname}. The townblock they are standing in will be the home block for the town, the exact spot/position will be the spawn point for the town. More townblocks can be claimed using /town claim. These townblocks need to be directly adjacent to already claimed townblocks.

[]()Joining Towns
-----------------

There are two ways to join towns, the first is by being invited by a Mayor or a Town assistant. The second it by joining an open town. Mayors and assistants can add players to their town with the command /town add {playername}. The player will receive a prompt to either /accept or /deny the invitation. Mayors can set their towns to open using /town toggle open. A player who isn't in a town already can use the command /town join {townname} to join open towns. When residents join towns they increase the number of townblocks accessible to the mayor for claiming.

------------------------------------------------------------------------

[]()Plot System of Land Ownership
=================================

[]()Town Blocks
---------------

Towny provides a server admin a hands-off approach to block-protection. Block protection is broken down into plots of land, called townblocks, which by default are 16x16x256 (the full height of the world.) Townblocks are claimed by town mayors who can then sell/give individual plots to their town's residents.

As of Towny 0.95.1.0 it is possible to store MetaData on a townblock, see [here](https://github.com/TownyAdvanced/Towny/wiki/Configuring-Metadata-in-Towns-and-Townblocks) for details.

### []()Town Block Size

You change the townblock size in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `town_block_size: 16`. **Changing this value is suggested only when you first install Towny.** Doing so after entering data will shift things unwantedly. Using smaller value will allow higher precision, at the cost of more work setting up. Also, extremely small values will render the caching system used by Towny useless. Each cell is (town_block_size x town_block_size x 256) in size, with 256 being from bedrock to clouds.

### []()Claiming Townblocks

Towns' residents can claim townblocks for the town as long as they have the right permission nodes. By default this is restricted to Mayors and people with the Assistant rank. The player uses `/town claim` or `/town claim #` or `/town claim rect|circ #` or `/town claim auto` to claim townblocks for their town. 

- /town claim - will claim one plot, where the player is standing.
- /town claim # - will claim a square with a radius equal to the given #.
- /town claim rect # - will claim a square with a radius equal to the given #.
- /town claim circ # - will claim a circle with a radius equal to the given #.
- /town claim auto - will claim all possible townblocks in a square shape.

Using the `/town` command will list how many townblocks are available to be claimed. 

As of 0.95.0.0 you may set a refund amount for unclaiming townblocks at `economy.new_expand.price_claim_townblock_refund`, it is not recommended that this be set at or higher than the cost to claim a townblock.

As of 0.95.0.0 you may make the cost of claiming townblocks increase at `economy.new_expand.price_claim_townblock_increase`. When set to 1 this is deactivated. 1.3 means +30% to every bonus claim block cost. Cost increase can be seen in `/towny prices` output.

### []()Setting How Many Town Blocks A Town Receives

You can change how many town blocks a town gets to claim. This is done in two places. Towny checks first in the config.yml at ` town_block_ratio: 8 ` and by default gives a town 8 townblocks per resident. You can override this by setting ` town_block_ratio: 0 ` and using the townLevel section of the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) More information on the townLevel line and how to configure it is [here.](#Configuring_Mayor_and_King_Titles,_Town_and_Nation_Names)

### []()Buying Townblocks

Mayors can buy townblocks using /town buy bonus {amount}. An admin can set a maximum limit on how many townblocks a town can buy in the config.yml at `max_purchased_blocks: '0'`. The price of a bought townblock is also set in the config.yml at `price_purchased_bonus_townblock: '25.0'`. The price can be configured to increase with each purchase using the `price_purchased_bonus_townblock_increase: '1.0'` config setting. Using this feature, mayors can grow their town without needing new residents. Increasing costs can be seen in `/town buy bonus` output.

[]()Plot Types
--------------

Players can use `/town plots {townname}` to view the counts of various plot types in a town. Towny post-0.75 has added plot types besides the default. This is to give mayors more control over their towns. 

As of Towny 0.95.1.0 there is a configurable cost to setting plot types. The plot types are as follows:

### []()Default Plots

These plots do not need any specific command to be designated. They are put up for sale with `/plot forsale {$$}`. A plot which is not of default type can be reset to a default plot with `/plot set reset`.

### []()Shop Plots

Shop plots are designated with `/plot set shop` A mayor can use `/town set shopprice {$$}` to set how much shop plots are sold at by default. This can be overridden when a mayor puts the actual plot up for sale with `/plot forsale {$$}`. A mayor can also charge an additional shoptax with `/town set shoptax {$$}`. This tax is charged in addition to the normal plottax.

### []()Arena Plots

Arena plots are designated with `/plot set arena.` PVP is on all the time in arena plots as well as friendly-fire damage. Town health regen is also disabled in arena plots.

### []()Embassy Plots

Embassy plots are designated with `/plot set embassy`. A mayor can use /town set embassyprice {$$} to set how much embassy plots are sold at by default. This can be overriden when a mayor puts the actual plot up for sale with /plot forsale {$$}. A mayor can also charge an additional embassytax with /town set embassytax {$$}. This tax is charged in addition to the normal plottax. An embassy plot can be bought by any player, whether they are in a town or not, as long as they have the `towny.command.plot.claim` permission node. The townblock remains owned by the host-town and a mayor from the host-town can take the plot from the owner at any time. Embassy plots can also be changed into shop plots, allowing for larger shop towns, where many different towns' players can set up shops. When a player leaves a town they do not lose ownership of their plots if those plots are set to be Embassy plots.

### []()Wilds Plots

Wilds plots are designated with `/plot set wilds` A wilds plot allows residents to destroy the blocks found on the wild ignore ID list. This includes ores, trees, flowers, mushrooms and other harvestable blocks by default. It does not include stone, dirt, grass and other terrain blocks. It is useful for creating tree farms, and protecting the terrain around a town, while still allowing residents to cut trees and explore caves. Setting up wilds plots can be slightly complex, here are instructions.

1.  Navigate to your towny\data\worlds\WORLDNAME.txt file
2.  Set:
    -   unclaimedZoneBuild=false
    -   unclaimedZoneDestroy=false

3.  Configure the unclaimedZoneIgnoreIds line to include the blocks you would like players to break/build.
4.  Go to the Wilds plots you can set using /plot set wilds
5.  Use '/plot set perm resident build on' and '/plot set perm resident destroy on' to enable residents to break/build using only the blocks in the ignoreIDs list.

You can also set allies or outsiders perms if you want non-town-members to use the Wilds plots.

### []()Inn Plots

Inn plots are designated with `/plot set inn` An Inn plot allows anyone to use a bed to set their '/res spawn' and spawn on death. The Inn plot will still deny a player who is in a nation declared as an enemy by your nation. For them to function `deny_bed_use: 'true'` must be set in the config.yml

### []()Jail Plots

Jail plots are designated with `/plot set jail`

Players can become jailed if:
-   The player's mayor/sheriffs send them to jail.
-   An attacker who attacks a town which considers him an Enemy (Nation-relationship) dies in that Town. He is sent to the first available Jail plot of the defending town.
-   An attacker who attacks a town which considers him an Outlaw dies in that Town by a player with the towny.outlaw.jailer permission node. He is sent to the first available Jail plot of the defending town. In the config `jail.is_jailing_attacking_outlaws` must be true.

Jailed players become unjailed if:
-   they leave their town and become a nomad,
-   the mayor/sheriff unjails them,
-   the player pays a bail amount to the town which jailed them, (using: /resident jail paybail)
-   they manage to escape the jail plot and the town and get into Wilderness.

In addition:
-   Jailed players cannot teleport.
-   Jailed players cannot use Ender Pearls unless enabled in the config.
-   Jailed players who die are sent back to their prescribed jail plot.
-   Jailed players do not give monetary payouts when they are killed.
-   Jailed players show their jailed status in the /res [playername] screen, along with the town they are jailed in.
-   It is suggested you make a new town rank in the townyperms.yml called Sheriff, and give that rank the towny.command.town.toggle.jail node. Newly generated townyperms.yml files will contain this rank by default.
-   There is a list in the config at `jail.blacklisted_commands` where you can set a list of commands which jailed players cannot use.

### []()Farm Plots

Farm plots are designated with `/plot set farm` A Farm plot players to only build/destroy blocks designated in the Towny Config.yml at `global_town_settings.farm_plot_allow_blocks`. By default this list includes "LONG_GRASS, DOUBLE_PLANT, YELLOW_FLOWER, RED_ROSE, PUMPKIN_STEM, MELON_STEM, BEETROOT_BLOCK, CARROT, POTATO, CROPS, MELON_BLOCK, PUMPKIN". 

Who can build/destroy these blocks is still determined by the plot's perm line seen in the /plot perm screen. This means that if B=rnao, anyone can plant/place the allowed blocks in the plot. If the B=r--- then only town residents can plant/place the allowed blocks. 

If admins want, they can add SOIL to the allowed blocks list, which will allow anyone allowed via the perm line to also make soil with a hoe. By default SOIL is not included and only admins/mayors/assistants will be able to create soil with a hoe. Towny already protects soil from being stomped into grass, so soil will only return to dirt if it is not irrigated. 

Farm plots also allow player to kill animals in the plot. In order to kill the configured animals list the player must be able to break wheat blocks on the plot. The list of animals is set in the config at global_town_settings.farm_animals. By default this list includes "PIG,COW,CHICKEN,SHEEP,MOOSHROOM".

### []()Bank Plots

Bank plots are designated with `/plot set bank` Bank plots can be used to limit town and nation bank depositing/withdrawing. By default this setting is off but can be turned on at `bank.is_banking_limited_to_bank_plots ` in the config.yml Bank plots are more useful for other plugins which would want to limit their banking features to within Towny bank plots.

[]()Outposts
------------

Normally townblocks are claimed around the home block, always connected to the town. To claim a townblock out in the wilderness, a mayor or assistant must claim an outpost. In order for players to claim outposts, the config must be set to `allow_outposts: true` and players require towny.town.claim.outpost in their permission node group. The outpost list can be viewed by using `/town outpost list` command. An admin can configure how many outposts a player can claim, this is set in your permissions plugin's info/option/meta node section using the towny_maxoutposts: {number} info node. [See here.](https://github.com/TownyAdvanced/Towny/wiki/Towny-Permission-Nodes) Alternatively, as of 0.93.0.0, you can use the TownLevels and NationLevel's maxoutpost values to give larger towns more outposts to claim, and bonus outposts to towns in nations. This requires enabling the feature in the config.yml at `global_town_settings.limit_outposts_using_town_and_nation_levels`.

An admin can also set a number of residents required by a town before they can claim outposts, using the `minimum_amount_of_residents_in_town_for_outpost` setting. By default there is no resident requirement. Outposts cannot be claimed too close to other home blocks, just like when a mayor starts a town they cannot be too close. The exact number is set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `min_distance_from_town_homeblock: 5`. In the default setting an outpost cannot be claimed within 5 townblocks of any other homeblock. You can also configure how close an outpost can get to any other town's plots using `town.min_distance_for_outpost_from_plot`. You can also set the cost of claiming an outpost in the config.yml at `price_outpost: 500.0`. Outposts can be teleported to, mayors set the spawn point of the outpost when they claim it or using '/town set outpost'. Players teleport to the outpost using '/town outpost x|name|name:x'

-   with x being a number 1 - however many outposts the town has
-   where name is the plot name of the outpost (seen in /t outpost list)
-   where name:1asdasda - useful for when a plot name begins with a number.

[]()Selling Land
----------------

Land is sold by Mayors to Residents that are a part of their town. `using_economy: true` must be set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) in order for costs to be applied. Mayors have a command used in game to set the cost of all the plots that are set for sale hence-forth.

-   `/town set plotprice {$} `
    -   This sets the cost of newly-set-for-sale plots, already set-for-sale plots keep their costs. If it is not set, the plots will cost $0 by default.

To put a plot up for sale a mayor, while standing in the plot, type /plot forsale {optional cost} The resident would then type /plot claim while standing in the plot to buy it.

[]()Using the Maps
------------------

The map in towny displays the grid system of plots. The map can be viewed once using `/towny map` one time or you can set the map to show every time you move from one block to another:

-   Use `/resident toggle map` to turn it on or off.

A large version of the map can be seen using /towny map big.

[]()Plot Regeneration & Unclaimed Plots
---------------------------------------

There are 4 options for affecting townblocks/plots.

### []()Reverting unclaimed townblocks to their original state on unclaim

When a town plot is unclaimed (by a player or through upkeep) it will slowly begin to revert to a pre town state. Blocks will slowly change back to whatever blocks we're present at the moment the town block was claimed. A townblock must revert completely before the snapshot of the townblock is removed. If townblock is reclaimed mid-revert, a new snapshot is not taken and if the townblock is unclaimed again it will revert to the original snapshot.

-   Disabling this feature is done in the towny\data\worlds\worldname.txt @ `usingPlotManagementRevert=false`
-   or by using '/tw toggle revertunclaim' while standing in the world you want to toggle it in.
-   Disabling this feature for new worlds is done in the config at new_world_settings.plot_management.revert_on_unclaim.enabled

You can configure certain block types you don't want restored to prevent players exploiting regen for diamond ores.

-   Block types to not restore are configured in block_ignore in the worlds txt file data/worlds/worldname.txt
-   Defaults for new worlds are set in the config at new_world_settings.plot_management.revert_on_unclaim.block_ignore:

### []()Deleting pre-defined blockIDs on unclaim

When a town plot is unclaimed (by a player or through upkeep) block IDs matching a list will be deleted within that townblock. This can be useful for deleting all signs within a townblock, ensuring any chests locked with Lockette or Deadbolt signs are unlocked.

-   Disabling this feature is done in the towny\data\worlds\worldname.txt @ `usingPlotManagementdelete=false`
-   Disabling this feature for new worlds is done in the config at new_world_settings.plot_management.block_delete.enabled

You can configure the list of Material names to be removed on a per-world basis.

-   The blockIDs listed in the towny\data\worlds\worldname.txt @ `plotManagementDeleteIds=` will be removed from the townblock.
-   Defaults for new worlds are set in the config at new_world_settings.plot_management.block_delete.unclaim_delete

### []()Plot-Owners' and Mayors' /plot clear command

A feature available only to Town Mayors on public town land: /plot clear. This command is meant to be used after a plot was personally owned by a resident, who either moved to another plot or left town. By default this list includes only signs, useful for mayors to remove sign-protection on doors, chests, furnaces, dispensers and trapdoors given via Lockette or Deadbolt.

-   Disabling this feature is done in the in the towny\data\worlds\worldname.txt @ `usingPlotManagementMayorDelete=false`
-   Disabling this feature for new worlds is done in the config at new_world_settings.plot_management.mayor_plotblock_delete.enabled

You configure the list of Material names to be removed when this command is used.

-   The list of blockIDs is listed in the towny\data\worlds\worldname.txt @ `plotManagementMayorDelete=ACACIA_SIGN,BIRCH_SIGN,DARK_OAK_SIGN,JUNGLE_SIGN,OAK_SIGN,SPRUCE_SIGN,ACACIA_WALL_SIGN,BIRCH_WALL_SIGN,DARK_OAK_WALL_SIGN,JUNGLE_WALL_SIGN,OAK_WALL_SIGN,SPRUCE_WALL_SIGN`
-   Defaults for new worlds are set in the config.yml at new_world_settings.plot_management.mayor_plotblock_delete.mayor_plot_delete

As of Towny 0.79.1.0, players can use this command within plots they personally own.

### []()Wilderness Regeneration

A simple wild_revert_on_mob_explosion option. Will regenerate explosions on a timer. As of Towny 0.79.1.0 You can now add any entities here you want explosions to revent for in the wilderness (includes Creeper,EnderCrystal,EnderDragon,Fireball,SmallFireball,TNTPrimed). These settings are copied to the individual world files, so you must make changes per world.

-   Disabling this feature is done in the in the towny\data\worlds\worldname.txt @ `usingPlotManagementWildRegen=true`
-   or by using '/tw toggle revertexpl' while standing in the world you want to toggle it in.
-   Disabling this feature for new worlds is done in the config at new_world_settings.plot_management.wild_revert_on_mob_explosion.enabled

You can configure how quickly the blocks will regenerate, specifically how much time in between each block being reverted.

-   The timer is changed in the towny\data\worlds\worldname.txt @ `usingPlotManagementWildRegenDelay=5`
-   The default for new worlds is set in the config.yml at new_world_settings.plot_management.wild_revert_on_mob_explosion.delay

------------------------------------------------------------------------

[]()How Towny Lets Players Protect Their Blocks
===============================================

Towny's genius is the way it lets players protect themselves. An admin doesn't need to go around protecting land for players, and players can't run rampant claiming massive amounts of land without working for it and building their towns. The first concept you need to digest are the 4 perm-types and 3 groups.

[]()Towny Plot Perms
--------------------

There are 4 permission-type values, which can be set for personal plots and for town plots as well (town permissions can be set by the mayor and affect plots who are not owned by any player.) The basic command for this is either `/resident set perm` or `/town set perm` followed by the proper flags for each permission. Available in Towny 0.77.0.0 and onward are per-plot permissions. Plots start with the default settings for plot perms (be it a resident-owned or town-owned plot,) but the owner of the plots can set different perms to different plots. To view a plots perm type `/plot perm` and to set a plots' perms use `/plot set perm`. Default permissions are viewable by typing either `/resident` for personal plot perms or by typing `/town` for town permissions.

As of Towny 0.95.1.0 there is an added Perm Group for plots, personally-owned plots have a Town group & town-owned plots have a Nation group.

### []()Perm-Types

The 4 permission-types available are Build, Destroy, Switch and Itemuse.

-   Build allows players to add blocks in your town/plot.

<!-- -->

-   Destroy allows players to remove blocks in your town/plot.

<!-- -->

-   Switch covers the use of:
    -   dispensers,
    -   noteblocks,
    -   chests,
    -   furnaces,
    -   wooden and iron doors,
    -   levers,
    -   gold, iron, stone and wood pressure plates,
    -   stone buttons,
    -   trapdoors,
    -   jukeboxes,
    -   redstone repeaters,
    -   gates,
    -   trapped chests,
    -   redstone comparators,
    -   beacon blocks,
    -   hoppers,
    -   droppers,
    -   item frames,
    -   Accessing minecart hoppers, minecart chests, minecart furnaces.
    -   Shulker boxes
    -   .... or any other type of block which is clicked on in some manner.

<!-- -->

-   Itemuse covers the use of:
    -   water and lava buckets,
    -   empty buckets,
    -   lighters,
    -   bonemeal and other dyes,
    -   enderpearls,
    -   placing/destroying all minecart types,
    -   firecharges,
    -   using bottles.
    -   .... or any other type of item which is used in some manner.

### []()Perm-Groups

Each permission-type has 4 perm-groups to which the pemissions can be set for, these are displayed on your `/resident` perm line as FTAO and stand for Friend, Town, Ally, Outsider. For residents the Friend group consists of a player's friend list; Town consists of townmembers. For towns the perm line reads RNAO, with R representing Residents (players in that town); Nation representing residents of towns in your nation. Mayors need to use `/t set perm resident blah on/off` instead of `/t set perm friend blah on/off` The other groups are:

-   Ally
    -   On personally-owned plots allies consist of players in your nation and players in your nation's allies.
    -   On town-owed plots it is players in your nation's allies.
-   Outsiders
    -   Players who are not part of your town or nation or nation's allies.

[All commands are found on the Wiki's Commands page.](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands)

### []()Setting perms in-game with commands

Setting perms for your town's public land or your personal plots is easy! There are two distinct levels of protection provided by towns. First are the town blocks, protected because they are part of a town and not owned by anyone. When you enter one of these plots from the wilderness or an owned plot the notification will show "~ Unowned". Mayors are able to set the permission for unowned plots using the the `/town set perm` command. A full list of commands is on the [commands](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands) page, here are some examples:

-   /town set perm {on/off} - This turns on or off all permissions for all perm-types and all perm-groups.
-   /town set perm ally {on/off} - This turns on or off all perm-types and for the town's allies (Nations to which their nation is allied with.)
-   /town set perm resident build {on/off} - This turns on or off all permissions for building done by residents of the town.

Second are the town blocks owned personally by a resident of a town. A resident is able to set the permission for unowned plots using the the `/resident set perm` command. A full list of commands is on the [commands](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands) page, here are some examples:

-   /resident set perm {on/off} - This turns on or off all permissions for all perm-types and all perm-groups.
-   /resident set perm friend {on/off} - This turns on or off all permissions for the resident's friend list.
-   /resident set perm ally {on/off} - This turns on or off all permissions for all perm-types to the resident's ally list. This consists of the nation's fellow towns and their nation's allied nations.
-   /resident set perm outsider switch {on/off} - This turns on or off permissions for switch use by outsiders.

Lastly, don't forget those are just the defaults for plots, any owned plot can be set with it's own individual perms:

-   /plot set perm {on/off} - This turns on or off all permissions for all perm-types and all perm-groups on the plot which is being stood in.
-   /plot set perm friend {on/off} - This turns on or off all permissions for the resident's friend list on the plot which is being stood in.
-   /plot set perm ally {on/off} - This turns on or off all permissions for all perm-types to the resident's ally list. This consists of the nation's fellow towns and their nation's allied nations. This affects the plot which is being stood in.
-   /plot set perm outsider switch {on/off} - This turns on or off permissions for switch use by outsiders on the plot which is being stood in.

Mayors can changed the protection of their town with the following commands:

-   /town toggle explosion
-   /town toggle fire
-   /town toggle pvp
-   /town toggle mobs

Mayors and Residents can change each of their plots individually using these commands:

-   /plot toggle explosion
-   /plot toggle fire
-   /plot toggle pvp
-   /plot toggle mobs

Per-plot toggles are overridden by a mayor's town toggles. The preceding commands by themselves will change the perm line seen from /town or /res. They will also change any plots that were using the previously-set default perm line (town-owned or player-owned plots.) They will not change plots which were not set to the default perm line see in /town or /res. In order to change all plots a mayor or resident must use the following command, which will propagate the current perm line seen in /town or /res to ALL plots owned by the town or resident.

-   /res set perm reset - Propagates the perm line in /res to ALL plots owned by that resident.
-   /town set perm reset - Propagates the perm line in /town to ALL town-owned plots owned by that town.
-   These commands also affect the /town toggle and /plot toggle settings.

[]()Protection Additions Found in Towny Advanced
------------------------------------------------

New in Towny Advanced (0.72+) are three new protection types, anti-explosion and anti-firespread and piston-protection. On the town level, a mayor can set these flags using:

-   /town toggle explosion
-   /town toggle fire

Explosion protection stops all explosions. This stops TNT, TNT cannons and creeper explosions. Firespread protection stops all fires from spreading, including lava, lightning and lighters. Piston-protection allows pistons to operate between similarly owned townblocks or wild areas.

As of 0.95.0.0 Animal Luring (drawing animals' attention using their preferred food,) is controlled in the following fashion: In town-owned plots and in the wilderness, luring is not stopped. In personally-owned resident plots, the player must be able to break dirt in the plot to lure an animal.

As of 0.95.1.0 Villagers are protected from evil-doers.

------------------------------------------------------------------------

[]()How Towny Controls PVP Combat
=================================

Towny affects PVP combat, deciding who can be damaged where and by whom.

[]()Friendly-fire
-----------------

By default Towny disables friendly-fire between townmembers, nationmembers and residents whose nation considers the attacker's nations an ally. Friendly fire can be disabled in the config.yml `friendly_fire: 'true'` by setting it to false. The friendly-fire settings affects all worlds in which towny is enabled.

[]()Plot, Town and World PVP Settings
-------------------------------------

Plots, Towns and Worlds all have PVP settings, here is how they work.

### []()World PVP Settings

World settings for PVP are controlled using in-game commands

-   /townyworld toggle pvp
    -   This command disables and enables PVP world-wide. If you type `/tw` you will see will see a red {PVP} next to the name of the world at the top of the output. If PVP is off in the world, no pvp combat can occur, even in Arena plots.
-   /townyworld toggle forcepvp
    -   This command forces pvp on world-wide, disregarding any plot or town pvp settings. Friendly-fire is still obeyed.
    -   As of Towny 0.93.0.0 there is a new config.yml option at `global_town_settings.homeblocks_prevent_forcepvp` which can be enabled to stop forcepvp from affecting town homeblocks.
    -   There is a way to override forcing pvp on in towns. Navigate to the Towny\Data\Towns\ folder and open the townname.txt file. Find the adminDisabledPvP flag and set it to `adminDisabledPvP=true` This is useful for forcing pvp on worldwide but leaving it off in a spawn-town.

### []()Town PVP Settings

Towns pvp settings are controlled using this in-game command

-   /town toggle pvp
    -   This toggles pvp on and off town-wide.
    
Additionally, admins have `/ta town {townname} toggle forcepvp` which will set a town's secret AdminEnabledPVP setting to true or false.

### []()Plot PVP Settings

Plots can have their pvp status controlled individually with this in-game command

-   /plot toggle pvp
    -   This toggles a single plot's pvp status.

------------------------------------------------------------------------

[]()Money
=========

[]()Taxes and Upkeep
--------------------

Taxes and Upkeep are two separate functions with to different results. `using_economy: true` must be set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) in order for Taxes and Upkeep to be applied. Taxes and Upkeep are charged at the same time, each 'Towny Day' or each time an admin type `/townyadmin newday`. The time of a 'Towny Day' can be set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `day_interval: 1d` and by default is 24 real-life hours. Any one can check how long until the next day starts by using /towny time.

### []()Taxes

Taxes are collected on the town level from residents and on the nation level from towns. The [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) has an entry to turn taxation on or off at `daily_taxes: true` Any player can check the taxes which apply to them with the in-game command /res tax Town mayors can use two commands to set their tax-rates.

-   /town set taxes {$}
    -   This can be either a flat rate (ex: 10) or a percentage.
        -   Toggling taxes from flatrate to percentage is done using /town toggle taxpercent
        -   Flatrate:
            -   This charges each resident of a town the same amount. Setting it to 10 would charge each resident each 'Towny Day'.
            -   If a resident can't pay his town tax when using flatrate taxation then he is kicked from the town.
        -   Percentage:
            -   This charges a player a percentage of their money. If a player has no money left, he pays no taxes and is not kicked from the town.
-   /town set plottax {$}
    -   This charges each resident of a town for each plot they own. Setting it to 10 would charge Miner Steve 40 dollars if he owned 4 plots.
    -   If a resident can't pay his plot tax he loses his plot.

Nation leaders can use one command to set a tax on their towns.

-   /nation set taxes {$}
    -   This charges each town that is a member of the nation. Setting it to 100 would charge each town's townbank 100 each 'Towny Day'.
    -   If a town can't pay it's tax then it is kicked from the nation.

Admins can set options in the config.yml for controlling maximum/minimum tax amounts on towns. There is max_tax_amount which defaults to 1000 and max_tax_percent which defaults to 25%. Which one is used depends on how the town is taxing, a flat rate or by percentage. `town.default_taxes.minimumtax` sets the minimum tax required when mayors use the '/t set taxes' command. There are also settings for default taxes in new towns, which can set default plottax, embassy taxes, shop taxes.

#### []()How to pay landowners

A new option added to post-0.78.0.0 versions of Towny allows you to pay players money each day, based on the number of plots they own. To use this do the following:

-   Set a negative town upkeep and enable `use_plot_payments: true` in the config.yml
-   At a new day the negative upkeep will be used to calculate the towns upkeep, but instead of taking it from the town, it will be divided between the plot owners.
-   These funds are paid by the server, not the town.

### []()Upkeep

Upkeep collection can be set on towns and on nations separately. Upkeep money is taken from townbanks and nationbanks and removed from the game. You can set the upkeep amounts to negative numbers to pay towns and nations instead of charging them. Upkeep is used by a server admin to remove inactive towns and nations from the server. Setting the upkeep to a negative number gives the town or nation-banks that amount each new day. Upkeep is set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) with two flags:

-   `price_nation_upkeep: 100.0`
    -   The server's daily charge on each nation. If a nation fails to pay this upkeep, all of it's member towns are kicked and the Nation is removed.
-   `price_town_upkeep: 10.0`
    -   The server's daily charge on each town. If a town fails to pay this upkeep, all of it's residents are kicked and the town is removed.

Upkeep can be modified in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) to affect different-sized towns differently. There are two ways to calculate the upkeep using the upkeep modifier found in the townLevel and nationLevel lines. By default the townLevel and nationLevel lines use the resident-count to determine upkeep via the upkeep modifier. The other option is to base it off plot-count rather than resident count. If you would like to set it based on plot-count set `town_plotbased_upkeep:true` in your config.yml. More information on the townLevel line and how to configure it is [here.](#Configuring_Mayor_and_King_Titles,_Town_and_Nation_Names)

As of 0.95.0.0 you may now charge nations upkeep per-town at `economy.daily_taxes.nation_pertown_upkeep`. Uses total number of towns in the nation to determine upkeep instead of nation level (Number of Residents), calculated by (number of towns in nation X price_nation_upkeep). If `economy.daily_taxes.nation_pertown_upkeep_affected_by_nation_level_modifier` is true, the nation levels upkeep modifier will have an affect.

As of 0.95.0.0 you may now penalize towns which have claimed more townblocks than they are allowed. By setting `economy.daily_taxes.price_town_overclaimed_upkeep_penalty` to true and putting an amount at `economy.daily_taxes.price_town_overclaimed_upkeep_penalty` towns will be charged this amount per townblock they are overclaimed by, in addition to their normal upkeep.

[]()Town and Nation Banks
-------------------------

Towns and Nations both have banks, to which any resident can deposit money but only town mayors and nation kings (and assistants) can withdraw from. Any money collected via taxes is deposited to the nation/town bank. When a town needs money, to claim a townblock or an outpost, it is taken from the townbank. Since mayors and kings can deposit money to their respective banks, some servers will find that mayors and kings shield their wealth from plugins that take a players money for dying from pvp combat. To prevent townbanks from being exploited an admin can use two options:

-   Admins can set a cap on a town/nation banks at town_bank_cap and nation_bank_cap in the config.yml.
-   Admins can use '/ta toggle withdraw' to prevent mayors and kings from removing money from their bank.

As of Towny 0.82.0.0 and on-wards the cap on banks is a hard cap and does not allow any money to be added to the town/nation banks if it would put the bank over the limit. This does not remove money from town/nation banks which are already over the limit.

------------------------------------------------------------------------

[]()Chat
========

[]()PlaceHolderAPI Support
--------------------------

As of 0.95.0.0 Towny natively supports PlaceholderAPI, and provides you with the following placeholders:

- %townyadvanced_town% - displays town name (if they have one.)
- %townyadvanced_town_formatted% - displays long-form town name (if they have one.)
- %townyadvanced_nation% - displays nation name (if they have one.)
- %townyadvanced_nation_formatted% - displays long-form nation name (if they have one.)
- %townyadvanced_town_balance% - displays town bank value.
- %townyadvanced_nation_balance% - displays nation bank value.
- %townyadvanced_town_tag% - displays town tag (if they have one.)
- %townyadvanced_town_tag_override% - displays town tag (if they have one,) or the full town name.
- %townyadvanced_nation_tag% - displays nation tag (if they have one.)
- %townyadvanced_nation_tag_override% - displays nation tag (if they have one,) or the full nation name.
- %townyadvanced_towny_tag% - displays town and nation tags.
- %townyadvanced_towny_tag_override% - displays town and nation tags if they exist, falling back to names if they don't.
- %townyadvanced_towny_tag_formatted% - displays town and nation tags if they exist, falling back to long-form names if they don't.
- %townyadvanced_title% - displays king-granted title.
- %townyadvanced_surname% - displays king-granted surname.
- %townyadvanced_towny_name_prefix% - displays mayor and king prefix.
- %townyadvanced_towny_name_postfix% - displays mayor and king postfix.
- %townyadvanced_towny_prefix% - displays title if it exists, falls back to mayor and king prefixes.
- %townyadvanced_towny_postfix% - displays surname if it exists, falls back to mayor and king postfixes.
- %townyadvanced_towny_colour% - used to show colours before nomads, residents, mayors and kings. (Set in the config.yml.)
- %townyadvanced_town_residents_amount% - number of residents in a town.
- %townyadvanced_town_residents_online% - number of residents in a town that are currently online.
- %townyadvanced_town_townblocks_used% - number of townblocks claimed by a resident's town.
- %townyadvanced_town_townblocks_bought% - number of townblocks bought by a resident's town.
- %townyadvanced_town_townblocks_bonus% - number of bonus blocks given to a resident's town.
- %townyadvanced_town_townblocks_maximum% - number of townblocks a town has available to claim.
- %townyadvanced_town_townblocks_natural_maximum% - number of townblocks a town has available to claim, not counting bonus/bought townblocks.
- %townyadvanced_town_mayor% - a resident's town's mayor's name.
- %townyadvanced_nation_king% - a resident's nation's king's name.
- %townyadvanced_resident_friends_amount% - number of friends a resident has.
- %townyadvanced_nation_residents_amount% - number of residents in a resident's nation.
- %townyadvanced_nation_residents_online% - number of residents in a resident's nation that are currently online.
- %townyadvanced_nation_capital% - name of a resident's nation's capital.


[]()Townychat.jar
-----------------

If you want Towny’s variables in chat, or the town/nation channels, you must download and install TownyChat.jar.

### []()Using TownyChat with Other Chat Plugins

To use Towny and another Chat plugin follow these instructions:

-   Go into the Towny [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml and locate: `modify_chat.enable:` and be sure to set it to true like this: `modify_chat.enable: 'true'`
-   Now add Towny’s chat variables to your chat plugins config. The variables can be found in the comments of the [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml
-   Make sure that no players have the towny.chat.general node or they'll be talking in the towny channel and not your other chat plugins default chat channel. You might need to negate the permission node for your admins if they have the `'*'` in their permission nodes.

Examples:

-   iChat:
    -   ingame-format: '[+prefix+group+suffix&f]{townytag} {townycolor}{townyprefix}+displayname{townypostfix}'
-   mChat:
    -   mchat-message-format: '{townytag} +p{townycolor}{townyprefix}+dn{townypostfix}+s&f: +m'
-   RoyalChat:
    -   [Guide on configuring towny prefixes in RoyalChat](http://dev.bukkit.org/server-mods/royalchat/pages/configuration/)

### []()Using TownyChat Without Another Chat Plugin

To use Towny as your sole chat plugin follow these instructions:

-   Go into the Towny [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml and locate: `modify_chat.enable:` and be sure to set it to true like this: `modify_chat.enable: 'true'`
-   Configure the chat lines using the information found in the section below.

[]()Chatconfig.yml
------------------

The first config file for Towny's chat is the [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml found at \plugins\towny\settings\[ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml

### []()Towny chat formats

These are the pieces which can be used to make the Channel_format lines.

```
  {worldname} - Displays the world the player is currently in.
  
  {town} - Displays town name if a member of a town.
  {townformatted} - Displays town name (if a member of a town) using tag_format.town.
  {towntag} - Displays the formated town tag (if a member of a town) using modify_chat.tag_format.town.
  {towntagoverride} - Displays the formated town tag (if a member of a town and present) or falls back to the full name (using modify_chat.tag_format.town).
   
  {nation} - Displays nation name if a member of a nation.
  {nationformatted} - Displays nation name (if a member of a nation) using tag_format.town.
  {nationtag} - Displays the formated nation tag (if a member of a nation) using modify_chat.tag_format.nation.
  {nationtagoverride} - Displays the formated nation tag (if a member of a nation and present) or falls back to the full name (using modify_chat.tag_format.nation).
   
  {townytag} - Displays the formated town/nation tag as specified in modify_chat.tag_format.both.
  {townyformatted} - Displays the formated full town/nation names as specified in modify_chat.tag_format.both.
  {townytagoverride} - Displays the formated town/nation tag (if present) or falls back to the full names (using modify_chat.tag_format.both).
   
  {title} - Towny resident Title
  {surname} - Towny resident surname
  {townynameprefix} - Towny name prefix taken from the townLevel/nationLevels
  {townynamepostfix} - Towny name postfix taken from the townLevel/nationLevels.
  {townyprefix} - Towny resident title, or townynameprefix if no title exists
  {townypostfix} - Towny resident surname, or townynamepostfix if no surname exists
   
  {townycolor} - Towny name colour for king/mayor/resident
  {group} - Players group name pulled from your permissions plugin
  {permprefix} - Permission group prefix
  {permsuffix} - Permission group suffix.
  {permuserprefix} - Permission group prefix
  {permusersuffix} - Permission group suffix.
   
  {playername} - Default player name.
  {modplayername} - Modified player name (use if Towny is over writing some other plugins changes).
  {msg} - The message sent.

  {channelTag} - Defined in the channels entry in Channels.yml
  {msgcolour} - Defined in the channels entry in Channels.yml
```

Message spam control is set at spam_time: 0.5 The channel_formats section determines what each chat channel will look like. The tag_formats section determines what the tags will appear as. The colour section determines colours applied with {townycolor} for mayors, kings and residents. The modify_chat section is where you can disable all chat additions from Towny. You can also set per_world to true if you'd like to use the worlds: section to change chat lines' channels on a per-world basis.

[]()Chat Channels
-----------------

Chat Channels are set in Channels.yml found at \plugins\towny\settings\Channels.yml There are six chat channels by default in Towny, although an admin can create as many chat channels as they'd like in Channels.yml. Channels.yml allows you to set commands for joining and using each channel:

-   /g
    -   Put in from of text to speak in general/global chat, or without text afterwards to enter the channel.
-   /l or /lc
    -   Put in from of text to speak in local chat, or without text afterwards to enter the channel.
-   /tc
    -   Put in from of text to speak with members of your town only, or without text afterwards to enter the channel.
-   /nc
    -   Put in from of text to speak with members of your nation only, or without text afterwards to enter the channel.
-   /ac
    -   Put in from of text to speak with all members of your nation as well as any member of a nation you are allied with, or without text afterwards to enter the channel.
-   /a or /admin
    -   Put in from of text to speak in adminchat, or without text afterwards to enter the channel.
-   /m or /mod
    -   Put in from of text to speak in modchat, or without text afterwards to enter the channel.
-   /res set mode reset
    -   Reset chat mode to default chat.

The tags for each channel can be set, these are used in the [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml for {channelTag}. Permission nodes for each channel can be set. Ranges for each channel can be set:

-   -1 = no limits
-   0 = same world only
-   any positive value = limited range in the same world.

### []()Putting players into channels on join

Using the info|option|meta nodes provided by GroupManger, PEX and bPermissions it is possible to put users into chat channels upon joining the server. In the same section as prefix: and suffix: add a node towny_default_modes: '' Possible channels are general, town, nation, admin, mod and local. Example in group manager:

```
                groups:
                  Default:
                    default: true
                    permissions:
                    - general.spawn
                    inheritance: []
                    info:
                      prefix: ''
                      build: true
                      suffix: ''
                      towny_maxplots: 1
                      towny_default_modes: 'local'
                  Admins:
                    default: false
                    permissions:
                    - '*'
                    inheritance:
                    info:
                      prefix: ''
                      build: true
                      suffix: ''
                      towny_maxplots: -1  
                      towny_default_modes: 'admin'
```

[]()Kings' minions' prefixes and suffixes
-----------------------------------------

Kings of nations can use two commands to change the displayed chat names of their minions:

-   `/nation set title {resident} {text of prefix} `
    -   Adds a prefix to the player.
-   `/nation set surname {resident} {text of suffix} `
    -   Adds a suffix to the player.
-   A title/surname given to a mayor will override the MayorPrefix/MayorPostfix set in the townLevels of the config. He will still retain the colouring set on mayor names (default is light blue.)

[]()Spying on chat channels
---------------------------

Admins can spy on all chat channels by using the command `/towny spy` or `/res set mode spy`. Any player can be given the ability to spy by being given the permission node towny.chat.spy

------------------------------------------------------------------------

[]()Multiworld
==============

Towny has mutliworld support. Each world has a datafile located at /plugins/towny/data/worlds/worldname.txt and each world is listed in /towny/data/worlds.txt.

[]()World Toggles
-----------------

Towny can be turned off in a world in-game. While standing in a world type `/townyworld toggle usingtowny`. Other toggles:

-   claimable - Whether townblocks can be claimed by mayors in this world.
-   pvp - Whether PVP is on in the world.
-   forcepvp - Used to force pvp on in towns.
-   explosion - Used to force explosions on in towns.
-   fire - Used to force firespread on in towns.
-   townmobs - Used to turn off mobremoval in all towns. Restricted mobs are listed in the config.yml.
-   worldmobs - Toggles mobremoval in the wilderness. Restricted mobs are listed in the config.yml.
-   usingtowny - Turns towny off in a world.
-   revertunclaim - toggles the revert-on-unclaim setting for that world.
-   revertexpl - toggles the revert-on-explosion in the wilderness setting for that world.

------------------------------------------------------------------------

[]()Towny War
=============

There are two distinct Towny war modes. Flag war is no longer supported or receiving updates.

[]()/ta toggle war (Event War)
------------------------------

Towny war is activated by a server admin using `/townyadmin toggle war`, there is a configurable 30 second countdown and then War begins. Using_economy must be set to true in the config.yml for an event war to begin. During war Nations fight each other. Towns without a nation are not included, cannot score points and cannot have their townblocks griefed. The config has the option `towns_are_neutral: 'true'` if you would like nation-less towns to still be able to fight and be attacked (but still not score points.) Nations can also pay a daily Neutrality cost to avoid taking part in a war. The cost of neutrality is set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) using `price_nation_neutrality: 100.0`. In this example, a nation would pay 100 dollars from its nationbank each 'Towny Day'. 

Useful during war is the '/towny war hud' which will make a scoreboard appear for the player, which details points and properties of the townblock they are standing in. 

Also useful is the '/towny war participants {page #}' command. It shows a list of towns and their nation who are in the war event.The list highlights enemies, allies and capital towns. While war is in effect, each competing town has a health points property attached to it. 

Normal townblocks have an HP of 60 while Home Blocks have 120 points by default. This can be changed in the config. A townblock loses HP by enemy-nation residents standing within the townblock. When a townblock has lost all HP and fallen the town which the attacker belongs to gains one townblock and points to their War Score. When a townblock is under attack, fireworks appear above. Red for damage, red creeperhead for a won townblock, and green when a townblock is being healed by a defender. Fireworks can be turned off in the config at war.event.plots.firework_on_attacked. 

As of Towny 0.92.0.0 when players are killed in a town where they are considered to be enemies in the war, they may be sent to the town's Jail. This is configurable at `jail.is_jailing_attacking_enemies: 'false'`. If the jail plot is attacked and has its HP reduced to 0, any prisoners-of-war imprisoned there will be let free in a 'jailbreak'. POWs are also freed if the town they are kept in falls out of the war. 

As of Towny 0.95.1.0 you can make it so Townblocks which are conquered in war are transfered over permanently to the victor, set `war.event.winner_takes_ownership_of_townblocks` to true in your config to make towns lose townblocks.

War allows for a great deal of customizability when it comes to griefing. The config's `WarzoneBlockPermissions EditableMaterials` section can be used for Event war as of Towny 0.92.0.0. This means you may set which blocks can be placed and broken by players in the war. By default that list includes: tnt,fence,ladder,wood_door,iron_door,fire. Switch, Item_use, Fire and Explosion protections can be overriden during Event War as well. `explosions_regen_blocks: 'true'` will determine whether the explosion-griefing is permanent. 

If you would like to bybass the WarzoneBlockPermissions fine-grained approach and allow anyone to do anything during war you can set the the config's `war.event.allow_block_griefing` option to true. By default, only townblocks on the edge of the wilderness can be attacked first, this is optional in the config. 

A Town can be knocked out of a war when their Home Block falls or if their Mayor is killed. A Nation can be knocked out of a war if its capital city is knocked out of the war, or if the King is killed. Points in war given for the following:

-   A enemy killed: 1
-   A townblock stolen: 1
-   A town knocked out of the war: 10
-   A nation knocked out of the war: 100

Towny war ends when there is only one nation who's Home Block has not been conquered or when the admin toggles war off. Although the townblocks are restored at the end of war, the damage from any griefing is permanent.

[]()flag-war mode
-----------------

Developed on the side by Shadeness, the original author of Towny. See his explanation [here.](https://web.archive.org/web/20140912091755/http://xshade.ca/projects/towny/tutorial/war/)

------------------------------------------------------------------------

[]()Using SQL instead of Flatfile
=================================

As of Towny 0.80.0.0 admins can choose to use an SQL database instead of flatfile.

[]()Configuring SQL
-------------------

3 Data base types are supported:

### []()MySQL

-   Open the \towny\settings\config.yml and find the Plugin Interfacing section.
-   Navigate to the sql: section.
-   Configure towny with your mysql database hostname/port/username and password.
-   Save the config and read below for conversion instructions.

### []()H2

-   Download [h2.jar](http://mirror.nexua.org/Dependencies/h2.jar) and place it in the lib folder in your server's root folder.
-   Read below for conversion instructions.

### []()sqlite

-   Follow the same instructions as H2

[]()Converting Flatfile to SQL
------------------------------

1.  Stop your server
2.  Open the \towny\settings\config.yml and find the Plugin Interfacing section.
3.  Find the database_load, make sure it's set to flatfile.
4.  Find the database_save, set it to either mysql, sqlite or h2.
5.  Save the config and start your server.
6.  While your server is running:
    -   Set the database_load to mysql, sqlite or h2.
    -   Type /ta reload ingame.

7.  Open the Towny\Data\ folder and remove all but the plot-block-data folder. This folder contains the plot-snapshots used in the revert-on-unclaim feature. If you do not use that feature you may delete the entire Towny\data\ folder.
8.  It is important to note that Towny does not back up the sql database. It is up to you to do this.

[]()Converting SQL to Flatfile
------------------------------

1.  Stop your server
2.  Open the \towny\settings\config.yml and find the Plugin Interfacing section.
3.  Find the database_load, make sure it's set to your database type (mysql, sqlite or h2.
4.  Find the database_save, set it to flatfile
5.  Save the config and start your server.
6.  While your server is running:
    -   Set the database_load to flatfile
    -   Type /ta reload ingame.


