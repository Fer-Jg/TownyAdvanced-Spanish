Folks that [sponsor me on GitHub](https://github.com/sponsors/LlmDl) will gain access to some exclusive plugins, which are available on the [Discord](https://discord.gg/gnpVs5m) in private channels. Below is a summary of what you get access to when you choose to support my work on Towny and the TownyAdvanced suite of plugins. If you've become a sponsor drop into the discord and give me an @ letting me know!

Your developer,

LlmDl

## TownyCamps

TownyCamps allows a player to place down a campfire in the wilderness which will then "claim" a camp, providing them 1 plot for a configured amount of time.

<details><summary>Click for details</summary>
A town-less player is able to place a campfire in the wilderness to "claim" a chunk of land. They do need the townycamps.campfire permission node. 

Camps are limited to the min-distance-from-townblocks Towny setting, so player cannot park a camp too close to another town. Towns can claim right up to Camps.

Players that own the Camp can make a town at that location.

Camps are protected from Build/Destroy/Switch/Itemuse. Camp owners can allow their friendlist to interact based on the owners perm line.

Explosion and Burning actions are always protected.

Chunk Notifications are shown when players enter and exit Camps.

Camp-owners can use LWCx in their camp. LWCx protections are removed when a camp is removed.

Camps appear in-game on Towny's ASCII map.

Camps are removed when:
- the campfire is broken,
- the campfire duration passes (defaults to 24 hours, is configurable,)
- the player joins or makes a town.

It uses Towny resident metadata so there's no database, it has a lang file and a config that updates itself just like Towny's.

Camps appear will appear on your server's Dynmap.
</details>

## TownyHistories

What happens when a Town is deleted? Where Towny leaves off, TownyHistories takes over. Towns become Ruins, appearing on your Dynmap, Lecterns mark the old spawn point with a book that has recorded some historical information about the now defunct Town, and more... 

<details><summary>Click for details</summary>
When Towns are deleted, they generate a Ruin. Ruins appear on your Dynmap (if you have it enabled,) with an icon marking the town's old spawn point and the town's old townblocks displayed in a shade of grey. 

At the old spawn point you will find a protected lectern and with a protected book sharing information about the ruin's Town.

Ruins can optionally be preserved from build/destroy actions.

Ruins display an actionbar message when they are entered into. 

Ruins appear on Towny's ASCII map.

Ruins' townblocks which are claimed by a town are removed from the ruin. If a ruin's homeblock is claimed by a town the ruin is removed entirely.

Note: this plugin somewhat assumes you have the revert-on-unclaim feature deactivated. This is not a hard-restriction, but future features will likely mean restoring the ruin would be detrimental.
</details>