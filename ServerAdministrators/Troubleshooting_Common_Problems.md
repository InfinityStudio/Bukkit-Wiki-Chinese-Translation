# 常见问题与解决方案

在这一篇章中我们罗列了很多在服务器运行过程中出现的错误及其解决方案。这些错误基本上包含了所有你在运营服务器中可能遇到的错误，而且解决方案已经被测试过可行。如果你已经阅读完整篇文章但是你的问题并不在这些问题之内，那么你可能是遇到了插件的问题。无论如何，先读完这篇文章之后再向论坛发起提问。


## 目录

  * 1 判断插件问题
  * 2 救命！相同名字的玩家已经登陆！
  * 3 救命！没有人能建造！
  * 4 只有OP才能放置/破坏出生点周围的方块.
  * 5 朋友无法连接？
  * 6 朋友以前可以连接但是现在不行了！
  * 7 我怎么才能找到自己服务器的IP?
    * 7.1 如何找到服务器的本地IP地址？（Windows适用）
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

最小系统法（译注：原文为隔离插件法）在应对大部分插件问题的时候都非常的有效。

  1. 移除所有的插件 - 你可以直接将插件文件夹重命名为其他的名字比如将＂plugin＂命名为＂plugins_test＂。
  2. 启动服务器检查问题是否已经解决．如果问题依然存在，请重新生成你的地图．如果生成地图都无法解决的话，请继续往下阅读其他的解决方案，最终你可能需要将你的问题在线提交至Bukkit帮助版块。

  3. 假如重命名插件文件夹后没有再出现问题，将一个最为重要的插件放入plugin（比如权限控制插件）然后重启服务器。
  4. 重复上一步知道原先的问题重新出现．
  5. 当问题出现的时候，你刚刚放入文件夹的插件就是罪魁祸首。仔细阅读这个插件的说明文档，如果无法解决的话再联系插件作者汇报你的问题。

#### 救命！相同名字的玩家已经登陆！

用文本编辑器打开_server.properties_找到下面这一行：

	online-mode=false
	
将_false_值设置为_true_。如果值是false的话说明你的服务器运行于离线模式下。虽然玩家不需要正版就可以游戏，但是同样会使你的服务器暴露在攻击的风险下。最好的办法就是将_false_设置为_true_，这样的话玩家必须是正版才能进入游戏，同样你的服务器被攻击的风险被大为降低。

#### 救命！没有人能建造！

有很多的原因可能导致这个问题。

  1. 你距离出生点太近了 
    * 在默认情况下，不是OP的话是不能够在距离出生点半径16格以内建造的。走出出生点16格以外再试试看。 
    * 如果你发现走出16格就可以建造了，而且你还想把这个出生点保护的功能关掉的话，用文本编辑器打开_server.properties_找到下面这一行：
	
	spawn-protection=16
	
    将值设置为0即可。

  2. 你建造/破坏的行为被插件阻止了 
    * 首先你得确定是不是插件导致的这个问题，请阅读第一节_判断插件问题_。
    * 在判断是插件导致的问题之后，请详细阅读这个插件的文档，确保所有的权限已经被正确的设置。
    * 通常可能会阻止建造的插件包括（但不限于）：反作弊插件，权限插件，通用插件（比如：Essentials），或者其他地图相关插件（比如：WorldBorder和Multiverse）

#### 只有OP才能放置/破坏出生点周围的方块.

这说明出生点保护功能启动了。用文本编辑器打开_server.properties_找到下面这一行：
	
	spawn-protection=16
	
    将值设置为0即可。
    
#### 朋友无法连接？

请通过<http://canyouseeme.org/>来检测端口是不是正常的开放。如果没有开放的话，你需要检测你的端口是不是被防火墙阻挡了（也许是路由器的防火墙也许是服务器的防火墙）。除此之外请确保在_server.properties_中下面这一项的值是否是空：

	server-ip=
	
不是的话请将其留空。

如果玩家通过域名进行连接的话，你需要测试你的DNS情况。请使用ping指令测试域名（假设你的域名是yourserver.com）：
	
	ping yourserver.com
	
