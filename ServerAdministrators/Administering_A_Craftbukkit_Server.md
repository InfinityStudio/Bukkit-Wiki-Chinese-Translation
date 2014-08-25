#  管理一个Craftbukkit服务器
原文来自BukkitWiki

介绍  

开宗立意  
这个教程是提供给目前的Craftbukkit服务器管理员，或是那些想申请服务器管理员的人的。
无论你是否拥有这个服务器，还是你只是开起来玩玩（甚至是这两种成分都有）。这个教程
旨在为你开启一个成功的服务器提供大量的指南和十分珍贵的资源。从细微的小事，再到每
天对你自己的自我管理和对服务器的管理。

让我们从零基础开始！开启你的服务器吧！

## 目录

  * 1 第 1 部分: 开天辟地
    * 1.1 “纯净”服务器和“插件”服务器
    * 1.2 Bukkit项目
    * 1.3 The Hosting Plans
    * 1.4 CraftBukkit or Bukkit?
    * 1.5 Pick your Operating System, Memory, and RAM!
    * 1.6 Pricing
  * 2 第 2 部分: The Community
    * 2.1 As an administrator, how you should act with players.
      * 2.1.1 What you should do:
    * 2.2 Appointing moderators
      * 2.2.1 Application system:
        * 2.2.1.1 Reviewing
      * 2.2.2 Watching your players
    * 2.3 The ban hammer of legend
      * 2.3.1 Responsible banning and how irresponsible banning is bad for the community
      * 2.3.2 Lenience and sternness
      * 2.3.3 Global bans - responsibility
    * 2.4 Keeping your community involved
    * 2.5 Choosing the correct plugins
      * 2.5.1 Development
    * 2.6 Scheduling
    * 2.7 Preparing for the unexpected
    * 2.8 Somewhere to meet when the server is offline
    * 2.9 "It might be your server but it was made for them"
  * 3 第 3 部分: Keeping it Rolling
    * 3.1 Help! Minecraft Updated!
    * 3.2 Are my plugins updated? How can I tell?
    * 3.3 Updating your plugins
    * 3.4 Asking Others

# 第 1 部分：开天辟地

这个部分意旨给你介绍几个十分简单的、基本的常识：

  1. “原版”服务器和“MOD”服务器之间的区别
  2. Bukkit是什么？
  3. 按照人数租用的服务器 和 自由的服务器（VPS, VDS或独立机）之间的区别

这一部分就是你开服苦旅的开始，也是它的一部分


##“原版”服务器和“插件”服务器

开服之前，你首先需要知道的是“纯净”服和“插件”服（如Craftbukkit）之间的区别。
由于这些东西能够应用在几乎任何的游戏上面，而通常会搞得一些新人晕头转向，所
以介绍这方面的知识十分必要。
“纯净”服是你从<http://www.minecraft.net>上面下载下来的 minecraft_server.jar，
而它通常没有任何的修改。从一种角度来说，这是一种最纯净、最未被更改、最易被破坏
的插件，而这正是大多数服主所畏惧的。“感谢”一种叫做熊孩子的生物和其他的一些问题
存在于Minecraft这个群体中，“原版”服务器是各种恶作剧和各种混乱所发生的地方，
管理一个原版服务器会令人很心烦，因为你必须监事每一个玩家来保证一切都在正轨上。
而这正是“插件”服务器派上用场的时候，而不仅仅是Craftbukkit的作者，还有成百上千
的玩家有一种对于修改原本的代码的强烈需求，因为他们在玩家增长的同时，也感受到了
强烈的管理需求。“插件服”将更好的安全性和更好的游戏性结合到了一起，构成了插件多人服务器。

The main difference between “Vanilla” and “Modified” is that Mojang only
supports Vanilla servers as of this article. Currently Mojang is developing a
Mod API for modification makers to use, but aside from that the communities
built around the Modified servers are the only official support for their
mods. For example, Bukkit. Bukkit answers questions about Bukkit and
Craftbukkit Mods, not CanaryMod.

## The Bukkit Project

The Bukkit project is seen to many as the successor of the Hey0 server mod as
started by Hey0. However, Bukkit is an independent project which seeks to
improve Minecraft like any mod would, but at a different level that offers
convenience and ease to the people running it. Normally there is only one
instance of the modification, but the Bukkit project releases two versions:
One is called Bukkit, like the project, and is the “Missing API” of a Vanilla
Server; Normally, server owners would **not** use Bukkit, as it is only an API
for Bukkit (the platform in which plugins are created). CraftBukkit is the
sealed up Bukkit .jar file in an easy-to-use environment for server
administrators, made specifically for running the Minecraft server. This
tutorial primarily works with CraftBukkit over Bukkit seeing as CraftBukkit is
used by the Bukkit Project for server admins rather than for developers.

## The Hosting Plans

There are two primary paid hosting plans, or at-least two categories: Game
Hosting Plans and Freeform Plans (VDS, VPS, Dedicated Hardware, etc.)

**Game Hosting Plans**. You are given a web panel and a FTP access (or something along these lines) and are very user friendly. However, the downside to this is that some plans are too restrictive and proprietary software gets into conflicts with the Modifications.

