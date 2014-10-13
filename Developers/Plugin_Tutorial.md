# 插件开发入门指南

## Contents

  * 1 Introduction
  * 2 Learning Java
  * 3 The Development Environment
  * 4 Starting a Plugin Project
    * 4.1 Create a Project
    * 4.2 Reference the Bukkit API
    * 4.3 Bukkit Javadocs
    * 4.4 Creating a package
    * 4.5 Creating the Plugin's Class
    * 4.6 Creating plugin.yml
  * 5 onEnable() and onDisable()
    * 5.1 Introduction to onEnable() and onDisable()
    * 5.2 Logging a message
    * 5.3 Handling Reloads
  * 6 Listeners
  * 7 Commands
    * 7.1 The onCommand() Method
      * 7.1.1 Setting up the command
    * 7.2 Adding your Command to the Plugin.yml
    * 7.3 Console Commands vs. Player Commands
    * 7.4 Using a separate CommandExecutor class
    * 7.5 Writing a safe onCommand
      * 7.5.1 Make sure the sender is a Player before casting
      * 7.5.2 Check the arguments length
      * 7.5.3 Check if a Player is online before getting them
  * 8 Plugin Configuration/Settings
  * 9 Permissions
    * 9.1 Configuring your permissions
      * 9.1.1 Defaults
      * 9.1.2 Children
    * 9.2 Setting your own permissions
  * 10 Scheduling Tasks and Background Tasks
  * 11 Block Manipulation
  * 12 (Player) Inventory Manipulation
  * 13 Item Manipulation
    * 13.1 Enchantments
    * 13.2 ItemMeta
  * 14 Maps, and Sets, and Lists, Oh My!
    * 14.1 HashMaps and How to Use Them
      * 14.1.1 Defining a HashMap
      * 14.1.2 More Ideas for HashMaps
        * 14.1.2.1 Data Value Lookups
      * 14.1.3 Saving/Loading a HashMap
        * 14.1.3.1 Tips & Examples
  * 15 Metadata
    * 15.1 Why to use Metadata
    * 15.2 Why not use Metadata
    * 15.3 Getting & Setting Metadata
  * 16 Databases
    * 16.1 SQLite
    * 16.2 MySQL
  * 17 Deploying your Plugin
  * 18 Importing other plugins
  * 19 Tips and Tricks
    * 19.1 Setting a Player on Fire
    * 19.2 Killing the player
    * 19.3 Creating a Fake Explosion
    * 19.4 Hiding a Player From Another Player
    * 19.5 Spawn Lightning Bolt Where Player is Looking
    * 19.6 Automatically formatting your code
  * 20 Request Section
  * 21 Example Files and Templates

这个看起来有点长的指南旨在让你开始入门开发Bukkit的插件。诚然，无论如何一个指南无法涵盖Bukkit的所有细节，但这个指南依然可以让你对Bukkit插件开发有一个了解和起步。通过这篇指南，你将学会如何使用Java进行开发、在IDE中设置工作目录和Bukkit插件最为基础的开发。

## 学习JAVA

**这篇指南需要你对JAVA编程语言有最为基础的知识** 如果你刚刚开始学习JAVA或者想更进一步，底下的这些链接应该非常有帮助。

