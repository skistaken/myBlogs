# 绿色版JDK制作

使用官方exe版本的JDK安装包制作绿色便携版JDK

1. 下载官方JDK安装包

2. 使用7-zip将jdk.exe文件打开

3. 将7-zip打开的文件中此目录下（下面以jdk1.8为例）的tools.zip文件解压出来（这就是jdk安装完之后的程序目录）

   ` \jdk-8u161-windows-x64.exe\.rsrc\1033\JAVA_CAB10\111\tools.zip\ `

4. 以管理员身份运行cmd，进入第3步中解压出来的目录中，执行下面的命令（用upack200这个程序将*.pack文件解压为.jar文件）

   `for /r %x in (*.pack) do .\bin\unpack200 -r "%x" "%~dx%~px%~nx.jar"`

5. 解压之后至此JDK绿色版制作完毕。可以在windows平台任意移植，需要用哪一个jdk就配置相应的环境变量即可。

   

   ---

   

tips：

​	JDK环境变量的配置：

```
JAVA_HOME = D:\JDK\jdk1.8_64bit
Path = %JAVA_HOME%\bin;%JAVA_HOME%\jre\lib
CLASSPATH = .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
```

​	最简配置：

```
JAVA_HOME = D:\JDK\jdk1.8_64bit
Path = %JAVA_HOME%\bin
```

​	jdk1.5之后不需要配置classpath了。

- 在没有配置CLASSPATH环境变量时，java命令在找class文件时是默认在当前目录下寻找的。
- 配置过CLASSPATH环境后，java命令是按照CLASSPATH变量中的路径来的寻找class文件的，这就是为什么CLASSPATH变量中配置没有当前目录时，即使当前目录中有class文件，java命令仍然不能正常运行的原因。


