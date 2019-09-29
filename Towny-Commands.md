-   [/towny](#towny)
-   [/plot](#plot)
-   [/resident](#resident)
-   [/town](#town)
-   [/nation](#nation)
-   [/townyadmin](#townyadmin)
-   [/townyworld](#townyworld)
-   [Chat Commands](#chat-commands)

-   This list breaks each command down by word. Eg: /resident set perm {on/off}.
-   For resident commands, the add command would auto-match online players, while add+ requires exact spelling to choose offline players.
-   Just about every subcommand has it's own help menu. Use /resident set, or a similar cutoff, to show all the options for that command ingame. You can also use /resident set ?, you will probably need to use that in the case where a subcommand actually has a function by itself. Example: /town claim, and /town claim ? would show all it's subcommands.
-   The { } brackets are used to show variables, or what you need to fill in. The elipse ".." (or shortened elipse) is used to show that you can specify multiple things at once (like inviting 10 residents at once).
-   The {bleh/blah/bluh} is used to show that the input can be multiple words.
-   An empty bullet represents that the subcommand itself does something and will not show a help menu.

[]()/towny
----------

-   /towny
    -   - Shows basic towny commands.
    -   ? - Shows more towny commands.
    -   map - Shows the towny map.
    -   prices - Shows taxes/costs associated with running a town.
    -   time - Shows time until next new-day (tax/upkeep collection.)
    -   top
        -   residents {all/town/nation} - Shows top residents.
        -   land {all/resident/town} - Shows top land owners.
    -   spy - Admin command to spy on all chat channels
    -   tree - Shows lots of stuff.
    -   universe - Shows full towny stats, resident/town/nation/world counts as well as townblocks claimed.
    -   v - Shows towny version.
    -   war
        -   stats
        -   scores
        -   hud
        -   participants {page #}

[]()/plot
---------

-   /plot
    -   - Shows the /plot commands.
    -   claim - Resident command to personally claims a plot that are for sale.
        -   auto - Resident command to personally claim an area of plots that are for sale, around the player typing the command.
    -   unclaim - Resident command to unclaim personally owned plots.
        -   circle/rect - Resident command to unclaim personally owned plots in a circle or rectangle shape.
            -   {# (radius around current position)} - Radius of the area to unclaim.
    -   {forsale/fs} - Set a plot for sale.
        -   circle/rect - Set a shape.
            -   {# (radius around current position)} - Radius of the area to set forsale.
        -   $$ - Cost of plot.
            -   circle/rect - Set a shape.
                -   {# (radius around current position)} - Radius of the area to set forsale.
    -   {notforsale/nfs} - Set a plot to not be for sale.
        -   circle/rect - Set a shape.
            -   {# (radius around current position)} - Radius of the area to set notforsale.
    -   evict - Used to remove a plot from a plot owner, usually by the mayor or assistant.
    -   perm - Shows the perm line of the plot in which the player stands.
    -   perm hud - Toggles on/off the plot perm hud scoreboard which shows the perm line of the plot in which the player stands along with more useful plot info.
    -   set
        -   reset - Sets a shop/embassy/arena/wilds plot back to a normal plot.
        -   shop - Sets a plot to a shop plot.
        -   embassy - Sets a plot to an embassy plot.
        -   arena - Sets a plot to an arena plot.
        -   wilds - Sets a plot to a wilds plot.
        -   inn - Set a plot to an inn plot.
        -   jail - Set a plot to an jail plot.
        -   farm - Set a plot to a farm plot.
        -   bank - Set a plot to a bank plot.
        -   name - allows a mayor or plot-owner to rename plots they own, overwriting the ~Unowned message. Personal-plots display both the plot's given name and the name of the plot-owner.
        -   perm
            -   {on/off} - Edits the perm line of the single plot in which the player is standing. [See here for details.](https://github.com/TownyAdvanced/Towny/wiki/How-Towny-Works#towny-plot-perms)
            -   {resident/ally/outsider} {on/off}
            -   {build/destroy/switch/itemuse} {on/off}
            -   {resident/ally/outsider} {build/destroy/switch/itemuse} {on/off}
            -   reset - Resets the plot in which you stand to the default perm line of the /town or /resident screen (depending on if the plot is owned personally or by the town.)

    -   toggle
        -   fire - Turn on/off firespread in the plot in which you stand.
        -   pvp - Turn on/off pvp in the plot in which you stand.
        -   explosion - Turn on/off explosions in the plot in which you stand.
        -   mob - Turn on/off hostile mobspawning in the plot in which you stand.
    -   clear - Command to remove list of block id's from a plot, used by a mayor on town-owned land, or by a plot-owner on their personal plots.

[]()/resident
-------------

-   /resident
    -   - Shows a player their resident screen.
    -   ? - Shows /res commands available.
    -   {resident} - Shows a player another player's resident screen.
    -   friend
        -   add {resident} .. {resident} - Resident adds online player to their friends list.
        -   add+ {resident} .. {resident} - Resident adds offline player to their friends list.
        -   remove {resident} .. {resident} - Resident removes online player from their friends list.
        -   remove+ {resident} .. {resident} - Resident removes offline player from their friends list.
        -   clearlist - Removes all friends from a resident's friend list.
    -   list - Lists residents in towny's data folder who are online.
    -   jail paybail - Allows a player to pay to get out of jail. Funds go to the town which owns the Jail.
    -   spawn - If deny_bed_use: true and player has a current bed spawn, command will teleport player to their bed.
    -   toggle
        -   map - Turns on map which refreshes when moving across plot borders.
        -   townclaim - Turns on mode where /town claim is automatically used when moving across plot borders.
        -   plotborder - Turns on smokey plot-border view. Border shows when players cross to different townblocks.
        -   constantplotborder - Turns on smokey plot-border view. Border doesn't disappear.
        -   spy - Admins can turn on chat-channel spying.
        -   ignoreplots - Turns on/off plot notifications in town.
        -   reset - This turns off all modes that are active.
-   set
    -   perm
        -   {on/off} - Edits the perm line on the resident screen. [See here for details.](https://github.com/TownyAdvanced/Towny/wiki/How-Towny-Works#towny-plot-perms)
        -   {friend/ally/outsider} {on/off}
        -   {build/destroy/switch/itemuse} {on/off}
        -   {friend/ally/outsider} {build/destroy/switch/itemuse} {on/off}
        -   reset - This takes the perm line seen in the /resident screen and applies it to all plots personally owned by the player typing it.
-   tax - Shows taxes a player pays.

[]()/town
---------

-   /town
    -   - Shows a player their town's town screen.
    -   ? - Shows /town commands available.
    -   {town} - Shows a player another town's town screen.
    -   here - Shows you the town screen of the town in which you stand.
    -   leave - Leaves a town.
    -   list {page #} - Lists towns.
    -   online - Shows players in your town which are online.
    -   plots {townname} - Shows a helpful list of plots and their types/revenue which are owned by the town.
    -   new {townname} - Creates a new town.
    -   add {resident} .. {resident} - Mayor command to add residents to your town.
    -   kick {resident} .. {resident} - Mayor command to remove residents from your town.
    -   spawn - Teleports you to your town's spawn.
    -   spawn {town} - Teleports you to another town's spawn.
    -   claim - Mayor command to claim the townblock in which you stand for your town.
        -   outpost <#|{name}|{name:#} - Claims an outpost for your town. {name} uses the plot name. {name:#} is used when a plot name begins with a number.
        -   {# (radius around current position)} - Claims an area of townblocks around you for your town.
        -   auto - Claims as many townblocks around you as is possible given money in townbank and available townblocks.
    -   unclaim - Mayor command to unclaim the townblock in which you stand.
        -   all - Mayor command to unclaim all townblocks.
        -   {# (radius around current position)} - Command to unclaim an area of townblocks around you.
        -   outpost - Used to unclaim glitched outposts on MySQL Towny servers pre-0.92.0.0
    -   withdraw {$} - Removes money from town bank.
    -   deposit {$} - Adds money from player to the town bank.
    -   buy
        -   bonus {amount} - Buys available bonus townblocks.
    -   delete {town name} - Admin/Mayor command to delete a town from towny's data folder's files.
    -   outlawlist {town} - Displays a list of outlaws for a town.
    -   outlaw {add/remove} {name} - Adds or removes an outlaw from a town's outlaw list
    -   outpost
        -   {# (where # equals the corresponding outpost's number)} - Teleports to an outpost.
        -   {list} - lists your town's outposts.
    -   ranklist - Displays residents and their ranks.
    -   rank {add|remove} {playername} {rankname} - Grants or removes a rank to a resident of the town.
    -   reslist {townname} - See a FULL list of all residents in a town.
    -   say {msg} - Broadcast a message to online town members.
    -   set
        -   board {message} - Sets message seen by residents upon logging in.
        -   mayor {resident} - Mayor command to give mayor status to another resident.
        -   homeblock - Sets the homeblock and spawn of your town.
        -   spawn - Sets the town spawn, must be done inside the homeblock.
        -   spawncost - Set the cost of spawning to a public town. Doesn't affect town residents, nation members and nation-allies.
        -   name {name} - Change your town's name.
        -   outpost - Resets the outpost's spawn point to the player location. Must be used in an existing outpost plot.
        -   jail - Resets a jail plot's spawn to current position within a jail plot.
        -   perm
            -   {on/off} - Edits the perm line on the town screen. [See here for details.](https://github.com/TownyAdvanced/Towny/wiki/How-Towny-Works#towny-plot-perms)
            -   {resident/ally/outsider} {on/off}
            -   {build/destroy/switch/itemuse} {on/off}
            -   {resident/ally/outsider} {build/destroy/switch/itemuse} {on/off}
            -   reset - This takes the perm line seen in the /town screen and applies it to all plots owned by the town.
        -   tag {upto4character} - Sets the town's tag, which is sometimes used on that chat line.
            -   clear - Clears the tag set for the town.
        -   taxes {$} - Sets taxes collected from each resident daily. Also sets percentage if taxpercent is toggled on.
        -   plottax {$} - Set taxes collected from each resident daily, per plot that they own.
        -   plotprice {$} - Sets default cost of plot for the town.
        -   shopprice {$} - Sets default cost of a shopplot for the town.
        -   shoptax {$} - Set taxes collected from each resident daily, per shopplot that they own.
        -   embassyprice {$} - Sets default cost of a embassy plot for the town.
        -   embassytax {$} - Set taxes collected from each resident daily, per embassy plot that they own.
    -   toggle
        -   explosion - Turn on/off explosions in town.
        -   fire - Turn on/off firespread in town.
        -   mobs - Turn on/off hostile mobspawning in town.
        -   public - Turn on/off public /town spawning and the co-ordinates of the town's homeblock in the /town screen.
        -   pvp - Turn on/off pvp in town.
        -   taxpercent - Turn on/off taxing by percent/flatrate.
        -   open - Turn on/off public joining to your town.
        -   jail {number} {residentname} - Sends a resident of your town to the jail spawn number specified. Same command unjails a player.
    -   join {townname} - Command to join a town that doesn't require invites.

[]()/nation
-----------

-   /nation
    -   - Shows a player their nation's nation screen.
    -   ? - Shows /nation commands.
    -   list {page #} - Lists nations.
    -   online - Shows players in your nation which are online.
    -   {nation} - Shows a player the /nation screen of another nation.
    -   leave - Mayor command to leave the nation they are a part of.
    -   withdraw {$} - King command to remove money from the nation bank.
    -   deposit {$} - King command to add money to the nation bank.
    -   new
        -   {nationname} - Mayor command to create a nation.
        -   {nationname} {capitaltown} - Admin command to create a new nation, set capitol.
    -   rank - Command to set assistant/custom ranks in the nation.
    -   add {town} .. {town} - Invites/Adds a town to your nation.
    -   kick {town} .. {town} - Removes a town from your nation.
    -   delete {nation} - Deletes your nation.
    -   ally
        -   add {nation} .. {nation} - Add a nation to your nation's ally list.
        -   remove {nation} .. {nation} - Removes a nation from your nation's ally list.
    -   enemy
        -   add {nation} .. {nation} - Add a nation to your nation's enemy list.
        -   remove {nation} .. {nation} - Removes a nation from your nation's enemy list.
    -   rank {add|remove} {playername} {rankname} - Grants or removes a rank to a resident of the nation.
    -   say {msg} - Broadcast a message to online nation members.
    -   set
        -   king {resident} - King command to change the king of the nation.
        -   capital {town} - Sets the capitol and king of the nation.
        -   board {message} - Sets message seen by residents upon logging in.
        -   taxes {$} - Sets nationtax applied to the towns within the nation.
        -   name {name} - Sets the nation's name.
        -   spawn - Sets the nation spawn point.
        -   spawncost - Sets the cost of public spawns to that nation's spawn point. No effect on members of the nation or nation-allies
        -   title {name} {titlegoeshere} - King command to add a Title to a member of the nation.
        -   surname {name} {surnamegoeshere} - King command to add a Suffix to a member of the nation.
        -   tag {upto4character} - Sets the nation's tag, which is sometimes used on that chat line.
            -   clear - Clears the tag set for the nation.
    -   toggle
        -   neutral - Sets whether your nation will pay daily to be neutral during towny war.

[]()/townyadmin
---------------

- /townyadmin

  - Shows Memory, Threads, War status, Health regen setting, Time, Whether daily-timer/taxes are on.
  - ? - Shows /ta commands.
  - delete {playername} - Deletes a player's towny data.
  - resident 
    -   {oldname} rename {newname} - Admin command to manually rename a resident to a new name. Not need if TownyNameUpdater.jar is present.

  - town {townname}
    -   new [name] [mayor] - Admin command to create a town for the mayor where the command sender is standing.
    -   add {resident} .. {resident} - Admin command to invite/add a resident to a town.
    -   remove {resident} .. {resident} - Admin command to remove a resident from a town.
    -   kick {resident} - Admin command to remove a resident from a town.
    -   rename {newname} - Admin command to rename a town.
    -   spawn - Admin command to spawn at at town spawn.
    -   tpplot {world} {x} {z} - Teleports an admin to the Towny chunk coordinates seen in the /towny map command. Be careful with large numbers, you could be teleported farther than you think and end up generating chunks.
    -   outpost # - Admin command to spawn at any towns outposts.
    -   delete - Admin command to delete a town.
    -   rank {add/remove} {name} {rank} - Admin command to give/remove a rank to a town member.

  - nation {nationname}
    -   add {town} - Admin command to invite/add a town to a nation.
    -   rename {newname} - Admin command to rename a nation.
    -   delete - Admin command to delete a town.

  - reset - resets the towny config.yml to its current default.

  - toggle
    -   war - Turn on/off towny war.
    -   neutral - Turn on/off a nation's ability to declare neutrality.
    -   npc {residentname} - Toggles a player's resident file to isNPC=true, this exempts the player from taxes/upkeep.
    -   debug - Turns on/off debug mode.
    -   devmode - Turns on/off special devmode for when towny's devs join your server to find a bug.
    -   withdraw - Turns on/off town/nation's ability to withdraw money from their town/nation banks.

  - set
    - plot {town} - Sets a plot to a town.
        -   When in a town only a single plot can be transfered at one time. Does not require a town to have available townblocks to claim.
        -   When in the wilderness two types of sub commands can be used to do area claims:
        -   Does require a town to have available townblocks to claim.
        -   Does obey proximity rules for claims between towns/homeblocks.
        -   /ta set plot {town} {rect|circle} {radius}
        -   /ta set plot {town} {rect|circle} auto
    - title {name} {title} - A command for admins to be able to set a player's title.
    - surname {name} {surname} - A command for admins to be able to set a player's surname.
    -   capital {townname} - A command for admins to be able to change a nations capital. Town to be set must already be a member of the nation.
    -   mayor
        -   {town} {resident} - Admin command to set a resident as mayor of a town.
        -   {town} npc - Admin command to set a town to have an npc mayor.

  - givebonus {town} {#} - Gives extra townblocks to a town.
  - reload - Reloads towny's config.yml.
  - backup - Creates a backup.
  - checkperm {player} {node} - Quick test of whether a player has a permission node.
  - newday - Causes a new day to happen, this does not stop the next new day from happening when it was already scheduled.
  - unclaim
    -   rect {radius} - Admin command to unclaim an area.
  - purge {# as in days} - Deletes old residents.

[]()/townyworld
---------------

-   /townyworld
    -   - Shows world settings for the world in which you stand.
    -   ? - Shows /tw commands.
    -   list - Lists worlds.
    -   {world} - Show settings for world.
    -   toggle
        -   claimable - Turn on/off whether mayors can claim townblocks in the world.
        -   usingtowny - Turn on/off whether towny is used in the world.
        -   pvp - Turn on/off pvp in the world.
        -   forcepvp - Turn on/off whether pvp is forced on in all towns in the world.
        -   explosion - Turn on/off whether explosions are on in the wilderness/towns in the world.
        -   forceexplosion - Force explosions on in that world.
        -   fire - Turn on/off whether firespread is on in the wilderness/towns in the world.
        -   townmobs - Turn on/off hostile mobspawning in towns in the world.
        -   worldmobs - Turn on/off the mobs listed in the world mobs in the world.
        -   revertunclaim - Turn on/off the revert on unclaim feature for that world.
        -   revertexpl - Turn on/off the reverting explosions in the wilderness feature for that world.
    -   set
        -   wildname {name} - Sets name of the wilderness.
        -   wildperm {perm} .. {perm} - Deprecated.
        -   wildignore {id} .. {id} - Deprecated.
        -   wildregen {Creeper,EnderCrystal,EnderDragon,Fireball,SmallFireball,LargeFireball,TNTPrimed,ExplosiveMinecart} - Sets what explosions are reverted in the wilderness.
        -   usedefault - Deprecated.
    -   regen - Regenerates the MC chunk in which back to the seed.
    -   undo - Undoes /tw regen.

[]()Chat Commands
-----------------

-   /townychat reload - Reloads chatconfig.yml and channels.yml
-   /townchat, /tc
    -   Put in from of text to speak with members of your town only, or without text afterwards to enter the channel.
-   /nationchat, /nc
    -   Put in from of text to speak with members of your nation only, or without text afterwards to enter the channel.
-   /global, /g
    -   Put in from of text to speak in globalchat, or without text afterwards to enter the channel.
-   /res set mode reset
    -   Reset chat mode to default chat.
-   /a - admin chat.
-   /m - moderator chat.

<!-- -->

-   /channel leave|join {channel} - Channel leaving and joining.
-   /ch list - list what channels a player is currently listening to. Courtesy of Yaiyan.
-   /leave {channel} - Leaves a channel.
-   /join {channel} - Joins a channel.
-   /chmute {channel} {player} - Mutes a player in a channel.
-   /mutelist {channel} - Displays mute list for a channel.
-   /chunmute {channel} {player} - Unmutes a player in a channel.