[甲骨文Java入门](http://docs.oracle.com/javase/tutorial/) \- 官方入门指导

  * [Java2s.com](http://www.java2s.com/Tutorial/Java/CatalogJava.htm) \- 入门 
  * [Java 101](http://www.javacoffeebreak.com/java101/java101.html) \- 入门 
  * [JavaNotes](http://math.hws.edu/javanotes/) \- 免费在线教材
  * [TheNewBoston](http://thenewboston.org/list.php?cat=31) \- 视频入门指导 

## The Development Environment

在开发插件（或者学习Java）之前，首先你需要部署开发环境。这包含但不限于安装IDE（集成开发环境）。下面的内容将指导你如何安装部署以Eclipse作为IDE的Java开发环境。    

     _For further information, see [Setting Up Your Workspace](/Setting_Up_Your_Workspace)_

你**必须**下载Eclipse来进行**Java**开发，请**不要**使用**JavaEE**开发环境。JavaEE对Maven支持非常不好，而Maven是这篇指南中必须用到的。

## 开始你的插件项目

### 建立你的项目

在开始之前，你首先需要部署你的Eclipse工作区和文件。
启动Eclipse，然后点击_File -> New -> Project:_菜单的来创建一个新项目。

![Newproject.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/1/13/Newproj
ect.png?version=72c02ac1c1c013513549f355e16bc924)

现在，打开_Maven_文件夹后选择_Maven Project_。点击next，然后勾选_Create a simple project_后点击下一步。
如果你无法看到_Maven_文件夹，你需要点击[这里](http://eclipse.org/m2e/download/)下载Eclipse的Maven插件。

![Newproject2.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/5/56/Newpro
ject2.png?version=95b9104780740c46c966b585e36ee13e)

Now, you need to name your group as follows:

  * If you have a domain name, the package would be the domain name in reverse. 
    * Ex: i-am-a-bukkit-developer.com your package would be com.i_am_a_bukkit_developer [source](http://docs.oracle.com/javase/tutorial/java/package/namingpkgs.html)
    * Avoid using a domain you do not own. 
  * No domain? Here are some common conventions 
    1. Create an account on a source control site such as GitHub or sourceforge 
      * For GitHub, follow the instructions [here](http://pages.github.com/) and you will have a sub-domain, so your package would be io.github.<username>  

    2. Use your email. Ex: <username>@gmail.com would be com.gmail.<username>  

    3. This is the least preferred method. Simply use any unique group naming, again, use this as your last resort. 

There are several things that your group must **not** begin with and those
are:

  * org.bukkit 
  * net.bukkit 
  * com.bukkit 
  * net.minecraft 

Once you have the base group name, you will want to finish it off with the
plugin name. Lets use the GitHub Pages example for this. If you are creating a
plugin called _TestPlugin_ your full group name would be
_io.github.<username>_, and your artifact name would be _TestPlugin_. For the
version, simply stick with the default for now. It can be changed later.

Finish the wizard:

![Newproject3.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/b/be/Newpro
ject3.png?version=2f3062f93e96402066ea0fc6a34e9522)

If this is your first time using Eclipse, close the Welcome tab by clicking
the "X" next to the Welcome tab on the tab bar. Now, you should have a window
that looks like this:

![Eclipsemain.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/d/de/Eclips
emain.png?version=ea3d2c48ebba456e2109413cc77b8741)

Click the arrow to the left of your artifact name, and let's get started!

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=6)] Reference
the Bukkit API

Before you begin developing your plugin you will need to add the Bukkit API
library to your project as a dependency, you can also add any other API's you
may want to use.

Double-click _pom.xml_, which is at the bottom of your project's folder. Click
the _pom.xml_ tab at the bottom, and you should see something like this:

![Pomeditor.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/f/f0/Pomedito
r.png?version=eccc160e55c7c1a78bf5cbe2587147be)

If you wish to use Java 6+ language features, you must specify the Java
version that the project should be built on. Copy and paste this (specifies
that the project should be built under Java 7) before _</project>_:

`

    
    
       <build>
          <plugins>
              <plugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-compiler-plugin</artifactId>
                  <configuration>
                      <source>1.7</source>
                      <target>1.7</target>
                  </configuration>
              </plugin>
          </plugins>
       </build>
    

`

You may use other levels, such as `1.8` for Java 8. Please note that
[according to MCStats](http://mcstats.org/global/), the vast majority of
server owners run Java 7, so compiling for Java 8 will result in most server
owners being unable to run your plugin. If you do use Java 1.7 features,
Eclipse will suggest changing the language level when you hover over the code
"error". Do so.

Before the _</project>_ at the bottom, copy and paste this block (it tells
Eclipse where Bukkit's repository is located):

`

    
    
       <repositories>
           <repository>
               <id>bukkit-repo</id>
               <url><http://repo.bukkit.org/content/groups/public/></url>
           </repository>
       </repositories>
    

`

Next, before the _</project>_ at the bottom, copy and paste this block (it
tells Eclipse that we're building against Bukkit):

`

    
    
       <dependencies>
           <dependency>
               <groupId>org.bukkit</groupId>
               <artifactId>bukkit</artifactId>
               <version>1.6.4-R2.0</version>
               <type>jar</type>
               <scope>provided</scope>
           </dependency>
       </dependencies>
    

`

If you wish to, you may change the version of Bukkit you're building against.
You can view the available versions
[here](http://repo.bukkit.org/content/groups/public/org/bukkit/bukkit/).

When you finish, your _pom.xml_ should look similar to this:

![Finishedpom.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/c/c0/Finish
edpom.png?version=6b5a18b506faa0a574ca6f3d5a35aa74)

Save your _pom.xml_ using _File -> Save_ or pressing `Ctrl + S`. Then, right
click the projects title and click _Maven -> Update Project_.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=7)] Bukkit
Javadocs

If you have some experience with Eclipse and Java you will know that when you
hover your mouse over any built in class or method a yellow box will pop up,
containing the documentation for that class or method. This is known as a
Javadoc and can also be accessed online at the [Oracle
website](http://download.oracle.com/javase/6/docs/api/). Bukkit also has
documentation which often contains useful descriptions of each method and
class provided by the API, which is available
[here](http://jd.bukkit.org/apidocs/) (Beta Javadocs can be found
[here](http://jd.bukkit.org/beta/apidocs/), and development build Javadocs
[here](http://jd.bukkit.org/dev/apidocs/)). In order to have this information
available within Eclipse, so that it will pop up whenever you hover over a
Bukkit method or class, first right click on the Bukkit jar where it appears
under "Maven Dependencies" in the project explorer, and select "Properties".
Choose the _Javadoc Location_ item on the left of the window that pops up, and
paste the url **<http://jd.bukkit.org/apidocs/>** (or that of the
beta/development Javadocs linked above) into the textbox under "Javadoc URL".
It should look like this:

![Bukkitjavadocs.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/8/89/Buk
kitjavadocs.png?version=c50acf48ca4a97c85593157f886e2db8)

Click "Validate", and then click "OK". Done! Now the Bukkit Javadocs are
linked to the Bukkit source, and you can access helpful documentation from
within Eclipse.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=8)] Creating
a package

Now you need to create a 'package' which will store all the Java class files
we will be using. Right click on the folder labelled _src/main/java_ and
select _New > Package_:

![Newpackage.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/67/Newpack
age.png?version=bc979d071247525b1eb22f4f02eb4278)

For your package name, put your group name, then a period, and then your
artifact name in lowercase. For example, if your group name is
_io.github.name_ and your artifact name is _TestPlugin_, your package name
would be _io.github.name.testplugin_.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=9)] Creating
the Plugin's Class

Now that we have our project set up we can start to add class files and begin
making our plugin. The plugin's main class is the class that extends
JavaPlugin. There should only ever be one class in your plugin that extends
JavaPlugin either directly or indirectly. It's always good practice to create
your main class first and give it the same name as your plugin. Right click on
the package you created before, and select  _New > Class_. You should have a
new class similar to the following

>

>     package {$GroupName}.{$ArtifactName};

>

>     import org.bukkit.plugin.java.JavaPlugin;

>

>     public final class {$ArtifactName} extends JavaPlugin {

>

>     }

![Warning](http://hydra-
media.cursecdn.com/wiki.bukkit.org/thumb/5/51/Attention_niels_epting.svg/18px-
Attention_niels_epting.svg.png?version=f594b4cdba86f489bc057c8896dddc91)
**Warning**:

Plugins should never invoke their constructor and create new instances

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=10)] Creating
plugin.yml

Now you have setup the project and the main class. To allow Bukkit to load
your plugin, you must create the **[plugin.yml](/Plugin_YAML)** file. This
file will contain essential information, and without it your plugin will NOT
work. This time we want to right click on _src/main/resources_. Select _New >
File_. Name the file "**plugin.yml**" and click finish. Eclipse will open your
currently blank **plugin.yml** file in the default text editor. _(Hint: If you
want to keep your workspace organized, close the text editor and drag the
**plugin.yml** file onto the main workspace(To the right) and you will be able
to edit the file inside eclipse.)_

There are three essential attributes that must be declared in the plugin.yml.

     name: the simple name of your plugin. 
     main: [fully qualified name](http://docs.oracle.com/javase/specs/jls/se7/html/jls-6.html#jls-6.7) of the plugin's main class. 
     version: the version string of your plugin. 

The most simple **plugin.yml** file would look like this :

>

>     name: {$PluginName}

>     main: {$PackageName}.{$MainClass}

>     version: {$VersionNumber}

    ![Lightbulb.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**: The package name for plugins often includes the plugin name so don't be surprised to see <pluginname>.<pluginname> at the end of the second line! 
    ![Lightbulb.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**: Your main class may or may not be the name of your plugin depending on what you named it earlier, keep in mind this is case-sensitive. 

_**For more examples**, see #Example_Files_and_Templates_

At this point your plugin can be loaded by Bukkit, and will be accompanied
with log entries indicating this. But, it will do nothing!

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=11)]
onEnable() and onDisable()

These methods are called whenever the plugin is enabled and disabled. By
default your plugin will automatically enable itself when loaded so you can
register your events and provide some debug output here. `onEnable()` is
invoked when the plugin is enabled, and should contain logic to set up your
plugin when it is enabled. `onDisable()` is invoked when a plugin is disabled,
and should contain logic to clean up your plugin and associated state.
Additionally plugins can override the `onLoad()` method to perform additional
logic when the plugin loads.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=12)]
Introduction to onEnable() and onDisable()

Create the methods `onEnable()` and `onDisable()` inside the main class
created in the previous section. It will look something like the following

>

>     package {$TopLevelDomain}.{$Domain}.{$PluginName};

>

>     import org.bukkit.plugin.java.JavaPlugin;

>

>     public final class {$PluginName} extends JavaPlugin {

>         @Override

>         public void onEnable() {

>             // TODO Insert logic to be performed when the plugin is enabled

>         }

>

>         @Override

>         public void onDisable() {

>             // TODO Insert logic to be performed when the plugin is disabled

>         }

>     }

The methods now exist, but they don't do anything yet. Note: There is no
reason to print a message such as "{$PluginName} has been enabled!" as bukkit
will do this automatically.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=13)] Logging
a message

A plugin can print a message to the console and the server log. It can
accomplish this by invoking the correct method from the plugin's logger. First
we must invoke the `getLogger()` method to retrieve the logger associate with
this plugin. Then we can start logging.

We will write to the log when `onEnable()` method is called. We can do that by
inserting the following line into the `onEnable()` method.

>

>     getLogger().info("onEnable has been invoked!");

You can then do the same inside `**onDisable()**`, making sure to change the
message.

Your main class should now look something like this:

>

>     package {$TopLevelDomain}.{$Domain}.{$PluginName};

>

>     import org.bukkit.plugin.java.JavaPlugin;

>

>     public final class {$PluginName} extends JavaPlugin {

>       @Override

>       public void onEnable() {

>               getLogger().info("onEnable has been invoked!");

>       }

>

>       @Override

>       public void onDisable() {

>               getLogger().info("onDisable has been invoked!");

>       }

>     }

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=14)] Handling
Reloads

