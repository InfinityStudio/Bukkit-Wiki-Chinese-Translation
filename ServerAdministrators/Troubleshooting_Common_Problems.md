# 常见问题与解决方案

在这一篇章中我们罗列了很多在服务器运行过程中出现的错误及其解决方案。这些错误基本上包含了所有你在运营服务器中可能遇到的错误，而且解决方案已经被测试过可行。如果你已经阅读完整篇文章但是你的问题并不在这些问题之内，那么你可能是遇到了插件的问题。无论如何，先读完这篇文章之后再向论坛发起提问。

It is **UP TO YOU** to do your due diligence when searching for help.

## 目录

  * 1 判断插件问题
  * 2 救命！相同名字的玩家已经登陆！
  * 3 救命！没有人能建造！
  * 4 只有OP才能破坏出生点周围的方块.
  * 5 朋友无法连接？
  * 6 朋友以前可以连接但是现在不行了！
  * 7 我怎么才能找到自己服务器的IP?
    * 7.1 如何找到自己的IP地址？（Windows适用）
  * 8 如何更换地图种子？
  * 9 我经常因为飞行被踢出游戏．
  * 10 权限控制不工作或者工作不正常．
  * 11 控制台显示了错误信息，这是什么问题？
  * 12 在服务器游戏时玩家客户端出现了崩溃．
  * 13 当使用hamachi的时候玩家无法连接游戏．
  * 14 服务器延迟严重，我该怎么办？
  * 15 其他常见问题
    * 15.1 java.lang.NoClassDefFoundError: Could not initialize class org.fusesource.jansi.internal.kernel32
    * 15.2 [SEVERE] java.io.IOException: Not in GZIP format
    * 15.3 [SEVERE] Chunk (x, y) stored at (x, y) in world '<world name>'
    * 15.4 [WARNING] **** FAILED TO BIND TO PORT!
      * 15.4.1 在使用某些端口的时候报错（Windows适用）
    * 15.5 Error: Unable to access jarfile craftbukkit.jar
      * 15.5.1 当我下载完水桶服务端尝试开服的时候，我的服务端在报了一些file or directory not found错误之后马上关闭了．
      * 15.5.2 The system cannot find path specified
    * 15.6 NoSuchMethodError or ClassNotFoundException in error message
    * 15.7 Outdated Server
    * 15.8 ConcurrentModificationException
    * 15.9 [SEVERE] java.net.SocketException: Socket Closed
    * 15.10 [SEVERE] java.lang.UnsupportedClassVersionError: Unsupported major.minor version 51.0
    * 15.11 [SEVERE] java.lang.UnsupportedClassVersionError: Unsupported major.minor version 52.0
    * 15.12 endOfStream while joining a server
    * 15.13 java.lang.NullPointerException at java.io.Reader.<init>

#### 判断插件问题

* * *

最小系统法（译注：原文为隔离插件法）在应对大部分插件问题的时候都非常的有效．

  1. 移除所有的插件 - 你可以直接将插件文件夹重命名为其他的名字比如将＂plugin＂命名为＂plugins_test＂
  2. 启动服务器检查问题是否已经解决．如果问题依然存在，请重新生成你的地图．如果生成地图都无法解决的话，请继续往下阅读其他的解决方案，最终你可能需要将你的问题在线提交至Bukkit帮助版块．

  3. 假如重命名插件文件夹后没有再出现问题，将一个最为重要的插件放入plugin（比如权限控制插件）然后重启服务器．
  4. 重复上一步知道原先的问题重新出现．
  5. 当问题出现的时候，你刚刚放入文件夹的插件就是罪魁祸首．仔细阅读这个插件的说明文档，如果无法解决的话再联系插件作者汇报你的问题．

#### Help, Someone has logged in as me!

* * *

Open your _server.properties_ file and make sure that this line appears:

    
    
    online-mode=true
    

If this option is set to `false`, your server is running in offline mode, and
will receive no support. There is only one good way to protect your server,
and that is by running online-mode=true.

#### Help, No one can build!

* * *

