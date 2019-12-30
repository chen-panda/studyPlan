背景：在一些特殊情况下（例如去给客户演示项目，客户那边只有内网），maven不能从远程仓库下载依赖的jar包，也访问不了镜像仓库，这个时候就需要在无网络的情况下运行项目。

需要做的很简单，但是网上相关的文档相当少，你只需修改maven目录下conf/setting.xml文件中的两个地址便能实现在无网络的情况下运行项目。

第一步：设置maven的本地仓库地址

第二部：把镜像地址也指向本地的maven仓库地址

修改好之后的setting.xml文件如下：

```
<?xml version="1.0" encoding="UTF-8"?>
 
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
 
	<!-- 本地仓库地址 -->
	<localRepository>E:\wokesoftware\maven-repository</localRepository>
	
  <mirrors>
	 <mirror>
            <id>central</id>
            <name>central</name>
            <!-- 将镜像地址设置为本地maven地址 -->
            <url>file://E:\wokesoftware\maven-repository</url>
            <mirrorOf>*</mirrorOf>
        </mirror>
  </mirrors>
</settings>


```

要想在完成以上两步就能运行项目的前提是你已经将项目中需要依赖的jar包都下载到本地的maven仓库中，并在Eclipse中正确配置了本地maven。