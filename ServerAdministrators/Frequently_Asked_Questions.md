#  FAQ

## Contents

  * 1 Bukkit维基是什么？
  * 2 Bukkit和CraftBukkit的区别是什么？
  * 3 我可以从哪里得到这些东西？
  * 4 稳定版，测试版，和开发版之间的区别是什么？
  * 5 我可以从哪里找到插件？如何将插件的功能添加到我的服务器上？
  * 6 我做了一个插件，怎么才能上传？
  * 7 我如何才能得到Bukkit的源码？
  * 8 我如何将一个指令重命名？
  * 9 如何编辑我的服务器帮助页面？

#### Bukkit维基是什么?

Bukkit维基是一个包含Bukkit官方文档和其他帮助信息的主页。不过既然作为一个维基，那么就意味着所有人都可以向维基贡献自己的内容。在你向维基贡献的同时，你将默认遵守下面的规定：你对Bukkit维基的所有内容都允许继续被Bukkit组织和或他人所编辑，你的名字不会被明确标注但是你可以在修改日志中找到。当你提交你的内容后，内容会被审核。所有可能会导致内容混杂或者不正确的内容都会被剔除。

#### Bukkit和CraftBukkit的区别是什么？

Bukkit是一个提供给开发人员的API,而CraftBukkit是一个在一个官方服务端的基础上支持BukkitAPI的服务端。

大体而言，Bukkit是一个插件平台允许你向服务端添加插件而令你的服务器更加的炫酷。

而CraftBukkit则是**我们**发行的一个以官方服务器为基础但是搭载了BukkitAPI支持的服务端再发行版本。

#### 我可以从哪里得到这些东西？

最新稳定版本可以在[dl.bukkit.org](http://dl.bukkit.org)找到。然后请参阅[dl.bukkit.org](http://dl.bukkit.org)来开启你的服务器。

你同样可以在[dl.bukkit.org](http://dl.bukkit.org)点击下载到测试版本和开发版本。

#### 稳定版，测试版，和开发版之间的区别是什么？

稳定版是经过我们大量的测试后认为已经几乎没有任何Bug并且满足了我们的要求的版本。测试版是基本上已经稳定运行但是尚未经过大量测试的版本。开发版和前面两个都不一样，它包含着所有的改动。这导致开发版有可能极为稳定或者极为不稳定。更多的细节请参阅EvilSeph所写的[thispost](http://forums.bukkit.org/threads/reminder-bukkit-is-following-a-new-release-system.65358/)。

#### 我可以从哪里找到插件？如何将插件的功能添加到我的服务器上？

插件可以为你的CraftBukkit服务器带来更多新鲜有趣的功能。大部分情况下，你只需下载插件并将jar文件放入服务端文件夹下的“plugins”文件夹即可。但是有些插件需要额外的设置才能正常工作，具体细节请参阅 [Installing Plugins](/Installing_Plugins)

我们已经拥有了至少10,000个不但可用而且经常维护的插件。你可以在[PluginList](http://plugins.bukkit.org)和[Bukkit Dev](http://dev.bukkit.org/server-mods)找到。
#### 我做了一个插件，怎么才能上传？

你至少需要在[BukkitDev](http://dev.bukkit.org/)上创建一个项目。BukkitDev是由官方人员维护的，请参阅[Project Submission　Guidelines](/BukkitDev:Project_Submission_Guidelines)来获取更多的细节。

#### 我如何才能得到Bukkit的源码？

你可以在[这里](https://github.com/Bukkit/)找到Bukkit的源码。如果你希望自己构建的话，你需要使用[Maven3](http://maven.apache.org/)来构建。

#### 我如何将一个指令重命名？

如果想重命名一个指令的话，你需要编辑bukkit.yml或者commands.yml的别名部分。

更多细节请参阅[Commands.yml](/Commands.yml)

#### 如何编辑我的服务器帮助页面？

修改帮助列表可以通过编辑[Help.yml](/Help.yml)来完成。
