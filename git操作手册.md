# 								git�����ֲ�

��Ѷ���� �� https://ke.qq.com/course/304010?taid=2213613259760522&tuin=3a91c9ec 

```
�ֲ�ʽ�汾���� 	git
����ʽ�汾����		svn cvs

gitHub(����)/gitLab����˾��

git����״̬
���޸ģ�modified��
���ݴ棨staged��
���ύ��commited��




```



### һ������Git����  ���� �û��������ַ�ʽ��

#### 1��git config --system���Ƽ�ʹ�ã�����ǰ�û�һ�������ã�

#### 	  git config --system --unset user.name (ɾ���û���)

#### 	  git config --system --unset user.email(ɾ������)���������ַ�ʽͬ�ϣ�

```
	git config --system user.email  "m13476065293@163.com"    (��������)
	git config --system user.name  "chenyu"  (�����û���)
	���ú���c/user/administrator/.gitconfig�п��Բ鿴
```

#### 2��git config --global���������ã������������һ�������ã�

```
	git config --global user.email  "m13476065293@163.com"    (��������)
	git config --global user.name  "chenyu"  (�����û���)
```

#### 3��git config --local������ǰ��Ŀһ�������ã�

```
	git config --local user.email  "m13476065293@163.com"    (��������)
	git config --local user.name  "chenyu"  (�����û���)
	���ú��ڵ�ǰ��Ŀ.git/config�п��Բ鿴
```

#### ����linux��������

	1���½��ļ� ʹ�� touch ����
		touch world.txt
	2�� ctrl + a �ص�������λ 	
		ctrl + e �ص�����βλ
		ctrl + c ������ǰ�� ֱ�ӵ���һ��
	3�����ǵ�ǰ�ļ��е�����
		echo 'world' > hello.txt
	4��ɾ������ ��ɾ����ǰĿ¼�����µ�������Ŀ¼��
		rm -rf (�ļ���)
	5������ 
		clear ���� ctrl + l


#### ��������

?	1�����ĳ���ļ����ύ�����Ҷ���������޸ģ����Է����޸Ļ�ԭ�����ύ��״̬

```
	git checkout -- hello.txt(��Ҫ���˵��ļ�)
```

?	2���ݴ��� -> �����������ַ�����

```
	��һ�ַ�ʽ��  git reset head world.txt(�ļ���)
	�ڶ��ַ�ʽ��  git rm --cached
	
```

?	3�� ɾ�����ύ���ļ� �����֣�

```
	��һ�֣�ͨ��git rm ��ɾ��֮����ļ������ݻᱻ�ŵ��ݴ�����ֱ���� git commit �ɽ��ļ�����ɾ����
	git rm hello.txt(�ļ���)
	�����Ҫ����ɾ�� ��Ҫ���ղ�ɾ���Ĳ������ύһ��
	
	�ڶ��֣�ͨ������ϵͳ���ļ�ɾ�� ��ɾ��֮����ļ�����ص�����������Ҫ��git add�ύ���ݴ�������git commit �������������ܽ��в��ɾ����
	
```

?	4�������ղŵ�ɾ�����Ժ��ҩ��

```
	���ظղŵ�ɾ�� ��������
	1���Ƚ��ղŵ�ɾ�� ���˵�������
		git reset head hello.txt
	2���ٽ��ղŵ��ļ�checkout 
		git checkout hello.txt
```

?	5����������move���� �������漰�������ļ���Դ�ļ������ļ���

```
	git mv hello.txt hello2.txt
	
```

?	6��ע����д����д�ύ˵����

```
	�����һ�ε��ύע�ͽ�������
	git commit --amend -m "����"
	
```

?	7�������ļ���.git��

```
	�½������ļ���gitignore
	���ļ�����������ҪŶ���Ե��ļ�(����a.properties ��ʹ��ͨ��� ֱ���� *.properties)
	Ҳ�������ò�����Ե��ļ� (����!b.properties)
	
	dir/:����dirĿ¼�е������ļ�
	dir/*txt 
	dir/*/*.txt ���� dir/abc/a.txt   dir/xya/a.txt,���ܺ��� dir/xyz/123/a.txt
	dir/**/*.txt �������⼶��Ŀ¼
	
```

?	8����֧	

