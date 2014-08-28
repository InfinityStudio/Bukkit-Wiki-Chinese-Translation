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
  * 9 如何将编辑我的服务器帮助页面？

#### What is the BukkitWiki?

The BukkitWiki is the official home of the Bukkit documentation and other help
related information. As this is a wiki, anyone within the community is free to
contribute information to it. By contributing to the wiki, you agree to
release your writing/articles to the Bukkit Organisation to be freely modified
and used wherever we deem necessary without any attribution of credit apart
from the wiki Recent Changes log. While we value contributions made by the
community, plastering credit all over content you've added creates clutter and
makes the wiki look messy.

#### What is the difference between Bukkit and CraftBukkit?

Bukkit is the developer API, while CraftBukkit is a mod for the official
Minecraft server that implements the Bukkit API.

Basically, Bukkit is what plugin developers work with to bring you those cool,
new features that make your server awesome.

CraftBukkit is what we've made so that you can use those plugins with the
official Minecraft server.

#### Where can I get it?

The latest Recommended Build of CraftBukkit can be found at
[dl.bukkit.org](http://dl.bukkit.org). Take a look at [Setting up a
server](/Setting_up_a_server) to get started.

From [dl.bukkit.org](http://dl.bukkit.org) you can also access beta and
development builds by clicking the Alternate Versions link or at [www.dl.bukki
t.org/downloads/craftbukkit/](http://dl.bukkit.org/downloads/craftbukkit/)

#### What is the difference between the Recommended, Beta, and Development builds?

A recommended build has met our highest requirements and testing for release
and we believe it to be bug-free. A beta build is considered stable but has
not received the amount of testing a recommended build needs. A development
build is any changes in between the other two types of builds. These can be
highly stable or highly unstable. See [this
post](http://forums.bukkit.org/threads/reminder-bukkit-is-following-a-new-
release-system.65358/) by EvilSeph for more information on the difference
between beta and recommended builds.

#### Where do I find plugins? or How do I add features to my server?

Plugins can be installed to add new, interesting features to your CraftBukkit
powered server. Generally, you just need to find a plugin and add it to your
"plugins" directory to install it, but some plugins require extra setup or
configuration - see [Installing Plugins](/Installing_Plugins) for more
information.

We already have over 10,000 plugins ready to be used and actively maintained
and supported which can be found by using our [Plugin
List](http://plugins.bukkit.org) Or [Bukkit Dev](http://dev.bukkit.org/server-
mods).

#### I made a plugin. Where do I submit it?

Create a project page for your plugin at [BukkitDev](http://dev.bukkit.org/),
the community plugin resource site. The system is managed by the BukkitDev
Staff. See the [Project Submission
Guidelines](/BukkitDev:Project_Submission_Guidelines) for information on what
you should do when submitting.

#### How do I get Bukkit source code?

The source code can be found [here](https://github.com/Bukkit/). You will need
[Maven3](http://maven.apache.org/) to build Bukkit.

#### How do I rename a command?

Commands can be renamed by creating aliases in the file bukkit.yml or
commands.yml

Have a look at [Commands.yml](/Commands.yml) for instructions on how to do
this.

#### How do I customize my server's help pages?

Help can be customized by editing the [Help.yml](/Help.yml) file.
