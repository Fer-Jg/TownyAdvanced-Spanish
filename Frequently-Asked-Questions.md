Q: Why can users not break or build in the wilderness outside of their towns?

A: Use `/ta toggle wildernessuse`.

----

Q: Where did the notifications for entering/exiting towns and the wilderness go?

A: If you are on MC 1.17.* you have to update your Towny to the [latest pre-release version](https://github.com/TownyAdvanced/Towny/releases).

----

Q: When towns fall or unclaim land all the blocks start to disappear back into wilderness. How do I stop this?

A: Using `/tw toggle revertunclaim` in each world. 

> - The New World Settings section of the [config](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) is only default settings for new worlds, it's explained in the config section comments, the [install guide](https://github.com/TownyAdvanced/Towny/wiki/Installation#configuring-existing-worlds) and the [how towny works](https://github.com/TownyAdvanced/Towny/wiki/How-Towny-Works#reverting-unclaimed-townblocks-to-their-original-state-on-unclaim) page. You need to be using the /tw toggle commands or manually setting the worldname.txt file.

----

Q: Which economy plugins do you recommend using with Towny?

A: You have lots of options

>  - Complex:
>    - **[TheNewEconomy](https://www.spigotmc.org/resources/the-new-economy.7805/)**  
>    - **[HyperConomy](https://www.spigotmc.org/resources/hyperconomy-1-13-2.65028/)**
>  - Simple:
>    - **[HellConomy](https://www.spigotmc.org/resources/hellconomy.67355/)**
>    - **[iConomy5](https://github.com/iconomy5legacy/iConomy "May not receive future updates")**
>  - Just about every economy plugin will work. You will still need either Vault or Reserve for Towny to be able to communicate with your economy plugin of choice.
>  - Plugins known to not work: aConomy, XConomy, Gringotts. EssentialsEconomy can work only if you use their dev builds. (2.19+)
>  - Plugins which may not work: UltimateEconomy, Economy.

----

Q: How can I protect my WorldGuard spawn point from being claimed?

A: Get [WorldGuard-Towny from the website](https://townyadvanced.github.io) and follow the readme.
