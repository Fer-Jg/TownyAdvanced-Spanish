[]()Siege War
-------------
Siege War is a non-destructive war-on-demand system focused on geo-politics

--- FEATURES -------------------------------------------------------------------------------------------------------------
* Sieges are between nations - who attack, and towns - who defend
* A nation can start a siege against a town at any time (except when a town is new, recently besieged, or peaceful)
* Towns cannot fall due to war costs (they can only go 'bankrupt', preserving the town completely but blocking expansion)
* Town structures & stored items remain safe (because town perm protections are unaffected)
* Towns can be plundered (transferring wealth from the defeated town to the victorious nation)
* Towns can be captured (temporarily adding the defeated town to the victorious nation)
* Casual & cross-timezone players can contribute to most wars (because the siege duration is 3 days)
* Soldier inventory item durability is degraded by 10% if killed during a siege (similar to the system used in top online RPG games e.g. WOW, LOTRO)
* Soldiers can disappear from the dynmap at any time (unlocking the development and use of both basic & advanced military tactics)
* Player battle fatigue is moderated  (because fighting is organised into  hour 'battle sessions' for each player. After each session, the player gets a 10 min. enforced break from combat)
* Peaceful towns can opt out of war (by toggling 'peaceful', a town opts out of war, receiving immunity from siege attacks & taxes. In return, its nation choice is more restricted. See below for full details)

--- ACTIONS -------------------------------------------------------------------------------------------------------------
* Go Tactically Invisible - As a player, equip a specific combination of items in your hands to disappear from the dynmap. Combos:
    - compass & diamond-sword
    - compass & bow
* Attack town - As a king or general, place a colored banner in the wilderness close to a town. This action will initiate a new siege on the town. $20/plot will be deposited into a 'war-chest', which will be automatically recovered by the siege winner. While under siege, the town has PVP forced-on, cannot recruit new residents, cannot claim/unclaim land, and only residents can spawn there.
* Gain Siege Points: Banner Control - As a military-ranked attacked or defender, gain banner control for your side, by remaining alive and within 16 blocks of the siege-banner for 10 minutes. Once your side has banner control, 30 siege-points will be awarded automatically every minute for each player on the banner control list. Banner is control is lost once all player on the list log off.
* Gain Siege Points: Kill Enemy - As an attacker or defender, kill enemy players of military rank, within 150 blocks of the siege-banner. Each kill gives a base 150 siege-points, regardless of how the player was killed.
* Win Siege - Be the side with the best score when the siege-victory-timer hits zero. The attacker requires positive points to win. The defender requires negative points to win.
* Plunder town - As an attacking king or general, after the siege is won, place a chest in the wilderness close to the town. This action will rob the town of $40/plot, transferring it to the plundering nation. 
* Capture town - As an attacking king or general, after the siege is won, place a colored banner in the wilderness close to the town. This action will temporarily capture the town, forcibly adding it to the nation for 10 days. The town will be in an 'occupied' state, in which its residents cannot affect siege points.
* Abandon attack - As an attacking king or general, place an all-white banner in the wilderness close to the town.
* Surrender town - As the defending mayor, place an all-white banner anywhere in the town.

--- COMMANDS ----------------------------------------------------------------------------------------------------------------

