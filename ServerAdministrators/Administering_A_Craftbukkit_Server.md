#  管理一个Craftbukkit服务器

如果你是一名使用Craftbukkit的服务器管理员，或者是想要申请成为服务器的管理员的人，甚至是为了浅尝辄止的人，你可以将这个教程作为你开服的参考资料。这个教程旨在通过为管理员们提供大量的指南和一些十分珍贵的资源，来引导他们开启一个从各个方面看都是成功的服务器。这个教程从细琐的小事介绍起，再到服务器每一天的运行、维护和管理，包含着开启一个Minecraft服务器所需的大部分知识。

让我们从零基础开始！开启你的服务器吧！

## 目录

  * 1 第 1 部分: 基础知识
    * 1.1 “纯净”服务器和“插件”服务器
    * 1.2 Bukkit项目
    * 1.3 租用服务器的套餐
    * 1.4 CraftBukkit 还是 Bukkit？
    * 1.5 选择你的操作系统，存储设备大小和内存大小
    * 1.6 价格
  * 2 第 2 部分: 玩家社群
    * 2.1 作为服务器管理员，你应该如何对待自己的玩家
      * 2.1.1 你应该怎样做
    * 2.2 招收管理员
      * 2.2.1 申请系统
        * 2.2.1.1 审核
      * 2.2.2 观察你的玩家
    * 2.3 关于封禁
      * 2.3.1 什么是对玩家负责任的封禁。不负责任的封禁对玩家社群有什么影响？
      * 2.3.2 仁慈和严厉
      * 2.3.3 全局封禁 - 你的志高责任
    * 2.4 让你的玩家社群真正参与进服务器中
    * 2.5 选择你真正所需的插件
      * 2.5.1 开发插件
    * 2.6 日程编排
    * 2.7 做好最坏的准备
    * 2.8 当你的服务器暂时关闭的时候
    * 2.9 “这或许是你的服务器，但它是为玩家而生的”
  * 3 第 3 部分: 服务器运维
    * 3.1 救命！Minecraft升级了！
    * 3.2 我的插件升级了吗？我怎么判断呢？
    * 3.3 升级你的插件
    * 3.4 向别人问问题
# 第 1 部分：基础知识

这个部分旨在给你介绍几个简单的常识：

  1. “原版”服务器和“插件”服务器之间的区别
  2. 什么是Bukkit项目？
  3. 按照人数租用的服务器 和 自由的服务器（VPS, VDS或独立机）之间的区别

这一部分就是你开服苦旅的开始，也是它的一部分


##“原版”服务器和“插件”服务器

开服之前，你首先需要知道的是“纯净”服和“插件”服（如Craftbukkit）之间的区别。由于这些东西能够应用在几乎任何的游戏上面，而通常会搞得一些新人晕头转向，所以介绍这方面的知识十分必要。“纯净”服是你从<http://www.minecraft.net>上面下载下来的 minecraft_server.jar，而它通常没有任何的修改。从一种角度来说，这是一种最纯净、最未被更改、最易被破坏的插件，而这正是大多数服主所畏惧的。“感谢”一种叫做熊孩子的生物和其他的一些问题存在于Minecraft这个群体中，“原版”服务器是各种恶作剧和各种混乱所发生的地方，管理一个原版服务器会令人很心烦，因为你必须监事每一个玩家来保证一切都在正轨上。而这正是“插件”服务器派上用场的时候，而不仅仅是Craftbukkit的作者，还有成百上千的玩家有一种对于修改原本的代码的强烈需求，因为他们在玩家增长的同时，也感受到了强烈的管理需求。“插件服”将更好的安全性和更好的游戏性结合到了一起，构成了插件多人服务器。

“原版”服务器和“插件”服务器之间的主要区别是。“原版”服务器是受Mojang官方支持的服务端，目前Mojang正在开发Mod的API来供给给针对服务端和客户端的修改。对于每一种服务端来说，他们的社区仅仅支持他们自己的服务端。比如说Bukkit，它的社区只会回答关于Bukkit和Craftbukkit的问题，而不会回答关于CanaryMod服务端的问题。

## Bukkit项目

