#  CraftBukkit Command Line Arguments

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

