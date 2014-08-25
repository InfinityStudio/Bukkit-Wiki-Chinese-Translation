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

  * **[Login**](http://wiki.bukkit.org/Special:UserLogin?returnto=Setting_Up_Your_Workspace)
  * [Don't have an account? **Register**](http://wiki.bukkit.org/Special:UserLogin/signup)

##### Namespaces

  * [Page](/Setting_Up_Your_Workspace)
  * [Discussion](/index.php?title=Talk:Setting_Up_Your_Workspace&action=edit&redlink=1)

####

##### Variants

#### Share

##### Share

  * ![](/extensions/Social/images/square_icons/twitter.png)![](/extensions/Social/images/square_icons/facebook.png)![](/extensions/Social/images/square_icons/googleplus.png)![](/extensions/Social/images/square_icons/reddit.png)![](/extensions/Social/images/square_icons/tumblr.png)

##### Views

  * [View](/Setting_Up_Your_Workspace)
  * [Edit](/index.php?title=Setting_Up_Your_Workspace&action=edit)
  * [History](/index.php?title=Setting_Up_Your_Workspace&action=history)

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

  * [What links here](/Special:WhatLinksHere/Setting_Up_Your_Workspace)
  * [Related changes](/Special:RecentChangesLinked/Setting_Up_Your_Workspace)
  * [Special pages](/Special:SpecialPages)
  * [Printable version](/index.php?title=Setting_Up_Your_Workspace&printable=yes)
  * [Permanent link](/index.php?title=Setting_Up_Your_Workspace&oldid=10592)
  * [Page information](/index.php?title=Setting_Up_Your_Workspace&action=info)

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

#  Setting Up Your Workspace

From BukkitWiki

Jump to: navigation, search

This page will go through some of the tools that you will need to use to work
with Bukkit and building Bukkit plugins.

## Contents

  * 1 Tools
    * 1.1 Java Development Kit
      * 1.1.1 Which version of the JDK?
      * 1.1.2 64-bit (x64) or 32-bit (x86)?
    * 1.2 Git
      * 1.2.1 Using Git
        * 1.2.1.1 GitHub
    * 1.3 Apache Maven
      * 1.3.1 Using Maven
    * 1.4 Integrated Development Environments
      * 1.4.1 Eclipse
      * 1.4.2 NetBeans
      * 1.4.3 IntelliJ IDEA
  * 2 Where To From Here

# [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=1)]
Tools

There is some developer choice when it comes to what you use to build your
software, however there are some key tools every developer needs. Even if you
only want to make plugins, there are some tools that will make your job
easier, and if you to go open source, easier for everyone who helps you!

## [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=2)]
Java Development Kit

A JDK (Java Development Kit) is required to compile Java for use in the JRE
(Java Runtime Environment). The latest version of the JDK is available from
the [Oracle Technology
Network](http://www.oracle.com/technetwork/java/javase/downloads/index.html).

### [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=3)]
Which version of the JDK?

There are multiple versions of Java, and consequently, multiple versions of
the JDK. Both Bukkit and Minecraft are now compiled for Java 6. Most Bukkit
servers are running Java 6, but a few run Java 7. Generally, newer versions of
the JDK can target older Java versions, however, by default they target their
own version. Programs and plugins compiled with a new version of Java are not
compatible with older versions of the JRE, attempting to run such a plugin
results in a [UnsupportedClassVersionError](http://docs.oracle.com/javase/1.5.
0/docs/api/index.html?java/lang/UnsupportedClassVersionError.html). In
practice, it is common to use the JDK version that corresponds with your
runtime environment.

### [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=4)]
64-bit (x64) or 32-bit (x86)?

Unless your computer is not capable of running 64-bit software, you should use
a 64-bit (x64) JDK. The rest of the development environment will need to match
the version of the JDK you have installed. On 64-bit systems it is possible to
have both 64-bit and 32-bit JDKs installed at the same time.

## [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=5)]
Git

![git](http://hydra-media.cursecdn.com/wiki.bukkit.org/thumb/2/29/Git-Logo-
2Color.png/40px-Git-Logo-2Color.png?version=03ffd9ff8306dfaf62725ef54b60f1e5)
is a distributed version control system. The Bukkit Project manages all its
code through Git. Git allows the lone developer to keep track of their work
and different developers to collaborate on work, tracking all changes that
were made and by whom. It is very powerful, and consequently can be a little
difficult to use sometimes. The latest version of git can be found on
[here](http://git-scm.com/download) on the git-scm site.

### [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=6)]
Using Git

Detailed instructions for installing and using git can be found in the [Pro
Git](http://git-scm.com/book) book on git-scm.

####
[[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=7)]
GitHub

[GitHub](https://github.com) is a code sharing website, and hosts the source
code of the Bukkit Project. Bukkit Projects can be cloned from our repository
found at [github.com/Bukkit](http://github.com/Bukkit).

Sharing of code works both ways - you can download shared code, but you can
also share yours with the world. This is a great idea in this open community,
as it allows others to help you with your project, or even develop new
features for your plugins! If you intend to contribute to the Bukkit Project
you must be willing to share your code. Additional instructions for using
GitHub can be found at [GitHub:Help](https://help.github.com/)

## [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=8)]
Apache Maven

[Apache Maven](http://maven.apache.org) is a tool that the Bukkit Project uses
to manage building our code. The latest version of Maven can be found on the
[here](http://maven.apache.org/download.html) on the Apache Maven site.

### [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=9)]
Using Maven

Additional instructions for installing and using Maven can be found
[here](http://maven.apache.org/guides/getting-started/maven-in-five-
minutes.html) on the maven site.

Once installed, Maven should be utilised to compile Bukkit and CraftBukkit.
Refer to the respective README files in the repositories for instructions.

## [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=10)]
Integrated Development Environments

The IDE (Intergraded Development Environment) is a program you can use to
compile and debug your plugins. An IDE is an optional piece of the developer
tool chain. It is possible to use notepad (or its equivalent) and produce a
working a plugin. An IDE however, makes the life of a developer much easier by
integrating powerful tools, providing syntax highlighting, and error checking.
The choice of which IDE to use is yours to make!

###
[[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=11)]
Eclipse

The [Eclipse IDE](http://www.eclipse.org/) is a popular choice among plugin
developers. The latest version, Eclipse Kepler (4.3.1), can be found
[here](http://www.eclipse.org/downloads/packages/) on the eclipse site. Plugin
developers should download the **Eclipse IDE for Java Developers**. Eclipse
provides Maven integration by means of the m2Eclipse plugin, Git integration
with by mean of the eGit plugin. Additionally, the
[YEdit](http://code.google.com/p/yedit/) plugin can be installed to provide a
YAML editor.

     _For general Eclipse IDE usage please refer to the [Eclipse documentaiton](http://www.eclipse.org/documentation/)._
     _For Maven integration usage please refer to the [m2eclipse documentation](http://www.sonatype.org/m2eclipse/)._
     _For Git integration usage please refer to the [eGit documentaiton](http://www.eclipse.org/egit/documentation/)._

###
[[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=12)]
NetBeans

The [Netbeans IDE](http://netbeans.org/) is developed by Oracle. The latest
version, 7.3, can be found [here](http://netbeans.org/downloads/) on the
Netbeans site. Plugin developers should download the **Netbeans Java SE
bundle**. Netbeans provides native integration with Maven and Git integration
by means of a Git plugin.

     _For usage instructions please refer to the [Netbeans documentation](http://netbeans.org/kb/index.html)._

###
[[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=13)]
IntelliJ IDEA

[IntelliJ IDEA](http://www.jetbrains.com/idea/) is another popular IDE. The
latest version, 13, can be found
[here](http://www.jetbrains.com/idea/download/index.html) on the IntelliJ
site. Plugin developers should download the **Community Edition**. IntelliJ
provides native integration with Maven and Git.

     _For usage instructions please refer to the [IntelliJ documentation](http://www.jetbrains.com/idea/documentation/index.jsp)._

# [[edit](/index.php?title=Setting_Up_Your_Workspace&action=edit&section=14)]
Where To From Here

There is lots more involved in actually developing and testing your code,
however hopefully you now have the tools to get started. If you find any
particularly useful tutorials make sure to link them here!

It is suggested that you start with [Plugin Tutorial](/Plugin_Tutorial).

Language

  **English** • [Беларускі](/index.php?title=Setting_Up_Your_Workspace/by&action=edit&redlink=1) • [Deutsch](/Setting_Up_Your_Workspace/de) • [español](/index.php?title=Setting_Up_Your_Workspace/es&action=edit&redlink=1) • [suomi](/index.php?title=Setting_Up_Your_Workspace/fi&action=edit&redlink=1) • [français](/Setting_Up_Your_Workspace/fr) • [italiano](/Setting_Up_Your_Workspace/it) • [한국어](/Setting_Up_Your_Workspace/ko) • [Nederlands](/index.php?title=Setting_Up_Your_Workspace/nl&action=edit&redlink=1) • [norsk bokmål](/index.php?title=Setting_Up_Your_Workspace/no&action=edit&redlink=1) • [polski](/Setting_Up_Your_Workspace/pl) • [português](/index.php?title=Setting_Up_Your_Workspace/pt&action=edit&redlink=1) • [русский](/Setting_Up_Your_Workspace/ru) • [lietuvių](/index.php?title=Setting_Up_Your_Workspace/lt&action=edit&redlink=1) • [česky](/index.php?title=Setting_Up_Your_Workspace/cs&action=edit&redlink=1)

Retrieved from "[http://wiki.bukkit.org/index.php?title=Setting_Up_Your_Worksp
ace&oldid=10592](http://wiki.bukkit.org/index.php?title=Setting_Up_Your_Worksp
ace&oldid=10592)"

[Category](/Special:Categories):

  * [Tutorials](/Category:Tutorials)

  * This page was last modified on 27 July 2014, at 22:10.
  * Content is available under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/) unless otherwise noted. Game content and materials are trademarks and copyrights of their respective publisher and its licensors. All rights reserved.  
This site is a part of Curse, Inc. and is not affiliated with the game
publisher.

  * [Privacy policy](/BukkitWiki:Privacy_policy)
  * [About BukkitWiki](/BukkitWiki:About)
  * [Disclaimers](/BukkitWiki:General_disclaimer)
  * [Mobile view](http://wiki.bukkit.org/index.php?title=Setting_Up_Your_Workspace&mobileaction=toggle_view_mobile)
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

