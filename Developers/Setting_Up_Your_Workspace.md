# 设置你的工作区

这篇指南罗列了一些你需要的工具来使用Bukkit api，通过这些工具你可以制作属于自己插件。

## 目录

  * 1 工具
    * 1.1 Java开发工具包（JDK）
      * 1.1.1 我应该使用哪个版本的JDK？
      * 1.1.2 使用64位（x64）还是32位（x86）？
    * 1.2 什么是Git
      * 1.2.1 使用Git
        * 1.2.1.1 什么是GitHub
    * 1.3 Apache Maven
      * 1.3.1 使用Maven
    * 1.4 集成开发环境（IDE）
      * 1.4.1 Eclipse
      * 1.4.2 NetBeans
      * 1.4.3 IntelliJ IDEA
  * 2 接下来？

# 工具

无论如何，一个开发者都需要使用工具来开发软件，但是每个人都自己喜欢的工具和不同的开发需求。如果你只是想制作插件的话，我们将会推荐几个工具来让开发更加的容易。与此同时，如果你将你制作的软件开源的话，这些工具也能让其他人更容易帮你一起开发这个插件。

## Java开发工具包（JDK）

JDK（Java开发工具包）是一个Jre（Java运行环境）的尚未编译版本，其中包含着JRE的源码和文档来帮助你开发。最新版本的JDK可以在[这里](http://www.oracle.com/technetwork/java/javase/downloads/index.html)下载。

### 我应该使用哪个版本的JDK？

因为Java有多个版本，所以JDK同样有多个版本。不过，无论是Bukkit还是Minecraft都是在Java6环境下编译的。与此同时，大部分服务器使用的都是Java6版本，还有一小部分使用更新的Java7。通常情况下新的Java版本都能向下兼容老的Java版本，不过他们同样只被自己兼容。这样的话，使用新的Java版本编译的插件通常无法兼容老版本的JRE。如果你这么做的话，通常会导致[UnsupportedClassVersionError](http://docs.oracle.com/javase/1.5.0/docs/api/index.html?java/lang/UnsupportedClassVersionError.html)错误。综上所述，在下面的练习中，请使用版本相同的JDK和JRE。

### 使用64位（x64）还是32位（x86）？

除非你的编译器不支持64位，否则你应该使用64的JDK位进行编译。同时，你的开发环境应当与你安装的JDK位数版本相匹配。此外，在64位系统下，你可以同时安装32位和64位的JDK。

## 什么是Git


![git](http://git-scm.com/images/logo@2x.png)

Git是一个分布式的版本控制系统。而且，Bukkit的项目也是使用Git进行管理和控制的。Git允许一个开发者开发的同时与其他开发者共同协作开发。不仅如此，Git还拥有允追踪任何人所做的任何更改的强大功能。当然，这也导致Git有点难以入门。Git的最新版本可以在[这里](http://git-scm.com/download)下载。

### 使用Git

你可以在[这里](http://git-scm.com/book)找到详细的安装和使用指南。

#### 什么是GitHub

[GitHub](https://github.com)是一个源代码分享网站，Bukkit项目的源代码也是托管在Github上面的。你可以使用Git的克隆功能从[Bukkit源代码仓库](http://github.com/Bukkit)克隆Bukkit的源代码。


代码分享是一个双向的过程-你可以下载别人分享的代码，同时你也可以向全世界分享你自己的代码。我们非常推荐分享你的代码，这样的话感兴趣的人就可以对你的项目提供帮助，甚至为你的插件开发新的功能。如果你希望向Bukkit项目贡献代码的话，首先你必须自愿接受分享代码。一些其他的Github使用指南可以在[这里](https://help.github.com/)找到。

## Apache Maven

[Apache Maven](http://maven.apache.org)是一个用于代码管理和构建的工具，Bukkit也是使用这种这个工具进行构建的。最新的Maven版本可以在[这里](http://maven.apache.org/download.html)找到的。

### 使用Maven

关于如何安装和使用Maven，首先你可以在[这里]找到一些有用的信息(http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)。

当你安装完毕后，Maven就可以用来编译Bukkit或者CraftBukkit啦。你可以在源代码中的README文件里找到编译和构建的方法。

## 集成开发环境（IDE）

IDE（集成开发环境）是用来编辑、编译和调试的工具。你可以用它来编写你的代码，同样通过它来运行你的代码从而找到代码中的错误所在。IDE的使用是编码开发中非常重要的一环。是的，你当然可以只使用记事本来编写你的插件，不过使用IDE将会让你更加便捷的编辑你的代码。无论是语法高亮还是自动查错都是非常实用的工具，没有这些便捷的工具，开发将会变得枯燥无味且难以继续。

### Eclipse

[Eclipse](http://www.eclipse.org/)是在插件开发者中非常流行的IDE。最新的版本可以在[这里](http://www.eclipse.org/downloads/packages/)找到。请注意，你需要下载的是**Eclipse IDE for Java Developers**！Eclipse通过m2Eclipse插件和eGit插件分别提供对Maven和Git的支持。同时，你可以下载[YEdit](http://code.google.com/p/yedit/)来获得对Yaml的支持，这在以后的开发过程中将会非常有用。

  _关于如何使用Eclipse，请参阅[Eclipse文档](http://www.eclipse.org/documentation/)。_
  _关于在Eclipse中Maven的使用，请参阅[m2eclipse文档](http://www.sonatype.org/m2eclipse/)。_
  _关于如何在Eclipse中使用Git，请参阅[eGit documentaiton](http://www.eclipse.org/egit/documentation/)。_

### NetBeans

[Netbeans IDE](http://netbeans.org/)是一款由甲骨文开发的IDE。最新的版本可以在[这里](http://netbeans.org/downloads/)找到。如果你希望使用这款IDE开发工具开发插件，请注意下载**Netbeans Java SE bundle**。Netbeans内部已经集成了Maven和Git支持，所以你不用再另外下载这些插件了。

  _更多使用指南请参阅[Netbeans文档](http://netbeans.org/kb/index.html)。_

### IntelliJ IDEA

[IntelliJ IDEA](http://www.jetbrains.com/idea/)是另外一款非常流行的IDE。最新的版本可以在[这里](http://www.jetbrains.com/idea/download/index.html)下载。同样，用它开开发插件的话，请留意下载**Community Edition**版本。IntelliJ同样也内继承了对于Git和Maven的支持。

  _更多使用指南请参阅[IntelliJ文档](http://www.jetbrains.com/idea/documentation/index.jsp)。_

# 接下来？

其实，还有很多的关于开发的细节比如如何测试你的代码之类的内容没有在这里详细阐述。不过既然你已经走到了这一步，希望你已经可以开始着手你的第一个插件了！此外，如果你找到其他很棒的教程，请务必告诉我们。

现在让我们一起开始下一章[插件开发入门](https://github.com/Trigonometry-F/Bukkit-Wiki-Chinese-Translation/blob/master/Developers/Plugin_Tutorial.md)吧！ 