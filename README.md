#Mac下使用Nexus搭建Maven私服

##1 下载安装
nexus 官网地址 http://www.sonatype.org/nexus/go/
	我们可以在nexus的官网上找到它的相关介绍，下载地址是http://www.sonatype.org/nexus/go，在这里可以找到最新的版本，如果需要以前的版本，在这里也可以找到下载地址。Nexus提供了两种安装方式，一种是内嵌Jetty的bundle，只要你有JRE就能直接运行。第二种方式是WAR，你只须简单的将其发布到web容器中即可使用。为了方便就直接选用bundle版本。我下载的是：nexus-2.2-bundle.tar.gz。
	在指定的目录解压下载的文件。解压后会看到两个文件夹，分别是nexus-2.2-01和sonatype-work，前者包含了nexus的运行环境和应用程序，后者包含了你自己的配置和存储构件的地方。nexus-2.2-01/conf/nexus.properties中可以修改端口信息以及工作区的路径。

##2 启动

   进入nexus-2.2-01/bin/jsw/目录，然后根据OS的版本进入相应的目录，在linux下，运行./nexus start即启动了服务，直接运行./nexus会看到提示信息，运行./nexus console 可以以控制台方式启动nexus，方便我们观察启动时的相关工作。neuxs默认监听端口是8081，此时在浏览器中运行访问http://127.0.0.1:8081/nexus或者http://localhost:8081/nexus或者http://0.0.0.0:8081/nexus应该可以看到neuxs的界面（默认用户名：admin ，默认密码：admin123）。
   
##3 配置

   配置maven setting.xml 参考项目中的
   
   pom.xml中引入
   ```json
	 <distributionManagement>
	    <repository>
	      <id>apple-releases</id>
	      <name>apple Release Repository</name>
	      <url>http://127.0.0.1:8081/nexus/content/repositories/releases</url>
	    </repository>
	    <snapshotRepository>
	      <id>apple-snapshots</id>
	      <name>apple Snapshot Repository</name>
	      <url>http://127.0.0.1:8081/nexus/content/repositories/snapshots</url>
	    </snapshotRepository>
	  </distributionManagement>
   ```


   

