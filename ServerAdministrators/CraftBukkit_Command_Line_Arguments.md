# CraftBukkit 启动脚本附加参数及说明

Craftbukkit gives you the ability from the command line to specify a wide
variety of start-up options. Below is a list of the current command line
arguments you can pass when first starting cb.jar from the command line.


<table width="100%" border="1" align="center" cellpadding="5" cellspacing="1">
<tr>
	<th scope="col">
		 Command Line Option
	</th>
	<th scope="col">
		 Shortcut
	</th>
	<th scope="col">
		 Description
	</th>
	<th scope="col">
		 Example
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
		 Shows the help menu. Following the printout, the JVM Terminates.
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
			Allows you to define the bukkit.yml settings file used during startup.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default bukkit config file is bukkit.yml
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
			Allows you to define the config file used in starting the server.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default config file is "server.properties"
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
			Allows you to define the date format used in your log files.<br/>
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
			Allows you to define the hostname or IP address to listen on.
		</p>
		<p>
			This argument is only for the IP Address, not the port.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default is located in your server.properties
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
			Allows you to define wether or not the logfile should be appended to with each startup or if it should be overidden.
		</p>
		<p>
			This argument only accepts boolean values true or false.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default value is true
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
			Allows you to define how many logs to cycle through.
		</p>
		<p>
			Log cycling begins when the maximum log size has been reached.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default number of logs is 1
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
			Allows you to define the maximum size your log file can become in number of lines.
		</p>
		<p>
			0 = unlimited
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default maximum log size is 0 (unlimited)
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
			Allows you to define the names used for your log files
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default log name is "server.log"
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
			Strips log colors when saving to the log.
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
			Disables console output entirely. Log files are still written, though.
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
			Disables the JLine console, removes the '&gt;', sets the timestamp to vanilla's and sets the language to English.
		</p>
		<p>
			This is useful for users who do not have the Visual C++ 2008 redistributable on Windows.
		</p>
		<p>
			Linux and UNIX users can safely ignore this option
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
			Disables the JLine console and removes the '&gt;'.
		</p>
		<p>
			This is useful for users who do not have the Visual C++ 2008 redistributable on Windows.
		</p>
		<p>
			Linux and UNIX users can safely ignore this option
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
			Allows a customized log4j2.xml file without modifying the CraftBukkit.jar.  log4j2.xml allows a server admin to modify the logging (latest.log) file found in MC 1.7.2 (and above).
This is useful for server admins who want to modify server log rotation, or change the location/name of the new server log.
		</p>
		<p>
			If you do not specify a path for the log4j2.xml file, it will grab the log4j2.xml file from the current working directory, NOT the server directory.
		</p>
		<p>
			Since this is technically not a CraftBukkit command line option, but rather a JVM option, the option must be added before the -jar option.
		</p>
		<p>
			Additional log4j2.xml documentation: <br/>
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
			Allows you to define wether or not the server should run in online mode.<br/>This argument only accepts a boolean answer, true or false.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default is located in your server.properties
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
			Allows you to define the plugins directory to use when starting the server.
		</p>
		<p>
			The path should be relative to the location of your current location in your system.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default plugins directory is "plugins/"
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
			Allows you to define the port number your server will listen on.
		</p>
		<p>
			This argument is only for the Port Number, not the IP Address.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default is located in your server.properties
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
			Allows you to define the number of players that are allowed to connect to your server at one time.
		</p>
		<p>
			This argument only accepts integer, or whole number, answers.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default is located in your server.properties
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
			Prints the current CraftBukkit Server and Bukkit API Versions. Similar to typing /version in-game
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
			Allows you to define the folder/directory containing your worlds. <br/> All worlds will be loaded and stored here.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default is located in bukkit.yml
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
			Allows you to define the startup world your server will use.
		</p>
		<p>
			<br/>
		</p>
		<p>
			The default is located in your server.properties
		</p>
	</td>
	<td>
		 java -jar cb.jar -w evilsephisevil
	</td>
</tr>
</table>