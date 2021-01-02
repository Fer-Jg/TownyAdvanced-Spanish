### This guide is for the new SiegeWar.jar versions of SiegeWar. If you are still using the older SiegeWar which was bundled into special builds of Towny.jar, see the [SiegeWar User Guide](https://github.com/TownyAdvanced/Towny/wiki/Siege-War-User-Guide) for the older installation guide.

<p align=center>
If you want to test out the SiegeWar.jar beta, join the [Discord's #siegewar-testers channel](https://discord.gg/2zsJRwaEUp) and ask for it.</p>

<table align=center>
<th> If you are upgrading from an older copy of SiegeWar that was bundled with Towny.jar, a note:</th>
<tr><td>
<br>The SiegeWar.jar version uses metadata instead of the old sieges.txt and sieges folder in the towny database.<br><br> By switching to the new SiegeWar any existing sieges and old siege war settings in Towns will vanish.<br><br> It is recommended to use a batch-text-editor to edit the townname.txt files in the towny\data\towns\ folder, changing the `peaceful=` setting to `neutral=`.</td></tr>
</table>

----

#### Required: Towny 0.96.5.11 or newer.

#### Required townyperms.yml edits:

> To the mayor and town assistant rank add: `- towny.town.siege.*`
> 
> It is recommended you add the `towny.town.siege.points` node to the sheriff while also creating a guard rank:
> ```
>         sheriff:
>             - towny.command.town.toggle.jail
>             - towny.outlaw.jailer
>             - towny.town.siege.points
>         guard:
>             - towny.town.siege.points
> ```
> 
> To the king and nation assistant rank add: `- towny.nation.siege.*`
> 
> and then create the following nation ranks:
> ```
>         soldier:
>             - towny.nation.siege.points
>         captain:
>             - towny.nation.siege.points
>             - towny.nation.siege.leadership
>         general:
>             - towny.nation.siege.*
> ```
> 
> For your server staff add:
> ```
> towny.siege.war.immune.to.war.nausea 
> towny.siege.war.immune.to.battle.fatigue 
> ```

#### That's it, configure the config.yml to your liking while reading the very informative comments.
#### SiegeWar has no added database, everything is stored in Towny's town metadata.