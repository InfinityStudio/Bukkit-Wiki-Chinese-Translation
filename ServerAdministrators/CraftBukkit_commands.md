#  CraftBukkit Commands
**This page has been suggested for inclusion in the Official Documentation**

This page has been **marked for inclusion in the Bukkit Offical Documentation
section, Docs**. You can deliberate about its inclusion on its [Talk
page](/Talk:CraftBukkit_Commands).

The following are all the server commands either a server administrator or
admin in-game can enter with CraftBukkit out-of-the-box. In addition to the
[original vanilla SMP
commands](http://www.minecraftwiki.net/wiki/SMP_Server_commands) there are 4
additional commands which are specific to CraftBukkit. CraftBukkit provides
built-in permissions which can be used in a permissions manager. Defaults are
also observed for the permissions. There are also additional permissions which
group together several of the single permissions.

Bukkit Commands and Permissions

Command  Description  Usage  Permission  Permission Default

version

Gives the version number of CraftBukkit this is installed on the server.

version

bukkit.command.version

Everybody

plugins

Lists all installed plugins on the server.

plugins

bukkit.command.plugins

Everybody

reload

Stops and restarts all plugins on the server.

reload

bukkit.command.reload

Operators

timings

Records timings for all plugin events.

timings <reset|merged|separate>

bukkit.command.timings

Operators

Default Minecraft Commands and Permissions

Command  Description  Usage  Bukkit Permission  Mojang Permission  Permission
Default

tell <_player_> <_message_>

Allows the user to privately message another player.

tell Notch Hey, how's it going?

bukkit.command.tell

minecraft.command.tell

Everybody

kill

Allows the player to kill themselves, returning to spawn (and losing items).

kill

bukkit.command.kill

minecraft.command.kill

Everybody

me

Says a message from the player's point of view: *player1 is building a castle!

me is building a castle!

bukkit.command.me

minecraft.command.me

Everybody

help or ?

Shows a list of server commands in the console or in-game.

help

bukkit.command.help

minecraft.command.help

Everybody

kick <_player_>

Removes a player from the server.

kick player1

bukkit.command.kick

minecraft.command.kick

Operators

ban <_player_>

Bans a player from the server.

ban player1

bukkit.command.ban.player

minecraft.command.ban

Operators

banlist

Shows the banned players.

banlist

bukkit.command.ban.list

minecraft.command.banlist

Operators

pardon <_player_>

Pardons a banned player so that they can connect again.

pardon player1

bukkit.command.unban.player

minecraft.command.pardon

Operators

ban-ip <_ip_>

Bans an IP address from the server.

ban-ip 192.168.1.5

bukkit.command.ban.ip

minecraft.command.ban-ip

Operators

pardon-ip <_ip_>

Pardons a banned IP address so that they can connect again.

pardon-ip 192.168.1.5

bukkit.command.unban.ip

minecraft.command.pardon-ip

Operators

op <_player_>

Turns a player into a server operator.

op player1

bukkit.command.op.give

minecraft.command.op

Operators

deop <_player_>

Removes server operator status from a player.

deop player1

bukkit.command.op.take

minecraft.command.deop

Operators

tp <_player1_> <_player2_>  

tp <_player1_> <_x_> <_y_> <_z_>

Moves player1 to the same location as player2.

Moves player1 to the exact coordinates.

tp player1 player2  

tp player1 0 70 12

bukkit.command.teleport

minecraft.command.tp

Operators

give <_player_> <_data-value_> [_amount_ [_damage_]]

Gives player blocks/items blockID _data-value_. _amount_ is is how many of the
block/item to give (Default: 1). _damage_ is the damage value of the
block/item (Default: 0). [Data
Values](http://www.minecraftwiki.net/wiki/Data_values).

give player1 267 _(gives player1 1 iron sword)_  
give player1 3 31 _(gives player1 31 blocks of dirt)_

bukkit.command.give

minecraft.command.give

Operators

stop

Gracefully stops the server (i.e. allows the server to save the worlds and
lets all the plugins shut down properly).

stop

bukkit.command.stop

minecraft.command.stop

Operators

save-all

Forces a server-wide level save of the terrain.

save-all

bukkit.command.save.perform

minecraft.command.save-all

Operators

save-off

Disables automatic terrain saving (useful for backup scripts).

save-off

bukkit.command.save.disable

minecraft.command.save-off

Operators

save-on

Re-enables automatic terrain saving.

save-on

bukkit.command.save.enable

minecraft.command.save-on

Operators

list

Lists all currently connected players.

list

bukkit.command.list

minecraft.command.list

Operators

say <_message_>

Broadcasts a message to all players as the server.

say Hello minecraft world!

bukkit.command.say

minecraft.command.say

Operators

whitelist <_on_/_off_>

Enable or disable whitelisting (i.e. only listed players may join).

whitelist on  
whitelist off

bukkit.command.whitelist.enable  
bukkit.command.whitelist.disable

minecraft.command.whitelist

Operators

whitelist <_add_/_remove_> <_player_>

Add or remove a player from the whitelist.

whitelist add Notch  
whitelist remove Notch

bukkit.command.whitelist.add  
bukkit.command.whitelist.remove

minecraft.command.whitelist

Operators

whitelist list

Lists all currently whitelisted players.

whitelist list

bukkit.command.whitelist.list

minecraft.command.whitelist

Operators

whitelist reload

Reload the whitelist from file. Useful if you edited the file manually.

whitelist reload

bukkit.command.whitelist.reload

minecraft.command.whitelist

Operators

time <_add_/_set_> <_amount_>

_Add_ to or _set_ the world time. _Amount_ may be a number between 0 and
24000, inclusive, where 0 is dawn (i.e. clock is bisected; left side is day)
and 12000 is noon.

time add 6000  
time set 0

bukkit.command.time.add  
bukkit.command.time.set

minecraft.command.time

Operators

gamemode <0/1/2> <_player_>

Change the game mode of a player. 0 = Survival mode, 1 = Creative mode, 2 =
Adventure mode.

gamemode 1 Notch

bukkit.command.gamemode

minecraft.command.gamemode

Operators

xp <_player_> <_amount_>

Gives the specified player a certain amount of experience.

xp Notch 100

bukkit.command.xp

minecraft.command.xp

Operators

toggledownfall

Turn on or off rain/snow in the current world.

toggledownfall

bukkit.command.toggledownfall

minecraft.command.toggledownfall

Operators

defaultgamemode <0/1/2/3>

Change the gamemode of new players joining the server.

defaultgamemode 1

bukkit.command.defaultgamemode

minecraft.command.defaultgamemode

Operators

seed

Outputs the world seed.

seed

bukkit.command.seed

minecraft.command.seed

Operators

enchant <_user_> <_enchant number or ID_> <_level_> <_force_>

Enchants the item in the user's hand.

enchant Notch 1 1 1

bukkit.command.enchant

minecraft.command.enchant

Operators

weather <_weather_>

Changes the weather in-game.

weather clear

bukkit.command.weather

minecraft.command.weather

Operators

clear <_user_>

Clears a user's inventory.

clear Notch

bukkit.command.clear

minecraft.command.clear

Operators

difficulty <_diff level_>

Changes the difficulty of the server.

difficulty 0

bukkit.command.difficulty

minecraft.command.difficulty

Operators

spawnpoint <_User_> <_x_> <_y_> <_z_>

Sets the spawnpoint of the user specified.

spawnpoint Notch

bukkit.command.spawnpoint

minecraft.command.spawnpoint

Operators

gamerule

Prints out the current game rules being applied to the server.

gamerule

bukkit.command.gamerule

minecraft.command.gamerule

Operators

effect <_player_> <_effect id_> [_seconds_] [_amplifier_]

Adds the specified effect to a player for the duration of 30 seconds or as
specified by the user.

effect Notch 9

bukkit.command.effect

minecraft.command.effect

Operators

setidletimeout <Minutes until kick>

Sets the server's idle timeout

setidletimeout 10

bukkit.command.setidletimeout

minecraft.command.setidletimeout

Operators

setworldspawn OR setworldspawn <x> <y> <z>

Sets a worlds's spawn point. If no coordinates are specified, the player's
coordinates will be used.

setworldspawn 0 0 0

bukkit.command.setworldspawn

minecraft.command.setworldspawn

Operators

achievement give <stat_name> [player]

Gives the specified player an achievement or changes a statistic value. Use
'*' to give all achievements.

achievement give * Notch

bukkit.command.achievement

minecraft.command.achievement

Operators

Additional Permissions

Permission  Description  Default

bukkit.broadcast.user

Allows the user to receive user broadcasts

Everybody

bukkit.command.plugins

Allows user to look at plugins. Disables: /pl and /plugins

Everybody

bukkit.command.baN

Combines the Player ban and the IP ban permissions

Operators

bukkit.command.unban

Combines the Player Unban and IP Unban permissions.

Operators

bukkit.command.op

Combines the Op Give and Op Take permissions.

Operators

bukkit.command.time

Combines the Time Add and Time Set permissions.

Operators

bukkit.command.save

Combines the Save Enable, Save Disable and Save Perform permissions.

Operators

bukkit.broadcast

Allows the user to receive all broadcast messages.

Operators

bukkit.broadcast.admin

Allows the user to receive administrative broadcasts.

Operators