Bukkit项目看上去是由Hey0启动的Hey0服务端模组的一个成功者之一。但实际上，Bukkit是一个独立的项目，它的目的是在为运行它的人提供方便和简洁的环境的情况下，像任何其他的Mod一样来改进Minecraft。一般来说，只会发布一种版本的修改，但是Bukkit项目发布了两种版本：第一种称之为Bukkit，它和这个项目同名，它是作为“原版”服务器的API来使用的。一般情况下，服主们 **不会** 使用Bukkit，因为它只是Bukkit项目的一个API（创建插件的平台）。Craftbukkit则是经过封装的Bukkit的jar，设计为为服主提供简单易用的运行环境，和对Minecraft服务器支持。这个教程中的Craftbukkit是提供给服主们开服的，而不是为开发者提供的环境。

## 租用服务器的套餐

目前市面上有两种主要的服务器租用套餐：按人数计的套餐和自由的硬件平台（VDS, VPS,
 独立机等）

**按人数计的套餐** 你会被授予网络后台（如Multicraft）和FTP（或者类似的东西）。这些东西
通常都对用户很友好。但是这些套餐有的时候限制会过多，并且无法使用特定的软件

**自由的硬件平台** 从基本上来讲，这些设备是在数据中心之中的一台电脑，它拥有网络连接和一个
操作系统。VDS、VPS和独立机都是这种种类的机器。你拥有这台服务器的完全控制权，你可以在你的
出租商的服务条款的允许范围内做任何事情。几乎大多数人都喜欢这种租用方式，因为这种租用方式
能够给你服务器的完全控制，包括他里面运行了什么、存储着什么。当然，你也失去了那些网络后台
能够基于你的方便，除非你自己安装一个。总而言之，由于这种方式没有太多的限制，所以本教程认
为这种方式是最好的部署服务器的方式。[请注意：你的独立机必须开启25565端口(Minecraft使用的端口)]。
当然，你也可以使用[SRV记录](http://www.reddit.com/r/admincraft/comments/16cac2/srv_records_tutorial_revisited/)_)
这篇教程可以使用在这两种开服方式之中。

## CraftBukkit 还是 Bukkit？

前文已解释过，Craftbukkit是Minecraft服务器的插件服务端。相对来说，Bukkit只是
提供给开发者开发插件的API。因为Bukkit是提供给开发者的API，故这篇教程仅会针对Craftbukkit

## 选择你的操作系统，存储设备大小和内存大小

阅读这篇教程将会帮助你学会运行一个Craftbukkit服务端。这里有几个关于选择租用套
餐的小提示。首先：由于Linux和它的衍生物对于Craftbukkit的插件兼容性更好，所以
使用Linux系统的套餐是更好的（译者注：使用Linux系统请务必注意将所有设定转化
为**UTF-8**编码）。话虽如此，如果你不会用Linux，你可以使用Windows，因为它有更
好的GUI支持，易用性好。

当你需要决定使用64位系统还是32位系统的时候，我们推荐你使用64为系统，因为
它能让你使用大于4G的内存。当然，如果不知道怎么选的话，你看哪个爽就选哪个
吧。

 **注意**: 32位和x86是一个意思，x86并不是68位！

在选择内存大小是，我们**强烈**建议你每增加10个玩家，就添加1024MB（1GB）的
内存。如果你的玩家数量小于10个，我们建议你最少使用768MB的内存。由于Java对
于服务端插件极高的内存消耗，你可能(_绝对_)不会有足够的内存。

## 价格

就和上面的一样，价格对于服务器管理者来说也十分重要，因为它涉及到了管理员的钱。
如果你想要建立一个成功的社群，你需要如下条件：有很多钱烧或者建立一套捐款体制。
曾经有一句话这样说：“如果你从小型服务器开始，你的成果应该不差。不要从大型服务
器开始然后越来越小！”请记住，一个大型的玩家社群通常是从小的社群发展出来的。

# 第 2 部分： 玩家社群

玩家社群的本身和运行它的人，同服务器的配置和价格一样，都对于你的社群的成功极其
重要。如果你像一个混蛋一样运行着他，又不去关心玩家们真正能让玩家高兴的东西……你
根本就不可能成功。对！开一个Minecraft服务器就应该像职业一样对待！如果你不能把自
己的全心全力投入到这上面上来的话，我建议你立刻关闭你的浏览器并去做你刚刚在做的
事情，什么都可以，请不要开服。

这个部分将会告诉你：

  * 如何成功地宣传你的服务器
  * 作为一名管理员，你应该如何与玩家相处？
  * 招募管理员，并了解什么时候应该封禁玩家
  * 让你的玩家社群真正地参与进服务器中
  * 选择你真正需要的正确的插件！

  * 为一些事情提前做出计划，并处理意外事件
  * 你的服务器暂时关闭时你所需要做的事
  * “这或许是你的服务器，但它是为玩家而生的”



## 作为服务器管理员，你应该如何对待自己的玩家

#### 你应该怎样做

  * 友好并且有礼貌 - 对你的玩家友好一些，帮他们建点东西，甚至是在他们的房子被破坏者入侵的时候保护他们。
  * 能够回答玩家的问题 - 你需要了解你的插件！没有人会喜欢对自己的插件半知半解的管理员！
  * 能够承受侮辱 - 有一些熊孩子的辱骂有时候会导致很多管理员愤怒至极。如果有些人侮辱了你，封禁他们，然后继续做你应该做的事儿。

_哪怕你拥有全部的权限，但也不要在你自己的服务器里面做一些很混球的事情 - 没有人会
喜欢一个在破坏完他们的房子之后，又逼着他们捐钱回档的服主。玩家会恨死你的，他们还会
告诉其他的人 - 而这对你来说很不好。_



## 招收管理员

在你的服务器迅速扩张的同时，追踪每个玩家的不当行为会变得越来越难。在那时，你需要
招收一些管理员来帮助你降低犯罪率。

基本上讲，有两种招收管理员的方式：玩家申请和观察现有玩家。那我们来看看这两种方法。

#### 申请系统

一般来说，这个系统是用来观察谁有成为管理员的意愿的。你应该以高标准审核他们。

你需要观察的几个方面：

  * 这个玩家活跃嘛？
  * 这个玩家对其他的玩家友好嘛？
  * 这个玩家有没有触犯过服务器规则？
  * 这个玩家的心理成熟嘛？

以上是你招收管理的一些标准。现在你应该注意一下申请表本身了。申请表应该
能够包含很多信息，而不是像下面这样简单：


    姓名：

    年龄：

    你为什么想当管理：

如果你用这种表格来审核管理员，那么其他人混进服务器管理员就十分简单了


你应该用更详细的申请表

    姓名：

    年龄：

    之前的管理经验：

    联系方式：

    你会如何对玩家社群做出贡献：


当然，毕竟人们可以撒谎，所以这中申请表仍然会有些漏洞。但是使用这种申请表能够
让尝试混进来的人更加少。

##### 审核

你还应该审核这些申请表来判断谁更适合这些职位。
You should also review these applications and see who's more fit for the job.
Do not make everyone who applied a moderator, that would defeat the purpose of
applications. Check their sources. If they say that they've been mods on 
previous servers, PM them asking for the IP and **cross-check! **It saves you
a lot of hassle later on.



#### 观察你的玩家

This method is more favorable, as you can see people's real-time interaction
with other players. Definitely spend some time watching those who are more
active. Look at their chat logs in server.log (found in your server folder) or
use an invisibility plugin to watch them as they're unaware of your presence.
One thing you should not do at any cost is **tell them that you're considering
them**! This will alert them and they will most likely change their behavior
patterns to satisfy you - then destroy all of your work in one keystroke.
Again, you should search for friendly, active, and helpful players.


**Don't op them straight away** This cannot be stressed enough. DO NOT give your new staff all permissions straight away. This is a very bad idea and you should always test the new staff members to see if they're capable of being responsible. This is why it's usually best to have a "sub-mod" rank that doesn't have as many permissions as the "full mod" rank, but still has basic staff capabilities. 

  

With that, you should be able to make wise choices with your staff!

  

## 关于封禁

An entire novel could be written about the ban hammer. This simple tool has
the power to remove anyone you want from the server indefinitely. That's why
it's important to understand the basics of banning.

  

There's a few parts to this:

  * Responsible banning and how it will affect your community 
  * Lenience and sternness 
  * Global bans 

  

#### 什么是对玩家负责任的封禁。不负责任的封禁对玩家社群有什么影响？

As has been mentioned, the ban hammer is a very powerful tool. That's why it's
important to exercise caution and use it only when necessary.

You should NEVER ban someone just cause they're getting on your nerves. As a
starting server, you don't want to intimidate your players into leaving.
Admins who ban for "sh*ts and giggles" will lose a lot of players. On the
other side, you shouldn't be overly lenient. You shouldn't let a guy who's
built offensive things out of blocks he stole from other players stay on your
server. That will also cause you to lose a lot of players.

  

#### 仁慈和严厉

It is important to let your players know the limits of what they can do on
your server. This means telling them that, "Yes, you will be banned if you
grief", or, "No, you don't get banned for caps". Stay true to what you tell
them, too. Don't let someone off for griefing after you told them that they
would be banned, and don't ban for caps if you told players that caps lock
wouldn't get them banned. No one likes a two-faced server admin.

  

#### 全局封禁 - 你的志高责任

Global ban services are used to keep track of a player's bans across multiple
servers and warn other servers about bad players. With that said, it is
important to be responsible with a global ban service. Don't global ban people
for random reasons. Most global ban services have a local ban functionality.
Even so, you should NOT local ban them for no reason. This will drive away a
lot of players and that is bad for your server. Too many invalid bans and some
global ban services may review your server. Remember to read your global ban
service's banning guideline to make sure you don't get in trouble with the
service.

## 让你的玩家社群真正参与进服务器中

In order for your server's community to grow, you will always have to keep you
and the players active within it.

Drop parties are known to attract players and can be good for the community.
With those you can attract players and give out free items. In a drop party do
not give out too many good items, try to balance the diamonds, or other rare
items, with more common items, such as flint, plant seeds, or other craftable
items. Make sure you don't have too many drop parties either, as they can
attract players to stay, they can also ruin the server's economy by having
certain players get good free items without having to do any of the hard work
in order to normally get those items. Make sure players know about the drop
parties as well, if they don't know, no one will show up. Once you find a
schedule, stick to it, players will soon get used to it and learn to expect
it, making the community grow.

Another good way at keeping the community involved is by opening public forums
on the server's official webpage. Players can then discus ideas, strategies,
and even review and suggest new things to make your server better. It is
always good to make announcements and upcoming things on those forums. As
people have free speech, make sure you don't over react to bad posts, if they
are too offensive take them down. Also set guidelines and sections for the
forums so it is easily navigable, the players won't stick around if they
cannot find what they are looking for.

One good idea is to run a YouTube channel dedicated to the server, players can
submit videos to you and you may post them on the page. This will give the
players a sense of participation within the community and can help boost
player activity. Allow players to record server spotlights or reviews on their
channels, never be afraid of getting out there. Try and encourage players to
make those videos and maybe give them a small reward, such as a diamond or in
game money.

As these all can help your server, it can also destroy it. Make sure you don't
over do something and ruin the way players look at the server. Don't give out
too many things or it will make some players TOO powerful and can make players
no longer want to play because of the players who have too much power. MAke
sure that the videos and posts are good about the server, anything bad can put
the wrong image into a new players mind.

## 选择你真正所需的插件

This is very important for a successful server. Choosing the right plugins
keeps the gameplay fresh, fun, and original - three things your server needs
to be fun. Don't choose plugins that no one will ever have permissions for
except you (for example, a plugin where you can attack others with fire and
lightning and explosions). These only bog your server down and add nothing for
your players except a cool new "permission denied" message. Yeah, it isn't
fun.

  

Be sure to do extensive testing on a test server. This makes sure that the
plugin works properly and isn't going to corrupt your map data or make
everyone an op or something dangerous.

**Tip**: Remember, download plugins from bukkit.org and ONLY bukkit.org. This is the only site where plugins are checked for maximum security. 

  

#### 开发插件

Can't find that plugin you want really badly? You can either ask someone to
develop it for you or develop it yourself. It takes a lot of practice to
become a good developer, but once you get the hang of it, you will be able to
develop anything you want for your server! This also contributes to your
server while adding some knowledge to your own brain.

  

## 日程编排

Scheduling is an important part of running a successful Minecraft server. You
should always keep your players notified of upcoming updates. Of course, you
can't really schedule a Minecraft update, but you should definitely schedule
when you perform plugin updates, add cool new features, etc. No one likes to
join and then be told that the server will be whitelisted for a week to fix a
critical error (this is where a test server comes in handy). You should always
schedule changes so players can know when they'll need to do something else.

  

## 做好最坏的准备

Face it, you won't always have time to run your server. You'll have
school/work, and other things will arise that keep you from having fun on your
server. But these things happen, and they're nothing to be afraid of! You will
always find SOME free time to run your server and build that giant mansion
you've always dreamed of. You should always tell your players when you'll be
gone for a long time. If an error occurs, tell your players that you're
working on the issue.

  

## 当你的服务器暂时关闭的时候

You should have somewhere to talk to your players when the server is offline.
In most cases, this will be a website or a forum where you can quickly inform
your players of upcoming downtime and other changes happening. Websites make a
great place to hang out and talk to other players.

  

Speaking of websites... don't make your server website look ugly. A lot of
people might actually google your server by accident and then be driven away
by a crappy, ad-infested website.

  

## “这或许是你的服务器，但它是为玩家而生的”

This is very, very, VERY important. This basically sums up this entire
section. You made the server for its players, not for yourself. You spend time
helping players, they spend time making houses. You spend money paying for a
server, they repay you with hours of entertainment. They are who you made this
server for, not yourself:

_**Do. what. the. players. want.**_

_(as long as it's reasonable)_

  

* * *

  

Well, this should be enough to get you started. Good luck!

# Section 3: Keeping it Rolling

A community is like a garden, it grows from a small community into a big one.
But that doesn’t happen overnight! You need to keep it rolling so everyone is
happy!

This section will show you:

  * Useful sites to bookmark and keep your eye on 
  * How to update your plugins 
  * Updating your server/Recommended Builds 

## 救命！Minecraft升级了！

It’s that time again! Craftbukkit is updating and so are your plugins!
Unfortunately this means that most of the time updating your server will not
be enough and most if not all of your plugins will break. Keeping this in
mind, here are some useful places to keep bookmarked as you expand your
Craftbukkit Server.  

Firstly: <http://www.bukkit.org/> should be kept a close eye on. The homepage
of the Bukkit Project always tells you the recommended build of Craftbukkit
and when it’s time to update.

Secondly: <http://plugins.bukkit.org/> is THE website to bookmark to look up
documentation of your plugins or help expand on the plugins you currently
have. With that being said...

Third: EVERY TOPIC FOR ANY PLUGIN ON YOUR SERVER. These should be bookmarked
indefinitely so you can return to check for updates and how to work out the
documentation and commands.

Fourth: <http://dev.bukkit.org/> BukkitDev Is swiftly replacing the old forum
system(linked above) for interaction between plugin developers and the
community(you) and your users. Bukkit dev has many strengths including the
ability to subscribe to alerts by email when your plugins are updated

Fifth: <http://wiki.bukkit.org/> always has a counter for the current
Craftbukkit build and tons of tutorials on how to run servers.

## 我的插件升级了吗？我怎么判断呢？

通常情况下，不仔细找寻一番是很难判断出你到底正在使用哪个版本。请打开你的插件控制台然后键入_/version_，马上你就可以找到你的CraftBukkit版本。将其与当前稳定的版本号相对比，你可以判断出来当前运行的版本是不是最新的稳定版本。此外，键入_/version [pluginName]_也可以很快的找到某一个正在运行的插件的版本。 

There are also plugins that can be used as a guiding resource that an admin
can use as a helping hand to keep plugins as well as CraftBukkit itself up to
date. These resources however are not a full replacement for doing the
research on your own as blindly updating can often cause more trouble than it
saves.  

## 升级你的插件

如果你希望升级服务器插件，首先请关停服务器，删除老版本插件并将新的放入。如果你发现Changelog表示新的版本在Config文件上有变化（Changelog通常可以在论坛对应插件的帖子中找到不过很多插件开发者喜欢将它放在对应版本的下载页中），那么请对应合适的改动。通常这个过程会伴随着插件的升级自动完成，但很少情况下需要我们手动的更改。

## 向别人问问题

那些已经成功开服的人的经验是你宝贵的资源。请不要畏惧向他人请教！大部分曾经担任服主或者正在担任服主的人都会尽可能的帮助你，或者向你推荐一些可以为你提供帮助的人。如果你认为没有任何认识的人了解相关的知识，那么请使用Bukkit IRC Channel。在IRC上有大量的服主，插件开发者和其他精通Bukkit的人乐于为你提供帮助。