# Java分布式搭建
一步步教你搭建基于Dubbox 的分布式服务的项目架构
Dubbo是一个来自阿里巴巴的开源分布式服务框架，当当根据自身的需求，为Dubbo实现了一些新的功能，包括REST风格远程调用、Kryo/FST序列化等等。并将其命名为Dubbox。
Dubbox基于非常成熟的JBoss RestEasy框架，在dubbo中实现了REST风格（HTTP + JSON/XML）的远程调用，以显著简化企业内部的跨语言交互，同时显著简化企业对外的Open API、无线API甚至AJAX服务端等等的开发。

工具：Eclipse IDE;dubbo-2.8.4.jar；apache-maven-3.2.2;
一.JDK安装（jdk1.7）
        略
二.Eclipse安装，
        略
三.Maven安装
        3.1.1. 前往https://maven.apache.org/download.cgi 下载最新版的Maven程序：       

        3.1.2. 将文件解压到D:\Program Files\Apache\maven目录下:

        3.1.3. 新建环境变量MAVEN_HOME，赋值D:\Program Files\Apache\maven

        3.1.4. 编辑环境变量Path，追加%MAVEN_HOME%\bin\;

        3.1.5. 至此，maven已经完成了安装，我们可以通过DOS命令检查一下我们是否安装成功：

                 mvn -v

    3.2、配置Maven本地仓库

        3.2.1. 在D:\Program Files\Apache\目录下新建maven-repository文件夹，该目录用作maven的本地库。

        3.2.2. 打开D:\Program Files\Apache\maven\conf\settings.xml文件，查找下面这行代码：

        <localRepository>/path/to/local/repo</localRepository>

        localRepository节点默认是被注释掉的，需要把它移到注释之外，然后将localRepository节点的值改为我们在3.1中创建的目录D:\Program Files\Apache\maven-repository。
        3.2.3、配置多个下载仓库中心，在<mirrors>之间添加下载镜像，以便快速下载相关文件。
        
        <mirror>
                <id>alimaven</id>      
                <name>aliyun maven</name>
                <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
	        <mirrorOf>central</mirrorOf>
        </mirror>
	<mirror>
                <id>repo2</id>      
                <name>repo2 maven</name>
                <url>http://repo2.maven.org/maven2</url>
	        <mirrorOf>central</mirrorOf>
        </mirror>

        3.2.3. localRepository节点用于配置本地仓库，本地仓库其实起到了一个缓存的作用，它的默认地址是 C:\Users\用户名.m2。

        当我们从maven中获取jar包的时候，maven首先会在本地仓库中查找，如果本地仓库有则返回；如果没有则从远程仓库中获取包，并在本地库中保存。

        此外，我们在maven项目中运行mvn install，项目将会自动打包并安装到本地仓库中。

        3.2.4. 运行一下DOS命令

        mvn help:system

        如果前面的配置成功，那么D:\Program Files\Apache\maven-repository会出现一些文件。

   3.3、配置Eclipse的Maven环境

        3.3.1. Eclipse Oxygen，打开Window->Preferences->Maven->Installations，右侧点击Add。

        3.3.2. 设置maven的安装目录，然后Finish

        3.3.3. 选中刚刚添加的maven，并Apply。

        3.3.4. 打开Window->Preferences->Maven->User Settings，配置如下并Apply：

   至此，Maven的安装和配置全部结束。