It is important to remember that this does not only occur on server shutdown
and startup, your plugin can also be disabled and enabled by other plugins or
through use of the /reload command while the server is running. Assuming that
the server has only just been started when the plugin is enabled is therefore
a dangerous assumption, as there may well already be players online,
additional worlds loaded, additional chunks loaded, and many other unexpected
differences.

For example:

  * You have a plugin that stores information about a player in a HashMap on the PlayerJoinEvent 
  * You rely on having that information available for every player 
  * An operator uses the /reload command 
  * Your plugin is disabled and all data stored is lost 
  * Your plugin is enabled again with several players already online 
  * These players do not have any information stored for them in the HashMap 
  * You try to retrieve information about them but there is none! 

For this to work correctly on reload, you would need to find all players
currently online during onEnable and store the correct information for that
player in the HashMap.

>

>     for (Player player : Bukkit.getServer().getOnlinePlayers()) {

>         playerList.put(player.getName(), playerData(player));

>     }

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=15)] Listeners

Listeners are classes whose methods are invoked in response to an event. All
listeners implement org.bukkit.event.Listener. For further details about
creating listeners,

    

     _ Please See: [Event API Reference](/Event_API_Reference)_

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=16)] Commands

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=17)] The
onCommand() Method

So, you now know how to register events and do something when they happen, but
what if you only want something to happen when a command is typed? You use
`**onCommand**`. This code is run whenever a player types a command preceded
by the "/" character. E.g. typing "/do something" would call the
`**onCommand**` method. In this case nothing would happen because no behaviour
has been programmed.

Avoid using command names that are the same as those that come with Bukkit,
and also consider carefully how unique your commands names will be. E.g. the
"give" command is already used by several plugins, and if you implement yet
another "give" command, your plugin will become incompatible with those other
plugins. You must register your commands in the plugin's **plugin.yml** or
they will not trigger this method.

The `**onCommand**` method must always return a boolean value - either true or
false. If the value returned is true then you won't see any noticable events.
However if it returns false then the plugin will revert to your plugin files'
'usage: property' and display a message to the user showing them how to use
the command as specified in the **plugin.yml** file.

When using `**onCommand**`, you should always register 4 parameters.

  * `**CommandSender sender**` \- who sent the command 
  * `**Command cmd**` \- the command that was executed 
  * `**String commandLabel**` \- the command alias that was used 
  * `**String[] args**` \- an array of additional arguments, e.g. typing _/hello abc def_ would put _abc_ in args[0], and _def_ in args[1] 

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=18)] Setting
up the command

>

>     @Override

>     public boolean onCommand(CommandSender sender, Command cmd, String
label, String[] args) {

>       if (cmd.getName().equalsIgnoreCase("basic")) { // If the player typed
/basic then do the following...

>               // doSomething

>               return true;

>       } //If this has happened the function will return true.

>             // If this hasn't happened the value of false will be returned.

>       return false;

>     }

When coding the `**onCommand**` function it is always good practice to return
false at the very end of the function. Returning false will display the usage
dialog set in **plugin.yml** (see below). This way if anything goes wrong the
help message will be displayed. When returning a value the function will exit
so if you return true any code underneath won't be run, unless a return
statement is nested in an if statement or similar.

The `**.equalsIgnoreCase("basic")**` just means that it won't distinguish
between upper and lower case characters. For example, the string "BAsIc" and
"BasiC" would both equal basic and the code would be executed.

Add also these two lines at the top of your file:

>

>     import org.bukkit.command.Command;

>     import org.bukkit.command.CommandSender;

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=19)] Adding
your Command to the Plugin.yml

You will also need to add the command to your **plugin.yml** file. Add the
following to the end of **plugin.yml**:

> `

>  
>  
>     commands:

>        basic:

>           description: This is a demo command.

>           usage: /<command> [player]

>           permission: <plugin name>.basic

>           permission-message: You don't have <permission>

>

> `

  * `**basic**` \- the name of the command. 
  * `**description**` \- the description of the command . 
  * `**usage**` \- the help dialog that users will see when you return false in the `**onCommand**` method. Write clearly, so that others can discern what the command is and how to use it. 
  * `**permission**` \- This is used by some help plugins to work out which commands to show to the user. 
  * `**permission-message**` \- This is output when the player attempts but does not have permission to use the command. 

Note that yml files use 2 spaces for tabs, as the tab character will cause
problems.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=20)] Console
Commands vs. Player Commands

You may have noticed the `**CommandSender sender**` parameter above.
`**CommandSender**` is a Bukkit interface which has two useful (for plugin
writers) subclasses: `**Player**` and `**ConsoleCommandSender**`.

