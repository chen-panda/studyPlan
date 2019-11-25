# 								git操作手册

腾讯课堂 ： https://ke.qq.com/course/304010?taid=2213613259760522&tuin=3a91c9ec 

```
分布式版本控制 	git
集中式版本控制		svn cvs

gitHub(个人)/gitLab（公司）

git三种状态
已修改（modified）
已暂存（staged）
已提交（commited）




```



### 一、配置Git本地  邮箱 用户名（三种方式）

#### 1、git config --system（推荐使用，给当前用户一次性设置）

#### 	  git config --system --unset user.name (删除用户名)

#### 	  git config --system --unset user.email(删除邮箱)（其他两种方式同上）

```
	git config --system user.email  "m13476065293@163.com"    (配置邮箱)
	git config --system user.name  "chenyu"  (配置用户名)
	设置后在c/user/administrator/.gitconfig中可以查看
```

#### 2、git config --global（基本不用，给整个计算机一次性设置）

```
	git config --global user.email  "m13476065293@163.com"    (配置邮箱)
	git config --global user.name  "chenyu"  (配置用户名)
```

#### 3、git config --local（给当前项目一次性设置）

```
	git config --local user.email  "m13476065293@163.com"    (配置邮箱)
	git config --local user.name  "chenyu"  (配置用户名)
	配置后在当前项目.git/config中可以查看
```

#### 二、linux基本命令

	1、新建文件 使用 touch 命令
		touch world.txt
	2、 ctrl + a 回到该行首位 	
		ctrl + e 回到该行尾位
		ctrl + c 放弃当前行 直接到下一行
	3、覆盖当前文件中的内容
		echo 'world' > hello.txt
	4、删除命令 （删除当前目录及以下的所欲子目录）
		rm -rf (文件名)
	5、清屏 
		clear 或者 ctrl + l


#### 二、操作

?	1、如果某个文件已提交，并且对其进行了修改，可以放弃修改还原到已提交的状态

```
	git checkout -- hello.txt(需要回退的文件)
```

?	2、暂存区 -> 工作区（两种方法）

```
	第一种方式：  git reset head world.txt(文件名)
	第二种方式：  git rm --cached
	
```

?	3、 删除已提交的文件 （两种）

```
	第一种：通过git rm （删除之后的文件或内容会被放到暂存区，直接在 git commit 可将文件彻底删除）
	git rm hello.txt(文件名)
	如果需要彻底删除 需要将刚才删除的操作再提交一下
	
	第二种：通过操作系统将文件删除 （删除之后的文件将会回到工作区，需要先git add提交到暂存区，再git commit 到对象区，才能进行测地删除）
	
```

?	4、撤销刚才的删除（吃后悔药）

```
	撤回刚才的删除 （两步）
	1、先将刚才的删除 回退到工作区
		git reset head hello.txt
	2、再讲刚才的文件checkout 
		git checkout hello.txt
```

?	5、重命名（move）（ 重命名涉及到两个文件，源文件和新文件）

```
	git mv hello.txt hello2.txt
	
```

?	6、注释重写（重写提交说明）

```
	将最后一次的提交注释进行修正
	git commit --amend -m "修正"
	
```

?	7、忽略文件（.git）

```
	新建忽略文件：gitignore
	在文件中设置所需要哦忽略的文件(例：a.properties 或使用通配符 直接用 *.properties)
	也可以设置不需忽略的文件 (例：!b.properties)
	
	dir/:忽略dir目录中的所有文件
	dir/*txt 
	dir/*/*.txt 忽略 dir/abc/a.txt   dir/xya/a.txt,不能忽略 dir/xyz/123/a.txt
	dir/**/*.txt 忽略任意级别目录
	
```

?	8、分支	