如果无法联通说明你的域名DNS出现了问题，请联系你的域名提供商。

#### 朋友以前可以连接但是现在不行了！

也许你的服务器IP地址被改动了。如果你是Unix/Linux系统请在终端输入‘ifconfig’，同理如果是windows系统请在命令提示符中输入‘ipconfig’来确认服务器的IP地址。如果你发现你的服务器ip地址是以192.168.*开头或者10.*开头，那么你可能需要登陆路由器来查找你的IP地址，通常情况下你可以找到你的端口对应的IP地址映射，请确保路由器的某个端口映射至服务器的IP地址（译注：简单方法直接百度IP即可得知自己的IP地址，上面都是废话）。还有请务必确保你_server.properties_文件中_server-ip_一项的值为空。

使用ping来测试你的域名连通性，如果如果无法连通请联系你的域名提供商。

#### 我怎么才能找到自己服务器的IP?

通过[www.whatsmyip.org](http://www.whatsmyip.org/)可以查看你的计算机的外网IP地址，内网IP地址可以通过‘ifconfig’（UNIX/LINUX）或者‘ipconfig’（Windows）来查看。同样_server.properties_中的_server-ip_一项必须为空。

##### 如何找到自己的IP？（适用于Windows用户）

关于如何找到自己的IP地址。请参考下面的文章：
<http://www.groovypost.com/howto/microsoft/windows-7/find-your-local-
ip-address-windows-7-cmd/> （只需参阅1章和2章）（Vista同样有效），按下Win键的同时按下R键，然后输入“cmd.exe”。接下来参考第二步。

#### 如何找到用于生成地图的种子？

你可以在server.properties文件中看到这一项：

	level-seed=

如果你希望更换地图种子，只需更改这个值后移动/重命名/删除以前的地图文件并重新生成地图即可。

#### 我总是因为飞行而被踢出游戏

打开你的server.properties文件并确保allow-flight的值如下面所示。

	allow-flight=true

#### 权限控制不工作或者报错

这极有可能是因为权限插件使用的YAML文件中不正确的语法导致的。你可以在这里找到一个很好用的纠错工具。将你的config粘贴至左边的窗口，右边的窗口会告诉你错误的位置。请记住，YAML必须使用冒号而且请不要使用TAB回格。

如果这么做无法解决问题，说明问题应该在插件或者其他原因。

#### 控制台报出了一个错误，这到底是怎么回事？

当你发现控制台报出了一个错误，你可以轻易的通过错误的内容判断是插件的错误还是Bukkit的错误。如果是插件的错误，你应当联系插件的开发者。

一个Bukkit错误的例子：
    
	10:02:47 \[SEVERE\] java.lang.NullPointerException
	at net.minecraft.server.PlayerManager.flush(PlayerManager.java:34)
    
你可以看到第二行明显的写出了 \[SEVERE\] java.lang.NullPointerException at net.minecraft.server....这意味着这个问题是由于服务器软件引起的（也就是Bukkit）。

一个插件错误的例子
    
	2011-11-24 16:28:42 [SEVERE] Could not pass event PLAYER_JOIN to Spout
	java.lang.NoSuchFieldError: k
	at org.getspout.spout.SpoutNetServerHandler.sendPacket(SpoutNetServerHandler.java:470)
    

你可以看到这里写着org.getspout.spout。你可以告诉开发者这个错误的细节来修复这个错误。（PS：你看到的只是一个例子，事实上它个可能是各种各样的比如me.dadaemon.MyOwnProPlugin）

#### 在服务器游戏时玩家客户端出现了崩溃

这可能是你客户端的问题，也有可能是你尝试登陆的服务器有问题。通过登陆其他的正常服务器来判断到底是哪个问题。

其他可能导致这个问题的原因是客户端安装了一些有问题的mod或者minecraft的文件损坏了。

在客户端登陆之前打开“options”点击“force redownload”。当你登陆的时候，所有的文件都将会重新下载。

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
