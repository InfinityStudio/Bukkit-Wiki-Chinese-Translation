# 如何建立一个CraftBukkit服务器

## 目录

  * 1 [预备工作](#预备工作)
  * 2 [Windows系统](#windows系统)
  * 3 [Linux系统](#linux系统)
  * 4 [Mac OS X系统](#mac-os-x系统)
  * 5 [错误诊断](#错误诊断)
  * 6 [相关教程](#相关教程)

## 预备工作

**注意**：在这个教程中我们将使用这个**craftbukkit.jar**文件，文件下载完成后你可以将其命名为其他的名字。不过你的启动脚本**必须**使用你重命名后的文件名。

**注意**：至少你需要有一台**多用户**服务器，你必须明白这到底是什么和其至关重要的原因。此外在server.properties中的**server-ip=**请保持默认值或者留空。

**注意**：当你第一次启动服务器的时候你会看到ERROR字样的提示。请不要担心，这是服务器发现有一些文件不存在而建立它们。

**注意**：Bukkit服务端旨在_完全替代_你从Minecraft.com下载的官方服务器的全部功能。基本上Bukkit服务端和官方服务端无法同时运行在一台电脑上。不过你可以将以前使用官方服务端时生成的所有数据包括world或者其他的配置文件全部拷贝到Bukkit的文件夹中从而继续使用以前的游戏。它们是完全兼容的。

##Windows系统

   1. 首先从这个链接下载最新的稳定版本：[CraftBukkit - Recommended Build](http://dl.bukkit.org/latest-rb/craftbukkit.jar)
   
   2. 选择一个你想作为服务端的文件夹，将下载的jar文件放入这个文件夹。
   
   3. 使用文本编辑器新建一个文本文件并输入：


    	java -Xmx1024M -jar craftbukkit.jar -o true
    	PAUSE


   4. 将文本文件保存为run.bat（注意！请不要保存为txt后缀）然后将保存好的文件拷贝到你选定的服务端文件夹中 **注意**：如果使用的是默认的windows记事本的话，文件可能会被保存为run.bat.txt。请在保存完毕后务必保证文件名称是run.bat。
   
   5. 双击run.bat后你会看到一个黑色的控制台!
   
   6. 在所有文件生成完成后你可以在控制台中看到Done的字样，这时请键入stop来停止服务器。

   如果你看到 "'Java' is not recognized as an internal or external command, operable program or batch file." 这说明你需要安装Java。如果正常安装之后依然不奏效的话，请参阅 [添加Java环境变量] (http://www.java.com/en/download/help/path.xml) 来添加Java的环境变量。

##Linux系统

   1. 首先从这个链接下载最新的稳定版本： [CraftBukkit - Recommended Build](http://dl.bukkit.org/latest-rb/craftbukkit.jar)
   
   2. 将下载的jar文件放在一个文件夹中，在这个例子中我们以_~/craftbukkit_路径作为示例。
   
   3. 在终端中使用使用_cd ~/craftbukkit_将当前目录改至保存jar和服务器文件的文件夹。
   
   4. 在当前目录中创建一个名为_craftbukkit.sh_的文件。在大部分Linux系统中你可以使用_touch craftbukkit.sh_来创建。
   
   5. 使用_nano craftbukkit.sh_打开刚刚建立的文件，黏贴下面的内容后保存：
   
   ```bash
	#!/bin/sh
	BINDIR=$(dirname "$(readlink -fn "$0")")
	cd "$BINDIR"
	java -Xmx1024M -jar craftbukkit.jar -o true
   ```  
   
   6. 为了赋予文件执行的权限，请键入这个指令_chmod +x ~/craftbukkit/craftbukkit.sh_。

   7. 然后键入_~/craftbukkit/craftbukkit.sh_来启动服务器。

   8. 在所有文件生成完成后你可以在终端中看到Done的字样，这时请键入stop来停止服务器。

   如果你通过启动脚本启动服务器，但是希望在关闭终端的情况下服务端依然可以运行，请参阅 [minecraft-init](https://github.com/Ahtenus/minecraft-init)

   如果你想使用screen指令来运行服务器，请参阅 [ABM](http://dev.bukkit.org/server-mods/ascii-bukkit-menu/)

##Mac OS X系统

   1. 安装JAVA

    自从OS X 10.7开始，Java不再随着系统自动安装。所以你需要手动从Apple的官网下载安装Java<http：//support.apple.com/kb/DL1421>
   2. 获取服务端文件

    你至少需要有服务端文件来运行服务端。此外我们也需要一个地方放置服务端文件。
     1. 创建新的文件夹

     打开finder,创立一个新的文件夹并将其命名为_CraftBukkit_
     2. 下载文件

     下载服务端文件。你可以通过Wiki中的最新版本页面下载
     _**注意：**_ 如果你并不想追求最新的新功能的话请下载稳定版本。
     3. 移动文件

     将你下载的文件移动到刚才建立的_CraftBukkit_文件夹。
  3. 编写你的启动脚本

     为了启动服务端，你需要一个启动脚本。下面的内容将教你如何建立启动脚本。
     1. 打开TextEdit，将模式设置成普通文本模式。将下面的内容黏贴至文本中。
     ```bash
	#!/bin/bash
	cd "$( dirname "$0" )"
	java -Xmx1024M -jar craftbukkit.jar -o true
	```


    2. 保存文件

     将文件保存至你的CraftBukkit文件夹，并将其命名为_start\_server.command
     
    3. 赋予文件运行权限
      1. 打开Terminal.app
      2. 在控制台中输入
      ```bash
      chmod a+x
      ```
	
	  **警告**：不要敲击_返回_
      3. 将 start_server.command拖入控制台
      4. 敲击_返回_
  4. 启动服务器
     现在你可以通过双击start_server.command来启动服务器。
	 你至少需要启动一次服务器来生成文件。


**警告**：当关闭服务器的时候请不要直接关闭终端，在终端中输入stop来停止服务器，当服务器完全停止后再关闭终端，否则你的地图文件极有可能损坏！

**其他方法** [只针对有经验的高级用户]：

打开终端(你可以在程序/工具中找到)然后黏贴以下文本：

```bash
	cd ~/Desktop/
	mkdir BukkitServer
	cd BukkitServer/
	curl -LO http：//cbukk.it/craftbukkit.jar
	echo "cd ~/Desktop/BukkitServer/" >> start.command
	echo " java -Xmx1024M -jar craftbukkit.jar -o true" >> start.command
	chmod +x start.command
```


服务端已经安装在了你的桌面上的_Bukkit Server_文件夹中。启动服务器只需双击"LaunchServer.command"。

##错误诊断

[Troubleshooting Common Problems](Troubleshooting_Common_Problems.md)

##相关教程

[Ubuntu Server x64 教程](http://forums.bukkit.org/threads/how-to-setup-a-ubuntu-craftbukkit-server-x64-running-java-x64.598/)