```
	1���鿴��֧ git branch 
	2��������֧ git branch new_branch
	3���л���֧ git checkout ��֧��
	4��ɾ����֧ git branch -d ��֧��(��������²���ɾ��)
		1��δ�ϲ���֧����ɾ��
		2���������������ɾ����֧��Ҳ����ɾ���������е�������֮�²���
		�����Ҫǿ��ɾ����Сd ��ɴ�дD ��
		git branch -D ��֧��
	5���������л����·�֧
		git checkout -b new_branch (��֧��)
	ϸ�ڣ�	
		����ڷ�֧A�н�����д���������˲��������ڹ������н��У�ûadd commit������master����	  �������ò����������֧A�н�����д������������commit��������������master���޷��۲쵽����       ����
		������·�֧�н�����д���������˲��������ڹ������н��У�ûadd commit����ɾ����֧A ��	���Գɹ��ġ�
	6���鿴���з�֧���һ���ύ�ļ�¼��sha1ֵ������uuid����
    	git branch -v
```

9����֧�ϲ����ͻ���ϴ�ѧϰ�� https://ke.qq.com/course/404757?taid=3417389513714965&tuin=3a91c9ec ��





��������Կ��¼���ڱ�������һ��ssh key���͵�Զ�ֿ̲�1�����ڱ�������ssh��ssh-keygen -t rsa -C m13476065293@163.com һֱ�س� ֪������ssh key2�����͸�Զ��github -settings -SSH and .... - New SSH - title ���⡢key������ղ��ڱ������ɵ�ssh�����������ɵ�id_rsa.pub�ڵ�������֪��Զ��key�У�3��������ͨ�ԣ�ssh -T git@github.com  �س� �������ʾ����yes/no ����yes������غ�Զ�̳ɹ�ͨ�ţ��������/.ssh Ŀ¼�з���known_hosts�ļ�������Ŀ4.�����½�һ����Ŀ         ����Ŀ��·�������� git init��Զ���½�һ����Ŀnew -������Ŀ ���� ��Ŀssh ·��������Ŀ- Զ����Ŀ����git remote add oragin git@github.com:chen-panda/mygitremote.git ��  ��Ŀssh��ַ����һ�η�����Ŀ��    git  add .  //  �ļ�-�ݴ���    git commit -m "ע������" // �ݴ��� -���ط�֧��Ĭ��master��    git push -u origin master     ��һ���ύҪʹ�� -u Զ����Ŀclone������    git clone git@github.com:chen-panda/mygitremote.git��Ŀ�ύ������-Զ�̣�����ǰĿ¼���Ҽ� git bash��git  add .git commit -m "�ύ����֧"git push origin master    //����ʹ��-u���£�Զ��-���أ�git pullEclipse �в���git ��Egit����Ŀǰeclipse�ж�Ĭ��֧��git �������֧�֣����Ե�eclipse ��չ�����ض�git��1����git ������configuration�� ���� ���䣬�û���2����general  -network -ssh2ѡ��Eclipse ��һ�η���share project add to index commit����Ŀ���͵�Զ��commitʱ��commit and push �� commit ��ť������commit��ť�����ܵ���Pushĳһ���ļ���ֻ��push������Ŀcommit and push�����Ե���Pushĳһ���ļ�eclipse �и���team -remote - pullgit��ͻ�Ľ�����ֳ�ͻ������ͬ����ͼ  �Ҽ�  -- team  -- synchronized ...1��add to index 2��commit �����ط�֧  commit3�����·���˵����ݵ����� pull4���޸ĳ�ͻ��ֱ���޸�  ���� merge tool --> �Ѿ��޸���ͻgit���˿���  �Ŷ�Э������github �� ����Ŀ  -setting���Ӻ����ߣ� Collaborators ���� �����ߣ�github ȫ�������䷢���������Ӻ�����飺�򿪸����ӡ��������� git ɾ�����ط�֧��Զ�̷�֧1���鿴ɾ��ǰ��ķ�֧ ������ :git branch -a2�� ɾ�����ط�֧��git branch -d ��֧��3��ɾ��Զ�̷�֧�������� ������ :git push origin �Cdelete ��֧�� 
ͨ��tag��ʽ������Ŀ��
 1����ʼ��git�ֿ�:  git init
 2������ݻ�����git add .    git commit -m
3��Զ��git �����ֿ� 
4�����غ�Զ�ֿ̲����   git remote add origin �ֿ��ַ
5�����͵�Զ�̷�֧    git push -u origin master

֪ʶ��һ��
1���Ƚ������ύ������
2�������git tag ֪ʶ��һ

3���鿴�ύ��־   git log
4�����˰汾  git reset �汾�� ����Ҫȫ�����ƣ������͵�Զ�ֿ̲��ʱ��
       git reset --hard �汾�ţ����û���ύԶ�ֿ̲⣬Ҳ����ͨ��--hard ǿ�ƻ��˰汾��
5�������Ŀ���ļ��и�M ����ִ��  git status 

֪ʶ�����
1�����   git add .
2��git commit -m ��֪ʶ�����
3��git tag ֪ʶ���

�鿴��������tag
git tag

��tag���͵�Զ�̷�֧
git push --tags
