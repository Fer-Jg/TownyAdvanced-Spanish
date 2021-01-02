#### Required: Towny 0.96.5.11 or newer.

#### Required townyperms.yml edits:

To the mayor and town assistant rank add:
`- towny.town.siege.*`

It is recommended you add the `towny.town.siege.points` node to the sheriff while also creating a guard rank:
```
        sheriff:
            - towny.command.town.toggle.jail
            - towny.outlaw.jailer
            - towny.town.siege.points
        guard:
            - towny.town.siege.points
```

To the king and nation assistant rank add:
`- towny.nation.siege.*`

and then create the following nation ranks:
```
        soldier:
            - towny.nation.siege.points
        captain:
            - towny.nation.siege.points
            - towny.nation.siege.leadership
        general:
            - towny.nation.siege.*
```

For your server staff add:
```
towny.siege.war.immune.to.war.nausea 
towny.siege.war.immune.to.battle.fatigue 
```