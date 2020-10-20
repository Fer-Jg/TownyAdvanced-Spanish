Since Towny Version 0.94.0.18, Towny has provided some PlaceholderAPI support without needing an extension from the PAPI eCloud. Use of these placeholders requires PlaceholderAPI to be installed to be functional. Towny can not be configured to use placeholders at this time, though TownyChat can. 

If you are unable to run at minimum Towny 0.94.0.18, you can download the [old PAPI Towny Expansion](https://api.extendedclip.com/expansions/towny/) instead. 

You are able to format some of the Placeholder's appearances via the Towny [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml)'s papi_chat_formatting section. (Ex: removing the []'s, or changing colours.)

## Available Tags:

_Introduced as of v0.95.0.0_
- `%townyadvanced_town%` - Displays town name (if they have one.)
- `%townyadvanced_town_formatted%` - Displays long-form town name (if they have one.)
- `%townyadvanced_nation%` - Displays nation name (if they have one.)
- `%townyadvanced_nation_formatted%` - Displays long-form nation name (if they have one.)
- `%townyadvanced_town_balance%` - Displays town bank value.
- `%townyadvanced_nation_balance%` - Displays nation bank value.
- `%townyadvanced_town_tag%` - Displays town tag (if they have one.)
- `%townyadvanced_town_tag_override%` - Displays town tag (if they have one,) or the full town name.
- `%townyadvanced_nation_tag%` - Displays nation tag (if they have one.)
- `%townyadvanced_nation_tag_override%` - Displays nation tag (if they have one,) or the full nation name.
- `%townyadvanced_towny_tag%` - Displays town and nation tags.
- `%townyadvanced_towny_tag_override%` - Displays town and nation tags if they exist, falling back to names if they don't.
- `%townyadvanced_towny_tag_formatted%` - Displays town and nation tags if they exist, falling back to long-form names if they don't.
- `%townyadvanced_title%` - Displays king-granted title.
- `%townyadvanced_surname%` - Displays king-granted surname.
- `%townyadvanced_towny_name_prefix%` - Displays mayor and king prefix.
- `%townyadvanced_towny_name_postfix%` - Displays mayor and king postfix.
- `%townyadvanced_towny_prefix%` - Displays title if it exists, falls back to mayor and king prefixes.
- `%townyadvanced_towny_postfix%` - Displays surname if it exists, falls back to mayor and king postfixes.
- `%townyadvanced_towny_colour%` - Used to show colours before nomads, residents, mayors and kings. (Set in the config.yml.)  

_Introduced as of v0.95.1.0_
- `%townyadvanced_town_residents_amount%` - Number of residents in a town.
- `%townyadvanced_town_residents_online%` - Number of residents in a town that are currently online.
- `%townyadvanced_town_townblocks_used%` - Number of townblocks claimed by a resident's town.
- `%townyadvanced_town_townblocks_bought%` - Number of townblocks bought by a resident's town.
- `%townyadvanced_town_townblocks_bonus%` - Number of bonus blocks given to a resident's town.
- `%townyadvanced_town_townblocks_maximum%` - Number of townblocks a town has available to claim.
- `%townyadvanced_town_townblocks_natural_maximum%` - Number of townblocks a town has available to claim, not counting bonus/bought townblocks.
- `%townyadvanced_town_mayor%` - A resident's town's mayor's name.
- `%townyadvanced_nation_king%` - A resident's nation's king's name.
- `%townyadvanced_resident_friends_amount%` - Number of friends a resident has.
- `%townyadvanced_nation_residents_amount%` - Number of residents in a resident's nation.
- `%townyadvanced_nation_residents_online%` - Number of residents in a resident's nation that are currently online.
- `%townyadvanced_nation_capital%` - Name of a resident's nation's capital.

_Introduced as of v0.95.2.0_
- `%townyadvanced_daily_town_upkeep%` - Shows town's upkeep cost.
- `%townyadvanced_daily_nation_upkeep%` - Shows nation's upkeep cost.
- `%townyadvanced_has_town%` - Returns true or false whether the resident has a town.
- `%townyadvanced_has_nation%` - Returns true or false whether the resident has a nation.

_Introduced as of v0.96.0.0_
- `%townyadvanced_nation_tag_town_formatted%` - Shows the nation tag and the full town name. If nation tag is not set, only the town name is shown.

_Introduced as of v0.96.2.0_
- `%townyadvanced_town_ranks%` - Displays either Mayor, or the various town ranks a player has or nothing if they have none.
- `%townyadvanced_nation_ranks%` - Displays either King, or the various nation ranks a player has or nothing if they have none.
- `%townyadvanced_player_status%` - Displays Nomad, Resident, Mayor or King, depending on what position the player is in.