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

  * **[Login**](http://wiki.bukkit.org/Special:UserLogin?returnto=Event_API_Reference)
  * [Don't have an account? **Register**](http://wiki.bukkit.org/Special:UserLogin/signup)

##### Namespaces

  * [Page](/Event_API_Reference)
  * [Discussion](/Talk:Event_API_Reference)

####

##### Variants

#### Share

##### Share

  * ![](/extensions/Social/images/square_icons/twitter.png)![](/extensions/Social/images/square_icons/facebook.png)![](/extensions/Social/images/square_icons/googleplus.png)![](/extensions/Social/images/square_icons/reddit.png)![](/extensions/Social/images/square_icons/tumblr.png)

##### Views

  * [View](/Event_API_Reference)
  * [Edit](/index.php?title=Event_API_Reference&action=edit)
  * [History](/index.php?title=Event_API_Reference&action=history)

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

  * [What links here](/Special:WhatLinksHere/Event_API_Reference)
  * [Related changes](/Special:RecentChangesLinked/Event_API_Reference)
  * [Special pages](/Special:SpecialPages)
  * [Printable version](/index.php?title=Event_API_Reference&printable=yes)
  * [Permanent link](/index.php?title=Event_API_Reference&oldid=9913)
  * [Page information](/index.php?title=Event_API_Reference&action=info)

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

#  Event API Reference

From BukkitWiki

Jump to: navigation, search

**This page is part of the official Bukkit Documentation**

This page has been accepted and included in the official Bukkit Documentation.
You can discuss discrepancies, issues, or errors in the article on its [Talk
page](/Talk:Event_API_Reference).

Welcome to Bukkit's Event API reference page.

## Contents

  * 1 Introduction
  * 2 The Basics
    * 2.1 Setting up the Method
    * 2.2 @EventHandler
    * 2.3 Adding the listener
    * 2.4 EventHandler Parameters
      * 2.4.1 Event Priorities
  * 3 Registering Events
    * 3.1 Example Listener
    * 3.2 Registering Events in Plugin
      * 3.2.1 Registering Events with Plugin as Listener
    * 3.3 Registering Events in your Listener
  * 4 Un-registering events or listeners
    * 4.1 Un-register specific event
    * 4.2 Un-register all events
  * 5 Creating Custom Events
    * 5.1 Custom Event Example
      * 5.1.1 Calling your Custom Event
      * 5.1.2 Listening to a Custom Event
      * 5.1.3 Making your CustomEvent Cancellable
  * 6 Video Tutorial

## [[edit](/index.php?title=Event_API_Reference&action=edit&section=1)]
Introduction

**Events** are how the CraftBukkit server tells your plugin that something has happened in the world. Bukkit defines many events, in multiple categories; e.g. player actions (player logged in, player clicked a block, player died, player respawned...), block events (block placed, block broken, block's neighbour changed...), entity events (a mob targeted you, a creeper exploded...), world-wide events (a world loaded or unloaded, a chunk loaded or unloaded), and many more. A complete reference is available on the official Javadocs site <http://jd.bukkit.org> \- look for any class under the org.bukkit.event package. 

## [[edit](/index.php?title=Event_API_Reference&action=edit&section=2)] The
Basics

To keep this section simple, we're going to only work with PlayerLoginEvent.
Lets start with setting up the method

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=3)]
Setting up the Method

In order for your plugin to handle an event call, you need to create a method
for it:

    
    
    @EventHandler
    public void onLogin(PlayerLoginEvent event) {
        // Your code here...
    }

Before this method can be invoked by Bukkit when the "PlayerLoginEvent" is
fired, we need to annotate it. We do this with EventHandlers.

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=4)]
@EventHandler

The "@EventHandler" class is an Annotation, which goes just above your method.
It looks like this:

    
    
    @EventHandler // EventPriority.NORMAL by default

This marks your method as an EventHandler with the EventPriority as NORMAL.