**Freeform Plans**. These plans are, in the basic sense, a computer in a datacenter with a permanent internet connection and an Operating System. Virtual Dedicated Servers, Virtual Private Servers, and Dedicated Servers all fall under this category. You are given complete control of the system and are free to do as you please with your allowance within the host’s terms of service. This is the most favored type of plan because you have total control of your server and what is put in it, but you also lose the convenience of a simple user interface, unless you install a graphical server wrapper. However, in the end, this tutorial believes that it’s the best choice for server hosting due to the fact that there are no restrictions. (_Note: Make sure your host allows port 25565, which is Minecraft's port, or you can use [SRV Records](http://www.reddit.com/r/admincraft/comments/16cac2/srv_records_tutorial_revisited/)_). This tutorial will work under both interfaces for convenience.

## CraftBukkit or Bukkit?

As explained in the previous sections, CraftBukkit is the modification for
servers, as opposed to Bukkit which is an API so developers can make plugins.
This tutorial will focus only on CraftBukkit as Bukkit is only useful for
plugin developers.

## Pick your Operating System, Memory, and RAM!

Seeing as this tutorial will help you run a Craftbukkit Server, here are some
quick tips to look at when choosing a plan. Firstly: More Plugins for
Craftbukkit Support Linux and Linux derivatives only, so it’s recommended that
you get a Linux plan. That being said if you are a new user, Windows will be
more useful for you because it has a clean GUI (Graphical User Interface) and
is easy for server hosting.

When you come across the fabled 32-bit versus 64-bit decision; it’s
recommended that you choose a 64-bit plan as it will allow you to have more
(4GB or higher) RAM than a 32-bit plan will. If you're not sure, or simply
don’t care, choose what you fancy.

    ![Lightbulb.png](http://hydra-media.cursecdn.com/wiki.bukkit.org/6/6f/Lightbulb.png?version=0e5a9741aa6598c745ae089a294d0510) **Note**: 32-bit may be also displayed as x86, this isn't more!

When choosing RAM amounts, it is HIGHLY recommended to run a Craftbukkit
Server 1024MB (1GB) of RAM per 10 Player Slots. If your player slot amount is
below 10, we recommend a 768MB plan at minimum. Due to Java's high memory
consumption of the server and plugins you can (_and will_) never have enough
RAM.

## Pricing

Likewise, pricing is a huge issue for server admins because the money is
coming out of your pocket! If you want to run a successful community: Have a
lot of money to burn, or setup a donation system with rewards for members to
entice continuous play on your server and to help pay for it. That being said,
if you’re just starting out a small package should do you just fine. Don’t
start big and go small! A large community of players always starts from a
small one.

# Section 2: The Community

Like the pricing and the specs of the machine, the community itself and who
runs it is extremely crucial to your community’s success. If you run it “half-
assed” and don’t really care to learn about or keep your users happy... you
won’t do too well at all. Yes! Running a Minecraft server is a job! And if you
can’t commit to it then you should exit your browser right now and go back to
whatever it is you do.

This section will show you:

  * How to successfuly advertise your server
  * As an Administrator, how you should act while with players
  * Hire Moderators, know when to lay down the ban-hammer!
  * Keep the community involved
  * Choose correct plugins and abilities your players will love!

  * Planning in advance for things and dealing with unexpected events
  * Somewhere to meet if the server is offline
  * "It's your server but it's for the players"



## As an administrator, how you should act with players.

#### What you should do:

  * Be friendly and polite - be kind to your players, help them build something, maybe even protect their house from griefers.
  * Be able to answer questions - Know your plugins! No one likes a server admin who doesn't know how to use half of their plugins.
  * Be able to tolerate insults - One thing that many admins will do is rage quit when a "butthurt jerk" insults all of their work. So what if someone insults you? Ban them, and move on!



_Don't be a jerk just because you have all permissions - No one likes a server
owner that griefs their players and then makes them donate for a rollback.
People will hate you, and they will tell other people - and that is very bad
for you._



## Appointing moderators

As your server expands in size, it will become more and more difficult for you
to keep track of everyone's problems at the same time. You'll need to hire
moderators to help you out and keep server crime down to a low.

There are two general ways that people hire moderators: applications and
watching their players. Let's take a look at both.

#### Application system:

Generally, this is used to see who is interested in becoming a moderator. You
should have high standards and expectations.

Some things to look for:

  * Is the player active?
  * Is the player friendly towards other players?
  * Has the player followed the rules so far?
  * Is the player mature?



These are some of the criteria to look for. Now, you should look at the
application form itself. This should require a lot of detail and not be
something stupid like this:



    Name:

    Age:


    Why you want it:

With forms like this, it is extremely easy for someone to lie their way into a
staff position.



You should use something more detailed like this:



    Name:

    Age:

    Previous experience:

    Contact method:

    How will you contribute to the community:




Of course, this is still somewhat exploitable, as people can lie about their
previous experience and how they'd help the community, but it is much more
difficult to lie in this one than it is in the previous one.

##### Reviewing

You should also review these applications and see who's more fit for the job.
Do not make everyone who applied a moderator, that would defeat the purpose of
applications. Check their sources. If they say that they've been mods on
previous servers, PM them asking for the IP and **cross-check! **It saves you
a lot of hassle later on.



#### Watching your players

This method is more favorable, as you can see people's real-time interaction
with other players. Definitely spend some time watching those who are more
active. Look at their chat logs in server.log (found in your server folder) or
use an invisibility plugin to watch them as they're unaware of your presence.
One thing you should not do at any cost is **tell them that you're considering
them**! This will alert them and they will most likely change their behavior
patterns to satisfy you - then destroy all of your work in one keystroke.

