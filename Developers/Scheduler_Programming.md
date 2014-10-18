#  Scheduler Programming

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

# BukkitRunnable

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

## Defining work

Plugins should first
[extend](http://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html) [B
ukkitRunnable](http://jd.bukkit.org/apidocs/index.html?org/bukkit/scheduler/Bu
kkitRunnable.html) to define work that needs to be done. In other words, the
definition of the run method is what you want executed in accordance to a
schedule.

### Basic Example

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

### Self-Canceling Example

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

## Scheduling Work

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

### Example

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

### Self-Canceling Example

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

### Anonymous BukkitRunnable Example

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

# BukkitScheduler

The [BukkitScheduler](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/sc
heduler/BukkitScheduler.html) allows plugins to schedule a [Runnable](http://d
ocs.oracle.com/javase/6/docs/api/index.html?java/lang/Runnable.html) and/or a 
[Callable](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concu
rrent/Callable.html) , for execution at a later time. The list of methods for
BukkitScheduler can be found in the [Javadocs for BukkitScheduler](http://jd.b
ukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitScheduler.html).

    ![Lightbulb.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**: Plugins should not schedule a BukkitRunnable with the scheduler, instead they should run the BukkitRunnable with the desired schedule. 

### Example

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

### Repeating Example

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

**Warning**:

Asynchronous tasks should never access any API in Bukkit

## BukkitTask

A [BukkitTask](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler
/BukkitTask.html) object is returned whenever a Runnable is scheduled. This
object represents the task the scheduled task being executed by the scheduler.
For more information see, [Javadocs for BukkitTask](http://jd.bukkit.org/rb/ap
idocs/index.html?org/bukkit/scheduler/BukkitTask.html).

## Callable and Future

A [Callable](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/con
current/Callable.html) given to the scheduler to call synchronously returns a 
[Future](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concurr
ent/Future.html). These are standard Java classes, for more information see,
[Javadocs for Callable](http://docs.oracle.com/javase/6/docs/api/index.html?ja
va/util/concurrent/Callable.html) and [Javadocs for Future](http://docs.oracle
.com/javase/6/docs/api/index.html?java/util/concurrent/Future.html)

# Tips for thread safety

The Bukkit API, with the exception of the scheduler package, is not thread
safe nor guaranteed to be thread safe.

  1. Asynchronous tasks should never access any API in Bukkit. 
  2. Do not access or modify shared collections from your asynchronous tasks. Normal collections are [not](http://stackoverflow.com/questions/1003026/hashmap-concurrency-issue) [thread-safe](http://lightbody.net/blog/?p=307). This also applies to objects which are not thread safe. 
  3. An asynchronous task can schedule a synchronous task. 
  4. A synchronous task can schedule an asynchronous task. 