```
	1、查看分支 git branch 
	2、创建分支 git branch new_branch
	3、切换分支 git checkout 分支名
	4、删除分支 git branch -d 分支名(两种情况下不能删除)
		1、未合并分支不能删除
		2、如果现在在所需删除分支下也不能删除，必须切到其他分之下才行
		如果需要强行删除（小d 变成大写D ）
		git branch -D 分支名
	5、创建并切换到新分支
		git checkout -b new_branch (分支名)
	细节：	
		如果在分支A中进行了写操作，但此操作局限在工作区中进行（没add commit）。在master中能	  够看到该操作。如果分支A中进行了写操作，进行了commit（对象区），则master中无法观察到此文       件。
		如果在新分支中进行了写操作，但此操作局限在工作区中进行（没add commit）。删除分支A 是	可以成功的。
	6、查看所有分支最近一次提交的记录（sha1值（类似uuid））
    	git branch -v
```

9、分支合并与冲突（上次学习到 https://ke.qq.com/course/404757?taid=3417389513714965&tuin=3a91c9ec ）





配置免密钥登录：在本地生成一个ssh key发送到远程仓库1、先在本地生成ssh：ssh-keygen -t rsa -C m13476065293@163.com 一直回车 知道生成ssh key2、发送给远程github -settings -SSH and .... - New SSH - title 任意、key中输入刚才在本地生成的ssh（将本地生成的id_rsa.pub内的内容如知道远程key中）3、测试连通性：ssh -T git@github.com  回车 如果有提示输入yes/no 输入yes如果本地和远程成功通信，则可以在/.ssh 目录中发现known_hosts文件创建项目4.本地新建一个项目         在项目根路径下输入 git init在远程新建一个项目new -建立项目 生成 项目ssh 路径本地项目- 远程项目关联git remote add oragin git@github.com:chen-panda/mygitremote.git （  项目ssh地址）第一次发布项目：    git  add .  //  文件-暂存区    git commit -m "注释内容" // 暂存区 -本地分支（默认master）    git push -u origin master     第一次提交要使用 -u 远程项目clone到本地    git clone git@github.com:chen-panda/mygitremote.git项目提交（本地-远程）（当前目录中右键 git bash）git  add .git commit -m "提交到分支"git push origin master    //不用使用-u更新（远程-本地）git pullEclipse 中操作git （Egit）：目前eclipse中都默认支持git ，如果不支持，可以到eclipse 扩展中下载二git、1、在git ——》configuration中 设置 邮箱，用户名2、在general  -network -ssh2选中Eclipse 第一次发布share project add to index commit将项目推送到远程commit时：commit and push 和 commit 按钮的区别：commit按钮：不能单独Push某一个文件，只能push整个项目commit and push：可以单独Push某一个文件eclipse 中更新team -remote - pullgit冲突的解决发现冲突：进入同步视图  右键  -- team  -- synchronized ...1、add to index 2、commit 到本地分支  commit3、更新服务端的内容到本地 pull4、修改冲突：直接修改  或者 merge tool --> 已经修复冲突git多人开发  团队协作开发github 中 该项目  -setting增加合作者： Collaborators 加入 合作者：github 全名或邮箱发送邀请链接合作伙伴：打开该链接、接受邀请 git 删除本地分支和远程分支1、查看删除前后的分支 命令行 :git branch -a2、 删除本地分支　git branch -d 分支名3、删除远程分支　　　　 命令行 :git push origin –delete 分支名 
通过tag方式管理项目：
 1、初始化git仓库:  git init
 2、添加暂缓区：git add .    git commit -m
3、远程git 创建仓库 
4、本地和远程仓库关联   git remote add origin 仓库地址
5、推送到远程分支    git push -u origin master

知识点一：
1、先将代码提交到本地
2、打包：git tag 知识点一

3、查看提交日志   git log
4、回退版本  git reset 版本号 不需要全部复制（已推送到远程仓库的时候）
       git reset --hard 版本号（如果没有提交远程仓库，也可以通过--hard 强制回退版本）
5、如果项目中文件有个M 可以执行  git status 

知识点二：
1、添加   git add .
2、git commit -m “知识点二”
3、git tag 知识点二

查看本地所有tag
git tag

将tag推送到远程分支
git push --tags
