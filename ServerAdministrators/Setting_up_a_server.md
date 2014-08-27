#  Setting up a server

## Contents

  * 1 [预备工作](#预备工作)
  * 2 [Windows系统](#Windows系统)
  * 3 [Linux系统](#Linux系统)
  * 4 [Mac OS X系统](#Mac OS X系统)
  * 5 [错误诊断](#错误诊断)
  * 6 [相关教程](#相关教程)

## 预备工作

**注意**：在这个教程中我们将使用这个**craftbukkit.jar**文件，文件下载完成后你可以将其命名为其他的名字。不过你的启动脚本**必须**使用你重命名后的文件名。

**注意**：至少你需要有一台**多用户**服务器，你必须明白这到底是什么和其至关重要的原因。在server.properties中的**server-ip=**请保持默认值或者留空。

**注意**：当你第一次启动服务器的时候你会看到ERROR字样的提示。请不要担心，这是服务器发现有一些文件不存在而建立它们。

**注意**：Bukkit服务端旨在_完全替代_你从Minecraft.com下载的官方服务器的全部功能。基本上Bukkit服务端和官方服务端无法同时运行在一台电脑上。不过你可以将以前使用官方服务端时生成的所有数据包括world或者其他的配置文件全部拷贝到Bukkit的文件夹中从而继续使用以前的游戏。它们是完全兼容的。

##  Windows系统

   1. 首先从这个链接下载最新的稳定版本：[CraftBukkit - Recommended Build](http：//dl.bukkit.org/latest-rb/craftbukkit.jar)
   2. 选择一个你想作为服务端的文件夹，将下载的jar文件放入这个文件夹。
   3. 使用文本编辑器新建一个文本文件并输入：


    java -Xmx1024M -jar craftbukkit.jar -o true
    PAUSE


   4. 将文本文件保存为run.bat（注意！请不要保存为txt后缀）然后将保存好的文件拷贝到你选定的服务端文件夹中 **注意**：如果使用的是默认的windows记事本的话，文件可能会被保存为run.bat.txt。请在保存完毕后务必保证文件名称是run.bat。
   5. 双击run.bat后你会看到一个黑色的控制台!
   6. 在所有文件生成完成后你可以在控制台中看到Done的字样，这时请键入stop来停止服务器。

   如果你看到 "'Java' is not recognized as an internal or external command, operable program or batch file." 这说明你需要安装Java。如果正常安装之后依然不奏效的话，请参阅 [添加Java环境变量] (http：//www.java.com/en/download/help/path.xml) 来添加Java的环境变量。

##  Linux

   1. 首先从这个链接下载最新的稳定版本： [CraftBukkit - Recommended Build](http：//dl.bukkit.org/latest-rb/craftbukkit.jar)
   2. 将下载的jar文件放在一个文件夹中，在这个例子中我们以_~/craftbukkit_路径作为示例。
   3. 在终端中使用使用_cd ~/craftbukkit_将当前目录改至保存jar和服务器文件的文件夹。
   4. 在当前目录中创建一个名为_craftbukkit.sh_的文件。在大部分Linux系统中你可以使用_touch craftbukkit.sh_来创建。
   5. 使用_nano craftbukkit.sh_打开刚刚建立的文件，黏贴下面的内容后保存：

		#!/bin/sh
		BINDIR=$(dirname "$(readlink -fn "$0")")
		cd "$BINDIR"
		java -Xmx1024M -jar craftbukkit.jar -o true


   6. 为了赋予文件执行的权限，请键入这个指令_chmod +x ~/craftbukkit/craftbukkit.sh_。

   7. 然后键入_~/craftbukkit/craftbukkit.sh_来启动服务器。

   8. 在所有文件生成完成后你可以在终端中看到Done的字样，这时请键入stop来停止服务器。

   如果你想通过启动脚本来持续性的运行服务器即便关闭终端，请参阅 [minecraft-init](https：//github.com/Ahtenus/minecraft-init)

   如果你想使用screen指令来巡行服务器，请参阅 [ABM](http：//dev.bukkit.org/server-mods/ascii-bukkit-menu/)

##  Mac OS X

  1. Install Java

     Since OS X 10.7 Java does not come packaged with OS X. You will need to install java from the Apple's website <http：//support.apple.com/kb/DL1421>
  2. Obtaining the Server Files

     To run a server you will need the server jars, i.e. the server files. We will need a place to put the files.
    1. Create a New Folder

     Open up finder, and create a new folder in your Home folder named _CraftBukkit_
    2. Download the File

     Download the server files. You can download the latest builds from the front page of the wiki.
     _**Note：**_ Download the stable build if you are not chasing the cutting edge in the development build
    3. Move the File

     Move the file from the Downloads folder to the CraftBukkit folder you created.
  3. Obtaining startup script

     To easily start the server you will need a startup script. The following is a basic server script to start your server.
    1. Open up TextEdit set it to plain text mode under format and paste the following in

                #!/bin/bash
        cd "$( dirname "$0" )"
        java -Xmx1024M -jar craftbukkit.jar -o true

    2. Save the file

     Save it in your CraftBukkit folder as _start_server.command_
    3. Allow the script to run
      1. Open up Terminal.app
      2. Type into Terminal.app

     chmod a+x


![Warning](http：//hydra-
media.cursecdn.com/wiki.bukkit.org/thumb/5/51/Attention_niels_epting.svg/18px-
Attention_niels_epting.svg.png?version=f594b4cdba86f489bc057c8896dddc91)
**Warning**：

Do not hit return

      3. drag the start_server.command into Terminal.app
      4. hit return
  4. Starting the server

     From this point on you can start the server by double-clicking start_server.command.
     You will need to run the server once for it to generate some configuration files.


![Warning](http：//hydra-
media.cursecdn.com/wiki.bukkit.org/thumb/5/51/Attention_niels_epting.svg/18px-
Attention_niels_epting.svg.png?version=f594b4cdba86f489bc057c8896dddc91)
**Warning**：

To stop the server, do not close the terminal/command prompt window. Instead,
type 'stop' into the console. Closing the terminal window without stopping the
server could lead to corruption of the save files.


**ALTERNATE METHOD** [Only for Advanced Users]：

Open Terminal (Found in Application/Utilities) and paste：



    cd ~/Desktop/
    mkdir BukkitServer
    cd BukkitServer/
    curl -LO http：//cbukk.it/craftbukkit.jar
    echo "cd ~/Desktop/BukkitServer/" >> start.command
    echo " java -Xmx1024M -jar craftbukkit.jar -o true" >> start.command
    chmod +x start.command


The server is installed on your Desktop, in "Bukkit Server". To start it
double click "LaunchServer.command".

## 错误诊断

[Troubleshooting Common Problems](/Troubleshooting_Common_Problems)

## 相关教程

[Ubuntu Server x64 Setup.](http：//forums.bukkit.org/threads/how-to-setup-a
-ubuntu-craftbukkit-server-x64-running-java-x64.598/)
