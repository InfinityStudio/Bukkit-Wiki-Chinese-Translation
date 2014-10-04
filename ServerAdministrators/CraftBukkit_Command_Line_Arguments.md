# CraftBukkit 启动脚本附加参数及说明

Craftbukkit通过启动参数的形式使启动更加的多样化。下面的这个表格列出了当前你第一次启动的时候可以向启动脚本增加的新参数。

<table width="100%" border="1" align="center" cellpadding="5" cellspacing="1">
<tr>
	<th scope="col">
		 附加参数
	</th>
	<th scope="col">
		 简写
	</th>
	<th scope="col">
		 介绍
	</th>
	<th scope="col">
		 例子
	</th>
</tr>
<tr>
	<td>
		 --help
	</td>
	<td>
		 -?
	</td>
	<td>
		 在控制台中输出帮助菜单。
	</td>
	<td>
		 java -jar cb.jar -?
	</td>
</tr>
<tr>
	<td>
		 --bukkit-settings &lt;file&gt;.yml
	</td>
	<td>
		 -b &lt;file&gt;.yml
	</td>
	<td>
		<p>
			允许自定义CraftBukkit使用替代bukkit.yml的文件名
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的bukkit配置文件名是bukkit.yml
		</p>
	</td>
	<td>
		 java -jar cb.jar -b potatos.yml
	</td>
</tr>
<tr>
	<td>
		 --config &lt;config file&gt;
	</td>
	<td>
		 -c &lt;config file&gt;.yml
	</td>
	<td>
		<p>
			允许自定义CraftBukkit使用替代server.peoperties的文件名
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的服务器配置文件名是"server.properties"
		</p>
	</td>
	<td>
		 java -jar cb.jar --config potatos.properties
	</td>
</tr>
<tr>
	<td>
		 --date-format &lt;definition&gt;
	</td>
	<td>
		 -d &lt;definition&gt;
	</td>
	<td>
		<p>
			允许你自定义日志文件的日期格式<br/>
		</p>
	</td>
	<td>
		<br/>
	</td>
</tr>
<tr>
	<td>
		 --host &lt;IP Address&gt;<br/>--server-ip &lt;IP Address&gt;
	</td>
	<td>
		 -h &lt;IP Address&gt;
	</td>
	<td>
		<p>
			允许你自定义服务器名称和监听的IP地址
		</p>
		<p>
			这个参数只能定义IP地址而无法定义端口
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的地址取决于server.properties中的设置
		</p>
	</td>
	<td>
		 java -jar cb.jar -h www.potatos.com
	</td>
</tr>
<tr>
	<td>
		 --log-append &lt;true/false&gt;
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			允许你定义日志文件行为。日志文件在每次启动后新添新的日志文件或者覆盖上次的日志文件
		</p>
		<p>
			参数只接受true或者false
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的值是true。也就是说日志将会以添加的方式记录。
		</p>
	</td>
	<td>
		 java -jar cb.jar --log-append false
	</td>
</tr>
<tr>
	<td>
		 --log-count &lt;number&gt;
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			允许你定义一次日志记录周期将有多少条日志
		</p>
		<p>
			新的日志周期开始于原周期达到了最大日志数量
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的日志记录周期是1，也就是说每一条日志都会实时的写入文件
		</p>
	</td>
	<td>
		 java -jar cb.jar --log-count 10
	</td>
</tr>
<tr>
	<td>
		 --log-limit &lt;# of lines&gt;
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			允许你定义日志文件的最大行数
		</p>
		<p>
			0 = 无限
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的最大行数是 0 (无限)
		</p>
	</td>
	<td>
		 java -jar cb.jar --log-limit 1337
	</td>
</tr>
<tr>
	<td>
		 --log-pattern &lt;name&gt;
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			允许你定义日志文件的文件名
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的日志文件名是"server.log"
		</p>
	</td>
	<td>
		 java -jar cb.jar --log-pattern potatos.log
	</td>
</tr>
<tr>
	<td>
		 --log-strip-color&#160;
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			允许在日志文件中记录控制台颜色
		</p>
	</td>
	<td>
		 java -jar cb.jar --log-strip-color
	</td>
</tr>
<tr>
	<td>
		 --noconsole
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			完全关闭控制台输出，但是日志文件会继续写入。
		</p>
	</td>
	<td>
		 java -jar cb.jar --noconsole
	</td>
</tr>
<tr>
	<td>
		 --nojline
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			关闭JLine控制台，移除'&gt;'，设置时间戳为原版服务器的时间戳并定义语言为英文
		</p>
		<p>
			这对于那些没有安装C++ 2008 redistributable的Windows用户非常有用
		</p>
		<p>
			Linux和UNIX用户可以忽略这一条
		</p>
	</td>
	<td>
		 java -jar cb.jar --nojline
	</td>
</tr>
<tr>
	<td>
		 -Djline.terminal=jline.UnsupportedTerminal
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			关闭JLine控制台，移除'&gt;'，设置时间戳为原版服务器的时间戳并定义语言为英文
		</p>
		<p>
			这对于那些没有安装C++ 2008 redistributable的Windows用户非常有用
		</p>
		<p>
			Linux和UNIX用户可以忽略这一条
		</p>
	</td>
	<td>
		 java -jar cb.jar -Djline.terminal=jline.UnsupportedTerminal
	</td>
