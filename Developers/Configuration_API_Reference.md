#  Configuration API Reference

The Configuration API is a set of tools to help developers quickly parse and
emit configuration files that are human readable and editable. Despite the
name, the API can easily be used to store plugin data in addition to plugin
configuration. Presently only [YAML](http://en.wikipedia.org/wiki/YAML)
configurations can be used. The API however was designed to be extensible and
allow for other implementations.

The Configuration API can be found in the org.bukkit.configuration and
org.bukkit.configuration.file packages. Plugins that were created before
version 1.1-R5 may have used an older and different implmention that resided
in org.bukkit.util.configuration. These implementations are not compatible and
the old package has since been removed.

This introduction assumes that you have some knowledge about proper object
oriented design, Java, and the core design of Bukkit plugins. This page is not
a substitute for the JavaDocs for the [FileConfiguration Class](http://jd.bukk
it.org/apidocs/index.html?org/bukkit/configuration/file/FileConfiguration.html
)

## Contents

  * 1 Basic Topics
    * 1.1 The Configuration Object
    * 1.2 Keys
    * 1.3 Paths
    * 1.4 Default Values
      * 1.4.1 Creating a copy of config.yml
    * 1.5 Getting Values
      * 1.5.1 HashMaps
    * 1.6 Setting Values
      * 1.6.1 HashMaps
    * 1.7 Saving the File
    * 1.8 Reloading from Disk
  * 2 Advanced Topics
    * 2.1 Options
      * 2.1.1 CopyDefaults
      * 2.1.2 PathSeperator
      * 2.1.3 Header
      * 2.1.4 copyHeader
    * 2.2 Arbitrary Configurations
      * 2.2.1 Mirroring the JavaPlugin implementation
        * 2.2.1.1 Implementation for Reloading
        * 2.2.1.2 Implementation for Getting
        * 2.2.1.3 Implementation for Saving
        * 2.2.1.4 Implementation for Defaults
    * 2.3 Serializing and Deserializing Objects
      * 2.3.1 Aliases
  * 3 Example Use

## Basic Topics

### The Configuration Object

Your plugin extends [JavaPlugin](http://jd.bukkit.org/doxygen/d7/deb/classorg_
1_1bukkit_1_1plugin_1_1java_1_1JavaPlugin.html), and in doing so, you
inherited methods and fields from JavaPlugin. The inherited method, _[getConfi
g()](http://jd.bukkit.org/doxygen/d7/deb/classorg_1_1bukkit_1_1plugin_1_1java_
1_1JavaPlugin.html#a79493f3bc9db2acbf9405c3a33e0acfd)_ returns an object of
type [FileConfiguration](http://jd.bukkit.org/doxygen/dd/d7c/classorg_1_1bukki
t_1_1configuration_1_1file_1_1FileConfiguration.html). This is the object that
represents _config.yml_ inside your plugin's data folder.

The first time _getConfig()_ is invoked on your plugin, _config.yml_ is loaded
from disk, and default values are loaded from the jar. Subsequent invocations
of _getConfig()_ will return the existing _FileConfiguration_ object that is
in memory. Operations performed on this object will not be written to disk
unless explicitly saved. Likewise, any modifications done after the file has
been loaded will not be reflected in the object. If _config.yml_ does not
exist in your data folder, it is equivalent to an empty _config.yml_, and will
load an empty _FileConfiguration_.

**Warning**: if you assign the returned object from _getConfig()_ DO NOT
assign it to a static field  
**Warning**: if you do the above, assign _getConfig()_ to the variable AGAIN
after a reloadConfig
**Note**: it is better to just use _getConfig()_ instead of assigning it to an instance variable 

### Keys

A configuration file is organized into key value pairs where all keys are
Strings. The value for the other keys may be a ConfigurationSection or a
single piece of data. The _getKeys(boolean)_ method returns the set of keys
for the current _FileConfigurationSection_. The boolean value determines if
the returned set is recursive, if true it will return the keys of the given
section and their children keys, if false will only return keys of the given
section. To get the keys of a particular section, the _getKeys(boolean)_
method must be invoked on that particular section. To get the section you will
have to invoke _getConfigurationSection(String)_.

    ![Lightbulb.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**: The getKeys method returns a [Set](http://download.oracle.com/javase/1,5.0/docs/api/java/util/Set.html) of Strings 

### Paths

The Configuration API uses Paths to form a unique key to value pairs. A path
is the set of keys used to associate a value. Each level is separated by the
path separator, which is by default the '.' (period). For example the
following YAML file has the following set of paths.

>

>     key: value

>     one:

>       two: value

>       three:

>         - values

>         - values

>         - values

>       four:

>         five: value

>       *:

>         six: value

>         seven: value

  * key 
  * one 
  * one.two 
  * one.three 
  * one.four 
  * one.four.five 
  * one.* 
  * one.*.six 
  * one.*.seven 

### Default Values

A default _config.yml_ should be provided in your jar for users. In the event
that a config.yml is missing or incomplete, values will be loaded from
included _config.yml_. The provided file must be named _config.yml_ and be
placed in the same directory as your [plugin.yml](/Plugin_YAML). The file
should have the intended structure of your _config.yml_. This file can be
copied as is into the datafolder by invoking saveDefaultConfig() on the
Appropriate instance of JavaPlugin.

>

>     this.saveDefaultConfig()

If dynamic key-value pairs are required as default values, they can added as
defaults to the configuration with invocations of _addDefault(String, Object)_
and _addDefaults(Map<String,Object>)_ methods.

In certain cases if you wish to append new key-value pairs to an existing
config.yml you can set the copyDefaults to true for the ConfigurationOptions
object.

>

>     this.getConfig().options().copyDefaults(true)

#### Creating a copy of config.yml

You can create a copy of config.yml from the jar into the plugin's data folder
by invoking JavaPlugin's saveDefaultConfig() method. saveDefaultConfig() will
not overwrite an existing file.

### Getting Values

Reading values from the configuration involves invoking one of the many getter
methods. A complete list of getters can be found [here](http://jd.bukkit.org/d
oxygen/dd/d7c/classorg_1_1bukkit_1_1configuration_1_1file_1_1FileConfiguration
.html). Every getter method takes a configuration path detailed above. Some of
the commonly used getter methods are as follows

  * getBoolean(String) 
  * getInt(String) 
  * getString(String) 
  * getList(String) 
  * getStringList(String) 

#### HashMaps

In the case of HashMaps as a value, they are treated differently than other
forms of data. There is a restriction for Map types. It must use a String as a
key, and the value but be either a boxed primitive, String, List, Map, or a
ConfigurationSerializable type. They will lose their type.

To get a _HashMap_, a _ConfigurationSection_ must must first be retrieved. You
can return the configuration with getConfigurationSection method. The
getValues method will return the values in the ConfigurationSection as a map,
it takes a boolean which controls if the nested maps will be returned in the
map. You can obtain the original map by invoking getValues(false) on the
returned ConfigurationSection. Due to the way Java handles generic classes,
type information will be lost, thus a cast will need to be performed to set
the original type information. The API makes no guarantees that the cast you
perform will be safe.

>

>     this.getConfig().getConfigurationSection("path.to.map").getValues(false)

### Setting Values

Writing values involves invoking the _set(String, Object)_ method on an
instance of Configuration. Unlike the different get methods that
_FileConfiguration_ has, there is only one set method. Not all objects can be
set, only primitive types, _String_, _Lists_, and types that implement
_ConfigurationSerializable_, such as _Vector_ and _ItemStack_, can be set. To
erase a value supply null as a parameter. All changes made by set will only
affect the copy of the configuration in memory, and will not persist beyond
restarting the server until the configuration is saved. Following are some
example uses:

>

>     // setting a boolean value

>     this.getConfig().set("path.to.boolean", true);

>

>     // setting a String

>     String stringValue = "Hello World!";

>     this.getConfig().set("path.to.string", stringValue);

>

>     // setting an int value

>     int integerValue = 8;

>     this.getConfig().set("path.to.integer", integerValue);

>

>     // Setting a List of Strings

>     // The List of Strings is first defined in this array

>     List<String> listOfStrings = Arrays.asList("Hello World", "Welcome to
Bukkit", "Have a Good Day!");

>     this.getConfig().set("path.to.list", listOfStrings);

>

>     // Setting a vector

>     // event is assumed to be an existing event inside an "onEvent" method.

>     Vector vector = event.getPlayer().getLocation().toVector();

>     this.getConfig().set("path.to.vector", vector);

>

>     // Erasing a value

>     this.getConfig().set("path.to.value", null);

  

#### HashMaps

When HashMaps are used as a value, they are treated slightly differently. The
Map must parameterized with a String type for the key, and the value must be
parameterized as a boxed primitive, String, List, Map, or a
ConfigurationSerializable.

While you can use the set method to directly set a HashMap to a key, you
cannot directly retrieve the Map back with the get method after reading
directly from disk. The context above is to minimize unpredictability.

To set a _HashMap_, a _ConfigurationSection_ must be created for that HashMap.
You can only set HashMap where the key is a string the the value is something
that is ConfigurationSerializable. The createSectionMethod

>

>     this.getConfig().createSection(String path, Map< String, Object > map)

### Saving the File

If make any changes to the_FileConfiguration_ with set methods, or mutate any
_Lists_, you will need to save the changes to disk if you wish to keep these
changes after the plugin is disabled. To save the file to disk invoke the
saveConfig method for your plugin, it will overwrite the file already there.

>

>     this.saveConfig();

### Reloading from Disk

If you suspect that users have made changes to the _config.yml_ in the data
folder, those changes are not reflected in memory. Invoke the _reloadConfig()_
method of your plugin to load from the disk again. It will destroy all changes
in memory.

>

>     this.reloadConfig();

## Advanced Topics

The following are some more advanced topics, meant for more advanced plugins.
If you only require the default _config.yml_, creating custom methods for
reading, and saving, you will not need to go this far.

### Options

Every _FileConfiguration_ instance is associated with a [FileConfigurationOpti
ons](http://jd.bukkit.org/apidocs/index.html?org/bukkit/configuration/file/Fil
eConfigurationOptions.html) object. The _FileConfigurationOptions_ object
controls the behavior of the _FileConfiguration_ it is associated with.
_FileConfiguration'_s _options()_ method returns the
_FileConfigurationOption's_ responsible for it. With it you can check and set
each option. There are currently four options. Be aware that the methods are
overloaded, for example _copyDefaults()_ which returns a boolean and
_copyDefaults(boolean)_ which returns it self, but has a side effect which
changes the state.

#### CopyDefaults

The _copyDefaults_ option changes the behavior of Configuration's save method.
By default, the defaults of the configuration will not be written to the
target save file. If set to true, it will write out the default values, to the
target file. However, once written, you will not be able to tell the
difference between a default and a value from the configuration.

#### PathSeperator

PathSeperator changes the character that is used to separate the different
levels of the configuration. By default it is the "." (period) but it can be
changed to any char.

#### Header

Header is the comment block at the top of a YAML file, it is applied to the
save output. The header is the only comment that Configuration API knows how
to copy.

#### copyHeader

If _copyHeader()_ returns true then the header will be copied on save, from
the default source.

### Arbitrary Configurations

If you require additional YAML files, for storing configuration information or
persisting additional game information you will need to write your own methods
for accessing the additional configuration files. Modeled after JavaPlugin
getConfig, reloadConfig, saveConfig methods, the following is an example how
to write your own methods to read and save to custom configuration files.
Since these config files belong to your plugin, you can put this method in
your main class so that you can have the same access as you have with
config.yml. You will have to write a set of these methods for each YAML file.
The advantage here, is that you can use each set in the same manner as the
provided methods for the default config.yml. Alternately, adding additional
methods can keep the method count lower and allow access to multiple files.

#### Mirroring the JavaPlugin implementation

JavaPlugin implements methods for config.yml. A plugin needs to implement its
own methods to access configuration files unique to the plugin. After
implementing the methods for the plugin, they can be invoked in the same
context as the inherited _getConfig()_, _reloadConfig()_, _saveConfig()_, and
"saveDefaultConfig()" methods from JavaPlugin. The following can be made into
a single class which allows access to any yaml file. Such a class can be found
[here](https://gist.github.com/3174347)

First you will need to declare two fields and initialize them to null for each
of the custom configuration files. One to hold the _FileConfiguration_ object
and one to hold the _File_ object. The File object represents the file on the
disk, and the FileConfiguration represents the contents of the configuration.

>

>     private FileConfiguration customConfig = null;

>     private File customConfigFile = null;

##### Implementation for Reloading

Then, write the method that is responsible for loading the config from disk.
It will load the file, and search the jar for a default customConfig.yml.

>

>     public void reloadCustomConfig() {

>         if (customConfigFile == null) {

>         customConfigFile = new File(getDataFolder(), "customConfig.yml");

>         }

>         customConfig =
YamlConfiguration.loadConfiguration(customConfigFile);

>

>         // Look for defaults in the jar

>         Reader defConfigStream = new
InputStreamReader(this.getResource("customConfig.yml"), "UTF8");

>         if (defConfigStream != null) {

>             YamlConfiguration defConfig =
YamlConfiguration.loadConfiguration(defConfigStream);

>             customConfig.setDefaults(defConfig);

>         }

>     }

##### Implementation for Getting

Next, you need to write the getter method. Check if _customConfig_ is null, if
it is load from disk.

>

>     public FileConfiguration getCustomConfig() {

>         if (customConfig == null) {

>             reloadCustomConfig();

>         }

>         return customConfig;

>     }

##### Implementation for Saving

Finally, write the save method, which saves changes and overwrites the file on
disk.

>

>     public void saveCustomConfig() {

>         if (customConfig == null || customConfigFile == null) {

>             return;

>         }

>         try {

>             getCustomConfig().save(customConfigFile);

>         } catch (IOException ex) {

>             getLogger().log(Level.SEVERE, "Could not save config to " +
customConfigFile, ex);

>         }

>     }

##### Implementation for Defaults

Optionally, you may want to write a method that mimics JavaPlugin's
saveDefaultConfig() method.

>

>     public void saveDefaultConfig() {

>         if (customConfigFile == null) {

>             customConfigFile = new File(getDataFolder(),
"customConfig.yml");

>         }

>         if (!customConfigFile.exists()) {  
>              plugin.saveResource("customConfig.yml", false);

>          }

>     }

### Serializing and Deserializing Objects

The Configuration API, as mentioned above can store Java objects that
implement the _ConfigurationSerializable_ Interface. Object serialization
facilitates easy saving and loading so plugin authors can focus on other parts
of their plugin. It greatly simplifies tasks such as storing a _[Location](htt
p://jd.bukkit.org/doxygen/da/dac/classorg_1_1bukkit_1_1Location.html)_ in
YAML, a developer can serialize a wrapper class, which provide methods to
retrieve a _Location_.  

Classes, in addition to implementing the _ConfigurationSerializable_ interface
must also implment one of the following as noted in the Javadoc, so that they
can be serialized by the API:

  * A constructor that accepts a single _Map_. 
  * A static method "deserialize" that accepts a single _Map_ and returns the class. 
  * A static method "valueOf" that accepts a single Map and returns the class. 

In order for a serialized object to be deserialized, it must also be
registered with ConfigurationSerialization. The static registerClass method
must be invoked once per class that has been serialized.

This statement must be placed in your onEnable method or some other location
that gets called every time your plugin is initialized:

>

>     ConfigurationSerialization.registerClass(Class<? extends
ConfigurationSerializable>)

**Warning**: Do not use a static block to execute the above; if you do so, it
will not be called a second time when `/reload` is used and you will encounter
errors due to it not being registered!

#### Aliases

When classes are serialized they are marked with their fully qualified name.

You can provide an alias to your class so that it does not serialize with the
fully qualified name of your class, but the alias instead. You provide the
alias with the _SerializableAs_ annotation to the class implementing
_ConfigurationSerializable_.

    
    
    @SerializableAs(String)

When registering a class with an alias, the alias must be provided on
registration.

>

>     ConfigurationSerialization.registerClass(Class<? extends
ConfigurationSerializable>, String)

## Example Use

Below is the an example plugin that uses the new Configuration API to be
display messages as an MOTD as players join, and for the player to retrieve
the rules on command. It does not follow proper style and plugin layout to
keep the number of lines to a minimum.

>

>     import java.util.*;

>     import org.bukkit.command.*;

>     import org.bukkit.event.*;

>     import org.bukkit.plugin.java.JavaPlugin;

>     import org.bukkit.configuration.file.FileConfiguration;

>

>

>     public class SimpleMOTD extends JavaPlugin {

>

>         @Override

>         public void onEnable() {

>             // Save a copy of the default config.yml if one is not there

>             this.saveDefaultConfig();

>

>             // Register a new listener

>             getServer().getPluginManager().registerEvents(new Listener() {

>

>                 @EventHandler

>                 public void playerJoin(PlayerJoinEvent event) {

>                     // On player join send them the message from config.yml

>                     event.getPlayer().sendMessage(SimpleMOTD.this.getConfig(
).getString("message"));

>                 }

>             }, this);

>

>             // Set the command executor for the rules command

>             this.getCommand("rules").setExecutor(new CommandExecutor() {

>

>                 public boolean onCommand(CommandSender sender, Command
command, String label, String[] args) {

>                     // On command send the rules from config.yml to the
sender of the command

>                     List<String> rules =
SimpleMOTD.this.getConfig().getStringList("rules");

>                     for (String s : rules)

>                         sender.sendMessage(s);

>                     }

>                     return true;

>                 }

>             });

>         }

>     }

The default config.yml that is in the plugin's jar

    
    
    # default config.yml
    message: Hello World and Welcome! :)
    rules:
      - Play Nice
      - Respect others
      - Have Fun
