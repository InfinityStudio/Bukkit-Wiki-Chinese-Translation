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

  * **[Login**](http://wiki.bukkit.org/Special:UserLogin?returnto=CraftBukkit_Command_Line_Arguments)
  * [Don't have an account? **Register**](http://wiki.bukkit.org/Special:UserLogin/signup)

##### Namespaces

  * [Page](/CraftBukkit_Command_Line_Arguments)
  * [Discussion](/Talk:CraftBukkit_Command_Line_Arguments)

####

##### Variants

#### Share

##### Share

  * ![](/extensions/Social/images/square_icons/twitter.png)![](/extensions/Social/images/square_icons/facebook.png)![](/extensions/Social/images/square_icons/googleplus.png)![](/extensions/Social/images/square_icons/reddit.png)![](/extensions/Social/images/square_icons/tumblr.png)

##### Views

  * [View](/CraftBukkit_Command_Line_Arguments)
  * [Edit](/index.php?title=CraftBukkit_Command_Line_Arguments&action=edit)
  * [History](/index.php?title=CraftBukkit_Command_Line_Arguments&action=history)

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

  * [What links here](/Special:WhatLinksHere/CraftBukkit_Command_Line_Arguments)
  * [Related changes](/Special:RecentChangesLinked/CraftBukkit_Command_Line_Arguments)
  * [Special pages](/Special:SpecialPages)
  * [Printable version](/index.php?title=CraftBukkit_Command_Line_Arguments&printable=yes)
  * [Permanent link](/index.php?title=CraftBukkit_Command_Line_Arguments&oldid=9274)
  * [Page information](/index.php?title=CraftBukkit_Command_Line_Arguments&action=info)

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

#  CraftBukkit Command Line Arguments

From BukkitWiki

Jump to: navigation, search

**This page is part of the official Bukkit Documentation**

This page has been accepted and included in the official Bukkit Documentation.
You can discuss discrepancies, issues, or errors in the article on its [Talk
page](/Talk:CraftBukkit_Command_Line_Arguments).

Craftbukkit gives you the ability from the command line to specify a wide
variety of start-up options. Below is a list of the current command line
arguments you can pass when first starting cb.jar from the command line.

  

Command Line Option  Shortcut  Description  Example

\--help

-? 
Shows the help menu. Following the printout, the JVM Terminates.

java -jar cb.jar -?

\--bukkit-settings <file>.yml

-b <file>.yml 

Allows you to define the bukkit.yml settings file used during startup.

  

The default bukkit config file is bukkit.yml

java -jar cb.jar -b potatos.yml

\--config <config file>

-c <config file>.yml 

Allows you to define the config file used in starting the server.

  

The default config file is "server.properties"

java -jar cb.jar --config potatos.properties

\--date-format <definition>

-d <definition>

Allows you to define the date format used in your log files.  

  

\--host <IP Address>  
\--server-ip <IP Address>

-h <IP Address>

Allows you to define the hostname or IP address to listen on.

This argument is only for the IP Address, not the port.

  

The default is located in your server.properties

java -jar cb.jar -h www.potatos.com

\--log-append <true/false>

  

Allows you to define wether or not the logfile should be appended to with each
startup or if it should be overidden.

This argument only accepts boolean values true or false.

  

The default value is true

java -jar cb.jar --log-append false

\--log-count <number>

  

Allows you to define how many logs to cycle through.

Log cycling begins when the maximum log size has been reached.

  

The default number of logs is 1

java -jar cb.jar --log-count 10

\--log-limit <# of lines>

  

Allows you to define the maximum size your log file can become in number of
lines.

0 = unlimited

  

The default maximum log size is 0 (unlimited)

java -jar cb.jar --log-limit 1337

\--log-pattern <name>

  

Allows you to define the names used for your log files

  

The default log name is "server.log"

java -jar cb.jar --log-pattern potatos.log

\--log-strip-color

  

Strips log colors when saving to the log.

java -jar cb.jar --log-strip-color

\--noconsole

  

Disables console output entirely. Log files are still written, though.

java -jar cb.jar --noconsole

\--nojline

  

Disables the JLine console, removes the '>', sets the timestamp to vanilla's
and sets the language to English.

This is useful for users who do not have the Visual C++ 2008 redistributable
on Windows.

Linux and UNIX users can safely ignore this option

java -jar cb.jar --nojline

-Djline.terminal=jline.UnsupportedTerminal 
  

Disables the JLine console and removes the '>'.

This is useful for users who do not have the Visual C++ 2008 redistributable
on Windows.

Linux and UNIX users can safely ignore this option

java -jar cb.jar -Djline.terminal=jline.UnsupportedTerminal

-Dlog4j.configurationFile=log4j2.xml 
  

Allows a customized log4j2.xml file without modifying the CraftBukkit.jar.
log4j2.xml allows a server admin to modify the logging (latest.log) file found
in MC 1.7.2 (and above). This is useful for server admins who want to modify
server log rotation, or change the location/name of the new server log.

If you do not specify a path for the log4j2.xml file, it will grab the
log4j2.xml file from the current working directory, NOT the server directory.

Since this is technically not a CraftBukkit command line option, but rather a
JVM option, the option must be added before the -jar option.

Additional log4j2.xml documentation:  
<http://logging.apache.org/log4j/2.x/manual/appenders.html#RandomAccessFileApp
ender>  
<http://logging.apache.org/log4j/2.x/manual/layouts.html#PatternLayout>

Default log4j2.xml file:  
<https://raw.github.com/Bukkit/CraftBukkit/master/src/main/resources/log4j2.xm
l>

java -Dlog4j.configurationFile=/opt/server/log4j2.xml -jar cb.jar

\--online-mode <true/false>

-o <true/false>

Allows you to define wether or not the server should run in online mode.  
This argument only accepts a boolean answer, true or false.

  

The default is located in your server.properties

java -jar cb.jar -o true

\--plugins <directory>

-P <directrory>

Allows you to define the plugins directory to use when starting the server.

The path should be relative to the location of your current location in your
system.

  

The default plugins directory is "plugins/"

java -jar cb.jar -P notplugins/

\--port <port number>  
\--server-port <port number>

-p <port number>

Allows you to define the port number your server will listen on.

This argument is only for the Port Number, not the IP Address.

  

The default is located in your server.properties

java -jar cb.jar -p 1337

  

\--size <# of players>  
\--max-players <# of players>

-s <# of players>

Allows you to define the number of players that are allowed to connect to your
server at one time.

This argument only accepts integer, or whole number, answers.

  

The default is located in your server.properties

java -jar cb.jar -s 36

\--version

-v 

Prints the current CraftBukkit Server and Bukkit API Versions. Similar to
typing /version in-game

Following the printout, the JVM terminates.

java -jar cb.jar -v

\--world-dir <worlds dir>  
\--universe <worlds dir>

-W <worlds dir>

Allows you to define the folder/directory containing your worlds.  
All worlds will be loaded and stored here.

  

The default is located in bukkit.yml

java -jar cb.jar -W C:/minecraft/worlds

\--world <world name>  
\--level-name <world name>

-w <world name>

Allows you to define the startup world your server will use.

  

The default is located in your server.properties

java -jar cb.jar -w evilsephisevil

Language

  **English** • [Беларускі](/index.php?title=CraftBukkit_Command_Line_Arguments/by&action=edit&redlink=1) • [Deutsch](/index.php?title=CraftBukkit_Command_Line_Arguments/de&action=edit&redlink=1) • [español](/index.php?title=CraftBukkit_Command_Line_Arguments/es&action=edit&redlink=1) • [suomi](/index.php?title=CraftBukkit_Command_Line_Arguments/fi&action=edit&redlink=1) • [français](/CraftBukkit_Command_Line_Arguments/fr) • [italiano](/index.php?title=CraftBukkit_Command_Line_Arguments/it&action=edit&redlink=1) • [한국어](/CraftBukkit_Command_Line_Arguments/ko) • [Nederlands](/index.php?title=CraftBukkit_Command_Line_Arguments/nl&action=edit&redlink=1) • [norsk bokmål](/index.php?title=CraftBukkit_Command_Line_Arguments/no&action=edit&redlink=1) • [polski](/index.php?title=CraftBukkit_Command_Line_Arguments/pl&action=edit&redlink=1) • [português](/index.php?title=CraftBukkit_Command_Line_Arguments/pt&action=edit&redlink=1) • [русский](/index.php?title=CraftBukkit_Command_Line_Arguments/ru&action=edit&redlink=1) • [lietuvių](/index.php?title=CraftBukkit_Command_Line_Arguments/lt&action=edit&redlink=1) • [česky](/index.php?title=CraftBukkit_Command_Line_Arguments/cs&action=edit&redlink=1)

Retrieved from "[http://wiki.bukkit.org/index.php?title=CraftBukkit_Command_Li
ne_Arguments&oldid=9274](http://wiki.bukkit.org/index.php?title=CraftBukkit_Co
mmand_Line_Arguments&oldid=9274)"

[Category](/Special:Categories):

  * [Docs](/Category:Docs)

  * This page was last modified on 28 January 2014, at 02:12.
  * Content is available under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/) unless otherwise noted. Game content and materials are trademarks and copyrights of their respective publisher and its licensors. All rights reserved.  
This site is a part of Curse, Inc. and is not affiliated with the game
publisher.

  * [Privacy policy](/BukkitWiki:Privacy_policy)
  * [About BukkitWiki](/BukkitWiki:About)
  * [Disclaimers](/BukkitWiki:General_disclaimer)
  * [Mobile view](http://wiki.bukkit.org/index.php?title=CraftBukkit_Command_Line_Arguments&mobileaction=toggle_view_mobile)
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

