# CraftBukkit指令

这个文档罗列了所有服务器指令。这些指令无论是服务器管理员还是游戏管理员都可以使用。此外，不同于[原版服务器指令](http://www.minecraftwiki.net/wiki/SMP_Server_commands)，这里有4条扩展指令特别为CraftBukkit而设计。CraftBukkit还提供了内建的权限系统可以用于权限控制。还有一些扩展权限是由几个权限组成的权限组。

##Bukkit指令和对应的权限

<table class="wikitable" border="1">
<tr>
	<th>
		指令
	</th>
	<th>
		介绍
	</th>
	<th>
		使用方法
	</th>
	<th>
		权限
	</th>
	<th>
		权限默认
	</th>
</tr>
<tr>
	<td>
		version
	</td>
	<td>
		Gives the version number of CraftBukkit this is installed on the server.
	</td>
	<td>
		version
	</td>
	<td>
		bukkit.command.version
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		plugins
	</td>
	<td>
		Lists all installed plugins on the server.
	</td>
	<td>
		plugins
	</td>
	<td>
		bukkit.command.plugins
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		reload
	</td>
	<td>
		Stops and restarts all plugins on the server.
	</td>
	<td>
		reload
	</td>
	<td>
		bukkit.command.reload
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		timings
	</td>
	<td>
		Records timings for all plugin events.
	</td>
	<td>
		timings &lt;reset|merged|separate&gt;
	</td>
	<td>
		bukkit.command.timings
	</td>
	<td>
		Operators
	</td>
</tr>
</table>

##Default Minecraft Commands and Permissions

<table class="wikitable" border="1">
<tr>
	<th>
		Command
	</th>
	<th>
		Description
	</th>
	<th>
		Usage
	</th>
	<th>
		Bukkit Permission
	</th>
	<th>
		Mojang Permission
	</th>
	<th>
		Permission Default
	</th>
</tr>
<tr>
	<td>
		tell &lt;<i>player</i>&gt; &lt;<i>message</i>&gt;
	</td>
	<td>
		Allows the user to privately message another player.
	</td>
	<td>
		tell Notch Hey, how's it going?
	</td>
	<td>
		bukkit.command.tell
	</td>
	<td>
		minecraft.command.tell
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		kill
	</td>
	<td>
		Allows the player to kill themselves, returning to spawn (and losing items).
	</td>
	<td>
		kill
	</td>
	<td>
		bukkit.command.kill
	</td>
	<td>
		minecraft.command.kill
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		me
	</td>
	<td>
		Says a message from the player's point of view: *player1 is building a castle!
	</td>
	<td>
		me is building a castle!
	</td>
	<td>
		bukkit.command.me
	</td>
	<td>
		minecraft.command.me
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		help or&#160;?
	</td>
	<td>
		Shows a list of server commands in the console or in-game.
	</td>
	<td>
		help
	</td>
	<td>
		bukkit.command.help
	</td>
	<td>
		minecraft.command.help
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		kick &lt;<i>player</i>&gt;
	</td>
	<td>
		Removes a player from the server.
	</td>
	<td>
		kick player1
	</td>
	<td>
		bukkit.command.kick
	</td>
	<td>
		minecraft.command.kick
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		ban &lt;<i>player</i>&gt;
	</td>
	<td>
		Bans a player from the server.
	</td>
	<td>
		ban player1
	</td>
	<td>
		bukkit.command.ban.player
	</td>
	<td>
		minecraft.command.ban
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		banlist
	</td>
	<td>
		Shows the banned players.
	</td>
	<td>
		banlist
	</td>
	<td>
		bukkit.command.ban.list
	</td>
	<td>
		minecraft.command.banlist
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		pardon &lt;<i>player</i>&gt;
	</td>
	<td>
		Pardons a banned player so that they can connect again.
	</td>
	<td>
		pardon player1
	</td>
	<td>
		bukkit.command.unban.player
	</td>
	<td>
		minecraft.command.pardon
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		ban-ip &lt;<i>ip</i>&gt;
	</td>
	<td>
		Bans an IP address from the server.
	</td>
	<td>
		ban-ip 192.168.1.5
	</td>
	<td>
		bukkit.command.ban.ip
	</td>
	<td>
		minecraft.command.ban-ip
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		pardon-ip &lt;<i>ip</i>&gt;
	</td>
	<td>
		Pardons a banned IP address so that they can connect again.
	</td>
	<td>
		pardon-ip 192.168.1.5
	</td>
	<td>
		bukkit.command.unban.ip
	</td>
	<td>
		minecraft.command.pardon-ip
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		op &lt;<i>player</i>&gt;
	</td>
	<td>
		Turns a player into a server operator.
	</td>
	<td>
		op player1
	</td>
	<td>
		bukkit.command.op.give
	</td>
	<td>
		minecraft.command.op
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		deop &lt;<i>player</i>&gt;
	</td>
	<td>
		Removes server operator status from a player.
	</td>
	<td>
		deop player1
	</td>
	<td>
		bukkit.command.op.take
	</td>
	<td>
		minecraft.command.deop
	</td>
	<td>
		 Operators
	</td>
</tr>
<tr>
	<td>
		tp &lt;<i>player1</i>&gt; &lt;<i>player2</i>&gt;<br/>
		<p>
			tp &lt;<i>player1</i>&gt; &lt;<i>x</i>&gt; &lt;<i>y</i>&gt; &lt;<i>z</i>&gt;
		</p>
	</td>
	<td>
		Moves player1 to the same location as player2.
		<p>
			Moves player1 to the exact coordinates.
		</p>
	</td>
	<td>
		tp player1 player2<br/>
		<p>
			tp player1 0 70 12
		</p>
	</td>
	<td>
		bukkit.command.teleport
	</td>
	<td>
		minecraft.command.tp
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		give &lt;<i>player</i>&gt; &lt;<i>data-value</i>&gt; [<i>amount</i> [<i>damage</i>]]
	</td>
	<td>
		Gives player blocks/items blockID <i>data-value</i>. <i>amount</i> is is how many of the block/item to give (Default: 1). <i>damage</i> is the damage value of the block/item (Default: 0). <a rel="nofollow" class="external text" href="http://www.minecraftwiki.net/wiki/Data_values">Data Values</a>.
	</td>
	<td>
		give player1 267 <i>(gives player1 1 iron sword)</i><br/>give player1 3 32 <i>(gives player1 32 blocks of dirt)</i>
	</td>
	<td>
		bukkit.command.give
	</td>
	<td>
		minecraft.command.give
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		stop
	</td>
	<td>
		Gracefully stops the server (i.e. allows the server to save the worlds and lets all the plugins shut down properly).
	</td>
	<td>
		stop
	</td>
	<td>
		bukkit.command.stop
	</td>
	<td>
		minecraft.command.stop
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		save-all
	</td>
	<td>
		Forces a server-wide level save of the terrain.
	</td>
	<td>
		save-all
	</td>
	<td>
		bukkit.command.save.perform
	</td>
	<td>
		minecraft.command.save-all
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		save-off
	</td>
	<td>
		Disables automatic terrain saving (useful for backup scripts).
	</td>
	<td>
		save-off
	</td>
	<td>
		bukkit.command.save.disable
	</td>
	<td>
		minecraft.command.save-off
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		save-on
	</td>
	<td>
		Re-enables automatic terrain saving.
	</td>
	<td>
		save-on
	</td>
	<td>
		bukkit.command.save.enable
	</td>
	<td>
		minecraft.command.save-on
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		list
	</td>
	<td>
		Lists all currently connected players.
	</td>
	<td>
		list
	</td>
	<td>
		bukkit.command.list
	</td>
	<td>
		minecraft.command.list
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		say &lt;<i>message</i>&gt;
	</td>
	<td>
		Broadcasts a message to all players as the server.
	</td>
	<td>
		say Hello minecraft world!
	</td>
	<td>
		bukkit.command.say
	</td>
	<td>
		minecraft.command.say
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		whitelist &lt;<i>on</i>/<i>off</i>&gt;
	</td>
	<td>
		Enable or disable whitelisting (i.e. only listed players may join).
	</td>
	<td>
		whitelist on<br/>whitelist off
	</td>
	<td>
		bukkit.command.whitelist.enable<br/>bukkit.command.whitelist.disable
	</td>
	<td>
		minecraft.command.whitelist
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		whitelist &lt;<i>add</i>/<i>remove</i>&gt; &lt;<i>player</i>&gt;
	</td>
	<td>
		Add or remove a player from the whitelist.
	</td>
	<td>
		whitelist add Notch<br/>whitelist remove Notch
	</td>
	<td>
		bukkit.command.whitelist.add<br/>bukkit.command.whitelist.remove
	</td>
	<td>
		minecraft.command.whitelist
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		whitelist list
	</td>
	<td>
		Lists all currently whitelisted players.
	</td>
	<td>
		whitelist list
	</td>
	<td>
		bukkit.command.whitelist.list
	</td>
	<td>
		minecraft.command.whitelist
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		whitelist reload
	</td>
	<td>
		Reload the whitelist from file. Useful if you edited the file manually.
	</td>
	<td>
		whitelist reload
	</td>
	<td>
		bukkit.command.whitelist.reload
	</td>
	<td>
		minecraft.command.whitelist
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		time &lt;<i>add</i>/<i>set</i>&gt; &lt;<i>amount</i>&gt;
	</td>
	<td>
		<i>Add</i> to or <i>set</i> the world time. <i>Amount</i> may be a number between 0 and 24000, inclusive, where 0 is dawn (i.e. clock is bisected; left side is day) and 12000 is noon.
	</td>
	<td>
		time add 6000<br/>time set 0
	</td>
	<td>
		bukkit.command.time.add<br/>bukkit.command.time.set
	</td>
	<td>
		minecraft.command.time
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		gamemode &lt;0/1/2&gt; &lt;<i>player</i>&gt;
	</td>
	<td>
		Change the game mode of a player. 0 = Survival mode, 1 = Creative mode, 2 = Adventure mode.
	</td>
	<td>
		gamemode 1 Notch
	</td>
	<td>
		bukkit.command.gamemode
	</td>
	<td>
		minecraft.command.gamemode
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		xp &lt;<i>player</i>&gt; &lt;<i>amount</i>&gt;
	</td>
	<td>
		Gives the specified player a certain amount of experience.
	</td>
	<td>
		xp Notch 100
	</td>
	<td>
		bukkit.command.xp
	</td>
	<td>
		minecraft.command.xp
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		toggledownfall
	</td>
	<td>
		Turn on or off rain/snow in the current world.
	</td>
	<td>
		toggledownfall
	</td>
	<td>
		bukkit.command.toggledownfall
	</td>
	<td>
		minecraft.command.toggledownfall
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		defaultgamemode &lt;0/1/2/3&gt;
	</td>
	<td>
		Change the gamemode of new players joining the server.
	</td>
	<td>
		defaultgamemode 1
	</td>
	<td>
		bukkit.command.defaultgamemode
	</td>
	<td>
		minecraft.command.defaultgamemode
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		seed
	</td>
	<td>
		Outputs the world seed.
	</td>
	<td>
		seed
	</td>
	<td>
		bukkit.command.seed
	</td>
	<td>
		minecraft.command.seed
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		enchant &lt;<i>user</i>&gt; &lt;<i>enchant number or ID</i>&gt; &lt;<i>level</i>&gt; &lt;<i>force</i>&gt;
	</td>
	<td>
		Enchants the item in the user's hand.
	</td>
	<td>
		enchant Notch 1 1 1
	</td>
	<td>
		bukkit.command.enchant
	</td>
	<td>
		minecraft.command.enchant
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		weather &lt;<i>weather</i>&gt;
	</td>
	<td>
		Changes the weather in-game.
	</td>
	<td>
		weather clear
	</td>
	<td>
		bukkit.command.weather
	</td>
	<td>
		minecraft.command.weather
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		clear &lt;<i>user</i>&gt;
	</td>
	<td>
		Clears a user's inventory.
	</td>
	<td>
		clear Notch
	</td>
	<td>
		bukkit.command.clear
	</td>
	<td>
		minecraft.command.clear
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		difficulty &lt;<i>diff level</i>&gt;
	</td>
	<td>
		Changes the difficulty of the server.
	</td>
	<td>
		difficulty 0
	</td>
	<td>
		bukkit.command.difficulty
	</td>
	<td>
		minecraft.command.difficulty
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		spawnpoint &lt;<i>User</i>&gt; &lt;<i>x</i>&gt; &lt;<i>y</i>&gt; &lt;<i>z</i>&gt;
	</td>
	<td>
		Sets the spawnpoint of the user specified.
	</td>
	<td>
		spawnpoint Notch
	</td>
	<td>
		bukkit.command.spawnpoint
	</td>
	<td>
		minecraft.command.spawnpoint
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		gamerule
	</td>
	<td>
		Prints out the current game rules being applied to the server.
	</td>
	<td>
		gamerule
	</td>
	<td>
		bukkit.command.gamerule
	</td>
	<td>
		minecraft.command.gamerule
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		effect &lt;<i>player</i>&gt; &lt;<i>effect id</i>&gt; [<i>seconds</i>] [<i>amplifier</i>]
	</td>
	<td>
		Adds the specified effect to a player for the duration of 30 seconds or as specified by the user.
	</td>
	<td>
		effect Notch 9
	</td>
	<td>
		bukkit.command.effect
	</td>
	<td>
		minecraft.command.effect
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		setidletimeout &lt;Minutes until kick&gt;
	</td>
	<td>
		Sets the server's idle timeout
	</td>
	<td>
		setidletimeout 10
	</td>
	<td>
		bukkit.command.setidletimeout
	</td>
	<td>
		minecraft.command.setidletimeout
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		setworldspawn OR setworldspawn &lt;x&gt; &lt;y&gt; &lt;z&gt;
	</td>
	<td>
		Sets a worlds's spawn point. If no coordinates are specified, the player's coordinates will be used.
	</td>
	<td>
		setworldspawn 0 0 0
	</td>
	<td>
		bukkit.command.setworldspawn
	</td>
	<td>
		minecraft.command.setworldspawn
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		achievement give &lt;stat_name&gt; [player]
	</td>
	<td>
		Gives the specified player an achievement or changes a statistic value. Use '*' to give all achievements.
	</td>
	<td>
		achievement give * Notch
	</td>
	<td>
		bukkit.command.achievement
	</td>
	<td>
		minecraft.command.achievement
	</td>
	<td>
		Operators
	</td>
</tr>
</table>

##Additional Permissions

<table class="wikitable" border="1">
<tr>
	<th>
		Permission
	</th>
	<th>
		Description
	</th>
	<th>
		Default
	</th>
</tr>
<tr>
	<td>
		bukkit.broadcast.user
	</td>
	<td>
		Allows the user to receive user broadcasts
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		bukkit.command.plugins
	</td>
	<td>
		Allows user to look at plugins. Disables: /pl and /plugins
	</td>
	<td>
		Everybody
	</td>
</tr>
<tr>
	<td>
		bukkit.command.ban
	</td>
	<td>
		Combines the Player ban and the IP ban permissions
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		bukkit.command.unban
	</td>
	<td>
		Combines the Player Unban and IP Unban permissions.
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		bukkit.command.op
	</td>
	<td>
		Combines the Op Give and Op Take permissions.
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		bukkit.command.time
	</td>
	<td>
		Combines the Time Add and Time Set permissions.
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		bukkit.command.save
	</td>
	<td>
		Combines the Save Enable, Save Disable and Save Perform permissions.
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		bukkit.broadcast
	</td>
	<td>
		Allows the user to receive all broadcast messages.
	</td>
	<td>
		Operators
	</td>
</tr>
<tr>
	<td>
		bukkit.broadcast.admin
	</td>
	<td>
		Allows the user to receive administrative broadcasts.
	</td>
	<td>
		Operators
	</td>
</tr>
</table>