  * Curse Sites __
    * Top Sites
    * __[Gamepedia](http://www.gamepedia.com/)
    * __[MMO-Champion](http://www.mmo-champion.com/)
    * __[Arena Junkies](http://www.arenajunkies.com/)
    * __[Reign of Gaming](http://www.reignofgaming.net)
    * __[LoL Pro](http://lolpro.com)
    * __[Minecraft Forums](http://www.minecraftforum.net/)
    * __[Guild Wars 2 Guru](http://guildwars2guru.com)
    * __[FPS General](http://fpsgeneral.com)
    * [Curse.com](http://www.curse.com/)
  * [Help](http://support.curse.com/)
  * [Get an Epic Experience with Premium](http://www.curse.com/premium)
  * [Support This Wiki](http://store.curse.com/products/gamepedia?pagesize=12)

  * **[Login**](http://wiki.bukkit.org/Special:UserLogin?returnto=CraftBukkit_Commands)
  * [Don't have an account? **Register**](http://wiki.bukkit.org/Special:UserLogin/signup)

##### Namespaces

  * [Page](/CraftBukkit_Commands)
  * [Discussion](/Talk:CraftBukkit_Commands)

####

##### Variants

#### Share

##### Share

  * ![](/extensions/Social/images/square_icons/twitter.png)![](/extensions/Social/images/square_icons/facebook.png)![](/extensions/Social/images/square_icons/googleplus.png)![](/extensions/Social/images/square_icons/reddit.png)![](/extensions/Social/images/square_icons/tumblr.png)

##### Views

  * [View](/CraftBukkit_Commands)
  * [Edit](/index.php?title=CraftBukkit_Commands&action=edit)
  * [History](/index.php?title=CraftBukkit_Commands&action=history)

##### Actions

##### Search

![](http://hydra-media.cursecdn.com/wiki.bukkit.org/b/bc/Wiki.png?version=0a20
81b450303b747b43d45d178fd129)

##### Wiki

  * [Main page](/Main_Page)
  * [Recent changes](/Special:RecentChanges)
  * [Random page](/Special:Random)
  * [Wiki Issue Tracker](https://bukkit.atlassian.net/browse/WIKI)
  * [Help](/Help:Contents)

##### Community

  * [Bukkit Website](http://www.bukkit.org)
  * [Bukkit Forums](http://forums.bukkit.org)
  * [BukkitDev](http://dev.bukkit.org)
  * [Get Bukkit](http://dl.bukkit.org)
  * [Minecraft Website](http://minecraft.net)
  * [Minecraft Wiki](http://www.minecraftwiki.net)

##### Tools

  * [What links here](/Special:WhatLinksHere/CraftBukkit_Commands)
  * [Related changes](/Special:RecentChangesLinked/CraftBukkit_Commands)
  * [Special pages](/Special:SpecialPages)
  * [Printable version](/index.php?title=CraftBukkit_Commands&printable=yes)
  * [Permanent link](/index.php?title=CraftBukkit_Commands&oldid=10675)
  * [Page information](/index.php?title=CraftBukkit_Commands&action=info)

#####

![](http://media-mercury.cursecdn.com/attachments/1/806/mccapepromo.png)
![](http://media-
mercury.cursecdn.com/attachments/1/809/pacmanfriends_sidebadge_tall.png)
![](http://media-
mercury.cursecdn.com/attachments/1/810/outcast_sidebadge_tall.png) ![](http
://media-mercury.cursecdn.com/attachments/0/180/warface.png) ![](http://media-
mercury.cursecdn.com/attachments/0/95/destiny.png) ![](http://media-
mercury.cursecdn.com/attachments/0/365/gardenwarfare_sidebadge_tall.png)

#####

![](/extensions/Social/images/square_icons/twitter.png)

![](/extensions/Social/images/square_icons/facebook.png)

![](/extensions/Social/images/square_icons/youtube.png)

![](/extensions/Social/images/square_icons/googleplus.png)

_Welcome to the BukkitWiki!_

This Wiki is home to Bukkit's documentation and regulations surrounding the
Bukkit Project and it's services. Want to help out? We would love to have you!
Signup to get started!

[Home](/Main_Page)

#  CraftBukkit Commands

From BukkitWiki

(Redirected from [CraftBukkit
commands](/index.php?title=CraftBukkit_commands&redirect=no))

Jump to: navigation, search

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

## [[edit](/index.php?title=CraftBukkit_Commands&action=edit&section=1)]
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

## [[edit](/index.php?title=CraftBukkit_Commands&action=edit&section=2)]
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

## [[edit](/index.php?title=CraftBukkit_Commands&action=edit&section=3)]
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

Retrieved from "[http://wiki.bukkit.org/index.php?title=CraftBukkit_Commands&o
ldid=10675](http://wiki.bukkit.org/index.php?title=CraftBukkit_Commands&oldid=
10675)"

[Category](/Special:Categories):

  * [DocsNominees](/Category:DocsNominees)

  * This page was last modified on 23 August 2014, at 21:14.
  * Content is available under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/) unless otherwise noted. Game content and materials are trademarks and copyrights of their respective publisher and its licensors. All rights reserved.  
This site is a part of Curse, Inc. and is not affiliated with the game
publisher.

  * [Privacy policy](/BukkitWiki:Privacy_policy)
  * [About BukkitWiki](/BukkitWiki:About)
  * [Disclaimers](/BukkitWiki:General_disclaimer)
  * [Mobile view](http://wiki.bukkit.org/index.php?title=CraftBukkit_Commands&mobileaction=toggle_view_mobile)
  * ![CC BY-NC-SA 3.0](http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png)
  * ![Powered by MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png) ![Part of Gamepedia](/extensions/Curse/Icons/gamepedia_poweredby.png)

# Curse

## Curse is the **#1 Resource** for core online gamers.

#### Not a Member?

##### Get your Free Account!

[Sign up for Free!](http://www.curse.com)

  * __
  * __
  * __
  * __

#### Featured Sites

[More](http://www.curse.com)

  * [

#### Guild Wars 2 Guru

__Guild Wars 2 Guru

    The latest and greatest on Tyria.
](http://www.guildwars2guru.com)

  * [

#### LoL Pro

__LoL Pro

    Dominate with Pro LoL guides.
](http://www.lolpro.com)

  * [

#### MMO-Champion

__MMO-Champion

    Keep ahead with the champions of WoW coverage.
](http://www.mmo-champion.com)

  * [

#### GW2DB

__GW2DB

    Explore Tyria with Curse and GW2DB.
](http://www.gw2db.com)

#### Browse

  * [Core]()
    * [Curse](http://www.curse.com/)
    * [MMO-Champion](http://www.mmo-champion.com/)
    * [WowStead](http://www.wowstead.com/)
    * [CurseForge](http://www.curseforge.com/)
    * [WowAce](http://www.wowace.com/)
    * [SkyrimForge](http://www.skyrimforge.com/)
    * [SC2Mapster](http://www.sc2mapster.com/)
    * [LoLPro](http://www.lolpro.com/)
    * [ExilePro](http://www.exilepro.com)
  * [Community]()
    * [Minecraft Forum](http://www.minecraftforum.net/)
    * [Terraria Online](http://www.terrariaonline.com/)
    * [Arena Junkies](http://www.arenajunkies.com/)
    * [Guild Wars 2 Guru](http://guildwars2guru.com/)
    * [DiabloFans](http://www.diablofans.com/)
    * [FPS General](http://www.fpsgeneral.com/)
    * [DarthHater](http://www.darthhater.com/)
    * [Defiance Forum](http://www.defianceforum.com/)
    * [Wildstar Forums](http://www.wildstarforums.com/)
  * [Database]()
    * [Guild Wars 2 DB](http://www.gw2db.com/)
    * [Zybez](http://www.zybez.net/)
    * [DarthHater DB](http://db.darthhater.com/)
    * [Aion Armory](http://www.aionarmory.com/)
    * [WoW Database](http://www.wowdb.com/)
    * [Marriland](http://www.marriland.com)
  * [Wiki]()
    * [Minecraft Wiki](http://www.minecraftwiki.net/)
    * [Terraria Wiki](http://wiki.terrariaonline.com/)
    * [Wowpedia](http://www.wowpedia.org/)
    * [Skyrim Wiki](http://www.skyrimwiki.com/)
    * [Wiki SWTOR](http://www.wikiswtor.com/)
    * [Dragon Nest Wiki](http://www.dragonnestwiki.com/)
    * [Vindictus Wiki](http://www.vindictuswiki.com/)

Back to Top

  * [About Us](http://www.curse.com/about)
  * [Advertising](http://www.curse.com/advertising/overview)
  * [Privacy Policy](http://www.curse.com/privacy)
  * [Terms of Service](http://www.curse.com/terms)
  * [Premium Terms of Service](http://www.curse.com/premiumterms)
  * [Curse Newsletter](http://www.curse.com/newsletter)
  * [Jobs at Curse](http://www.curse.com/jobs)

Handcrafted in San Francisco & Huntsville

![](http://b.scorecardresearch.com/p?c1=2&c2=6035118&cv=2.0&cj=1)

![](//secure-us.imrworldwide.com/cgi-bin/m?ci=us-
603339h&cg=0&cc=1&ts=noscript)

