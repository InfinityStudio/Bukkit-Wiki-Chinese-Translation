#  Administering A Craftbukkit Server

Opening Notes
This tutorial is for current Craftbukkit Server admins and aspiring server
admins. Whether you own the place, or are simply running the show (or even a
little of both) this tutorial is meant to provide you with a set list of
guidelines and valuable resources to running a successful server. Everything
from the grits and gravy, to the day to day handling of yourself and your
server.

Alright Let’s get into it from ground Zero!

## Contents

  * 1 Section 1: Ground Breaking
    * 1.1 “Vanilla” Minecraft and “Modified” Minecraft Servers
    * 1.2 The Bukkit Project
    * 1.3 The Hosting Plans
    * 1.4 CraftBukkit or Bukkit?
    * 1.5 Pick your Operating System, Memory, and RAM!
    * 1.6 Pricing
  * 2 Section 2: The Community
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
  * 3 Section 3: Keeping it Rolling
    * 3.1 Help! Minecraft Updated!
    * 3.2 Are my plugins updated? How can I tell?
    * 3.3 Updating your plugins
    * 3.4 Asking Others

# Section 1: Ground Breaking

This section is meant to introduce you to the differences between a few
simple, but need to know basics:

  1. The difference between “Vanilla” and “Modified” Servers.
  2. What is the Bukkit Project?
  3. The differences between a Game Hosting Plan and a Freeform Plan (VDS, VPS, or Dedicated Hardware)

Really this section is the gritty “Where do I want to start my adventure?”
portion!

##“Vanilla” Minecraft and “Modified” Minecraft Servers

The first bit you need to realize is the difference between “Vanilla” flavored
Minecraft Servers and “Modified” Minecraft Servers, such as CraftBukkit.
Really, these terms can be applied to any video game and can simply confuse
someone who is brand new to the scene so it’s imperative that we talk about it
first. A “Vanilla” Minecraft Server is the minecraft_server.jar file you
download from <http://www.minecraft.net/> without any modifications,
tampering, or additions on in any way. In a sense, it’s Minecraft SMP in its
purest form: unaltered and vulnerable; thats what most server owners are
afraid of. Thanks to the addition of “griefers” to the Minecraft community and
a load of other issues, Vanilla servers are seen as gaping targets for every
type of mischief and discord to happen. It really gets under the skin of
anyone who runs one because you have to constantly keep an eye on it to make
sure nothing goes wrong. This is where “Modified” servers come into play; not
just CraftBukkit, but hundreds of Minecraft players feel the need to modify
the original code to better suit servers and the growing concerns of the
administators running them. Modified servers mix it up to better secure or
improve on the current gameplay mechanics of the Minecraft Multiplayer server.

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

