
***


Q. A handful of large nations are starting to dominate my server. What can I do ?

A.

**Step 1**
* Identify problem:

1. Is the 'points_for_<attacker/defender>_death' setting very high ?
  This will reduce the opportunities for smaller nations to try out risky tactics which might turn battles, thus usually favouring the larger nation.

2. Is the 'points_for_<attacker/defender>_occupation' setting very low ?
  This will reduce the opportunities for smaller nations to try out risky tactics which might turn battles, thus usually favouring the larger nation.

3. Is the keep_inventory_on_siege_death' setting turned off ?
  This will have made the production and accumulation/capture of gods kits a critical part of war. Large nations are very good at this, smaller nations cannot compete.

4. Is the 'tactical invisibility' setting turned off ?
  This will have made battles a numbers game, which always favours larger nations. Without this, smaller nations cannot use military tactics which would favour them, such as ambushes.

5. Is the 'counterattack_booster_enabled' setting turned off ?
  This is off by default, but if enabled will give a boost to small towns and nations.

6. Is the 'population_based_point_boosts_enabled' setting turned off ?
  This is off by default, but if enabled will give a boost to smaller nations

   **Step 2**
*  Enable features / adjust values.


***


Q. Many players are trying to win by A.F.K., instead of P.V.P. What can I do ?

A. 

**Step 1**

* Identify Problem:
1. Is the 'points_for_<attacker/defender>_death' setting very high ?
         This will cause the weaker side to be afraid of P.V.P, thus avoiding battle.
2. Is the 'points_for_<attacker/defender>_occupation' setting very low ?
         This will cause the weaker side to be afraid of P.V.P, thus avoiding battle.
3. Is the keep_inventory_on_siege_death' setting turned off ?
         This will have made the production and accumulation/capture of gods kits a critical part of pvp.
         Large nations are very good at this, smaller nations cannot compete.
         Thus smaller nations will avoid pvp.
4. Is the 'tactical invisibility' setting turned off ?
         This will have made battles a numbers game, which always favours larger nations.
         Without this, smaller nations cannot use military tactics which would favour them, such as ambushes.
         Thus smaller nations will avoid pvp.
5. Is the 'counterattack_booster_enabled' setting turned off ?
         This is off by default, but if enabled will encourage the weaker side to counter-attack and regain banner control.
6. Is the 'pillaging_enabled' setting turned off ?
         This is off by default, but if enabled will encourage the sides to more-violently compete for banner-control.

**Step 2**
* Enable features / adjust values.

***

Q. Non-Ranked players are interfering in the siege zone. What do I do ?

A. 

**Step 1**
* Identify the cause of the problem:
1.    Is the 'keep_inventory_on_siege_death' setting turned off ?
           This will be discouraging ranks-only in the siege zone,
           because although non-ranked players cannot get banner-control, 
           they lose LESS on death than ranked players (as siege points are unaffected).
2.   Are some players from uninvolved towns trying to 'spectate' the battle ?

**Step 2**
1.   If (i), turn the relevant setting back on.
            This strongly encourages ranks in the siege zone,
            because non-ranked players will then 
            lose MORE on death than ranked players (as they will lose their entire inventory).
3.  If (ii), although there is a small chance that such players may actually interfere in the battle,
            battle spectating for the purpose of News-Reporting may be good for the community.
            This is especially so if some soldiers are using tactical invisibility,
            in which case the Dynmap alone may not show critical details of the battle.

***

Q. Players are griefing the siegezone. What can I do ?

A. 
1. Ensure that the following configs are enabled. These configs will automatically prevent obsidian and cobble monsters:
       war.siege.zone_block_placement_restrictions.enabled
       war.siege.zone_bucket_usage_restrictions.enabled
2. In addition to the above configs, you should also apply moderation, and create a rule(s) for siegezone changes e.g.
       "No major terraforming is allowed at the siegezone." 
       "Only small forts, ramps and barriers are allowed."

***

Q. The political situation is getting stale because players refuse to attack their friends. What can I do ?

A.
1. Reduce the costs of war, to shift the system towards being more 'chess-like', in which players can compete against each other without any big losses or bad feelings.
1.1. Enable the keep_inventory_on_siege_death config. (so that a battle death does not mean a god kit gone)
1.2. Keep plunder to 15% or less of the town bank. 
1.3. Enable the player health limiter config. (This is a less important tweak)

2. Enable tactical invisibility, increasing the respect players may have for their opponents' armies, more so that if each side knew all details of the enemy army positions.

