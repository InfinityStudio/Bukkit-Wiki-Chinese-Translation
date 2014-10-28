# 设置你的工作区

这篇指南罗列了一些你需要的工具来使用Bukkit api，通过这些工具你可以制作属于自己插件。

## 目录

  * 1 工具
    * 1.1 Java Development Kit
      * 1.1.1 Which version of the JDK?
      * 1.1.2 64-bit (x64) or 32-bit (x86)?
    * 1.2 Git
      * 1.2.1 Using Git
        * 1.2.1.1 GitHub
    * 1.3 Apache Maven
      * 1.3.1 Using Maven
    * 1.4 Integrated Development Environments
      * 1.4.1 Eclipse
      * 1.4.2 NetBeans
      * 1.4.3 IntelliJ IDEA
  * 2 Where To From Here

# 公爵

无论如何，一个开发者都需要使用工具来开发软件，但是每个人都自己喜欢的工具和不同的开发需求。如果你只是想制作插件的话，我们将会推荐几个工具来让开发更加的容易。与此同时，如果你将你制作的软件开源的话，这些工具也能让其他人更容易帮你一起开发这个插件。

## Java开发工具包（JDK）

JDK（Java开发工具包）是一个Jre（Java运行环境）的尚未编译版本，其中包含着Jre的源码和文档来帮助你开发。最新版本的JDK可以在[这里](http://www.oracle.com/technetwork/java/javase/downloads/index.html)下载。

### 我应该使用哪个版本的JDK？

因为Java有多个版本，所以JDK同样有多个版本。不过，无论是Bukkit还是Minecraft都是在Java6环境下编译的。与此同时，大部分服务器使用的都是Java6版本，还有一小部分使用更新的Java7.通常情况下新的Java版本都能向下兼容老的Java版本，不过他们同样只被自己兼容。这样的话，使用新的Java版本编译的插件通常无法兼容老版本的JRE。如果你这么做的话，通常会导致[UnsupportedClassVersionError](http://docs.oracle.com/javase/1.5.0/docs/api/index.html?java/lang/UnsupportedClassVersionError.html)错误。综上所述，在下面的练习中，请使用版本相同的JDK和DRE。

### 使用64位（x64）还是32位（x86）？

除非你的编译器不支持64位，否则你应该使用64的JDK位进行编译。同时，你的开发环境应当与你安装的JDK位数版本相匹配。在64位系统下，你可以同时安装32位和64位的JDK。

## 什么是Git

![git](http://hydra-media.cursecdn.com/wiki.bukkit.org/thumb/2/29/Git-Logo-2Color.png/40px-Git-Logo-2Color.png?version=03ffd9ff8306dfaf62725ef54b60f1e5)

Git是一个分布式的版本控制系统。而且，Bukkit的项目也是使用Git进行管理和控制的。Git允许一个开发者开发的同时与其他开发者共同协作开发。不但如此，Git还拥有允追踪任何人所做的任何更改的强大功能。当然，这也导致Git有点难以入门。Git的最新版本可以在[这里](http://git-scm.com/download)下载。

### 使用Git

你可以在[这里](http://git-scm.com/book)找到详细的安装和使用指南。

#### 什么是GitHub

[GitHub](https://github.com)是一个源代码分享网站，Bukkit项目的源代码也是托管在Github上面的。你可以使用Git的克隆功能从[Bukkit源代码仓库](http://github.com/Bukkit)克隆Bukkit的源代码。



Sharing of code works both ways - you can download shared code, but you can
also share yours with the world. This is a great idea in this open community,
as it allows others to help you with your project, or even develop new
features for your plugins! If you intend to contribute to the Bukkit Project
you must be willing to share your code. Additional instructions for using
GitHub can be found at [GitHub:Help](https://help.github.com/)

## Apache Maven

[Apache Maven](http://maven.apache.org) is a tool that the Bukkit Project uses
to manage building our code. The latest version of Maven can be found on the
[here](http://maven.apache.org/download.html) on the Apache Maven site.

### Using Maven

Additional instructions for installing and using Maven can be found
[here](http://maven.apache.org/guides/getting-started/maven-in-five-
minutes.html) on the maven site.

Once installed, Maven should be utilised to compile Bukkit and CraftBukkit.
Refer to the respective README files in the repositories for instructions.

## Integrated Development Environments

The IDE (Intergraded Development Environment) is a program you can use to
compile and debug your plugins. An IDE is an optional piece of the developer
tool chain. It is possible to use notepad (or its equivalent) and produce a
working a plugin. An IDE however, makes the life of a developer much easier by
integrating powerful tools, providing syntax highlighting, and error checking.
The choice of which IDE to use is yours to make!

### Eclipse

The [Eclipse IDE](http://www.eclipse.org/) is a popular choice among plugin
developers. The latest version, Eclipse Kepler (4.3.1), can be found
[here](http://www.eclipse.org/downloads/packages/) on the eclipse site. Plugin
developers should download the **Eclipse IDE for Java Developers**. Eclipse
provides Maven integration by means of the m2Eclipse plugin, Git integration
with by mean of the eGit plugin. Additionally, the
[YEdit](http://code.google.com/p/yedit/) plugin can be installed to provide a
YAML editor.

     _For general Eclipse IDE usage please refer to the [Eclipse documentaiton](http://www.eclipse.org/documentation/)._
     _For Maven integration usage please refer to the [m2eclipse documentation](http://www.sonatype.org/m2eclipse/)._
     _For Git integration usage please refer to the [eGit documentaiton](http://www.eclipse.org/egit/documentation/)._

### NetBeans

The [Netbeans IDE](http://netbeans.org/) is developed by Oracle. The latest
version, 7.3, can be found [here](http://netbeans.org/downloads/) on the
Netbeans site. Plugin developers should download the **Netbeans Java SE
bundle**. Netbeans provides native integration with Maven and Git integration
by means of a Git plugin.

     _For usage instructions please refer to the [Netbeans documentation](http://netbeans.org/kb/index.html)._

### IntelliJ IDEA

[IntelliJ IDEA](http://www.jetbrains.com/idea/) is another popular IDE. The
latest version, 13, can be found
[here](http://www.jetbrains.com/idea/download/index.html) on the IntelliJ
site. Plugin developers should download the **Community Edition**. IntelliJ
provides native integration with Maven and Git.

     _For usage instructions please refer to the [IntelliJ documentation](http://www.jetbrains.com/idea/documentation/index.jsp)._

# Where To From Here

There is lots more involved in actually developing and testing your code,
however hopefully you now have the tools to get started. If you find any
particularly useful tutorials make sure to link them here!

It is suggested that you start with [Plugin Tutorial](/Plugin_Tutorial).