The EventHandler can take an EventPriority to specify the priority of the
method, like so:

    
    
    @EventHandler(priority = EventPriority.HIGHEST) // Makes your method Highest priority
    @EventHandler(priority = EventPriority.LOW) // Makes your method Low priority

Here's what it would look like in your class:

    
    
    @EventHandler
    public void onLogin(PlayerLoginEvent event) {
        // Your code here...
    }

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=5)]
Adding the listener

In order for Bukkit to be able to register your EventHandler's, the class
which contains your event handling methods must implement the _Listener_
(org.bukkit.event.Listener) interface, e.g.:

    
    
    public final class MyPlayerListener implements Listener {
        @EventHandler
        public void onLogin(PlayerLoginEvent event) {
            // Your code here...
        }
    }

The name of the method (_onLogin_ in the above example) does not matter; you
may call the method anything you like inside your listener.

You may be wondering.. "How does Bukkit know which event to listen to?" It
knows that by the event parameter you specify in the method's signature - in
the above example: `PlayerLoginEvent`.

    ![Lightbulb.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**: You _must_ specify a single specific event or Bukkit will not be able to register it 

Your main plugin class (i.e. the class which extends JavaPlugin) can also be
an event listener, and this might make sense if your plugin is very small.
E.g.:

    
    
    public class MyPlugin extends JavaPlugin implements Listener {
      @Override
      public void onEnable() {
        getServer().getPluginManager().registerEvents(this, this);
      }
     
      @EventHandler
      public void onLogin(PlayerLoginEvent event) {
        getLogger().log(Level.INFO, "Player " + event.getPlayer().getName() + " is logging in!");
      }
    }

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=6)]
EventHandler Parameters

The @EventHandler annotation can take parameters to further define how the
event handler behaves. At the moment you can specify:

Name  Type  Default  Description  Values

priority

EventPriority

EventPriority.NORMAL

Sets the priority of your method

  * EventPriority.MONITOR 
  * EventPriority.HIGHEST 
  * EventPriority.HIGH 
  * EventPriority.NORMAL 
  * EventPriority.LOW 
  * EventPriority.LOWEST 

ignoreCancelled

boolean

false

If set to true, your method will not get the event if the event has been
cancelled

  * true 
  * false 

  

#### [[edit](/index.php?title=Event_API_Reference&action=edit&section=7)]
Event Priorities

There are six priorities in Bukkit that are called in the following order

  * EventPriority.LOWEST 
  * EventPriority.LOW 
  * EventPriority.NORMAL 
  * EventPriority.HIGH 
  * EventPriority.HIGHEST 
  * EventPriority.MONITOR 

Every plugin gets a say in what happens, and every plugin must get a chance to
know the outcome of an event. So, we pass events to plugins even after they've
been cancelled. A plugin can actually uncancel an event after another plugin
cancelled it. This is where priorities become really important.

Let's say a BLOCK_PLACE event is being handled. The lowest priority listener
is called to get its say in whether it should be cancelled or not. Then the
low priority listener is called to see if it wants to override the lowest,
etc. Eventually it hits monitor, and at this point nothing should change the
outcome of the event. Monitor should be used to see the outcome of an event,
without changing any aspect of it. If we have three plugins enabled; one is a
basic area protection plugin, one is a fancy plugin using signs, and another
is a logging plugin. The protection plugin listens on Priority.LOWEST. It says
they can't place blocks in this area, and cancels the event. The fancy sign
plugin listens on Priority.NORMAL. It says they can place signs here, and
uncancels the event. The log plugin listens on Priority.MONITOR. It sees that
the event was actually allowed, and logs it.

If you want to change the outcome of an event, choose very carefully from
LOWEST to HIGHEST. Suggested generalized protection plugins on lowest, more
specific plugins on normal, and override plugins on high. If you want to act
when an event happens, but not change the outcome, use MONITOR. **It's really
really important that you use MONITOR, or an event might get cancelled after
you've acted on it, and it's even more important that you don't change the
outcome of the event on MONITOR or it'll break other plugins.**