When you're writing your plugin, it's a very good idea to ensure that commands
that _can_ be run from the console actually work, and that commands that
should only be run as a logged-in player really _are_ only run as a logged-in
player. Some plugins simply return if the sender is not a player (i.e. someone
tried to use the plugin's commands from the console), even when those commands
make perfect sense from the console (e.g. changing the weather on the server).

One way to do this is:

>

>     @Override

>     public boolean onCommand(CommandSender sender, Command cmd, String
label, String[] args) {

>       if (cmd.getName().equalsIgnoreCase("basic")) { // If the player typed
/basic then do the following...

>               // do something...

>               return true;

>       } else if (cmd.getName().equalsIgnoreCase("basic2")) {

>               if (!(sender instanceof Player)) {

>                       sender.sendMessage("This command can only be run by a
player.");

>               } else {

>                       Player player = (Player) sender;

>                       // do something

>               }

>               return true;

>       }

>       return false;

>     }

In this example, the command **basic** can be run by anyone - a logged-in
player, or the server operator on the console. But the command **basic2** can
only be run by logged-in players.

In general, you should allow as many commands as possible to work on both the
console and for players. Commands that _need_ a logged-in player can use the
mechanism in the example above to check that the `**CommandSender**` is
actually a player before continuing. Such commands would generally depend on
some attribute of the player, e.g. a teleportation command needs a player to
teleport, an item giving command needs a player to give the item to...

If you want to get more advanced, you could do some extra checks on your
command arguments so that e.g. a teleportation command could be used from the
console _if and only if_ a player's name is also supplied.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=21)] Using a
separate CommandExecutor class

The examples above just put the `**onCommand()**` method into the plugin's
main class. For small plugins, this is fine, but if you're writing something
more extensive, it may make sense to put your `**onCommand()**` method into
its own class. Fortunately, this isn't too hard:

  * Create a new class within your plugin's package. Call it something like **MyPluginCommandExecutor** (although of course replacing **MyPlugin** with your plugin's actual name). That class _must_ implement the Bukkit **CommandExecutor** interface. 
  * In your plugin's `**onEnable()**` method, you need to create an instance of your new command executor class, and then make a call like `getCommand("basic").setExecutor(myExecutor);`, where "basic" is the command we want to handle, and `myExecutor` is the instance we created. 

Best explained by example:

**MyPlugin.java** (the main plugin class): 

>

>     @Override

>     public void onEnable() {

>       // This will throw a NullPointerException if you don't have the
command defined in your plugin.yml file!

>       this.getCommand("basic").setExecutor(new
MyPluginCommandExecutor(this));

>     }

**MyPluginCommandExecutor.java**: 

>

>     public class MyPluginCommandExecutor implements CommandExecutor {

>       private final MyPlugin plugin;

>

>       public MyPluginCommandExecutor(MyPlugin plugin) {

>               this.plugin = plugin; // Store the plugin in situations where
you need it.

>       }

>

>       @Override

>       public boolean onCommand(CommandSender sender, Command cmd, String
label, String[] args) {

>               // implementation exactly as before...

>       }

>     }

Notice how we send a reference of the main plugin object to
**MyPluginCommandExecutor**. This allows us easy access to the main plugin
objects's methods if we need to.

By doing this, we can better organise our code - if the main `**onCommand()**`
method is large and complex, it can be split into submethods without
cluttering up the plugin's main class.

Note that if your plugin has multiple commands, you will need set the command
executor for each command individually.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=22)] Writing
a safe onCommand

When writing a onCommand, it's important that you don't assume any
information, such as the sender being a Player. Things to keep in mind:

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=23)] Make
sure the sender is a Player before casting

Using simple code like this makes it possible:

>

>     @Override

>     public boolean onCommand(CommandSender sender, Command cmd, String
label, String[] args) {

>       if (sender instanceof Player) {

>                Player player = (Player) sender;

>                // do something

>             } else {

>                sender.sendMessage("You must be a player!");

>                return false;

>             }

>             // do something

>             return false;

>     }

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=24)] Check
the arguments length

Don't always assume the sender typed the correct amount of arguments.

>

>     @Override

>     public boolean onCommand(CommandSender sender, Command cmd, String
label, String[] args) {

>       if (args.length > 4) {

>                sender.sendMessage("Too many arguments!");

>                return false;

>             }

>             if (args.length < 2) {

>                sender.sendMessage("Not enough arguments!");

>                return false;

>             }

>     }

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=25)] Check
if a Player is online before getting them

Sometimes you want to get another player by the name entered by the player.
Always make sure the player is online!

>

>     @Override

>     public boolean onCommand(CommandSender sender, Command cmd, String
label, String[] args) {

>       Player target = (Bukkit.getServer().getPlayer(args[0]));

>             if (target == null) {

>                sender.sendMessage(args[0] + " is not online!");

>                return false;

>             }

>             return false;

>     }

If you need to modify a Player currently not online, the `**OfflinePlayer**`
class provides basic manipulation methods.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=26)] Plugin
Configuration/Settings

The Bukkit API provides a convenient way for plugins to manage user
configurable settings. Additionally it also serves as an easy way to store
data.

    

     _Please see: [Configuration API Reference](/Configuration_API_Reference)_

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=27)]
Permissions

With the new Bukkit API for permissions, they couldn't be easier. To find out
if a player has a particular permission use the following:

>

>     if (player.hasPermission("some.pointless.permission")) {

>        //Do something

>     } else {

>        //Do something else

>     }

You can also find if a permission has been set or not (equivalent to Java's
**null**) with the following function:

>

>     boolean isPermissionSet(String name)

You may be wondering why there aren't any groups. The answer to that is
because they aren't really needed. Previously one of the main uses for groups
was to format chat messages. That however can be done just as easily with
permissions. Inside your chat plugin's config you would define associations
between permissions and prefixes. For example the permission
"someChat.prefix.admin" would correspond to the prefix [Admin]. Whenever a
player speaks with that permission their name will be prefixed with [Admin].

Another common usage might be to send a message to all users within a group.
Again however this can be done with permissions with the following:

>

>     for (Player player: Bukkit.getServer().getOnlinePlayers()) {

>         if (player.hasPermission("send.receive.message")) {

>             player.sendMessage("You were sent a message");

>         }

>     }

Finally you may be asking, well how do I set and organise player's permissions
if there are no groups? Although the bukkit API doesn't provide groups itself,
you must install a permission provider plugin such as permissionsBukkit to
manage the groups for you. **This API provides the interface, not the
implementation.**

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=28)]
Configuring your permissions

If you want more control over your permissions, for example default values or
children then you should consider adding them to your
_[plugin.yml](/Plugin.yml)_. This is completely optional, however it is
advised. Below is an example permissions config that would be appended to the
end of your existing _plugin.yml_:

> `

>  
>  
>     permissions:

>         doorman.*:

>             description: Gives access to all doorman commands

>             children:

>                 doorman.kick: true

>                 doorman.ban: true

>                 doorman.knock: true

>                 doorman.denied: false

>         doorman.kick:

>             description: Allows you to kick a user

>             default: op

>         doorman.ban:

>             description: Allows you to ban a user

>             default: op

>         doorman.knock:

>             description: Knocks on the door!

>             default: true

>         doorman.denied:

>             description: Prevents this user from entering the door

>

> `

Firstly, each permission your plugin uses is defined as a child node of the
_permissions_ node. Each permission can then optionally have a description, a
default value, and children.

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=29)]
Defaults

By default when a permission isn't defined for a player _hasPermission_ will
return false. Inside your plugin.yml you can change this by setting the
default node to be one of four values:

  * **true** \- The permission will be true by default. 
  * **false** \- The permission will by false by default. 
  * **op** \- If the player is an op then this will be true. 
  * **not op** \- If the player is not an op then this will be true. 

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=30)]
Children

Before now you will probably be used to the * permission to automatically
assign all sub permissions. This has changed with the bukkit API and you can
now define the child permissions. This allows for a lot more flexibility.
Below is an example of how you do this:

>

>     permissions:

>         doorman.*:

>             description: Gives access to all doorman commands

>             children:

>                 doorman.kick: true

>                 doorman.ban: true

>                 doorman.knock: true

>                 doorman.denied: false

Here the _doorman.*_ permission has several child permissions assigned to it.
The way child permissions work is when _doorman.*_ is set to true, the child
permissions are set to their values defined in the _plugin.yml_. If however
_doorman.*_ was set to false then all child permissions would be inverted.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=31)] Setting
your own permissions

