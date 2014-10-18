#  Setting Up Your Workspace

This page will go through some of the tools that you will need to use to work
with Bukkit and building Bukkit plugins.

## Contents

  * 1 Tools
    * 1.1 Java Development Kit
      * 1.1.1 Which version of the JDK?
      * 1.1.2 64-bit (x64) or 32-bit (x86)?
    * 1.2 Git
      * 1.2.1 Using Git
        * 1.2.1.1 GitHub
    * 1.3 Apache Maven
      * 1.3.1 Using Maven
    * 1.4 Integrated Development Environments
      * 1.4.1 Eclipse
      * 1.4.2 NetBeans
      * 1.4.3 IntelliJ IDEA
  * 2 Where To From Here

# Tools

There is some developer choice when it comes to what you use to build your
software, however there are some key tools every developer needs. Even if you
only want to make plugins, there are some tools that will make your job
easier, and if you to go open source, easier for everyone who helps you!

## Java Development Kit

A JDK (Java Development Kit) is required to compile Java for use in the JRE
(Java Runtime Environment). The latest version of the JDK is available from
the [Oracle Technology
Network](http://www.oracle.com/technetwork/java/javase/downloads/index.html).

### Which version of the JDK?

There are multiple versions of Java, and consequently, multiple versions of
the JDK. Both Bukkit and Minecraft are now compiled for Java 6. Most Bukkit
servers are running Java 6, but a few run Java 7. Generally, newer versions of
the JDK can target older Java versions, however, by default they target their
own version. Programs and plugins compiled with a new version of Java are not
compatible with older versions of the JRE, attempting to run such a plugin
results in a [UnsupportedClassVersionError](http://docs.oracle.com/javase/1.5.
0/docs/api/index.html?java/lang/UnsupportedClassVersionError.html). In
practice, it is common to use the JDK version that corresponds with your
runtime environment.

### 64-bit (x64) or 32-bit (x86)?

Unless your computer is not capable of running 64-bit software, you should use
a 64-bit (x64) JDK. The rest of the development environment will need to match
the version of the JDK you have installed. On 64-bit systems it is possible to
have both 64-bit and 32-bit JDKs installed at the same time.

##Git

![git](http://hydra-media.cursecdn.com/wiki.bukkit.org/thumb/2/29/Git-Logo-
2Color.png/40px-Git-Logo-2Color.png?version=03ffd9ff8306dfaf62725ef54b60f1e5)
is a distributed version control system. The Bukkit Project manages all its
code through Git. Git allows the lone developer to keep track of their work
and different developers to collaborate on work, tracking all changes that
were made and by whom. It is very powerful, and consequently can be a little
difficult to use sometimes. The latest version of git can be found on
[here](http://git-scm.com/download) on the git-scm site.

### Using Git

Detailed instructions for installing and using git can be found in the [Pro
Git](http://git-scm.com/book) book on git-scm.

#### GitHub

[GitHub](https://github.com) is a code sharing website, and hosts the source
code of the Bukkit Project. Bukkit Projects can be cloned from our repository
found at [github.com/Bukkit](http://github.com/Bukkit).

Sharing of code works both ways - you can download shared code, but you can
also share yours with the world. This is a great idea in this open community,
as it allows others to help you with your project, or even develop new
features for your plugins! If you intend to contribute to the Bukkit Project
you must be willing to share your code. Additional instructions for using
GitHub can be found at [GitHub:Help](https://help.github.com/)

## Apache Maven

[Apache Maven](http://maven.apache.org) is a tool that the Bukkit Project uses
to manage building our code. The latest version of Maven can be found on the
[here](http://maven.apache.org/download.html) on the Apache Maven site.

### Using Maven

Additional instructions for installing and using Maven can be found
[here](http://maven.apache.org/guides/getting-started/maven-in-five-
minutes.html) on the maven site.

Once installed, Maven should be utilised to compile Bukkit and CraftBukkit.
Refer to the respective README files in the repositories for instructions.

## Integrated Development Environments

The IDE (Intergraded Development Environment) is a program you can use to
compile and debug your plugins. An IDE is an optional piece of the developer
tool chain. It is possible to use notepad (or its equivalent) and produce a
working a plugin. An IDE however, makes the life of a developer much easier by
integrating powerful tools, providing syntax highlighting, and error checking.
The choice of which IDE to use is yours to make!

### Eclipse

The [Eclipse IDE](http://www.eclipse.org/) is a popular choice among plugin
developers. The latest version, Eclipse Kepler (4.3.1), can be found
[here](http://www.eclipse.org/downloads/packages/) on the eclipse site. Plugin
developers should download the **Eclipse IDE for Java Developers**. Eclipse
provides Maven integration by means of the m2Eclipse plugin, Git integration
with by mean of the eGit plugin. Additionally, the
[YEdit](http://code.google.com/p/yedit/) plugin can be installed to provide a
YAML editor.

     _For general Eclipse IDE usage please refer to the [Eclipse documentaiton](http://www.eclipse.org/documentation/)._
     _For Maven integration usage please refer to the [m2eclipse documentation](http://www.sonatype.org/m2eclipse/)._
     _For Git integration usage please refer to the [eGit documentaiton](http://www.eclipse.org/egit/documentation/)._

### NetBeans

The [Netbeans IDE](http://netbeans.org/) is developed by Oracle. The latest
version, 7.3, can be found [here](http://netbeans.org/downloads/) on the
Netbeans site. Plugin developers should download the **Netbeans Java SE
bundle**. Netbeans provides native integration with Maven and Git integration
by means of a Git plugin.

     _For usage instructions please refer to the [Netbeans documentation](http://netbeans.org/kb/index.html)._

### IntelliJ IDEA

[IntelliJ IDEA](http://www.jetbrains.com/idea/) is another popular IDE. The
latest version, 13, can be found
[here](http://www.jetbrains.com/idea/download/index.html) on the IntelliJ
site. Plugin developers should download the **Community Edition**. IntelliJ
provides native integration with Maven and Git.

     _For usage instructions please refer to the [IntelliJ documentation](http://www.jetbrains.com/idea/documentation/index.jsp)._

# Where To From Here

There is lots more involved in actually developing and testing your code,
however hopefully you now have the tools to get started. If you find any
particularly useful tutorials make sure to link them here!

It is suggested that you start with [Plugin Tutorial](/Plugin_Tutorial).