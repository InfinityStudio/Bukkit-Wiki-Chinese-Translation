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

在完成对任务的定义后，插件需要提供对任务调度的细节。BukkitRunnables会在调度条件满足之后运行任务的run方法。BukkitRunnables的方法列表可以在[BukkitRunnables的JavaDoc](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitRunnable.html)中找到。尽管方法不同，但是它们将都返回BukkitTask类型的方法。

**注意**:请不要在异步任务中使用任何的BukkitAPI

### 例子

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

###匿名BukkitRunnable例子

使用匿名BukkitRunnable允许你在不另外建立新类就可以使用任务调度的功能。下面的例子描述了如何使用这个功能：

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

#Bukkit任务调度器

[任务调度器](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitScheduler.html)是一个允许你在插件运行过程中一句时间调度一个[Runnable](http://docs.oracle.com/javase/6/docs/api/index.html?java/lang/Runnable.html)和/或一个[Callable](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concurrent/Callable.html)来让他们在一段时间之后执行的组件。任务调度器的方法列表可以在它的[JavaDocs](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitScheduler.html)中找到。

**提示**： 插件不应该使用调度器调度BukkitRunnable，应当使用想要的任务调度直接执行BukkitRunnable。

### 例子

一个在20tick后使用调度器调度一个匿名的Runnable的小例子：

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

**注意**：请不要使用异步任务调度中使用BukkitAPI

## BukkitTask

[BukkitTask](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitTask.html)是一个无论是否Runnable被调度了都将返回的对象。这个对象指示了Runnable是否已经被调度。更多相关信息请参见[Javadocs for BukkitTask](http://jd.bukkit.org/rb/apidocs/index.html?org/bukkit/scheduler/BukkitTask.html)。

## Callable和Future

[Callable](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concurrent/Callable.html)将被调度器异步调用并返回一个[Future](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concurrent/Future.html)。他们都是Java的原生类，更多信息请参见[Javadocs for Callable](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concurrent/Callable.html)和[Javadocs for Future](http://docs.oracle.com/javase/6/docs/api/index.html?java/util/concurrent/Future.html)。

# 线程安全小提示

BukkitAPI和任务调度包并不是线程安全的，也不保证线程安全。

  1. 异步任务不应该使用BukkitAPI。
  2. 请不要在异步任务中使用或者修改公共的集合。普通的集合都[不是](http://stackoverflow.com/questions/1003026/hashmap-concurrency-issue)[线程安全](http://lightbody.net/blog/?p=307)的。  
  3. 异步调度和同步调度可以相互调度。