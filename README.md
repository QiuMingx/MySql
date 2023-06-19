# MySql
```mysql
create table  tb_user01(
    id int comment 'ID,唯一表示',
    username varchar(20) comment '用户名',
    name varchar(10) comment '姓名',
    age int comment '年龄',
    gender char(1) comment '性别'
) comment '用户表';
```

```mysql
create table  tb_user01(
       id int primary key auto_increment comment 'ID,唯一表示',
       username  varchar(20) not null unique comment '用户名',
       name varchar(10) not null comment '姓名',
       age int comment '年龄',
       gender char(1) default '男' comment '性别'
) comment '用户表'
```
##### 数值类型： tinyint  smallint mediumint int bigint float(5,2) double(5,2) decimal(5,2)
   > age tinyint unsigned
   > score double(4,1)

#####  字符串： char varchar
> char(10) 最多只能存10个字符，不足10个字符，占用10个字符（定长）
> varchar(10):最多只能存10个字符，不足10个字符，按照长度储存（变长）
> phone char(11)
> username varchar(20)

##### 日期类型 date YY-MM-DD time HH:MM:SS datetime YYYY-MM-DD HH:MM:SS
> birthday date
> update_time datetime

#####  根据原型 确定字段 + 基础字段  ——> create_time 记录的是当前这条数据的插入时间 update_time 记录这条数据的最后更新时间
```mysql
    # 查看当前数据库的表
    show tables;
    # 查看表结构
    desc tb_emp;
    # 查看数据库的建表语句
    show create table tb_emp;
```
#### DDL（表操作）# 修改
- 添加字段：alter table 表名 add 字段名 类型（长度）[comment 注释] [约束]
- 修改字段类型 alter table 表名 modify 字段名 新数据类型(长度）
- 修改字段名和字段类型 alter table 表名 change 旧字段名 新字段名 类型（长度）[comment注释] [约束]
- 删除字段： alter table 表名 drop column 字段名
- 修改表名： rename table 表名 to 新表名
- 删除表：drop table [if exists]表名

```mysql
alter table tb_emp add qq varchar(11) comment 'QQ';

alter table tb_emp modify qq varchar(20) comment 'myqq';

alter table tb_emp change qq qq_num varchar(30) comment 'youqq' not null ;

alter table  tb_emp drop column qq_num;

rename table tb_emp to tb_emp01;

drop table if exists tb_user01;
```

#### DML Data Manipulation Language(数据操作语言）
- INSERT UPDATE DELETE
- insert into 表名（字段1，字段2） values(值1，值1）
- insert into 表名 values(值1，值2，....)
- insert into 表名（字段1，字段2） values(值1，值2），（值1， 值2）;
```mysql
insert  into  tb_emp(username,name,gender, create_time, update_time) values('lining', 'oo', 1, now(),now());

insert  into tb_emp(id, username, password, name, gender, image, job, entrydate, create_time, update_time, qq) values (null, 'lin', '123', 'ddd',2,'1.jpg',2,'2010-04-10',now(), now(), '00')

insert  into  tb_emp(username,name,gender, create_time, update_time) values('lining3', 'oo', 1, now(),now()),('lining2', 'oo', 1, now(),now());
```
#update 表名 set 字段名1 = 值1， 字段名2 = 值2，...[where 条件]

update tb_emp set name = '张三', update_time=now() where id= 1;
update tb_emp set entrydate = '2010-01-01', update_time=now();

# delete from 表名 [where 条件]
```mysql    
delete from tb_emp where id = 1;
delete from tb_emp;
```
#### DQL Date Query Language (数据查询语言）
# select 
![image](https://github.com/Qiluzz/MySql/assets/4120789/d397beca-a728-4955-9a0f-0161682214ac)