## [[edit](/index.php?title=Event_API_Reference&action=edit&section=8)]
Registering Events

To register your methods, the class containing the EventHandler(s) must
implement the Listener class.

>

>     import org.bukkit.event.Listener;

>

>     public final class LoginListener implements Listener {

>     }

You only need to provide a plugin and a listener to register them in the
PluginManager.

>

>     getServer().getPluginManager().registerEvents(Listener, Plugin);

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=9)]
Example Listener

This listener contains two EventHandlers. One listening on HIGH, and one on
NORMAL.

>

>     import org.bukkit.event.Listener;

>     import org.bukkit.event.EventHandler;

>     import org.bukkit.event.EventPriority;

>     import org.bukkit.event.player.PlayerLoginEvent;

>

>     public final class LoginListener implements Listener {

>         @EventHandler

>         public void normalLogin(PlayerLoginEvent event) {

>             // Some code here

>         }

>

>         @EventHandler(priority = EventPriority.HIGH)

>         public void highLogin(PlayerLoginEvent event) {

>             // Some code here

>         }

>     }

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=10)]
Registering Events in Plugin

The registerEvents method requires a listener and a plugin. Luckily, we
already have our LoginListener. Now for the LoginPlugin!

>

>     import org.bukkit.plugin.java.JavaPlugin;

>

>     public final class LoginPlugin extends JavaPlugin {

>         public void onEnable() {

>             getServer().getPluginManager().registerEvents(new
LoginListener(), this);

>         }

>     }

  

#### [[edit](/index.php?title=Event_API_Reference&action=edit&section=11)]
Registering Events with Plugin as Listener

You could even have the events in the main class, for example:

>

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.event.Listener;

>     import org.bukkit.event.EventHandler;

>     import org.bukkit.event.player.PlayerLoginEvent;

>

>     public final class LoginPlugin extends JavaPlugin implements Listener {

>         public void onEnable() {

>             getServer().getPluginManager().registerEvents(this, this);

>         }

>

>         @EventHandler

>         public void normalLogin(PlayerLoginEvent event) {

>             // Some code here

>         }

>     }

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=12)]
Registering Events in your Listener

There are many ways to register your events. Here's an example where you
register them in your listener class.

>

>     import org.bukkit.event.Listener;

>     import org.bukkit.event.EventHandler;

>     import org.bukkit.event.EventPriority;

>     import org.bukkit.event.player.PlayerLoginEvent;

>

>     public final class LoginListener implements Listener {

>         public LoginListener(LoginPlugin plugin) {

>             plugin.getServer().getPluginManager().registerEvents(this,
plugin);

>         }

>

>         @EventHandler

>         public void normalLogin(PlayerLoginEvent event) {

>             // Some code here

>         }

>

>         @EventHandler(priority = EventPriority.HIGH)

>         public void highLogin(PlayerLoginEvent event) {

>             // Some code here

>         }

>     }

The LoginPlugin would look like this:

>

>     import org.bukkit.plugin.java.JavaPlugin;

>

>     public final class LoginPlugin extends JavaPlugin {

>         public void onEnable() {

>             new LoginListener(this);

>         }

>     }

## [[edit](/index.php?title=Event_API_Reference&action=edit&section=13)] Un-
registering events or listeners

You can un-register individual events, entire listener classes or all events
registered by your plugin or even by other plugins!

#### [[edit](/index.php?title=Event_API_Reference&action=edit&section=14)] Un-
register specific event

Each event class has the getHandlerList() static method, call that and then
you can use .unregister() method. Example:

>

>     PlayerInteractEvent.getHandlerList().unregister(plugin);

>     // this will unregister all PlayerInteractEvent instances from the
plugin

>     // you can also specify a listener class instead of plugin.

Now you know why you'll need the getHandlerList() in your custom events.

#### [[edit](/index.php?title=Event_API_Reference&action=edit&section=15)] Un-
register all events

