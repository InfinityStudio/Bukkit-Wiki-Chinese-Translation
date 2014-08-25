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

  * **[Login**](http://wiki.bukkit.org/Special:UserLogin?returnto=Scheduler_Programming)
  * [Don't have an account? **Register**](http://wiki.bukkit.org/Special:UserLogin/signup)

##### Namespaces

  * [Page](/Scheduler_Programming)
  * [Discussion](/index.php?title=Talk:Scheduler_Programming&action=edit&redlink=1)

####

##### Variants

#### Share

##### Share

  * ![](/extensions/Social/images/square_icons/twitter.png)![](/extensions/Social/images/square_icons/facebook.png)![](/extensions/Social/images/square_icons/googleplus.png)![](/extensions/Social/images/square_icons/reddit.png)![](/extensions/Social/images/square_icons/tumblr.png)

##### Views

  * [View](/Scheduler_Programming)
  * [Edit](/index.php?title=Scheduler_Programming&action=edit)
  * [History](/index.php?title=Scheduler_Programming&action=history)

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

  * [What links here](/Special:WhatLinksHere/Scheduler_Programming)
  * [Related changes](/Special:RecentChangesLinked/Scheduler_Programming)
  * [Special pages](/Special:SpecialPages)
  * [Printable version](/index.php?title=Scheduler_Programming&printable=yes)
  * [Permanent link](/index.php?title=Scheduler_Programming&oldid=10193)
  * [Page information](/index.php?title=Scheduler_Programming&action=info)

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

#  Scheduler Programming

From BukkitWiki

Jump to: navigation, search

This tutorial will guide you in using the scheduler provided by bukkit. It
will allow you to defer the execution of code to a later time. This is not the
same as registering a [Listener](http://jd.bukkit.org/apidocs/index.html?org/b
ukkit/event/Listener.html), a block of code which is executed in response to
an [event](http://wiki.bukkit.org/Event_API_Reference) in the game. Blocks of
code may also be scheduled to be executed repeatedly at a fixed interval, with
or without a delay. They will continue to execute until completed, or
canceled, or your plugin is disabled.

When using BukkitRunnable, with a separate class, scheduling work occurs in
two steps for the programmer.

  1. Define the work to be done, see the section Defining Work
  2. Notify Bukkit when the work should be executed, see the section Scheduling Work

Alternatively, work can be scheduled directly with the scheduler, this also
occurs in two steps for the programmer.

  1. Define the work to be done, in a Runnable or Callable 
  2. Then directly scheduling the work with the Bukkit Scheduler, see the section BukkitScheduler

## Contents

  * 1 BukkitRunnable
    * 1.1 Defining work
      * 1.1.1 Basic Example
      * 1.1.2 Self-Canceling Example
    * 1.2 Scheduling Work
      * 1.2.1 Example
      * 1.2.2 Self-Canceling Example
      * 1.2.3 Anonymous BukkitRunnable Example
  * 2 BukkitScheduler
    * 2.1 Example
    * 2.2 Repeating Example
    * 2.3 BukkitTask
    * 2.4 Callable and Future
  * 3 Tips for thread safety

# [[edit](/index.php?title=Scheduler_Programming&action=edit&section=1)]
BukkitRunnable

[BukkitRunnable](http://jd.bukkit.org/apidocs/index.html?org/bukkit/scheduler/
BukkitRunnable.html) is an abstract implementation of [Runnable](http://docs.o
racle.com/javase/6/docs/api/index.html?java/lang/Runnable.html). It also
supports additional operations that a Runnable is not capable of, most
conveniently, BukkitRunnables can schedule and cancel their own execution.
However, if the BukkitRunnable did not schedule itself for execution, it
cannot cancel itself from execution. BukkitRunnables are not schedulers, do
not contain any scheduler logic, and are not expensive to create. Plugins
should prefer defining a BukkitRunnable and calling the appropriate run method
over directly scheduling a Runnable with the BukkitScheduler.

     _For more information on BukkitRunnable, see the [BukkitRunnable JavaDocs](http://jd.bukkit.org/apidocs/index.html?org/bukkit/scheduler/BukkitRunnable.html)_

## [[edit](/index.php?title=Scheduler_Programming&action=edit&section=2)]
Defining work

Plugins should first
[extend](http://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html) [B
ukkitRunnable](http://jd.bukkit.org/apidocs/index.html?org/bukkit/scheduler/Bu
kkitRunnable.html) to define work that needs to be done. In other words, the
definition of the run method is what you want executed in accordance to a
schedule.

### [[edit](/index.php?title=Scheduler_Programming&action=edit&section=3)]
Basic Example

This is an example definition of a task that can be scheduled.

>

>     import org.bukkit.Bukkit;

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.scheduler.BukkitRunnable;

>

>     public class ExampleTask extends BukkitRunnable {

>

>         private final JavaPlugin plugin;

>

>         public ExampleTask(JavaPlugin plugin) {

>             this.plugin = plugin;

>         }

>

>         @Override

>         public void run() {

>             // What you want to schedule goes here

>             plugin.getServer().broadcastMessage("Welcome to Bukkit! Remember
to read the documentation!");

>         }

>

>     }

### [[edit](/index.php?title=Scheduler_Programming&action=edit&section=4)]
Self-Canceling Example

This is an example of a definition of a task that will cancel itself when it
has executed the specified number of times

>

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.scheduler.BukkitRunnable;

>

>     public class ExampleSelfCancelingTask extends BukkitRunnable {

>

>         private final JavaPlugin plugin;

>

>         private int counter;

>

>         public ExampleSelfCancelingTask(JavaPlugin plugin, int counter) {

>             this.plugin = plugin;

>             if (counter < 1) {

>                 throw new IllegalArgumentException("counter must be greater
than 1");

>             } else {

>                 this.counter = counter;

>             }

>         }

>

>         @Override

>         public void run() {

>             // What you want to schedule goes here

>             if (counter > 0) {

>                 plugin.getServer().broadcastMessage("Commence greeting in "
+ counter--);

>             } else {

>                 plugin.getServer().broadcastMessage("Welcome to Bukkit!
Remember to read the documentation!");

>                 this.cancel();

>             }

>         }

>

>     }

## [[edit](/index.php?title=Scheduler_Programming&action=edit&section=5)]
Scheduling Work

After defining the task, the plugin needs to schedule the task.
BukkitRunnables are scheduled when the desired run method is invoked on an
instance of the task. The list of methods for BukkitRunnable can be found in
the [Javadocs for BukkitRunnable](http://jd.bukkit.org/rb/apidocs/index.html?o
rg/bukkit/scheduler/BukkitRunnable.html). The different run methods all return
a  BukkitTask object

![Warning](http://hydra-
media.cursecdn.com/wiki.bukkit.org/thumb/5/51/Attention_niels_epting.svg/18px-
Attention_niels_epting.svg.png?version=f594b4cdba86f489bc057c8896dddc91)
**Warning**:

Asynchronous tasks should never access any API in Bukkit

### [[edit](/index.php?title=Scheduler_Programming&action=edit&section=6)]
Example

This is an example of a plugin which registers a listener and when a player
joins, schedules a task to be run 20 ticks later.

>

>     import org.bukkit.event.EventHandler;

>     import org.bukkit.event.Listener;

>     import org.bukkit.event.player.PlayerJoinEvent;

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.scheduler.BukkitRunnable;

>     import org.bukkit.scheduler.BukkitTask;

>

>     public final class ExamplePlugin extends JavaPlugin {

>

>         @Override

>         public void onEnable() {

>             new ExampleListener(this);

>         }

>     }

>

>     class ExampleListener implements Listener {

>

>         private final ExamplePlugin plugin;

>

>         public ExampleListener(ExamplePlugin plugin) {

>             this.plugin = plugin;

>             plugin.getServer().getPluginManager().registerEvents(this,
plugin);

>         }

>

>         @EventHandler

>         public void onJoin(PlayerJoinEvent event) {

>             // Create the task and schedule to run it once, after 20 ticks

>             BukkitTask task = new
ExampleTask(this.plugin).runTaskLater(this.plugin, 20);

>         }

>

>     }

### [[edit](/index.php?title=Scheduler_Programming&action=edit&section=7)]
Self-Canceling Example

This is example takes the above ExampleSelfCancelingTask and scheules it to
run every 20 ticks after waiting 10 ticks.

>

>     import org.bukkit.event.EventHandler;

>     import org.bukkit.event.Listener;

>     import org.bukkit.event.player.PlayerJoinEvent;

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.scheduler.BukkitRunnable;

>     import org.bukkit.scheduler.BukkitTask;

>

>     public final class ExamplePlugin extends JavaPlugin {

>

>         @Override

>         public void onEnable() {

>             new ExampleListener(this);

>         }

>     }

>

>     class ExampleListener implements Listener {

>

>         private final ExamplePlugin plugin;

>

>         public ExampleListener(ExamplePlugin plugin) {

>             this.plugin = plugin;

>             plugin.getServer().getPluginManager().registerEvents(this,
plugin);

>         }

>

>         @EventHandler

>         public void onJoin(PlayerJoinEvent event) {

>             // Create the task and schedule

>             BukkitTask task = new ExampleSelfCancelingTask(this.plugin,
5).runTaskTimer(this.plugin, 10, 20);

>         }

>

>     }

### [[edit](/index.php?title=Scheduler_Programming&action=edit&section=8)]
Anonymous BukkitRunnable Example

An anonymous BukkitRunnable will allow you to schedule a task, without
creating a new class with a name. This examples combines the above two basic
examples.

>

>     import org.bukkit.event.EventHandler;

>     import org.bukkit.event.Listener;

>     import org.bukkit.event.player.PlayerJoinEvent;

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.scheduler.BukkitRunnable;

>     import org.bukkit.scheduler.BukkitTask;

>

>     public final class ExamplePlugin extends JavaPlugin {

>

>         @Override

>         public void onEnable() {

>             new ExampleListener(this);

>         }

>     }

>

>     class ExampleListener implements Listener {

>

>         private final ExamplePlugin plugin;

>

>         public ExampleListener(ExamplePlugin plugin) {

>             this.plugin = plugin;

>             plugin.getServer().getPluginManager().registerEvents(this,
plugin);

>         }

>

>         @EventHandler

>         public void onJoin(PlayerJoinEvent event) {

>             // Create the task anonymously and schedule to run it once,
after 20 ticks

>             new BukkitRunnable() {

>

>                 @Override

>                 public void run() {

>                     // What you want to schedule goes here

>                     plugin.getServer().broadcastMessage(

>                         "Welcome to Bukkit! Remember to read the
documentation!");

>                 }

>

>             }.runTaskLater(this.plugin, 20);

>         }

>

>     }

# [[edit](/index.php?title=Scheduler_Programming&action=edit&section=9)]
BukkitScheduler

The [BukkitScheduler](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/sc
heduler/BukkitScheduler.html) allows plugins to schedule a [Runnable](http://d
ocs.oracle.com/javase/6/docs/api/index.html?java/lang/Runnable.html) and/or a 
[Callable](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concu
rrent/Callable.html) , for execution at a later time. The list of methods for
BukkitScheduler can be found in the [Javadocs for BukkitScheduler](http://jd.b
ukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitScheduler.html).

    ![Lightbulb.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**: Plugins should not schedule a BukkitRunnable with the scheduler, instead they should run the BukkitRunnable with the desired schedule. 

### [[edit](/index.php?title=Scheduler_Programming&action=edit&section=10)]
Example

Example for directly scheduling an anonymous Runnable with the BukkitScheduler
to run after 20 ticks.

>

>     import org.bukkit.Bukkit;

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.scheduler.BukkitScheduler;

>

>     public final class ExamplePlugin extends JavaPlugin {

>         public void onEnable() {

>             BukkitScheduler scheduler = Bukkit.getServer().getScheduler();

>             scheduler.scheduleSyncDelayedTask(this, new Runnable() {

>                 @Override

>                 public void run() {

>                     // Do something

>                 }

>             }, 20L);

>         }

>     }

### [[edit](/index.php?title=Scheduler_Programming&action=edit&section=11)]
Repeating Example

Example for directly scheduling an anonymous Runnable with the BukkitScheduler
to run every twenty ticks, forever, starting from when you schedule it.

>

>     import org.bukkit.Bukkit;

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.scheduler.BukkitScheduler;

>

>     public final class ExamplePlugin extends JavaPlugin {

>         public void onEnable() {

>             BukkitScheduler scheduler = Bukkit.getServer().getScheduler();

>             scheduler.scheduleSyncRepeatingTask(this, new Runnable() {

>                 @Override

>                 public void run() {

>                     // Do something

>                 }

>             }, 0L, 20L);

>         }

>     }

![Warning](http://hydra-
media.cursecdn.com/wiki.bukkit.org/thumb/5/51/Attention_niels_epting.svg/18px-
Attention_niels_epting.svg.png?version=f594b4cdba86f489bc057c8896dddc91)
**Warning**:

Asynchronous tasks should never access any API in Bukkit

## [[edit](/index.php?title=Scheduler_Programming&action=edit&section=12)]
BukkitTask

A [BukkitTask](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler
/BukkitTask.html) object is returned whenever a Runnable is scheduled. This
object represents the task the scheduled task being executed by the scheduler.
For more information see, [Javadocs for BukkitTask](http://jd.bukkit.org/rb/ap
idocs/index.html?org/bukkit/scheduler/BukkitTask.html).

## [[edit](/index.php?title=Scheduler_Programming&action=edit&section=13)]
Callable and Future

A [Callable](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/con
current/Callable.html) given to the scheduler to call synchronously returns a 
[Future](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concurr
ent/Future.html). These are standard Java classes, for more information see,
[Javadocs for Callable](http://docs.oracle.com/javase/6/docs/api/index.html?ja
va/util/concurrent/Callable.html) and [Javadocs for Future](http://docs.oracle
.com/javase/6/docs/api/index.html?java/util/concurrent/Future.html)

# [[edit](/index.php?title=Scheduler_Programming&action=edit&section=14)] Tips
for thread safety

The Bukkit API, with the exception of the scheduler package, is not thread
safe nor guaranteed to be thread safe.

  1. Asynchronous tasks should never access any API in Bukkit. 
  2. Do not access or modify shared collections from your asynchronous tasks. Normal collections are [not](http://stackoverflow.com/questions/1003026/hashmap-concurrency-issue) [thread-safe](http://lightbody.net/blog/?p=307). This also applies to objects which are not thread safe. 
  3. An asynchronous task can schedule a synchronous task. 
  4. A synchronous task can schedule an asynchronous task. 

Language

  **English** • [Беларускі](/index.php?title=Scheduler_Programming/by&action=edit&redlink=1) • [Deutsch](/Scheduler_Programming/de) • [español](/index.php?title=Scheduler_Programming/es&action=edit&redlink=1) • [suomi](/index.php?title=Scheduler_Programming/fi&action=edit&redlink=1) • [français](/Scheduler_Programming/fr) • [italiano](/index.php?title=Scheduler_Programming/it&action=edit&redlink=1) • [한국어](/Scheduler_Programming/ko) • [Nederlands](/index.php?title=Scheduler_Programming/nl&action=edit&redlink=1) • [norsk bokmål](/index.php?title=Scheduler_Programming/no&action=edit&redlink=1) • [polski](/Scheduler_Programming/pl) • [português](/Scheduler_Programming/pt) • [русский](/index.php?title=Scheduler_Programming/ru&action=edit&redlink=1) • [lietuvių](/index.php?title=Scheduler_Programming/lt&action=edit&redlink=1) • [česky](/index.php?title=Scheduler_Programming/cs&action=edit&redlink=1)

Retrieved from "[http://wiki.bukkit.org/index.php?title=Scheduler_Programming&
oldid=10193](http://wiki.bukkit.org/index.php?title=Scheduler_Programming&oldi
d=10193)"

  * This page was last modified on 26 June 2014, at 16:24.
  * Content is available under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/) unless otherwise noted. Game content and materials are trademarks and copyrights of their respective publisher and its licensors. All rights reserved.  
This site is a part of Curse, Inc. and is not affiliated with the game
publisher.

  * [Privacy policy](/BukkitWiki:Privacy_policy)
  * [About BukkitWiki](/BukkitWiki:About)
  * [Disclaimers](/BukkitWiki:General_disclaimer)
  * [Mobile view](http://wiki.bukkit.org/index.php?title=Scheduler_Programming&mobileaction=toggle_view_mobile)
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