If you wish to know about developing your own permissions plugins (Ones that
actually set permissions) then check out the tutorial on [Developing a
permissions plugin](/Developing_a_permissions_plugin).

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=32)]
Scheduling Tasks and Background Tasks

Currently, Minecraft servers operate nearly all of the game logic in one
thread, so each individual task that happens in the game needs to be kept very
short. A complicated piece of code in your plugin has the potential to cause
huge delays and lag spikes to the game logic, if not handled properly.

Luckily, Bukkit has support for scheduling code in your plugin. You can submit
a Runnable task to occur once in the future, or on a recurring basis, or you
can spin off a whole new independent thread that can perform lengthy tasks in
parallel with the game logic.

There is a separate [Scheduler Programming](/Scheduler_Programming) tutorial
which introduces the Scheduler, and gives more information on using it to
schedule synchronous tasks, and on kicking off asynchronous tasks in Bukkit.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=33)] Block
Manipulation  

The easiest way to create blocks is to get an existing block and modify it.
For example, if you want to change the block that is located five blocks above
you, you would first have to get your current location, add five to your
current y-coordinate, and then change it. For example:

>

>     @EventHandler

>     public void onPlayerMove(PlayerMoveEvent event) {

>         // Get the player's location.

>         Location loc = event.getPlayer().getLocation();

>         // Sets loc to five above where it used to be. Note that this
doesn't change the player's position.

>         loc.setY(loc.getY() + 5);

>         // Gets the block at the new location.

>         Block b = loc.getBlock();

>         // Sets the block to type id 1 (stone).

>         b.setType(Material.STONE);

>     }

The above code gets the player's location, gets the block five above it, and
sets it to stone. Note that once you have a `Block`, there are other things
you can do besides set its type. Consult the JavaDocs for more information.

You can use a similar concept to generate buildings and individual blocks
programmatically through the use of algorithms. For example, to generate a
solid cube, you could use nested `for` loops to loop over an entire cube and
fill it in.

>

>     public void generateCube(Location loc, int length) {

>         // Set one corner of the cube to the given location.

>         // Uses getBlockN() instead of getN() to avoid casting to an int
later.

>         int x1 = loc.getBlockX();

>         int y1 = loc.getBlockY();

>         int z1 = loc.getBlockZ();

>

>         // Figure out the opposite corner of the cube by taking the corner
and adding length to all coordinates.

>         int x2 = x1 + length;

>         int y2 = y1 + length;

>         int z2 = z1 + length;

>

>         World world = loc.getWorld();

>

>         // Loop over the cube in the x dimension.

>         for (int xPoint = x1; xPoint <= x2; xPoint++) {

>             // Loop over the cube in the y dimension.

>             for (int yPoint = y1; yPoint <= y2; yPoint++) {

>                 // Loop over the cube in the z dimension.

>                 for (int zPoint = z1; zPoint <= z2; zPoint++) {

>                     // Get the block that we are currently looping over.

>                     Block currentBlock = world.getBlockAt(xPoint, yPoint,
zPoint);

>                     // Set the block to type 57 (Diamond block!)

>                     currentBlock.setType(Material.DIAMOND_BLOCK);

>                 }

>             }

>         }

>     }

This method will construct a 3D cube or cuboid with the given length and
starting point. As for deleting blocks simply follow the same method for
creating them but set the ID to 0 (air).  

> ## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=34)]
(Player) Inventory Manipulation

This section mostly covers player inventory manipulation, but the same applies
to chest inventory manipulation as well if you find out how to get a chest's
inventory :P. Here is a simple example of inventory manipulation:

>

>     public void onPlayerJoin(PlayerJoinEvent evt) {

>         Player player = evt.getPlayer(); // The player who joined

>         PlayerInventory inventory = player.getInventory(); // The player's
inventory

>         ItemStack itemstack = new ItemStack(Material.DIAMOND, 64); // A
stack of diamonds

>

>         if (inventory.contains(itemstack)) {

>             inventory.addItem(itemstack); // Adds a stack of diamonds to the
player's inventory

>             player.sendMessage("Welcome! You seem to be reeeally rich, so we
gave you some more diamonds!");

>         }

>     }

So inside onPlayerJoin we first make a few variables to make our job easier:
player, inventory and itemstack. Inventory is the player's inventory and
itemstack is a ItemStack that has 64 diamonds. After that we check if the
player's inventory contains a stack of diamonds. If the player has a stack of
diamonds, we give him/her another stack with inventory.addItem(itemstack) and
send a message. So inventory manipulation isn't actually that hard, if we
wanted we could remove the stack of diamonds by simply replacing
inventory.addItem(itemstack) with inventory.remove(itemstack) and change the
message a little bit. Hopefully this helped!

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=35)] Item
Manipulation

When dealing with items in the code, you use the ItemStack class for looking
up and setting all information on that stack.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=36)]
Enchantments

To enchant an item you must first know the [Item
Code](http://www.minecraftwiki.net/wiki/Data_values) and the [Effect
ID](http://www.minecraftwiki.net/wiki/Talk:Enchanting#Effect_IDs).
Enchantments themselves cannot be instantiated (new Enchantment() won't work)
because they're abstract, so you must use an EnchantmentWrapper. If you want
to enchant items that can't be enchanted inside normal SMP, use
addUnsafeEnchantment() instead of addEnchantment()

    
    
    int itemCode = 280;  //use the item code you want here
    int effectId = 20;  //use the enchantment code you want here
    int enchantmentLevel = 100;
     
    ItemStack myItem = new ItemStack(itemCode);  //new item of item code
    Enchantment myEnchantment = new EnchantmentWrapper(effectId);  //new enchantment of effect id
    myItem.addEnchantment(myEnchantment, enchantmentLevel);  //enchant the item

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=37)] ItemMeta

You can set the display name of an item by doing this.

    
    
    String myDisplayName = "Awesome Sword"; //use the displayname you want here
     
    ItemStack myItem = new ItemStack(Material.DIAMOND_SWORD);  //your item
    ItemMeta im = myItem.getItemMeta(); //get the itemmeta of the item
    im.setDisplayName(myDisplayName); //set the displayname
    myItem.setItemMeta(im); //give the item the new itemmeta

You can also set the lores of an item. The lores are the small annotations on
an item, like "+5 attack damage" on a stone sword.

    
    
    List<String> lores = new ArrayList<String>();
    lores.add("Example lore", "this one comes on line 2");
     
    ItemStack myItem = new ItemStack(Material.DIAMOND_SWORD);  //your item
    ItemMeta im = myItem.getItemMeta(); //get the itemmeta of the item again
    im.setLore(lores); //add the lores of course
    myItem.setItemMeta(im); //give the item the new itemmeta

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=38)] Maps, and
Sets, and Lists, Oh My!

Besides the Map/HashMap classes, Java offers many other data structures. They
offer these different classes because there are times when a Map is not the
most appropriate. Here's a separate page for discussing [Java data structure
classes](/index.php?title=Java_data_structure_classes&action=edit&redlink=1)
in more detail.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=39)] HashMaps
and How to Use Them

**Keep in mind to never use a player in a hashmap!** You need to use Strings instead. So use "p.getName()" to add, remove or check if a list contains a player. Saving a player as an object causes huge memory leaks. 

