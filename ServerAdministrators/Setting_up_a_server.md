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

**注意**：Bukkit服务端旨在_完全替代_你从Minecraft.com下载的官方服务器的全部功能。基本上Bukkit服务端和官方服务端无法同时运行在一台电脑上。不过你可以将以前使用官方服务端时生成的所有数据包括world或者其他的配置文件全部拷贝到Bukkit的文件夹中从而继续使用以前的游戏。 

##  Windows系统

    1\. Download CraftBukkit's latest recommended build： [CraftBukkit - Recommended Build](http：//dl.bukkit.org/latest-rb/craftbukkit.jar)
    2\. Put the .jar file in the directory you'd like the server to run from 
    3\. Open a text editor such as Notepad and type： 
    
    
    java -Xmx1024M -jar craftbukkit.jar -o true
    PAUSE
    

    4\. Save the document as run.bat (not as a .txt) in the same directory as craftbukkit.jar. 
    ![Lightbulb.png](http：//hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**： With some programs such as Notepad, it may try saving as run.bat.txt. When saving to a file name, put the name in quotes： "run.bat" 
    5\. Double click run.bat and you're away! 
    6\. To shut down, issue the "stop" command in console. 

     If you see "'Java' is not recognized as an internal or external command, operable program or batch file." then you need to reinstall Java. Still get this error? Follow this [guide](http：//www.java.com/en/download/help/path.xml) to adding Java to your system path. 

##  Linux

    1\. Download CraftBukkit's latest build： [CraftBukkit - Recommended Build](http：//dl.bukkit.org/latest-rb/craftbukkit.jar)
    2\. Put the .jar in a folder, for this example we'll use a generic one： ~/craftbukkit 
    3\. Move to the above directory in terminal with 'cd ~/craftbukkit' 
    4\. Create a new file in the minecraft folder and name it craftbukkit.sh 
    5\. Edit the file and paste this into it： 
    
    
    #!/bin/sh
     BINDIR=$(dirname "$(readlink -fn "$0")")
     cd "$BINDIR"
     java -Xmx1024M -jar craftbukkit.jar -o true
    

    6\. Make the file executable, either by running "chmod +x ~/craftbukkit/craftbukkit.sh" in a terminal, or by changing the permissions in the file's properties. 

    7\. Then, in terminal, type '~/craftbukkit/craftbukkit.sh' to run to start the server. 

    8\. When you're done playing around, issue the "stop" command in console. 

If you plan to run the server more permanently an init script like this one
(recommended) [[1]](https：//github.com/Ahtenus/minecraft-init)

If you want to run your server with screen, you can use a script like this one
(recommended) [ABM](http：//dev.bukkit.org/server-mods/ascii-bukkit-menu/)

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
