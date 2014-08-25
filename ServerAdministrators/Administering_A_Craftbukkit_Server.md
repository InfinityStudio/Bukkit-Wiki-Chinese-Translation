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

“原版”服务器和“插件”服务器之间的主要区别是。“原版”服务器是受Mojang官方支持的服务端，
目前Mojang正在开发Mod的API来供给给针对服务端和客户端的修改。对于每一种服务端来说，
他们的社区仅仅支持他们自己的服务端。比如说Bukkit，它的社区只会回答关于Bukkit和
Craftbukkit的问题，而不会回答关于CanaryMod服务端的问题。

## Bukkit项目

Bukkit项目看上去是由Hey0启动的Hey0服务端模组的一个成功者之一。但实际上，Bukkit
是一个独立的项目，它的目的是在为运行它的人提供方便和简洁的环境的情况下，像任何
其他的Mod一样来改进Minecraft。一般来说，只会发布一种版本的修改，但是Bukkit项目
发布了两种版本：第一种称之为Bukkit，它和这个项目同名，它是作为“原版”服务器的API
来使用的。一般情况下，服主们 **不会** 使用Bukkit，因为它只是Bukkit项目的一个API（创建插件的平台）。
Craftbukkit则是经过封装的Bukkit的jar，设计为为服主提供简单易用的运行环境，和对
Minecraft服务器支持。这个教程中的Craftbukkit是提供给服主们开服的，而不是为开发
者提供的环境。

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
Again, you should search for friendly, active, and helpful players.


**Don't op them straight away** This cannot be stressed enough. DO NOT give your new staff all permissions straight away. This is a very bad idea and you should always test the new staff members to see if they're capable of being responsible. This is why it's usually best to have a "sub-mod" rank that doesn't have as many permissions as the "full mod" rank, but still has basic staff capabilities. 

  

With that, you should be able to make wise choices with your staff!

  

## The ban hammer of legend

An entire novel could be written about the ban hammer. This simple tool has
the power to remove anyone you want from the server indefinitely. That's why
it's important to understand the basics of banning.

  

There's a few parts to this:

  * Responsible banning and how it will affect your community 
  * Lenience and sternness 
  * Global bans 

  

#### Responsible banning and how irresponsible banning is bad for the community

As has been mentioned, the ban hammer is a very powerful tool. That's why it's
important to exercise caution and use it only when necessary.

You should NEVER ban someone just cause they're getting on your nerves. As a
starting server, you don't want to intimidate your players into leaving.
Admins who ban for "sh*ts and giggles" will lose a lot of players. On the
other side, you shouldn't be overly lenient. You shouldn't let a guy who's
built offensive things out of blocks he stole from other players stay on your
server. That will also cause you to lose a lot of players.

  

#### Lenience and sternness

It is important to let your players know the limits of what they can do on
your server. This means telling them that, "Yes, you will be banned if you
grief", or, "No, you don't get banned for caps". Stay true to what you tell
them, too. Don't let someone off for griefing after you told them that they
would be banned, and don't ban for caps if you told players that caps lock
wouldn't get them banned. No one likes a two-faced server admin.

  

#### Global bans - responsibility

Global ban services are used to keep track of a player's bans across multiple
servers and warn other servers about bad players. With that said, it is
important to be responsible with a global ban service. Don't global ban people
for random reasons. Most global ban services have a local ban functionality.
Even so, you should NOT local ban them for no reason. This will drive away a
lot of players and that is bad for your server. Too many invalid bans and some
global ban services may review your server. Remember to read your global ban
service's banning guideline to make sure you don't get in trouble with the
service.

## Keeping your community involved

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

## Choosing the correct plugins

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

  

#### Development

Can't find that plugin you want really badly? You can either ask someone to
develop it for you or develop it yourself. It takes a lot of practice to
become a good developer, but once you get the hang of it, you will be able to
develop anything you want for your server! This also contributes to your
server while adding some knowledge to your own brain.

  

## Scheduling

Scheduling is an important part of running a successful Minecraft server. You
should always keep your players notified of upcoming updates. Of course, you
can't really schedule a Minecraft update, but you should definitely schedule
when you perform plugin updates, add cool new features, etc. No one likes to
join and then be told that the server will be whitelisted for a week to fix a
critical error (this is where a test server comes in handy). You should always
schedule changes so players can know when they'll need to do something else.

  

## Preparing for the unexpected

Face it, you won't always have time to run your server. You'll have
school/work, and other things will arise that keep you from having fun on your
server. But these things happen, and they're nothing to be afraid of! You will
always find SOME free time to run your server and build that giant mansion
you've always dreamed of. You should always tell your players when you'll be
gone for a long time. If an error occurs, tell your players that you're
working on the issue.

  

## Somewhere to meet when the server is offline

You should have somewhere to talk to your players when the server is offline.
In most cases, this will be a website or a forum where you can quickly inform
your players of upcoming downtime and other changes happening. Websites make a
great place to hang out and talk to other players.

  

Speaking of websites... don't make your server website look ugly. A lot of
people might actually google your server by accident and then be driven away
by a crappy, ad-infested website.

  

## "It might be your server but it was made for them"

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

## Help! Minecraft Updated!

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

## Are my plugins updated? How can I tell?

  
Normally, you can’t tell what version your plugin or server is... without a
little searching, that is! If you log in to your server and type /version you
can immediately find out what version is your Craftbukkit server and
immediately compare it to the Recommended Build. Additionally, /version
[pluginName] can tell you the version of your Plugin and the Recommended Build
it was Built for.  
  
There are also plugins that can be used as a guiding resource that an admin
can use as a helping hand to keep plugins as well as CraftBukkit itself up to
date. These resources however are not a full replacement for doing the
research on your own as blindly updating can often cause more trouble than it
saves.  

## Updating your plugins

  
To update your plugins, simply stop your server, delete the Jar file, and
replace it with the new one. If the changelog for the plugin (usually
displayed on the plugin’s forum post) says there is a change in the config
files, make the appropriate changes before finishing and restarting your
server.

## Asking Others

  
People who have already been there done that are extremely valuable resources
for you to use. Never EVER be afraid to ask others for help! Most of the time
ex-server admins or current server admins will try to assist you as much as
they know, or try to refer you to someone who does know. If you don't know
anyone, the [Bukkit IRC Channel](/IRC) is a plethora of Admins, Plugin
Developers, and other people who know how to do what you may not!