When making a plugin you will get to a point where just using single variables
to state an event has happened or a condition has been met will be
insufficient, due to more than one player performing that action/event.

This was the problem I had with one of my old plugins, Zones, now improved and
re-named to Regions. I was getting most of these errors because I didn't
consider how the plugin would behave on an actual server with more than one on
at any given time. I was using a single boolean variable to check whether
players were in the region or not and obviously this wouldn't work as the
values for each individual player need to be separate. So if one player was in
a region and one was out the variable would constantly be changing which
could/would/did cause numerous errors.

A HashMap is an excellent way of doing this. A HashMap is a way of
mapping/assigning a value to a key. You could set up the HashMap so that the
key is a player and the value could be anything you want, however the useful
things with HashMaps is that one key can only contain one value and there can
be no duplicate keys. So say for example I put "adam" as the key and assigned
a value of "a" to it. That would work as intended, but then say afterwards I
wanted to assign the value of "b" to key "adam" I would be able to and would
get no errors but the value of "a" assigned to key "adam" in the HashMap would
be overwritten because HashMaps cannot contain duplicate values.

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=40)]
Defining a HashMap

>

>     public Map<KeyType, DataType> HashMapName = new HashMap<>(); //Example
syntax

>

>     // Example Declaration

>     public Map<String, Boolean> pluginEnabled = new HashMap<>();

>     public Map<String, Boolean> isGodMode = new HashMap<>();

Keep that code in mind because we will be using it for the rest of the
tutorial on HashMaps. So, for example lets create a simple function which will
toggle whether the plugin has been enabled or not. Firstly, inside your on
command function which I explained earlier you will need to create a function
to send the player name to the function and adjust the players state
accordingly.

So inside on command you'll need this, the function name can be different but
for the sake of simplicity it's best if you keep it the same.

>

>     Player player = (Player) sender;

>     togglePluginState(player);

This code above will cast the value of sender to player and pass that argument
to the function togglePluginState(). But now we need to create our
togglePluginState() function.

>

>     public void togglePluginState(Player player) {

>         // Notice how we use the player name as the key here,

>         // not the player object

>         String playerName = player.getName();

>         if (pluginEnabled.containsKey(playerName)) {

>             if (pluginEnabled.get(playerName)) {

>                 pluginEnabled.put(playerName, false);

>                 player.sendMessage("Plugin disabled");

>             } else {

>                 pluginEnabled.put(playerName, true);

>                 player.sendMessage("Plugin enabled");

>             }

>         } else {

>             pluginEnabled.put(playerName, true); //If you want plugin
disabled by default change this value to false.

>             player.sendMessage("Plugin enabled");

>         }

>     }

Now, what this code is doing is checking if the HashMap first contains the key
player, so if it has been put into the HashMap, if it is then we check the
value of the HashMap key by get(player); if this is true then set value to
false and send the player a message, else if the value is false then do the
opposite, set the value to true and send a message again. But if the HashMap
does not contain the key player then we can assume that this is their first
run/use so we change the default value and add the player to the HashMap.

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=41)] More
Ideas for HashMaps

A HashMap (or really any kind of Map in Java) is an association. It allows
quick and efficient lookup of some sort of **value**, given a unique **key**.
Anywhere this happens in your code, a Map may be your solution.

Here are a few other ideas which are ideally suited to using Maps. As you will
see, it doesn't have to be data that you store per player, but can be any kind
of data that needs to be "translated" from one form to another.

##### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=42)] Data
Value Lookups

>

>     public Map<String, Integer> wool_colors = new HashMap<>();

>

>     // Run this on plugin startup (ideally reading from a file instead of
copied out row by row):

>     wool_colors.put("orange", 1);

>     wool_colors.put("magenta", 2);

>     wool_colors.put("light blue", 3);

>        ..

>     wool_colors.put("black", 15);

>

>     // Run this in response to user commands - turn "green" into 13

>     int datavalue = 0;

>     if (wool_colors.containsKey(argument)) {

>         datavalue = wool_colors.get(argument);

>     } else {

>         try { datavalue = Integer.parseInt(argument); }

>         catch (Exception e) {}

>     }

#### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=43)]
Saving/Loading a HashMap

Once you know how to work with HashMaps, you probably want to know how to save
and load the HashMap data. Saving and loading HashMap data is appropriate if

  * you don't want an administrator to edit the data manually 
  * you need to save data in binary format (too complex to organize for YAML) 
  * you want to avoid parsing block names and/or other objects from freeform text 

This is very simple way how to save any HashMap. You can replace
HashMap<String, Integer> with any type of HashMap you want. Let's take an
example HashMap with code to save it:

>

>             HashMap<String, Integer> mapToSave = new
HashMap<String,Integer>();

>             public void save(HashMap<String, Integer> map, String path) {

>       try {

>               ObjectOutputStream oos = new ObjectOutputStream(new
FileOutputStream(path));

>               oos.writeObject(map);

>               oos.flush();

>               oos.close();

>               //Handle I/O exceptions

>       } catch(Exception e) {

>               e.printStackTrace();

>       }

>     }

>

>     // ...

>

>     save(mapToSave, getDataFolder() + File.separator + "example.bin");

You can see it's really easy. Loading works very very similar but we use
ObjectInputStream instead of ObjectOutputStream ,FileInputStream instead of
FileOutputStream,readObject() instead of writeObject() and we return the
HashMap.

>

>     public HashMap<String, Integer> load(String path) {

>       try {

>               ObjectInputStream ois = new ObjectInputStream(new
FileInputStream(path));

>               Object result = ois.readObject();

>               //you can feel free to cast result to HashMap<String, Integer>
if you know there's that HashMap in the file

>               return (HashMap<String, Integer>)result;

>       } catch(Exception e) {

>               e.printStackTrace();

>       }

>     }

>

>     // ...

>

>     HashMap<Integer, String> loadedMap;

>

>     String path = getDataFolder() + File.separator + "example.bin";

>     File file = new File(path);

>

>     if (file.exists()) { // check if file exists before loading to avoid
errors!

>       loadedMap  = load(path);

>     }

You can use this "API" for saving/loading HashMaps, ArrayLists, and all
Objects which implement Serializable or Externalizable interface.

>

>     /** SLAPI = Saving/Loading API

>      * API for Saving and Loading Objects.

>      * Everyone has permission to include this code in their plugins as they
wish :)

>      * @author Tomsik68<[[email protected]](http://www.cloudflare.com/email-
protection)>

>      */

>     public class SLAPI

>     {

>       public static <T extends Object> void save(T obj,String path) throws
Exception

>       {

>               ObjectOutputStream oos = new ObjectOutputStream(new
FileOutputStream(path));

>               oos.writeObject(obj);

>               oos.flush();

>               oos.close();

>       }

>       public static <T extends Object> T load(String path) throws Exception

>       {

>               ObjectInputStream ois = new ObjectInputStream(new
FileInputStream(path));

>               T result = (T)ois.readObject();

>               ois.close();

>               return result;

>       }

>     }

Example implementation of this API: **I'm skipping some part of code in this
source**

>