Using the HandlerList class and its unregisterAll() static method you can
easily unregister events from listener classes or plugins. Example:

>

>     HandlerList.unregisterAll(plugin);

>     // this will unregister all events from the specified plugin

>     // you can also specify a listener class instead of plugin.

## [[edit](/index.php?title=Event_API_Reference&action=edit&section=16)]
Creating Custom Events

Creating custom events is very simple, you can use the same system that Bukkit
uses without ruining performance.

There are two (2) things to keep in mind when you create a Custom Event. They
are "extend Event" and "static handlers." With static handlers, you must input
the following code into your custom event:

>

>     private static final HandlerList handlers = new HandlerList();

>

>     public HandlerList getHandlers() {

>         return handlers;

>     }

>

>     public static HandlerList getHandlerList() {

>         return handlers;

>     }

This block of code makes the EventHandlers contained inside your own event,
keeping any unrelated events completely separated.

### [[edit](/index.php?title=Event_API_Reference&action=edit&section=17)]
Custom Event Example

The following example shows how easy it is to create your own "CustomEvent."

>

>     import org.bukkit.event.Event;

>     import org.bukkit.event.HandlerList;

>

>     public final class CustomEvent extends Event {

>         private static final HandlerList handlers = new HandlerList();

>         private String message;

>

>         public CustomEvent(String example) {

>             message = example;

>         }

>

>         public String getMessage() {

>             return message;

>         }

>

>         public HandlerList getHandlers() {

>             return handlers;

>         }

>

>         public static HandlerList getHandlerList() {

>             return handlers;

>         }

>     }

#### [[edit](/index.php?title=Event_API_Reference&action=edit&section=18)]
Calling your Custom Event

You are in control of creating and calling your events, where you call it is
completely up to you. Here's an example

>

>     // Create the event here

>     CustomEvent event = new CustomEvent("Sample Message");

>     // Call the event

>     Bukkit.getServer().getPluginManager().callEvent(event);

>     // Now you do the event

>     Bukkit.getServer().broadcastMessage(event.getMessage());

Remember: You are in control of your events. If you don't call it, and act
upon it, it doesn't happen!

#### [[edit](/index.php?title=Event_API_Reference&action=edit&section=19)]
Listening to a Custom Event

How do you listen to a custom event you say? Simple, the same way as listening
to a normal event!

>

>     import org.bukkit.event.Listener;

>     import org.bukkit.event.EventHandler;

>

>     public final class CustomListener implements Listener {

>         @EventHandler

>         public void normalLogin(CustomEvent event) {

>             // Some code here

>         }

>     }

#### [[edit](/index.php?title=Event_API_Reference&action=edit&section=20)]
Making your CustomEvent Cancellable

If you ever want to make your event cancellable, remember one thing:
"implements Cancellable." Just like you would import Listener. It's really
that simple, let me show you an example!

>

>     import org.bukkit.event.Event;

>     import org.bukkit.event.HandlerList;

>     import org.bukkit.event.Cancellable;

>

>     public final class CustomEvent extends Event implements Cancellable {

>         private static final HandlerList handlers = new HandlerList();

>         private String message;

>         private boolean cancelled;

>

>         public CustomEvent(String example) {

>             message = example;

>         }

>

>         public String getMessage() {

>             return message;

>         }

>

>         public boolean isCancelled() {

>             return cancelled;

>         }

>

>         public void setCancelled(boolean cancel) {

>             cancelled = cancel;

>         }

>

>         public HandlerList getHandlers() {

>             return handlers;

>         }

>

>         public static HandlerList getHandlerList() {

>             return handlers;

>         }

>     }

Afterwards, you would check if a plugin had cancelled the event in your code,
before processing normally

>

>     // Create the event here

>     CustomEvent event = new CustomEvent("Sample Message");

>     // Call the event

>     Bukkit.getServer().getPluginManager().callEvent(event);

>     // Check if the event is not cancelled

>     if (!event.isCancelled()) {

>         // Now you do the event

>         Bukkit.getServer().broadcastMessage(event.getMessage());

>     }

