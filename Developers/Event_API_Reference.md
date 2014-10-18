#  Event API Reference
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

## Introduction

**Events** are how the CraftBukkit server tells your plugin that something has happened in the world. Bukkit defines many events, in multiple categories; e.g. player actions (player logged in, player clicked a block, player died, player respawned...), block events (block placed, block broken, block's neighbour changed...), entity events (a mob targeted you, a creeper exploded...), world-wide events (a world loaded or unloaded, a chunk loaded or unloaded), and many more. A complete reference is available on the official Javadocs site <http://jd.bukkit.org> \- look for any class under the org.bukkit.event package. 

## Basics

To keep this section simple, we're going to only work with PlayerLoginEvent.
Lets start with setting up the method

### Setting up the Method

In order for your plugin to handle an event call, you need to create a method
for it:

    
    
    @EventHandler
    public void onLogin(PlayerLoginEvent event) {
        // Your code here...
    }

Before this method can be invoked by Bukkit when the "PlayerLoginEvent" is
fired, we need to annotate it. We do this with EventHandlers.

### @EventHandler

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

### Adding the listener

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

    **Note**: You _must_ specify a single specific event or Bukkit will not be able to register it 

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

### EventHandler Parameters

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

  

#### Event Priorities

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

## Registering Events

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

### Example Listener

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

### Registering Events in Plugin

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

  

#### Registering Events with Plugin as Listener

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

### Registering Events in your Listener

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

## Un-registering events or listeners

You can un-register individual events, entire listener classes or all events
registered by your plugin or even by other plugins!

#### Un-register specific event

Each event class has the getHandlerList() static method, call that and then
you can use .unregister() method. Example:

>

>     PlayerInteractEvent.getHandlerList().unregister(plugin);

>     // this will unregister all PlayerInteractEvent instances from the
plugin

>     // you can also specify a listener class instead of plugin.

Now you know why you'll need the getHandlerList() in your custom events.

#### Un-register all events

Using the HandlerList class and its unregisterAll() static method you can
easily unregister events from listener classes or plugins. Example:

>

>     HandlerList.unregisterAll(plugin);

>     // this will unregister all events from the specified plugin

>     // you can also specify a listener class instead of plugin.

## Creating Custom Events

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

### Custom Event Example

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

#### Calling your Custom Event

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

#### Listening to a Custom Event

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

#### Making your CustomEvent Cancellable

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

## Tutorial

If you would prefer to watch a video tutorial version of this, please click
[here](http://www.youtube.com/watch?v=PWQNsqwD-AY).