>     public class Example extends JavaPlugin {

>       private ArrayList<Object> list = new ArrayList<>();

>

>       @Override

>       public void onEnable() {

>                 try {

>               list = SLAPI.load("example.bin");

>                 } catch(Exception e) {

>                     //handle the exception

>                     e.printStackTrace();

>                 }

>       }

>

>       @Override

>       public void onDisable() {

>                 try {

>               SLAPI.save(list,"example.bin");

>                 } catch(Exception e) {

>                      e.printStackTrace();

>                 }

>       }

>     }

Note #1: This will work un-modified with almost all well-known Java types like
Integer, String, HashMap. It will also work for some Bukkit types as well. If
you're writing your own data object classes, and you may want to save their
state using this technique, you should read about Java's Serializable or
Externalizable interface. The only difference between Externalizable and
Serializable is, that Serializable automatically takes all of class's fields
and tries to serialize them, while Externalizable allows you to define method
for reading and writing the Object. It's easy to add to your code, and it will
make your data persistent with very little work required. No more parsing!

Note #2: This API doesn't support changes. Once you change something in the
class, data files saved with older version of your plugin won't load
correctly.

##### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=44)] Tips &
Examples

1.) Simplify your save structure

Try to use as much simple types as possible. E.g. if you want to save player,
save their UUID instead. If you want to save world, save its UUID. If you want
to save location, save x,y,z world UUID. DO NOT DIRECTLY SAVE BUKKIT TYPES!

2.) Save version number along with data

You should always remember, that you don't know what you'll be saving in the
same file tomorrow. Will you ever migrate this file because of newer version
of your plugin, bukkit, or minecraft? You don't know!

3.) Migrate older files

If your plugin finds older version of some file, it should update the file
accordingly and change version number.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=45)] Metadata

Bukkit is trying to make plugin development as easy as possible, so HashMaps
with key of type Player, Entity, World or even a Block were replaced by
Metadata. Metadata is some kind of alternative to HashMap. It allows you to
add custom "fields" to Players, Entities, Worlds and Blocks. These things are
all members of Metadatable class(check [[1]](http://jd.bukkit.org/doxygen/de/d
59/interfaceorg_1_1bukkit_1_1metadata_1_1MetadataValue.html#ab49975fe013a0626d
d29d3b85c63a82f))It works very simply. Everything that is Metadatable holds
its own HashMap of Metadata which you have access to. That means, for example,
if you're creating an economy plugin, you would need a HashMap of Player and
Float or Double. With Metadata, you don't have to! You just attach to player
new metadata value, and that's it!  

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=46)] Why to
use Metadata

  * Metadata is all handled by Bukkit, which makes it a very good alternative to HashMaps. 
  * Metadata can be used to share information between plugins. 

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=47)] Why not
use Metadata  

  * Slightly more difficult to get the value. 
  * It is not saved on shutdown (but then again, neither are any Maps that you create). 

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=48)] Getting
& Setting Metadata

    
    
    public void setMetadata(Metadatable object, String key, Object value, Plugin plugin) {
      object.setMetadata(key, new FixedMetadataValue(plugin,value));
    }
     
    public Object getMetadata(Metadatable object, String key, Plugin plugin) {
      List<MetadataValue> values = object.getMetadata(key);  
      for (MetadataValue value : values) {
         // Plugins are singleton objects, so using == is safe here
         if (value.getOwningPlugin() == plugin) {
            return value.value();
         }
      }
      return null;
    }

Note: If you're manipulating with numbers, booleans or strings, use convenient
method to get the result. For example, you can use asInt(), asString() or
asBoolean() instead of value to find out the value.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=49)] Databases

Sometimes flat files aren't enough for what your looking to do, this is where
databases come in. The most common database engines available on
Linux/Mac/Windows machines typically run on some flavor of SQL (Structured
Query Language).

Software offering SQL allow you to create databases with columns and header to
identify to contents of each cell. Think of it as a spreadsheet on steroids,
where every column you set up in your database can enforce rules to ensure
integrity. Apart from being more organised than a simple custom data file, SQL
provides faster access and better searching than flat files.

The SQL standard helps applications like Bukkit implement database storage for
their data in a consistent way. Unfortunately, there's more than one SQL-ready
database engine, and each has minor differences in how to configure and use
it. Which one you choose may depend on your particular needs. (Some plugins
even offer configurable options to connect to multiple database engines!)

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=50)] SQLite

Alta189 has written a [fantastic SQLite
tutorial](http://forums.bukkit.org/threads/lib-tut-mysql-sqlite-bukkit-
drivers.33849/) which I suggest you watch if you're interested in using SQL in
your plugins, included with the tutorials is a handy library you can download
and import to make using SQL easier. Once you have watched these video
tutorials I would suggest you go and learn some SQL syntax, it's very
straightforward and shouldn't take you long to pick up. SQL Tutorials
[@W3Schools](http://www.w3schools.com/sql/default.asp) and
[@1Keydata](http://www.1keydata.com/sql/sql.html).

SQLite is great for very simple databases, because there's no server concerns
to set up. Just make a few calls to create a new database and table. It's easy
to back up: just copy the whole database file in one go. SQLite is a little
bit weaker at data integrity, flexibility in data types, and it may not be
something you would want to trust for huge databases of millions of rows. But
for a new plugin in development, it's often easiest and fastest to get the SQL
basics squared away with SQLite, even if you "graduate" to a more server-class
database engine later.

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=51)] MySQL

Another popular SQL database engine is called MySQL. It is closer to server-
grade than SQLite, where many popular companies or websites depend on it for
millions of webpage hits every day. With that security comes a little bit
steeper learning-curve, because MySQL has more tunable parameters and
capabilities.

The coding for plugins accessing MySQL is mostly the same as tiny SQLite or
mega-sized Oracle, with only small differences in syntax here or there. But
the administration has room to grow. You may want to set up accounts and
privileges inside your MySQL setup. You may want to set up SQL scripts that
organize your backups and rollback to previous states.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=52)] Deploying
your Plugin