## [[edit](/index.php?title=Event_API_Reference&action=edit&section=21)] Video
Tutorial

If you would prefer to watch a video tutorial version of this, please click
[here](http://www.youtube.com/watch?v=PWQNsqwD-AY).

Language

  **English** • [Беларускі](/index.php?title=Event_API_Reference/by&action=edit&redlink=1) • [Deutsch](/index.php?title=Event_API_Reference/de&action=edit&redlink=1) • [español](/index.php?title=Event_API_Reference/es&action=edit&redlink=1) • [suomi](/index.php?title=Event_API_Reference/fi&action=edit&redlink=1) • [français](/Event_API_Reference/fr) • [italiano](/index.php?title=Event_API_Reference/it&action=edit&redlink=1) • [한국어](/index.php?title=Event_API_Reference/ko&action=edit&redlink=1) • [Nederlands](/index.php?title=Event_API_Reference/nl&action=edit&redlink=1) • [norsk bokmål](/index.php?title=Event_API_Reference/no&action=edit&redlink=1) • [polski](/Event_API_Reference/pl) • [português](/index.php?title=Event_API_Reference/pt&action=edit&redlink=1) • [русский](/index.php?title=Event_API_Reference/ru&action=edit&redlink=1) • [lietuvių](/index.php?title=Event_API_Reference/lt&action=edit&redlink=1) • [česky](/index.php?title=Event_API_Reference/cs&action=edit&redlink=1)

Language

  [English](/Introduction_to_the_New_Event_System) • [Беларускі](/index.php?ti
tle=Introduction_to_the_New_Event_System/by&action=edit&redlink=1) •
[Deutsch](/Introduction_to_the_New_Event_System/de) • [español](/index.php?tit
le=Introduction_to_the_New_Event_System/es&action=edit&redlink=1) • [suomi](/i
ndex.php?title=Introduction_to_the_New_Event_System/fi&action=edit&redlink=1)
• [français](/Introduction_to_the_New_Event_System/fr) • [italiano](/index.php
?title=Introduction_to_the_New_Event_System/it&action=edit&redlink=1) • [한국어](
/index.php?title=Introduction_to_the_New_Event_System/ko&action=edit&redlink=1
) • [Nederlands](/index.php?title=Introduction_to_the_New_Event_System/nl&acti
on=edit&redlink=1) • [norsk bokmål](/index.php?title=Introduction_to_the_New_E
vent_System/no&action=edit&redlink=1) • [polski](/index.php?title=Introduction
_to_the_New_Event_System/pl&action=edit&redlink=1) • [português](/index.php?ti
tle=Introduction_to_the_New_Event_System/pt&action=edit&redlink=1) •
[русский](/Introduction_to_the_New_Event_System/ru) • [lietuvių](/index.php?ti
tle=Introduction_to_the_New_Event_System/lt&action=edit&redlink=1) • [česky](/
index.php?title=Introduction_to_the_New_Event_System/cs&action=edit&redlink=1)

Retrieved from "[http://wiki.bukkit.org/index.php?title=Event_API_Reference&ol
did=9913](http://wiki.bukkit.org/index.php?title=Event_API_Reference&oldid=991
3)"

[Categories](/Special:Categories):

  * [Docs](/Category:Docs)
  * [Tutorials](/Category:Tutorials)

  * This page was last modified on 23 April 2014, at 01:11.
  * Content is available under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/) unless otherwise noted. Game content and materials are trademarks and copyrights of their respective publisher and its licensors. All rights reserved.  
This site is a part of Curse, Inc. and is not affiliated with the game
publisher.

  * [Privacy policy](/BukkitWiki:Privacy_policy)
  * [About BukkitWiki](/BukkitWiki:About)
  * [Disclaimers](/BukkitWiki:General_disclaimer)
  * [Mobile view](http://wiki.bukkit.org/index.php?title=Event_API_Reference&mobileaction=toggle_view_mobile)
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

