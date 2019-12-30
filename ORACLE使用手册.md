

# ORACLE 开发手册

## 一、oracle基本手册

安装

 https://www.cnblogs.com/gaozejie/p/9741186.html 

 注册码  

```
PLSQL Developer 12.0.7 注册码
product code： 4vkjwhfeh3ufnqnmpr9brvcuyujrx3n3le 
serial Number：226959 
password: xs374ca
```



## 二 、oracle表分区

**-- step1 创建两个表空间，分别是TBSP_1和TBSP_2，方法是在SQL窗口中输入如下语句：**

CREATE TABLESPACE TBSP_1 DATAFILE 'E:\oracle\oracle\oradata\orcl/TBSP_1.dbf' SIZE 10M;
CREATE TABLESPACE TBSP_2 DATAFILE 'E:\oracle\oracle\oradata\ORCL/TBSP_2.dbf' SIZE 10M;

**-- step2 创建表 指定分区规则**
create table ware_retail_part
(
    id integer primary key,
    retail_date date,
    ware_name varchar2(50)
)
partition by range(retail_date)
(
   --2011年第一季度为par_1分区
   partition par_01 values less than(to_date('2011-04-01','yyyy-mm-dd')) tablespace TBSP_1,
   --2011年第二季度为par_2分区
   partition par_02 values less than(to_date('2011-07-01','yyyy-mm-dd')) tablespace TBSP_1,
   --2011年第三季度为par_3分区
   partition par_03 values less than(to_date('2011-10-01','yyyy-mm-dd')) tablespace TBSP_2,
   --2011年第四季度为par_4分区
   partition par_04 values less than(to_date('2012-01-01','yyyy-mm-dd')) tablespace TBSP_2
)

**-- step3 插入数据进行测试**

insert into ware_retail_part values(1,to_date('2011-01-20','yyyy-mm-dd'),'平板电脑');
insert into ware_retail_part values(2,to_date('2011-04-15','yyyy-mm-dd'),'小米3手机');
insert into ware_retail_part values(3,to_date('2011-07-25','yyyy-mm-dd'),'iWatch');
insert into ware_retail_part values(4,to_date('2011-12-17','yyyy-mm-dd'),'华硕笔记本');

SELECT * FROM ware_retail_part



**--  step4 查询当前表有多少分区**
select table_name , partition_name from user_tab_partitions where table_name = 'WARE_RETAIL_PART';



**-- step5 查询表某一分区的数据**
select * from ware_retail_part partition(par_01);
select * from ware_retail_part partition(par_02);
select * from ware_retail_part partition(par_03);
select * from ware_retail_part partition(par_04);



## 三 、Mybatiis + oracle  insert 返回自增主键配置

```
1、	建表 config_item_case
	create table config_item_case(
		id int primary key,
		case_name VARCHAR(255),
		case_code VARCHAR(255),
		parent_id 	int,
		case_level  int,
		create_time DATE DEFAULT SYSDATE,
		update_time DATE
	);
```

​	

    2、CONFIG_ITEM_CASE 触发器创建
    	a、创建自增序列 （start with 设置主键自增开始位置）
    	create sequence CONFIG_ITEM_CASE_id	minvalue 1 nomaxvalue increment by 1 start with 1 nocache;
    	b、创建触发规则
    create or replace trigger CONFIG_ITEM_CASE_tg_insertId before insert on CONFIG_ITEM_CASE for each row 
     begin
    	 select CONFIG_ITEM_CASE_id.Nextval into:new.id from dual;
     end;


​	   

	3、mybatis 中配置insert规则 返回自增主键 
	<insert id="insertItemCase"  useGeneratedKeys="true"
	        parameterType="com.kttsoft.kpi.api.modules.base.model.ConfigItemCase">  
	        <selectKey keyProperty="id" order="AFTER" resultType="java.lang.Integer">
	　			　select CONFIG_ITEM_CASE_id.currval as id  from dual
			</selectKey>
	        insert into  
	        config_item_case( CASE_NAME
	        <include refid="getCaseField" />  
	        )  
	        values( #{caseName}
	        <include refid="getCaseValue" />  
	        )  
	    </insert>  
```
 删除触发器方式
DROP TRIGGER PERSON_trigger  --删除触发器
DROP SEQUENCE PERSON_sequence  --删除序列
```

 

​	cmd 导出表

```
exp chenyu/123456@localhost/orcl

exp (用户名)/(密码)@192.168.1.119/orcl file=d:\xiangyangjixiao.dmp（文件存放地址） owner=xiangyangjixiao

导出一张或几张表时
exp zffxpg/zffxpg@localhost:1521/orcl file=D:\risk.dmp tables=(DATA_RISK_INFO1,DATA_RISK_INFO2)
```



cmd 导入dmp文件

```
imp (用户名)/(密码)@192.168.1.119/orcl file=d:\zffxpg.dmp（文件存放地址） full=y log=exp_table.log

```



oracle 创建表空间

```
create tablespace ZFFXPG  
logging  
datafile 'E:/oracle/oracle/oradata/ORCL/ZFFXPG.dbf' 
size 50m  
autoextend on  
next 50m maxsize 20480m  
extent management local; 
```

创建用户并制定默认表空间

```
create user ZFFXPG identified by ZFFXPG  default tablespace  ZFFXPG  temporary tablespace temp;
注解 default tablespace 默认表空间
temporary tablespace 临时表空间（可以使用temp）

```

授权

```
grant connect,resource,dba to username;
```

查询该用户表空间是否切换

```
select default_tablespace from dba_users where username='ZFFXPG'
```

oracle数据库建立dblinks

```
Name : 自定义取一个名字
UserName ： TYYW
Password：TYYW
Database:192.168.1.119/orcl
```