Once you have written your plugin, how do you get it from a collection of
source files into a working jar file that can be installed on a server? First,
set up a CraftBukkit server on your local machine. To do this, visit the wiki
page on [Setting up a server](http://wiki.bukkit.org/Setting_up_a_server).
Next you have to export your plugin to a .jar so that you can run it on your
new server. To do this in Eclipse, right-click the project and click _Run as >
Maven install_:

![Maveninstall.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/4/49/Maven
install.png?version=b7d672947451767dcf887d33fb8a202b)

In the future, when you make code changes to your plugin, you want to delete
the previous JAR by right-clicking the project and clicking _Run as > Maven
clean_ before doing the above. If you're having issues when building your
plugin, check if your Java Development Kit (JDK) is properly installed and
review [Setting Up Your Workspace](/Setting_Up_Your_Workspace). You may need
to configure your JDK manually if you see a JDK-related error in the console,
as Eclipse may not have detected it correctly. Go to _Window -> Preferences_,
and go to _Java -> Installed JREs_. Add the latest JDK you've installed as a
JRE, tick that one, and untick the active one that was giving you issues:

![Jrelocation.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/8/81/Jreloc
ation.png?version=d814215718a01ae0b09e1c7b912e3f80)

If your project built successfully, the JAR file is now under the _target_
folder in your project's folder under your Eclipse workspace. The JAR file you
have exported should now be a working plugin! Assuming of course that there
are no errors in your code or your plugin.yml file. You can now drop the jar
file you have exported into your Bukkit server's "plugins" folder, reload or
relaunch the server, and test away! In order to connect to a server running
locally on your computer, simply put "localhost" as the IP address of the
server in Minecraft multiplayer. If you run into errors that you can't solve
for yourself, try visiting the [plugin development
forum](http://forums.bukkit.org/forums/plugin-development.5/), asking in the
[bukkitdev IRC channel](http://wiki.bukkit.org/IRC), or re-reading this wiki.
Once you have a useful working plugin, consider submitting your project to
[dev.bukkit](http://dev.bukkit.org/) for consumption by the Bukkit community.
From the wizard above, you can see that the JAR file will be by default a
compressed archive (JARs are based on the ZIP archive format). As such, it
does not make sense to put your JAR into a ZIP archive when uploading to
BukkitDev and will only increase the file size. Further, config files can be
placed within the JAR and copied into the plugin's data folder if the
configuration file does not exist. There is usually no good reason for
packaging JAR files into another archive.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=53)] Importing
other plugins

You may wish to edit another plugin that has the source available. If that
plugin has a _pom.xml_ in its folder (most of the popular ones, for example
WorldEdit and Essentials, do), you can import it as a project by selecting
_File -> Import_, and then opening the _Maven_ folder and selecting _Existing
Maven Projects_:

![Importmaven.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/3/36/Import
maven.png?version=c73d4c245a245d3106f8ac52f2026189)

Then select the folder that the _pom.xml_ is in, and the project should be on
your sidebar. Edit it and compile it like you usually would.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=54)] Tips and
Tricks

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=55)] Setting
a Player on Fire

The Bukkit API is capable of a lot of cool stuff. Here are some code snippets
for some nice effects!

The following code allows a player to set another player on fire. Running a
command like **/ignite Notch** would cause Notch to be set on fire!

    
    
    @Override
    public boolean onCommand(CommandSender sender, Command cmd, String label, String[] args) {
        // Uses equalsIgnoreCase() over equals() to accept "ignite" and "IgNiTe."
        if (cmd.getName().equalsIgnoreCase("ignite")) {
            // Make sure that the player specified exactly one argument (the name of the player to ignite).
            if (args.length != 1) {
                // When onCommand() returns false, the help message associated with that command is displayed.
                return false;
            }
     
            // Make sure the sender is a player.
            if (!(sender instanceof Player)) {
                sender.sendMessage("Only players can set other players on fire.");
                sender.sendMessage("This is an arbitrary requirement for demonstration purposes only.");
                return true;
            }
     
            // Get the player who should be set on fire. Remember that indecies start with 0, not 1.
            Player target = Bukkit.getServer().getPlayer(args[0]);
     
            // Make sure the player is online.
            if (target == null) {
                sender.sendMessage(args[0] + " is not currently online.");
                return true;
            }
     
            // Sets the player on fire for 1,000 ticks (there are ~20 ticks in second, so 50 seconds total).
            target.setFireTicks(1000);
            return true;
        }
        return false;
    }

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=56)] Killing
the player

To keep with the theme, here's a way to kill the player.

Use this for your onCommand method:

>

>     @Override

>     public boolean onCommand(CommandSender sender, Command cmd, String
label, String[] args) {

>         if (cmd.getName().equalsIgnoreCase("KillPlayer")) {

>             Player target = sender.getServer().getPlayer(args[0]);

>              // Make sure the player is online.

>             if (target == null) {

>                 sender.sendMessage(args[0] + " is not currently online.");

>                 return true;

>             }

>             target.setHealth(0);

>         }

>         return false;

>     }

Here is an extension to that, that will kill the player with an explosion:

>

>     float explosionPower = 4F; //This is the explosion power - TNT
explosions are 4F by default

>     Player target = sender.getWorld().getPlayer(args[0]);

>     target.getWorld().createExplosion(target.getLocation(), explosionPower);

>     target.setHealth(0);

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=57)] Creating
a Fake Explosion

This code produces the TNT/Creeper Visual and Audio effects. However, no
explosion damage is dealt to surrounding entities or blocks. This is useful
for nerfing explosions while still keeping the aesthetics of them.

>

>     @EventHandler

>     public void onExplosionPrime(ExplosionPrimeEvent event) {

>         Entity entity = event.getEntity();

>

>         // If the event is about primed TNT (TNT that is about to explode),
then do something

>         if (entity instanceof TNTPrimed) {

>             entity.getWorld().createExplosion(entity.getLocation(), 0);

>         }

>     }

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=58)] Hiding a
Player From Another Player

This will hide the player who used this command from a specified player.
Everyone else will be able to see the player.

    
    
    @Override
    public boolean onCommand(CommandSender sender, Command cmd, String label, String[] args) {
        if (cmd.getName().equalsIgnoreCase("HideMe") && args.length == 1) {
            if (!(sender instanceof Player)) {
                sender.sendMessage("Only players can use this command!");
                return true;
            }
            // After checking to make sure that the sender is a Player, we can safely case it to one.
            Player s = (Player) sender;
     
            // Gets the player who shouldn't see the sender.
            Player target = Bukkit.getServer().getPlayer(args[0]);
            if (target == null) {
                sender.sendMessage("Player " + args[0] + " is not online.");
                return true;
            }
            // Hides a given Player (s) from someone (target).
            target.hidePlayer(s);
            return true;
        }
        return false;
    }

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=59)] Spawn
Lightning Bolt Where Player is Looking

The code below allows any player with a fishing rod to create a lightning
strike by clicking (and aiming somewhere). It's a simple and funny trick.

    
    
    @EventHandler
    public void onPlayerInteractBlock(PlayerInteractEvent event) {
        Player player = event.getPlayer();
        if (player.getItemInHand().getType() == Material.FISHING_ROD) {
            // Creates a bolt of lightning at a given location. In this case, that location is where the player is looking.
            // Can only create lightning up to 200 blocks away.
            player.getWorld().strikeLightning(player.getTargetBlock(null, 200).getLocation());
        }
    }

### [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=60)]
Automatically formatting your code

Eclipse provides functionality to automatically format your code to Oracle
conventions, fixing unconventional indentations, spacing, and such. Simply
select your project in the sidebar, and then select _Source -> Format_.

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=61)] Request
Section

<http://forums.bukkit.org/forums/plugin-requests.13/>

## [[edit](/index.php?title=Plugin_Tutorial&action=edit&section=62)] Example
Files and Templates

  * [Bukkit/SamplePlugin on GitHub](https://github.com/Bukkit/SamplePlugin/)
  * [Example.Java](http://pastebin.com/wpeTPx7N)
  * [ExamplePlayerListener.Java](http://pastebin.com/MTwaAVCT)
  * [ExampleBlockListener.Java](http://pastebin.com/6FLixfH3)
  * [ExampleEntityListener.Java](http://pastebin.com/8UZ6pkWC)