</tr>
<tr>
	<td>
		 -Dlog4j.configurationFile=log4j2.xml
	</td>
	<td>
		<br/>
	</td>
	<td>
		<p>
			 允许在不修改CraftBukkit.jar的情况下使用自定义的log4j2.xml。log4j2.xml允许服务器管理员修改日志文件的格式等相关信息。
		</p>
		<p>
			如果不指定log4j2.xml文件的位置，服务器在启动的时候将会使用当前文件夹内的的log4j2.xml而不是服务端文件夹。
			If you do not specify a path for the log4j2.xml file, it will grab the log4j2.xml file from the current working directory, NOT the server directory.
		</p>
		<p>
			自从这种技术不再是CraftBukkit控制台的选项而是JVM的选项，所以这个参数必须添加到-jar参数前。
		</p>
		<p>
			额外的log4j2.xml文档: <br/>
			<a rel="nofollow" class="external free" href="http://logging.apache.org/log4j/2.x/manual/appenders.html#RandomAccessFileAppender">http://logging.apache.org/log4j/2.x/manual/appenders.html#RandomAccessFileAppender</a><br/>
			<a rel="nofollow" class="external free" href="http://logging.apache.org/log4j/2.x/manual/layouts.html#PatternLayout">http://logging.apache.org/log4j/2.x/manual/layouts.html#PatternLayout</a>
		</p>
		<p>
			Default log4j2.xml file: <br/>
			<a rel="nofollow" class="external free" href="https://raw.github.com/Bukkit/CraftBukkit/master/src/main/resources/log4j2.xml">https://raw.github.com/Bukkit/CraftBukkit/master/src/main/resources/log4j2.xml</a>
		</p>
	</td>
	<td>
		 java -Dlog4j.configurationFile=/opt/server/log4j2.xml -jar cb.jar
	</td>
</tr>
<tr>
	<td>
		 --online-mode &lt;true/false&gt;
	</td>
	<td>
		 -o &lt;true/false&gt;
	</td>
	<td>
		<p>
			允许你设置服务器运行在”在线模式“还是”离线模式“。<br/>这个变量只接受布尔值，true或者false
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认值取决于server.properties中的对应值
		</p>
	</td>
	<td>
		 java -jar cb.jar -o true
	</td>
</tr>
<tr>
	<td>
		 --plugins &lt;directory&gt;
	</td>
	<td>
		 -P &lt;directrory&gt;
	</td>
	<td>
		<p>
			允许你设置服务端启动时的默认插件文件夹
		</p>
		<p>
			目标路径必须是当前文件夹的子文件夹
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认的位置是"plugins/"
		</p>
	</td>
	<td>
		 java -jar cb.jar -P notplugins/
	</td>
</tr>
<tr>
	<td>
		 --port &lt;port number&gt;<br/>--server-port &lt;port number&gt;
	</td>
	<td>
		 -p &lt;port number&gt;
	</td>
	<td>
		<p>
			允许你定义服务器监听的端口号
		</p>
		<p>
			这个参数只能定义端口号，无法定义IP地址。
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认值取决于server.properties中的对应值。
		</p>
	</td>
	<td>
		 java -jar cb.jar -p 1337
		<p>
			<br/>
		</p>
	</td>
</tr>
<tr>
	<td>
		 --size &lt;# of players&gt;<br/>--max-players &lt;# of players&gt;
	</td>
	<td>
		 -s &lt;# of players&gt;
	</td>
	<td>
		<p>
			允许你设置可以链接服务器的最大玩家数量。
		</p>
		<p>
			参数只接受整型值
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认值取决于server.properties中的对应值。
		</p>
	</td>
	<td>
		 java -jar cb.jar -s 36
	</td>
</tr>
<tr>
	<td>
		 --version
	</td>
	<td>
		 -v
	</td>
	<td>
		<p>
			在屏幕输出当前的CraftBukkit和Bukkit API版本。类似于在游戏中输入/version。
		</p>
		<p>
			Following the printout, the JVM terminates.
		</p>
	</td>
	<td>
		 java -jar cb.jar -v
	</td>
</tr>
<tr>
	<td>
		 --world-dir &lt;worlds dir&gt;<br/>--universe &lt;worlds dir&gt;
	</td>
	<td>
		 -W  &lt;worlds dir&gt;
	</td>
	<td>
		<p>
			允许你设置地图文件的文件夹名字。<br/> 所有世界的地图都将从那个文件夹读取。
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认值取决于bukkit.yml中的对应值
		</p>
	</td>
	<td>
		 java -jar cb.jar -W C:/minecraft/worlds
	</td>
</tr>
<tr>
	<td>
		 --world &lt;world name&gt;<br/>--level-name &lt;world name&gt;
	</td>
	<td>
		 -w &lt;world name&gt;
	</td>
	<td>
		<p>
			允许你设置服务端用于启动的地图文件夹名字。
		</p>
		<p>
			<br/>
		</p>
		<p>
			默认值取决于server.properties中的对应值
		</p>
	</td>
	<td>
		 java -jar cb.jar -w evilsephisevil
	</td>
</tr>
</table>