***

Q. Some large towns believe that war costs (like plunder) are meaningless for them because they are so rich. What can I do ?

A. Enable the following setting: 'extra_money_percentage_per_town_level'
   This setting increases all siege moneys by a configured percentage for each town level.
   Thus large towns will pay proportionally more, restoring the relevance of war costs to them.

***

Q. The server is getting very toxic, with too much aggression and smack-talk. What can I do ?

A. 
1. Reduce the costs of war, to shift the system towards being more 'chess-like', in which players can compete against each other without any big losses or bad feelings.
1.1. Enable the keep_inventory_on_siege_death config. (so that a death does not mean a god kit gone)
1.2. Keep plunder to 15% or less of the town bank. 
1.3. Enable the player health limiter config. (this is a less important tweak)

2. Reduce the number of daily battles, as follows:
2.1. Reduce the number of sieges allowed per nation (although 3 is pretty much the minimum feasible value)
2.2. Increase the siege-immunity-time-modifier.
2.3. Increase the expired-battle-session duration. (giving players longer breaks from PVP)

3. Enable tactical invisibility, increasing the respect players may have for their opponents' armies, more so that if each side knew all details of the enemy army positions.

***

Q. I am preparing for a siegewar trial and I am concerned the plunder money steal would create toxicity. Will it create a more relaxed server experience if I disable it?.

A. No. If you disable it, it will more likely creare a LESS relaxed server experience.
* The true value of plunder is not simply an adjustment of bank balances.
* Rather, the feature works as a 'glue' which allows empires to grow and hold together.
* A famous example of this in R.L. was the Mongols. Many towns in their path would quickly throw their doors open and surrender without a fight, simply to avoid the threat of plunder. The mongols would then generally peacefully occupy such towns.
* Without plunder, aggression levels would be predicted to be higher. Because there would be less material cost in losing, then there would be less need for negotiation. Thus towns would be predicted to fight to the bitter end of most sieges (rather than negotiate or surrender early), and revolts would happen more frequently for the same reasons, stifling nation growth and stability.

***

Q. What happens if a nation's capital is captured after a siege defeat ?

A. The same thing that happens if a capital leaves a nation for any other reason --> The remaining town with the highest population becomes the capital, AND the king changes to be the mayor of that town.

***

Q. My players are starting to use traps a lot in sieges and it's getting weird. What can I do?

A. Recommendations:
1. disable obsidian in siege zones (for easier trap destruction/escape)
2. disable string in siege zones (for easier trap escape)
3. disable fence gates in siege zones (for easier trap escape)
4. disable knockback 1 and 2 on all swords and possibly on bows too (should be highly effective in reducing the instances of players getting knocked by opponents into traps)
5. Allow enderpearl usage (for easier trap escape) ... consider a cooldown on each usage though
6. Allow spawning out from enemy claims (so that escape from unattended traps is not impossible)

***

Q. A town is peaceful and does not wish to fight. What can I do ?

A. The best option is for the mayor to toggle the town to peaceful using "/t toggle peaceful". See the user guide for a description of effects.

***

Q. An entire nation is peaceful and does not wish to fight, but rather wants to use the Towny-Nation feature as something like a 'social club' or 'trading company', and with complete immunity to military conquest. What can I do ?

A. 
1. These players will never be fully happy sharing territory with geopolitical/empire-building players, and vice-versa ---> One group will be unhappy if some lands are off-limits to attack, the other will be unhappy if some lands are NOT off limits to attack.
2. If possible move these two groups to separate locations e.g two continents (one for 'sandbox building', the other for 'geopolitics'), or separate servers (one with siegewar enabled, one without).

***

Q. Everyone is block-glitching these days. Doesn't this make walls useless?

A. No it doesn't. Walls will obstruct enemy movements and help you control the battlefield, while also giving you an elevated firing position (for bows).

***

Q. How do I use military ranks ?

A. Only give military ranks to players who can be trusted.  Soldiers: Can get banner control, and don't lose items on death. Captains: Same, but with a leadership aura. Generals: Same, but they can use siege management actions: attack/abandon/invade/plunder. 

***

Q. My nation is about to be destroyed, because my last remaining town will be captured. What do I do?

Option 1 - Create  a 'refugee town', and flee there with loyal soldiers. 

Option 2 - Accept defeat, take the 100% (for now) nation setup cost refund, and plan your next geopolitical move (maybe a revolt of some sort...)
