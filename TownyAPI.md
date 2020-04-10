 * [Getting started with Towny and your IDE](#getting-started-with-towny-and-your-ide)
 * [Common API uses](#common-api-uses)
    * [Checking if a player is in the wilderness](#checking-if-a-player-is-in-the-wilderness) 
    * [Checking if a player is in their own town](#checking-if-a-player-is-in-their-own-town) 
    * [Getting a Resident from a Player](#getting-a-resident-from-a-player) 
    * [Getting a Player from a Resident](#getting-a-player-from-a-resident) 
    * [Getting a Town](#getting-a-town) 
    * [Getting a Nation](#getting-a-nation)
    * [Checking if a player can build/destroy somewhere](#checking-if-a-player-can-builddestroy-somewhere)
    * [Checking if Towny would prevent PVP damage](#checking-if-towny-would-prevent-pvp-damage)
 * [Some useful events](#some-useful-events)
 * [Of use to Shop Plugin developers](#of-use-to-shop-plugin-developers)
 * [Working with Town and TownBlock MetaData](https://github.com/TownyAdvanced/Towny/wiki/TownyAPI#working-with-town-and-townblock-metadata)
 * [Example plugins using the TownyAPI](#example-plugins-using-the-townyapi)

Using the Towny API in your plugins is quite simple. There are two versions of the API.

1.  The original API which ran from version 0 to 0.94.0.0 (see old Javadoc [here](http://palmergames.com/javadoc/towny-bukkit/))
2.  The new API which is present in Towny 0.94.0.1 and onwards (see new Javadoc [here](https://townyadvanced.github.io/Towny/))

The new API supports the old API calls although they will appear as deprecated. It is recommended that authors do switch to the new API.

## Getting started with Towny and your IDE

The builds of Towny beyond version 0.94.0.12 are available on Maven.

Developers may use the following after [setting up their github token as shown here.](https://help.github.com/en/articles/configuring-apache-maven-for-use-with-github-package-registry#authenticating-to-github-package-registry)

If you are only wanting to add Towny to your existing plugin's pom.xml you will need to give your token `read:packages, write:packages` access.

To elaborate on the above link in your settings.xml file you must have the following in your <servers></servers> section:
```yml
  <servers>
    <server>
      <id>github-towny</id>
      <username>YourGithubUsernameHere</username>
      <password>YourAccessTokenHere</password>
    </server>
    <server>
      <id>github-tne</id>
      <username>YourGithubUsernameHere</username>
      <password>YourAccessTokenHere</password>
    </server>
  </servers>
```
The github-tne entry is only required if you're building Towny from the source using Maven, it is not required if you just want to use Towny in your own plugin.

It is critical that the above server <id> matches the below repository <id> value.

After you've configured your settings.xml file above you may enter the text below into your pom.xml file:
```yml
  <repositories>
    <repository>
      <id>github-towny</id>
      <url>https://maven.pkg.github.com/TownyAdvanced/Towny</url>
    </repository>   
  </repositories>
  <dependencies>                    
    <dependency>
      <groupId>com.palmergames.bukkit.towny</groupId>
      <artifactId>Towny</artifactId>
      <version>0.96.1.0</version>
      <scope>provided</scope>
    </dependency>
  </dependencies>  
```

Note again that the API changed after 0.94.0.2 and your version number should be set for that or newer. Once it is added you can put Towny into your plugin.yml's depend or softdepend list (depending on whether your plugin needs Towny present to function all of the time, or if you want to support Towny features when present.) Lastly you will need to add the following to your pre's import section:
```java
import com.palmergames.bukkit.towny.TownyAPI;
```
## Common API uses

### Checking if a player is in the wilderness

To check if the player is in the wilderness is easy:
```java
if (TownyAPI.getInstance().isWilderness(player.getLocation()))
   return false;
```
Any location is accepted.

### Checking if a player is in their own town.

To find the town a player is standing in, you have to look at the TownBlock, which is what towns are made up of. Looking up a TownBlock from a player's location can return null if the player is standing in the wilderness, so it is recommended that you perform an isWilderness(Location loc) test [seen directly above on this page] before you look up the TownBlock.
```java
try {
   Town town = TownyAPI.getInstance().getTownBlock(player.getLocation()).getTown();
   if (resident.getTown().equals(town)) {
   //Execute your code here
   }
} catch (NotRegisteredException e) {
   //Code put here can also be code that ought to be run if the player is in the wilderness and not a town.
   e.printStackTrace();
}
```
The above code will require the following imports:
```java
import com.palmergames.bukkit.towny.object.Resident;
import com.palmergames.bukkit.towny.object.Town;
import com.palmergames.bukkit.towny.exceptions.NotRegisteredException;
```

You've probably want to know how to get the resident so that you can use the above code, so here it is:

### Getting a Resident from a Player

Most of the time getting the resident object of a player is something you'll need quite often. Here is how you do it:
```java
import com.palmergames.bukkit.towny.object.Resident;

Resident resident = TownyAPI.getInstance().getDataSource().getResident(player.getName());
```

### Getting a Player from a Resident

If you have a Resident object and you want to get the Bukkit Player object it is done this way;
```
Player player = Bukkit.getServer().getPlayer(resident.getName());
```

### Getting a Town

Getting a town can be much like what you've seen already:
```java
import com.palmergames.bukkit.towny.object.Town;

//When you've already got a resident.
if (resident.hasTown())
   Town town = TownyAPI.getInstance().getDataSource().getTown(resident.getTown()); 

//When you've already got a townblock.
if (townblock.hasTown())
   Town town = TownyAPI.getInstance().getDataSource().getTown(townblock.getTown());
```
You can skip the .hasTown() checks if you want to surround your code with a Try/Catch block.

### Getting a Nation

Getting a town can be much like what you've seen already:
```java
import com.palmergames.bukkit.towny.object.Nation;

//When you've already got a town.
if (town.hasNation())
    Nation nation = TownyAPI.getInstance().getDataSource().getNation(town.getNation()); 
//When you've already got a resident.
if (resident.hasTown() && resident.getTown().hasNation())
    Nation nation = TownyAPI.getInstance().getDataSource().getNation(resident.getTown().getNation());
```
You can skip the .hasNation() checks if you want to surround your code with a Try/Catch block.

### Checking if a player can build/destroy somewhere

Using the PlayerCacheUtil you can easily test if a player can perform either of the four ActionTypes found in Towny (Build, Destroy, Switch, Item_use.)
```java
boolean bBuild = PlayerCacheUtil.getCachePermission(player, block.getLocation(), block.getType(), TownyPermission.ActionType.BUILD);
```

### Checking if Towny would prevent PVP damage

A common use of the API in magic/combat/rpg plugins is needing to know if Towny would prevent PVP combat. This is simple using our CombatUtil: While using Bukkit's EntityDamageByEntityEvent doing the following:

import com.palmergames.bukkit.towny.utils.CombatUtil;

private Towny towny = (Towny) Bukkit.getServer().getPluginManager().getPlugin("Towny");
```java
@EventHandler(priority = EventPriority.LOWEST)
private void playerPVPEvent (EntityDamageByEntityEvent event) { 
    Entity attacker = event.getDamager();
    Entity defender = event.getEntity();
        
    if (CombatUtil.preventDamageCall(towny, attacker, defender))
            return;
}
```
The preventDamageCall will return True if Towny would stop the damage from happening.

## Some useful events

Events thrown by Towny can be imported here: 
```java
import com.palmergames.bukkit.towny.event.*EventNameHere*
```
[For a full list of Events check out the github.](https://github.com/TownyAdvanced/Towny/tree/master/src/com/palmergames/bukkit/towny/event)

## Of use to Shop Plugin developers:

-   Our [ShopPlotUtil](https://github.com/TownyAdvanced/Towny/blob/master/src/com/palmergames/bukkit/towny/utils/ShopPlotUtil.java) provides easy-to-use tests to query if a player can make a shop at a location.

## Working with Town and TownBlock MetaData

Visit [this](https://github.com/TownyAdvanced/Towny/wiki/Configuring-Metadata-in-Towns-and-Townblocks) page for instructions on manipulating MetaData Towny can save for you.


## Example plugins using the TownyAPI:

-   [TownyFlight](https://github.com/TownyAdvanced/TownyFlight)

