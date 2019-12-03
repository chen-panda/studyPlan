# 							linux入门手册

## 一、linux基本命令

1、通过linux连接虚拟机

```
		ssh root@ssh192.168.160.68
```

2、linux 可以通过type 可以来区分内部命令和外部命令 通过cat 可以查看可执行文件内容，通过file  可以查看文件类型，通过whereis可以查看某一命令的可执行文件路径

```
cd 		可以执行切换目录
type ifconfig 		可以查看该命令（ifconfig）是内部命令还是外部命令
cat ifconfig		可以查看该命令（ifconfig）的可执行文件内容
file ifconfig		可以查看该命令（ifconfig）的可执行文件的类型
whereis	ifconfig	可以查看该命令（ifconfig）的可执行文件的路径
```

3、基本命令

```
ctrl + l 或（clear）		清屏
echo $PATH 				  查看环境变量


```