There are multiple possible causes of this:

  1. You are within spawn. 
    * By default, non-ops cannot build inside the 16 blocks of spawn. To test this, have your players move at least 16 away from the spawn region and try to break/build. 
    * If this is the case, open your _server.properties_ file and set this line to be zero: 
        
                spawn-protection=0

  2. You have a plugin blocking building or breaking blocks 
    * To check if it is a plugin issue, read the section on Diagnosing Plugin Issues
    * Read the documentation of the plugin that is causing the issue, and make sure any permissions requiring building are set. 
    * Plugins that contain anti-build measures include (but are not limited to): Anti-Cheat plugins, Permission plugins, General plugins (ex. Essentials), or World-based plugins (ex. WorldBorder, Multiverse) 

#### Only OP's can place and break blocks near the spawn

* * *

This indicates that spawn protection is active. Open your _server.properties_
file and set this line to be zero:

    
    
    spawn-protection=0

#### Friends are unable to connect?

* * *

Check if your port is open with <http://canyouseeme.org/> If it isn't, you
need to check your firewall (either router, or on the server itself, or both).
Make sure you have your server-ip= (Yes, no IP listed at all in the
server.properties. Leave the part after the = blank).

Test your DNS if you are trying to connect with a name, not IP (ex:
test.server.org, not 123.123.123.123). A simple test is to ping your DNS name
(ex: ping test.server.org). If you do not see a IP address being resolved
(even if it doesn't respond to a ping) you have a DNS problem.

#### Friends are now unable to connect... but could X time ago!

* * *

Your local IP address may have changed. Check that by running `ipconfig` for
Windows or `ifconfig` for Unix based systems in a command line. You can also
find your network settings and located your IPv4 address. On most networks it
will start with 192.168.* or 10.* You can also (on any platform) log in to
your router's interface and find the DHCP section or clients table. You should
be able to find your computer in that table, and also your IP. If it's
different from the one your port is already forwarded to, change it. Make sure
you have your server-ip= blank (in server.properties).

Alternatively, your external IP may have changed. Simply go to
[www.whatsmyip.org](http://www.whatsmyip.org/) or again to your router's
interface and give your friends the new one. To avoid this from ever
happening, [www.dyndns.com](http://dyn.com/dns/) offers free hostnames and a
client you can install on your computer which will always keep the name
pointing to you.

Test your DNS if you are trying to connect with a name, not IP (ex:
test.server.org, not 123.123.123.123). A simple test is to ping your DNS name
(ex: ping test.server.org). If you do not see a IP address being resolved
(even if it doesn't respond to a ping) you have a DNS problem.

#### How do I find my server IP?

* * *

You can find the internet facing IP address of your computer by visiting this
site: [www.whatsmyip.org](http://www.whatsmyip.org/) You can find the local IP
address of your computer by running the command: ipconfig (Windows) or
ifconfig (Unix based systems) You still want to keep the server-ip setting in
your server.properties blank, however.

##### How to find your local IP (windows only)

To find your local IP, check this informative
article:<http://www.groovypost.com/howto/microsoft/windows-7/find-your-local-
ip-address-windows-7-cmd/> (steps 1&2 only) (Also works on vista) For XP,
press the windows flag key and "r" at the same time, then type "cmd.exe" in
the window. Then do step 2.

#### How do I change the map seed?

* * *

There is an option in your server.properties file:

    
    
    level-seed=

Just change that as you would when creating a single player world, and
move/rename/delete the current world to generate a new one.

#### I keep getting kicked for flying.

* * *

Open up your server.properties and make sure allow-flight is set to true.
allow-flight=true

#### Permissions doesn't work and/or returns errors

* * *

This is most likely caused by incorrect syntax in the YAML data files
permissions plugins use. A good diagnostic parser can be found here. Paste
your config file into the left box, and the right box will tell you where the
errors can be found. Remember, YAML entries must have a colon ":" and lines
must never have tabs.

If this doesn't fix your problem, it may be a bug with the plugin or some
other problem preventing your permissions plugin from working correctly.

#### I get an error on the console! What's the problem?

* * *

When you get an error in the console you can easily check if it's an Bukkit
error or a plugin is giving errors. If an plugin gives an error you should
contact the plugin developer.

Example Bukkit error

    
    
    10:02:47 [SEVERE] java.lang.NullPointerException
    at net.minecraft.server.PlayerManager.flush(PlayerManager.java:34)
    

You can see this because the second line says [SEVERE] at
net.minecraft.server... This means there is an error in net.minecraft.server
and that's the server software (aka Bukkit.)

Example Plugin Error

    
    
    2011-11-24 16:28:42 [SEVERE] Could not pass event PLAYER_JOIN to Spout
    java.lang.NoSuchFieldError: k
    at org.getspout.spout.SpoutNetServerHandler.sendPacket(SpoutNetServerHandler.java:470)
    

Here you can see that the error is in org.getspout.spout. You should get help
from the Spout developer for a fix. (PS: This is an example. It could also say
me.dadaemon.MyOwnProPlugin.)

#### Client crashes when something happens on a server.

* * *

This could either be a problem with your client, or the server you are trying
to connect to is broken in some way. Try and verify that this problem does
indeed occur on other servers.

Another cause of this problem is that you may have installed some client mod
that is messing with the game, or minecraft has become corrupted somehow.

To un-corrupt/redownload, open minecraft, and before logging in, click
"options" then click "force redownload". When you log in, it will redownload
minecraft.

#### People cannot join hamachi-based server

* * *

Verify that the users have the hamachi software. They will need hamachi to
connect. If you are unable to join using the address given, try running the
server without hamachi, and connect with your local ip. (See how to find your
local IP below) If it works with your local ip, try to port forward. Visit
<http://portforward.com/> if you don't know how.

#### I am getting Lag! What can I do?

* * *

Common Symptom: [Warning] Can't keep up! Did the system time change or is the
server overloaded?

There are multiple ways to tackle this problem. You WILL have to spend time
searching and troubleshooting, so do not look for an easy fix.

Most lag issues are caused by plugins. Try removing them one by one until you
find the culprit.

You can also use a program to check your worlds for problems. Chunkster and
Minecraft Region Fixer are both good tools to use.

Alternatively, use a Java profiler. Here is a good tutorial on a free Java
profiler called VisualVM: <http://forums.bukkit.org/threads/wip-analysis-of-
your-server-jvm-using-visualvm.66536/>

### Common Errors

* * *

#### java.lang.NoClassDefFoundError: Could not initialize class
org.fusesource.jansi.internal.kernel32

Full error:

    
    
    java.lang.NoClassDefFoundError: Could not initialize class org.fusesource.jansi.internal.kernel32
    at org.fusesource.jansi.internal.WindowsSupport.getConsoleMode<WindowsSupport.java:50
    at jline.WindowsTerminal.getConsoleMode<WindowsTerminal.java:176>
    at jline.WindowsTerminal.init<WindowsTerminal.java"80>
    at jline.TerminalFactory.create<Terminalfactory.java:93>
    at jline.TerminalFactory.get<TerminalFactory.java:151>
    at jline.console.ConsoleReader.<init><ConsoleReader.java:140>
    at jline.console.ConsoleReader.<init><ConsoleReader.java::126
    at net .minecraft.server.MinecraftServer.<init><MinecraftServer.java:94>
    at net.minecraft.server.MinecraftServer.main<MinecraftServer.java:624>
    at org.bukkit.craftbukkit.Main.main<Main:136>
    Press any key to continue . . .
    

This error is caused by you not having Visual C++ 2008 Redistributable
installed, or having the wrong version installed that matches your Java
version.

The version of Visual C++ 2008 Redistributable (x64 or x86) must match the
version of Java you are using. If you are using Java x86 and have Visual C++
2008 Redistributable x64 installed, it will not work. You must either use Java
x64, or install Visual C++ 2008 Redistributable x86.

Alternatively, add in the -nojline option which turns off jline.

#### [SEVERE] java.io.IOException: Not in GZIP format

[spoiler=solution] Your world may be corrupt. Try removing all plugins first.
If you still get this error, try running your worlds through MCEdit. If that
fails, restore from backups. [Here](http://forums.bukkit.org/threads/how-to-
fix-your-world-errors-corrupt-chunks.54254/) is a tutorial for fixing worlds,
give it a try.

#### [SEVERE] Chunk (x, y) stored at (x, y) in world '<world name>'

[spoiler=solution] You have another form of world corruption. Try using
chunkster or MCEdit. If that fails, restore from backups. Try this tutorial
for fixing worlds.

#### [WARNING] **** FAILED TO BIND TO PORT!

![](http://hydra-media.cursecdn.com/wiki.bukkit.org/thumb/f/fa/Netstat.png
/450px-Netstat.png?version=059e893514b5933c576d6519d0b310fb)

![](/skins/common/images/magnify-clip.png)

netstat -o -n -a output

Stop your minecraft server and make sure you have no instances running. Make
sure you have your server-ip= blank (in server.properties). If that fails,
reboot.

##### Finding programs using the same port (Windows)

To check what program could be using it, go to CMD and type

    
    
    netstat -o -n -a | findstr 0.0:<Port Number>
    
    
    
     
    WINDOW SUCKS!
    Eg: netstat -o -n -a | findstr 0.0:25565
    

If something shows up (Eg: TCP 0.0.0.0:25565 0.0.0.0:0 LISTENING 2984), go to
Task Manager > Services and look for the number(2984) under the PID column,
that will tell you the program.

From there you can remove that program or change the port for that program.

#### Error: Unable to access jarfile craftbukkit.jar

##### After downloading the new CB, my server closes immediately after
opening and says file or directory not found

Not all versions of CraftBukkit are named exactly CraftBukkit.jar. You
probably entered that name when making the startup script and may not even
remember.

Either edit your startup script to match the new name of the CB Jarfile, or
just rename the CB Jarfile to craftbukkit.jar.

Beware if you are using Windows. Windows will hide the file extension by
default, so try renaming the file to just: craftbukkit

Alternatively, unhide file extensions.

##### The system cannot find path specified

This is normally fixed by changing the location of where the CraftBukkit jar
is in the bat file

Most craftbukkit files come as craftbukkit-<version>-R<revesion>.jar. This
file name HAS to be the same as the one in the startup file unless you changed
otherwise. Examples of startup files (With Bukkit jar named as
'craftbukkit.jar')  
Note: If the term "java" is already predefined, you could use it instead of
the whole directory

  

    
    
    @Echo off
    "C:\Program Files (x86)\Java\jre6\bin\java.exe" -Xms1024M -Xmx1024M -jar craftbukkit.jar
    pause
    

So, if you are running Java6 (32 bit) on a 64bit machine it would look like
this (with default jar location)

x86(32 Bit)

    
    
    @Echo off
    "C:\Program Files (x86)\Java\jre6\bin\java.exe" -Xms1024M -Xmx1024M -jar craftbukkit-1.2.5-R4.jar
    pause
    

x64(64 Bit)

    
    
    @Echo off
    "C:\Program Files\Java\jre6\bin\java.exe" -Xms1024M -Xmx1024M -jar craftbukkit-1.2.5-R4.jar
    pause
    

#### NoSuchMethodError or ClassNotFoundException in error message

If you are seeing any of these phrases in your error, something new is most
likely conflicting with something old. Search the error for a plugin name, if
found, update the plugin in the error. If not found, update Java.

#### Outdated Server

The client version of Minecraft you are using is newer than the server version
of Minecraft you are connecting to. Downgrade your client, or try connecting
to the server once they have updated.

#### ConcurrentModificationException

This fatal exception is caused in CraftBukkit by a poorly written plugin. Try
removing any of your recently added plugins first. If you still get this
error, try removing all of your plugins and adding them back in one by one
until the problem comes back. Updating the plugin to a newer version may help.

#### [SEVERE] java.net.SocketException: Socket Closed

Example Error:

    
    
    2011-11-30 00:39:34 [SEVERE] java.net.SocketException: Socket closed
    2011-11-30 00:39:34 [INFO] Connection reset
    2011-11-30 00:39:34 [SEVERE]    at java.net.SocketOutputStream.socketWrite(Unknown Source)
    2011-11-30 00:39:34 [SEVERE]    at java.net.SocketOutputStream.write(Unknown Source)
    2011-11-30 00:39:34 [SEVERE]    at java.io.BufferedOutputStream.flushBuffer(Unknown Source)
    2011-11-30 00:39:34 [SEVERE]    at java.io.BufferedOutputStream.flush(Unknown Source)
    2011-11-30 00:39:34 [SEVERE]    at java.io.DataOutputStream.flush(Unknown Source)
    2011-11-30 00:39:34 [SEVERE]    at net.minecraft.server.NetworkWriterThread.run(SourceFile:104)[/CODE]
    

This error is harmless, it occurs when someone disconnects using the 'x'
button instead of disconnecting and then quitting minecraft.

#### [SEVERE] java.lang.UnsupportedClassVersionError: Unsupported
major.minor version 51.0

This means your java version (java6) is out of date, and a plugin you are
using uses a newer java version (java7) than you have installed. Please
install either java7 or java8. (Preferably sun/oracle version)

#### [SEVERE] java.lang.UnsupportedClassVersionError: Unsupported
major.minor version 52.0

This means your java version (java6 or java7) is out of date, and a plugin you
are using uses a newer java version (java8) than you have installed. Please
install java8. (Preferably sun/oracle version)

#### endOfStream while joining a server

endOfStream is a network error in java that occurs when either the client or
server hang up on each other. It is typically a problem with the server. A
common solution is to simply restart the server.

Restarting periodically may also be a good idea, and there are plugins that do
just that. Note: restarting is NOT the same as reloading. Reloading often
glitches, especially with the new beta builds.

#### java.lang.NullPointerException at java.io.Reader.<init>

Full Error:

    
    
    java.lang.NullPointerException
    at java.io.Reader.<init>(Unknown Source)
    at java.io.InputStreamReader.<init>(Unknown Source)
    at net.minecraft.server.v1_6_R1.AchievementMap.<init>(SourceFile:15)
    at net.minecraft.server.v1_6_R1.AchievementMap.<clinit>(SourceFile:9)
    at net.minecraft.server.v1_6_R1.Statistic.g(SourceFile:37)
    at net.minecraft.server.v1_6_R1.CounterStatistic.g(SourceFile:15)
    at net.minecraft.server.v1_6_R1.StatisticList.<clinit>(SourceFile:27)
    at net.minecraft.server.v1_6_R1.MinecraftServer.main(MinecraftServer.jav
    a:611)
    at org.bukkit.craftbukkit.Main.main(Main.java:152)
    java.lang.ExceptionInInitializerError
    at net.minecraft.server.v1_6_R1.LocaleI18n.<clinit>(SourceFile:7)
    at net.minecraft.server.v1_6_R1.Item.v(SourceFile:495)
    at net.minecraft.server.v1_6_R1.StatisticList.a(SourceFile:139)
    at net.minecraft.server.v1_6_R1.StatisticList.c(SourceFile:85)
    at net.minecraft.server.v1_6_R1.Item.<clinit>(SourceFile:310)
    at net.minecraft.server.v1_6_R1.Block.<clinit>(Block.java:713)
    at net.minecraft.server.v1_6_R1.StatisticList.a(SourceFile:122)
    at net.minecraft.server.v1_6_R1.StatisticList.<clinit>(SourceFile:55)
    at net.minecraft.server.v1_6_R1.MinecraftServer.main(MinecraftServer.jav
    a:611)
    at org.bukkit.craftbukkit.Main.main(Main.java:152)
    Caused by: java.lang.NullPointerException
    at java.io.Reader.<init>(Unknown Source)
    at java.io.InputStreamReader.<init>(Unknown Source)
    at org.apache.commons.io.IOUtils.readLines(IOUtils.java:986)
    at net.minecraft.server.v1_6_R1.LocaleLanguage.<init>(SourceFile:26)
    at net.minecraft.server.v1_6_R1.LocaleLanguage.<clinit>(SourceFile:19)
    ... 10 more
    

Most likely you have unallowed characters in your server folder path, such as
a '!'. Make sure to use only a-z A-Z 0-9 . - and _ in the full path of your
server folder.