(Player)
* Assign Town Military Ranks - As a mayor, use the normal ranks system to assign:  guard, sheriff. Both can gain banner control in defence.
* Assign Town Military Ranks - As a king, use the normal ranks system to assign:  guard, captain, general. All can gain banner control in attack. Captains/generals have a leadership aura which affects nearby kill points, and generals can execute siege attack/abandon/invade/plunder.
* View Town Siege Information - View detailed information on a siege affecting the town, using '/t'
* View Nation Siege Information - View a list of sieges the nation is involved in, using '/n'
* Toggle Town Peacefulness - As a mayor, declare your town to be peaceful using '/t toggle peaceful'. The status will be confirmed in 5 days (2 days if the town is new). Once confirmed, the town becomes immune to sieges, taxes, & nationality-spawn-restrictions. It gets a public /t spawn (if it didn't have one already). Nation choice is more restricted, the town can only choose a nation which has a 'guardian town' with 75 chunks. A town qualifies as a guardian town if it has 30 plots or more, not-peaceful, not sieged, not recently-sieged, and the nation is open. Peaceful Town residents cannot receive nation-military ranks, and are afflicted by 'war allergy' if they enter a siege zone.
* Revolt - As a mayor, when 10 days have passed after a siege defeat, revolt and be free of an occupying nation using '/n leave'.
* Ruin Town - As a mayor, deny your town to an invader using '/t delete'. Your town will enter a ruined state for 3 days, after which full deletion occurs. In this state, all perm protections are disabled.
* Reclaim Town - As a resident, if your town falls into ruin, then after 24 hrs. have passed, reclaim it and become mayor, using '/t reclaim'.
* Receive Nation Refund - As a king, if your nation gets deleted for any reason, including capture of your last town, you will be refunded(80%) of the initial setup cost. This can be claimed using '/n refund'.

(Admin)
* Set siege immunities - As an admin, set siege immunities for 1 town, all towns in a nation, or all towns, using /ta set siegeimmunities ...'

--- ADMIN GUIDE -------------------------------------------------------------------------------------------
1. Configure Carefully
1.1. Read the configs in the war-siege and war-common sections, and set them up to suit your server.
1.2. Setup some town & claim refunds to avoid bankruptcy exploits.
1.3. Configure nation tax to a sensible maximum, because recently captured towns have no choice but to pay this.
2. Manage Rollout 
2.1. Give players a few days to prepare before enabling the system.
2.2. This could be done by deploying the system then setting all town immunities to a few days, allowing players to setup military ranks or toggle peaceful etc.

--- MODERATION GUIDE ------------------------------------------------------------------------------------
1. Prevent/Rollback Siege-Zone-Grief
1.1. With siegewar, a small wilderness area next to each besieged town will become an intense battleground.
1.2. Be prepared for this, and have rules in place before the system is enabled.
1.3. Example: "Only small functional military constructions are allowed in the siegezone (forts, ramps, traps etc.).". No pointless griefing etc.
2. Prevent Town-Claim-Surrounding
2.1. With siegewar, a town has complete immunity if it gets completely surrounded by the claims of another town.
2.2. Have rules in place to prevent this before the system is enabled
2.3. Example: "If you wish to surround a town with another town, the inner one must be peaceful."

--- SUPPORTING PLUGINS -------------------------------------------------------------------------------------
1. Respawn protection - If possible, add respawn protection (e.g. temporary damage immunity after respawn), so that players are not 'spawn killed' during battles.
2. Knockback Nerfing - To prevent extensive trap-warfare, if possible add nerfing of knockback effects, so players cannot be easily knocked into traps

--- NOTE ON THE NUMBERS SHOWN ABOVE -----------------------------------------------------------------
1. The numbers in this user-guide are just defaults - Almost all values can be modified to suit individual servers.

--- PERMISSION NODES ----------------------------------------------------------------------------------------

NATION PERM NODES
```
towny.nation.siege.*    (for generals)
towny.nation.siege.points  (for soldiers and captains)
towny.nation.siege.leadership  (for captains)
towny.nation.siege.attack  (not usually specified directly)
towny.nation.siege.abandon (not usually specified directly)
towny.nation.siege.invade (not usually specified directly)
towny.nation.siege.plunder (not usually specified directly)
```

TOWN PERM NODES
```
towny.town.siege.* (for mayors)
towny.town.siege.points (for guards and sheriffs)
towny.town.siege.surrender (not usually specified directly)
towny.command.town.toggle.peaceful (for mayors)
```

OTHER NODES
```
towny.siege.war.immune.to.war.nausea (for server staff)
towny.siege.war.immune.to.battle.fatigue (for server staff)
```

### The below installation guide is for older versions of SiegeWar which were included inside of special Towny.jar's.
### If you're using the new SiegeWar.jar file you will want to see the new [SiegeWar.jar installation guide.](https://github.com/TownyAdvanced/Towny/wiki/Siege-War-Installation)

--- INSTALLATION GUIDE ---

1. Backup all Towny data & config files
2. Stop server
3. Deploy the jar file from the ZIP file found in https://github.com/TownyAdvanced/Towny/projects/10#card-50506612
4. Start server
5. Configure Towny config.yml -> QUICK START: Set 'war.siege.switches.enabled' to 'true', and ensure the 'worlds' value is correct. 
6. Delete Towny 'english.yml'
7. Delete Towny 'townyperms.yml'
8. Stop server, then Start server again
9. If you use custom perms, now merge your backed up townyperms.yml file with the new townyperms.yml file, then run '/ta reload all'
10. If you use custom language strings, now merge your backed up english.yml file with the new english.yml file, then run '/ta reload all'

--- UPDATE GUIDE --------------------------------------------------------------------------------------------

1. Backup all towny data and configs
2. Stop server
3. Delete towny/settings/english.yml (towny will later automatically recreate this file)
4. Get the updated jar (usually just the Towny...jar) from zip file on the the Siegewar Project page
5. Drop the jar into the plugins folder on your server
6. Start server
﻿