# 							linux入门手册

## 一、linux下jdk的安装（两种方式）

### 第一种：使用yum方式安装jdk（推荐）

1.查看yum中管理的可用的JDK软件包列表：

```
		yum search java | grep -i --color JDK
```

![image-20191203110535458](C:\Users\98263\AppData\Roaming\Typora\typora-user-images\image-20191203110535458.png)

 2.选择合适版本，安装jdk，本人选择的是java-1.8.0-openjdk-devel.x86_64 

```
 yum install java-1.8.0-openjdk-devel.x86_64 
```

![image-20191203110615493](C:\Users\98263\AppData\Roaming\Typora\typora-user-images\image-20191203110615493.png)

3配置环境变量，打开etc文件下profile

```
vi  /etc/profile
在文件内添加

export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.71-2.b15.el7_2.x86_64
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin

```

4、保存关闭后，执行，让配置生效：

source  /etc/profile

5、然后分别输入下面命令确认jdk是否安装成功：

![image-20191203110911179](C:\Users\98263\AppData\Roaming\Typora\typora-user-images\image-20191203110911179.png)

![image-20191203110921077](C:\Users\98263\AppData\Roaming\Typora\typora-user-images\image-20191203110921077.png)

![image-20191203110935575](C:\Users\98263\AppData\Roaming\Typora\typora-user-images\image-20191203110935575.png)

## 第二种：直接官网下载压缩包进行安装

1.下载jdk8

登录网址：http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
选择对应jdk版本下载。（可在Windows下下载完成后，通过文件夹共享到Linux上）

2. 登录Linux，切换到root用户
su root 获取root用户权限，当前工作目录不变(需要root密码)
或
sudo -i 不需要root密码直接切换成root（需要当前用户密码）

3. 在usr目录下建立java安装目录
cd /usr


mkdir java

4.将jdk-8u60-linux-x64.tar.gz拷贝到java目录下
cp /mnt/hgfs/linux/jdk-8u60-linux-x64.tar.gz /usr/java/

5.解压jdk到当前目录
tar -zxvf jdk-8u60-linux-x64.tar.gz


得到文件夹 jdk1.8.0_60

6.安装完毕为他建立一个链接以节省目录长度
(我没用这一步)
ln -s /usr/java/jdk1.8.0_60/ /usr/jdk

7.编辑配置文件，配置环境变量
vim /etc/profile

添加如下内容：JAVA_HOME根据实际目录来
JAVA_HOME=/usr/java/jdk1.8.0_60
CLASSPATH=$JAVA_HOME/lib/
PATH=$PATH:$JAVA_HOME/bin
export PATH JAVA_HOME CLASSPATH

8.重启机器或执行命令 ：

source /etc/profile


sudo shutdown -r now

9.查看安装情况

java -version

java version "1.8.0_60"
Java(TM) SE Runtime Environment (build 1.8.0_60-b27)
Java HotSpot(TM) Client VM (build 25.60-b23, mixed mode)
————————————————
版权声明：本文为CSDN博主「CD_GodBo」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/u013268969/article/details/82115895