#调度式编程

这个指南将指导你使用Bukkit提供的调度式编程。通过这种编程方式，你可以在一段时间之后执行某个操作。这和前面所讲的通过绑定一个[监听器](http://jd.bukkit.org/apidocs/index.html?org/bukkit/event/Listener.html)后通过[事件](http://wiki.bukkit.org/Event_API_Reference)触发来执行一段代码不同，调度式编程允许你以一个固定的时间周期重复执行代码。直到这个调度完成、取消或者插件被关闭。

当使用BukkitRunnable来进行调度式编程时，子程序会被分为两个阶段：

  1.定义工作应当如何完成，参考“定义任务”
  2.设定工作应当以何种方式进行，参考“调度任务”

此外你也可以直接使用调度。这同样分为两个阶段：

  1.定义工作应当如何完成，参考“Runnable”或者“Callable”
  2.使用Bukkit的调度器直接调度任务，参考“Bukkit调度器”章节

## 目录

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

[BukkitRunnable](http://jd.bukkit.org/apidocs/index.html?org/bukkit/scheduler/BukkitRunnable.html)是一个对标准Java [Runnable](http://docs.oracle.com/javase/6/docs/api/index.html?java/lang/Runnable.html)的抽象实现。不过它实现了一些标准Runnable所没有的功能。简而言之，BukkitRunnable可以被调度执行和取消调度。不过，一个BukkitRunnable在被调度之前无法被取消调度。而且BukkitRunnable自身没有任何的调度逻辑，建立一个BukkitRunnable也并不复杂。只需明确的在插件中定义一个BukkitRunnable并通过调度器正确的调度执行Run方法即可。

_更多详细信息，请参见[BukkitRunnable JavaDocs](http://jd.bukkit.org/apidocs/index.html?org/bukkit/scheduler/BukkitRunnable.html)_

##定义任务

插件应当首先去[继承](http://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html) [BukkitRunnable](http://jd.bukkit.org/apidocs/index.html?org/bukkit/scheduler/BukkitRunnable.html)父类来定义任务的细节。换句话说，当满足调度条件时，run函数应当执行什么内容。

###小例子

这是一个可以被正确调度的任务小例子：


	import org.bukkit.Bukkit;
	import org.bukkit.plugin.java.JavaPlugin;
	import org.bukkit.scheduler.BukkitRunnable;

	public class ExampleTask extends BukkitRunnable {

		private final JavaPlugin plugin;



	public ExampleTask(JavaPlugin plugin) {
		this.plugin = plugin;
	}
		@Override
		public void run() {

			// What you want to schedule goes here
			plugin.getServer().broadcastMessage("Welcome to Bukkit! Remember to read the documentation!");
		}
}

### 可以自行取消调度的小例子

在这个例子中，任务在执行一定次数之后会将自己的调度取消：

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

##调度任务

在完成对任务的定义后，插件需要提供对任务调度的细节。BukkitRunnables会在调度条件满足之后运行任务的run方法。BukkitRunnables的方法列表可以在[BukkitRunnables的JavaDoc](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitRunnable.html)中找到。

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
