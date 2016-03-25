# MelonDamageLib
Better Damage Management and Kill Assist Tracker

### Server Owners
If the plugin is installed on a server, it will overwrite the default death messages as well as provide a players a summary of what damaged them within 5 seconds of their death

### Developers
DamageLib can be used to assist with damage tracking, including for custom damage.

#### Logging Custom Damage

When you want to log the custom damage, just instantiate a new **OtherDamageTick**.

```java

Player player = ...; // Also compatible with entities, there's just no chat output
double damage = 10; // My damage
EntityDamageEvent.DamageCause cause = EntityDamageEvent.DamageCause.CUSTOM; // An associated damage cause
String name = "Special Move"; // Used for display purposes
long time = System.currentTimeMillis(); // The time of when this happened. Damage received over 5 seconds ago will not be shown.

OtherDamageTick tick = new OtherDamageTick(damage, cause, name, time);
DamageManager.logTick(player.getUniqueId(), tick);

```

#### Custom Damage Tick
A damage tick simply represents a type of damage. They're used to assist with tracking of past damage events.

New custom damage tick classes should extend the **DamageTick** class.

#### Events

##### PlayerAssistedWithDeathEvent
This event contains the player that was killed, and a **KillAssist** object, which contains the player who made the assist, the percentage of damage the player dealt, and the raw amount of damage they dealt.

For an assist to be registered, the cause of death must not match the player on the assist, and the assist must have been for at least **20%** of the total PVP damage.

By default, KillAssists are only used to modify the death message, however this event can be listened for by other plugins for more accurate statistic tracking.

__Pull requests welcome. I'll be updating this resource as I need it for my own projects. You're welcome to use it, as long as you contribute whatever changes you've made. See the LICENSE.TXT for more info.__

[Download MelonDamageLib.jar](http://up.turqmelon.com/2a213V1T071w)
