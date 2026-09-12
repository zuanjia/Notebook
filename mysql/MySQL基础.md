# MySQL基础

## SQL 语法

### 启动sql服务

mysql.server start 

### 设置开机自动启动

brew services start mysql

### linux

再linux中mysql是有默认密码的
查看用户和密码
sudo cat /etc/mysql/debian.cnf

修改用户和密码
版本在5.7.9以上使用这个
alter user 'root'@'%' identified with mysql_native_password by '123456'     

版本在5.7.9以下的使用这个
update user set password=Password("123456") where user = 'root'

启动服务
systemctl start mysql

### 数据库基础语法

#### DDL 数据库定义语言
Data Definition Language
常见关键字：CREATE,DROP,ALTER,TRUNCATE

##### 创建数据库

create database game;

##### 删除数据库

DROP DATABASE game;

##### 使用数据库

use game;

##### 创建表

create table palyer (
id INT,
name VARCHR(100),
level INT,
exp INT,
dold DECIMAL(10,2)
)

##### 查看表结构

DESC player;

##### 修改表结构

ALTER TABLE player MOIFY COLUMN name VARCHAR(200);

##### 修改字段名称

ALTER TABLE player RENAME COLUMN name to nick_name;

##### 添加新字段

ALTER TABLE player ADD COLUMN last_login DATETIME;

##### 删除字段

ALTER TABLE player DROP COLUMN last_login;

##### 删除表

DROP TABLE player;

#### DML 数据库操作语言

Data Manipulation Language
常见关键字：INSERT,UPDATE,DELETE.CALL

##### 插入数据

INSERT INTO player (id,name,lever,exp,gold) VALUSE (1,'张三‘,1,1,1);

插入多个数据
INSERT INTO player (id,name,lever,exp,gold) VALUSE (1,'张三‘,1,1,1),(2,'王五‘,1,1,1);

##### 修改数据

UPDATE player set leverl = 1 wher name = '李四';

修改多个数据
UPDATE player set exp=0,gold=0;

##### 删除数据

DELETE FORM player where  gold=0;

#### DQL 数据库查询语言

Data Query Language
常见关键字：SELECT

##### 查询数据

select * from player;

#### DCL 数据库控制语言

Data control Language
常见关键字：CRANT,REVOKE

#### 数据库的导入导出

##### 导出

mysqldump -u root -p game > game.sql

##### 导入

mysql -u root -p game < game.sql

### 注释

#### 单行注释

格式：-- 注释内容

```sql
select * -- 简单的查询语句
from students;
```

==注意==--与注释文字之间用空格分隔；

#### 多行注释

```sql
/*
这是一个
多行注释的例子
*/
```

==注意== 

在Navicat 中按ctrl +/快速注释选中的sql代码

## 类型

### 数值类型

| 类型         | 大小                                     | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| :----------- | :--------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------- |
| TINYINT      | 1 Bytes                                  | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
| SMALLINT     | 2 Bytes                                  | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
| MEDIUMINT    | 3 Bytes                                  | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER | 4 Bytes                                  | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
| BIGINT       | 8 Bytes                                  | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
| FLOAT        | 4 Bytes                                  | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
| DOUBLE       | 8 Bytes                                  | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
| DECIMAL      | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |

### 日期和时间类型

| 类型      | 大小 ( bytes) | 范围                                                         | 格式                | 用途                     |
| :-------- | :------------ | :----------------------------------------------------------- | :------------------ | :----------------------- |
| DATE      | 3             | 1000-01-01/9999-12-31                                        | YYYY-MM-DD          | 日期值                   |
| TIME      | 3             | '-838:59:59'/'838:59:59'                                     | HH:MM:SS            | 时间值或持续时间         |
| YEAR      | 1             | 1901/2155                                                    | YYYY                | 年份值                   |
| DATETIME  | 8             | '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'               | YYYY-MM-DD hh:mm:ss | 混合日期和时间值         |
| TIMESTAMP | 4             | '1970-01-01 00:00:01' UTC 到 '2038-01-19 03:14:07' UTC结束时间是第 **2147483647** 秒，北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYY-MM-DD hh:mm:ss | 混合日期和时间值，时间戳 |

### 字符串类型

| 类型       | 大小                  | 用途                            |
| :--------- | :-------------------- | :------------------------------ |
| CHAR       | 0-255 bytes           | 定长字符串                      |
| VARCHAR    | 0-65535 bytes         | 变长字符串                      |
| TINYBLOB   | 0-255 bytes           | 不超过 255 个字符的二进制字符串 |
| TINYTEXT   | 0-255 bytes           | 短文本字符串                    |
| BLOB       | 0-65 535 bytes        | 二进制形式的长文本数据          |
| TEXT       | 0-65 535 bytes        | 长文本数据                      |
| MEDIUMBLOB | 0-16 777 215 bytes    | 二进制形式的中等长度文本数据    |
| MEDIUMTEXT | 0-16 777 215 bytes    | 中等长度文本数据                |
| LONGBLOB   | 0-4 294 967 295 bytes | 二进制形式的极大文本数据        |
| LONGTEXT   | 0-4 294 967 295 bytes | 极大文本数据                    |

### 枚举与集合类型 （Enumeration and set Types)

- **ENUM**: 枚举类型，用于存储单一值，可以选择一个预定义的集合。
- **SET**: 集合类型，用于存储多个值，可以选择多个预定义的集合。

### 数据库中的元素

- 数据库	database
- 表	table
- 字段（列）	field
- 记录（行）	record

### 创建表   CREATE  TABLE

- 语法

  ```mysql
  CREATE TABLE 表名(
  	字段名 数据类型,
  	字段名 数据类型
  	...
  );
  ```

  **例1：创建表a,字段要求：name（名字），数据类型：varchar(字符串)，长度为10**

  ```mysql
  CREATE TABLE a(
  	name VARCHAR(10)
  	);
  ```

  **例2：创建表b，字段要求：name（名字），数据类型为varchar（字符串），长度为10；height（身高），数据类型为decimal（小数），一共5位，其中3位整数，2位小数**

  ```mysql
  CREATE TABLE b(
  	name VARCHAR(10),
  	height DECIMAL(5,2)
  	);
  ```

  **例3：创创建表c,字段要求如下：id：数据类型为int（整数）；name姓名：数据类型为varchar（字符串）长度为20，age年龄：数据类型为tinyint unsigned（无符号小整数）

  ```mysql
  CREATE TABLE b(
  	name VARCHAR(10),
  	height DECIMAL(3,2)
  	);
  ```

  ### 字段的约束
  
  ####常用约束介绍
  
  - 主键（primary key)：值不能重复，auto_increment 代表值自动增长
  - 非空（not null）：此字段不允许填写空值
  - 唯一 （unique）；此字段的值不允许重复
  - 默认值（default）：当不填写此值时会使用默认值，如果填写以填写为准
  
  ### 主键
  
  - 主键的值不能重复
  - 自增长。auto_increment
  - 值会系统维护，自动增长
  
  ```sql
  -- 创建表d，字段要求如下
  -- id：数据类型为int unsigned （无符号整数），primary key (主键),auton_increment（自增长）；
  -- name 名字：数据类型为var插入（字符串）长度为10
  -- age 年龄：数据类型为int（整数）
  CREATE TABLE d (
  id INT UNSIGNED PRIMARY KEY auto_increment,
  name VARCHAR(10),
  age int);
  
  -- 如果不知道能字段，主键自增长字段的值可以用占位符，0或者null
  ```
  
  ### 非空
  
  - 非空 not null
    - 这个字段必须有值，如果没有值，insert插入会失败
  
  ```sql
  -- 创建表e，字段要求如下
  -- id：数据类型为int unsigned （无符号整数）
  -- name 姓名：数据类型为varchar （字符串）长度为10，not null（非空）
  -- age 年龄：数据类型为int（整数）；
  CREATE TABLE e (
  id int UNSIGNED ,
  name VARCHAR(10) NOT NULL,
  age INT);
  ```
  
  ### 唯一
  
  - 唯一unique
    - 字段的约束为唯一，表示字段的值不能重复
  
  ```sql
  -- 创建f，字段要求如下
  -- id：数据类型为int（整数）
  -- name 姓名：数据类型为varchar（字符串）长度为10，unique（唯一）
  -- age 年龄：数据类型为int（整数）
  CREATE TABLE F(
  id INT,
  name VARCHAR(10) UNIQUE,
  age INT);
  ```
  
  ### 默认值
  
  - 默认值（default）：当不填写此值时会使用默认值，如果填写时以填写为准
  - 语法：
  
  ```sql
  create table 表名 (
  字段名 数据类型 default 值,
  ...
  );
  ```
  
  ```sql
  -- 创建表g
  -- 字段要求如下：
  -- id：数据类型为int（整数）；
  -- name姓名：数据类型为varchar（字符串）长度为10
  -- age年龄：数据类型为int（整数），default（默认值）30；
  CREATE TABLE g (
  id INT,
  name VARCHAR(10),
  age INT DEFAULT 30
  );
  INSERT INTO g VALUES (1,'张三',20)
  -- --插入的时候不指定age的值
  INSERT INTO g(id,name) VALUES (2,'李四');
  
  SELECT * FROM g;
  ```
  
  

## select查询 基础语法

- 查询所有字段
- 语法

```sql
select * from 表名
```

​	例1：查询表c所有的数据

```sql
SELECT * FROM c
```

- 查询指定字段
- 语法

```sql
select 字段1，字段2,...from 表名
```

​	例2：查询指定的数据（id，age）

```sql
--查询c的id字段
SELECT id FROM c;
--查询表c的id和age字段
select id,age from c;
--查询表c的所有字段，但顺序自定义
select id,age,name from c;
```

### 字段的别名

- 通过字段名as别名的语法可以给字段起一个别名，别名可以是中文
- as可以省略
- 字段名as别名和字段名 别名结果是一样的

```sql
-- 通过as给字段起一个别名
SELECT card AS 身份证,name AS 姓名,sex AS 性别 FROM students;
-- 别名的as可以省略
SELECT card 身份证,name 姓名, sex 性别 FROM  students;
```

### 表的别名

- 通过表名as别名给表起一个别名
- as可以省略

```sql
SELECT * FROM students as stu;
-- 也是可以省略as
SELECT * FROM students stu;
```

### distinct过滤重复记录

- 通过select distinct 字段名，字段名 from 表名 来过滤select查询结果中的重复记录

```sql
SELECT DISTINCT sex FROM students;
```

### 条件查询

- where 后面跟一个条件，实现有选择地查询
- select * from 表名 where 条件

```sql
-- 查询students表中学号studentNo等于‘001’的记录
SELECT * FROM students WHERE studentNo = '001';
-- 查询students表中年龄age等于30的姓名name，班级class
SELECT name,class FROM students WHERE age = 30;
```

#### selext 查询的基本规则

- select 后面的* 或者字段名决定了返回什么样的字段（列）；
- select 中where子句，决定了返回什么样的记录（行）；
- where后面支持多种运算符，进行条件的处理
  - 比较运算；
  - 逻辑运算；
  - 模糊运算；
  - 范围查询；
  - 空判断；

#### 比较运算符

- 等于：=
- 大于：>
- 大于等于：>=
- 小于：<
- 小于等于：<=
- 不等于：!=或<>

```sql
--查询students表中name（名字）等于‘小乔’学生的age（年龄）
SELECT age FROM students WHERE name = '小乔';

--查询students表中30岁以下的学生记录
SELECT * FROM students WHERE age < 30;
```

#### 逻辑运算符

- and（与）
  - and有两个条件；
  - 条件1and条件2
  - 两个必须同时满足；

```sql
--查询age年龄小于30，并且sex性别为女的同学记录
SELECT * FROM students WHERE age <30 AND sex = '女'
```

- or(或)
  - or有两个条件
  - 条件1or条件2
  - 两个条件只要有一个满足即可

```sql
--查询sex性别为'女'或者班级class班级为‘1班’的学生记录
SELECT * FROM students WHERE sex = '女' OR class = '1班'
```



- not(非)
  - not只有一个条件
  - not条件；
  - 如果条件满足not后变为不满足，not后变为满足

```sql
--查询hometown老家非天津的学生记录
SELECT * FROM students WHERE NOT hometown = '天津'
```

#### 模糊查询

- like
- %表示任意多个任意字符
- _表示一个任意字符

```sql
-- 查询name姓名中以‘孙’开头的学生记录
SELECT * FROM students WHERE name LIKE '孙%'

-- 查询name名字以孙开头，且名字只有一个字的学生记录
SELECT * FROM students WHERE name LIKE '孙_'

-- 查询name为任意姓，名叫乔的学生记录
SELECT * FROM students WHERE name LIKE '%乔'

-- 查询name姓名中含白的学生记录
SELECT * FROM students WHERE name LIKE '%白%'
```

#### 范围查询

- in表示在一个非连续的范围内
- in(值，值，值)

```sql
-- 查询hometown家乡是北京，上海或广东的学生记录
SELECT * FROM students WHERE hometown in ('北京','上海','广东')
```



- between...and...表示在一个连续的范围内

```sql
-- 查询age年龄为25~30的学生记录
SELECT * FROM students WHERE age BETWEEN 25 and 30
```

#### 空判断

- 注意：null与‘’不同的
  - null：表示什么都没有
  - ‘’：表示长度为0的字符串
- 判断空：is null

```sql
-- 查询card身份证为null的学生记录
SELECT * FROM students WHERE card IS NULL
```

- 判断非空 is not null

```sql
-- 查询card身份证非null的学生记录
SELECT * FROM students WHERE card IS NOT NULL
```

#### where 子句在update与delete语句中同样有效

```sql
-- 修改age为25，并且name为孙尚香的学生class为2班
UPDATE students SET class = '2班' WHERE name= '孙尚香'AND age = 25

-- 删除class为一班，并且age大于30的学生记录
DELETE FROM students WHERE age>30 and class = '1班'
```

### 排序

- 为了方便查看数据，可以对数据进行排序
- 语法

```sql
select * from 表名
order by 字段1 asc|desc,字段2 asc|desc,...
```

- 将行数按照字段1进行排序，如果后写行字段1的相同时，按照字段2排序，以此类推；
- 默认按照字段值从小到大排序
- asc（默认)从小到大排序，即升序
- desc从大到小排序，即降序

```sql
-- 查询所有学生记录，按age年龄从小到大排序
SELECT * FROM students ORDER BY age ASC;

-- 查询所有得学生记录，按age年龄大到小排序
SELECT * FROM students ORDER BY age DESC
```

- 排序得优先级

```sql
-- 查询所有学生记录，按age年龄大到小排序，
-- 年龄相同时，再按studentNo学号从小到大排序
SELECT * FROM students ORDER BY age DESC , studentNo 
```

- 当以条select语句出现了where和order by
  - select * from 表名 where 条件 order by 字段1，字段2
  - 一定把where写在order by前面

```sql
SELECT * FROM students WHERE sex = '男' ORDER BY class , studentNo DESC
```

### 聚合函数

- 为了快速得到统计数据，经常会用到下面5个聚合函数
  - 注意：聚合函数不能再where 后面得条件中使用

#### count 总记录数

- count（*）表示计算总记录数，括号中写`*`与字段名，结果是相同的

```sql
-- 查询学生总数（查询students表有多少条记录）
SELECT COUNT(*) FROM students;
SELECT COUNT(name) FROM students;

-- 查询性别sex为‘女’的学生总数
SELECT count(*) FROM students WHERE sex = '女'
```

#### max 最大值

- max（字段）表示求此字段的最大值

```sql
-- 查询最大age年龄
select max(age) FROM students
-- 查询性别sex为女的最大age年龄
SELECT MAX(age) FROM students WHERE sex = '女'
```

### min 最小值

- min（字段）表示求此字段的最小值

```sql
-- 查询学生最小age年龄
SELECT MIN(age) FROM students
-- 查询class班级为‘1班’的最小age年龄
SELECT MIN(age) FROM students WHERE class = '1班'
```

#### 求和

- sum（字段）表示求此字段的和

```sql
-- 查询学生age年龄总和
SELECT sum(age) FROM students
-- 查询hometown为‘北京’的学生age年龄总和
SELECT sum(age) FROM students WHERE hometown = '北京'
```

#### avg 平均值

- avg(字段)表示求此字段的平均值

```sql
-- 查询学生平均年龄
SELECT avg(age) FROM students
-- 查询sex性别为‘男’的平均年龄
SELECT avg(age) FROM students WHERE sex = '男'
```

- avg的字段中如果有null，null不做为分母计算平均值

### 数据分组

#### 分组

- group by 字段名
- 按照字段分组，表示此字相同的数据会被放到一组中；
- 分组的目的是配合聚合函数，聚合函数会对每一组的数据分别进行统计
- 语法

```sql
select 字段1，字段2，聚合函数...from 表名 group by 字段1，字段2...
```

```sql
-- 查询各种sex性别的人数
SELECT sex,count(*) FROM students GROUP BY sex

-- 查询各种age年龄的人数
SELECT age ,COUNT(*) FROM students GROUP BY age
```

##### where 和 group by 和order by 的顺序

select * from students where 条件 group by 字段 order by 字段

###分组后的数据筛选  having

- 语法：

```sql
select 字段1，字段2，聚合...from 表名
group by 字段1，字段2，字段3...
having 字段1,...聚合...
```

```sql
-- 用where查询男生总数
-- where先筛选复合条件的记录让后再聚合统计
SELECT count(*) FROM students WHERE sex = '男' GROUP BY sex

-- 用having查询男生总数
-- having先分组聚合统计，再统计的结果中筛选
SELECT COUNT(*) FROM students GROUP BY sex HAVING sex = '男'
```

#### having配合聚合函数的使用

```sql
-- 求班级人数大于3的班级
SELECT class,count(*) FROM students GROUP BY class HAVING count(*) >3
```

- 对比where 与 having
  - where是对表的原始数据进行筛选
  - having是对group by 之后已经分组的数据进行筛选
  - having可以使用聚合函数，where不能使用聚合和函数

###数据分页显示

####获取部分行

- 当数据量过大时，再一页查看数据是一件非常麻烦的事情
- 语法：limit 开始行，获取行数

```sql
select * from 表名 limit start ,count
```

- 从start开始，获取count条数据；
- start索引从0开始，如省略start默认从0开始
- count代表要显示多少行
- 省略start默认从0开始，从第一行开始

```sql
-- 查询前三行记录
SELECT * FROM students LIMIT 0,3
SELECT * FROM students LIMIT 3

-- 查询从第四条记录开始的数据
SELECT * from students LIMIT 4,3
```

### 分页 

- 已知：每页显示m条数据，求：查询第n页的数据

```sql
select * from students limit (n-1)*m,m
```

```sql
-- 每页显示4条记录，查询第3页数据
SELECT * FROM students LIMIT 8,4
```

## 连接查询

### 内连接

- 语法1：
- 内连接最重要的时找两张关联的字段

```sql
select * from 表1 
inner join 表2 on 表1.字段=表2.字段
```

- students表和scores内连接查询结果

```sql
SELECT * FROM students INNER JOIN scores ON students.studentNo = scores.studentNo
```

- 语法二：

```sql
select * from 表1，表2
where 表1.字段= 表2.字段
```

```sql
隐式内连接
SELECT * FROM students , scores WHERE students.studentNo = scores.studentNo
```

```sql
-- students表与socres内连接，只显示name，课程号，成绩
SELECT name,courseNo,score FROM students INNER JOIN scores on students.studentNo = scores.studentNo
```

##### 表的别名在查询中的使用

```sql
SELECT name AS 名字,courseNo AS 科目编号,score AS 成绩 FROM students as st INNER JOIN scores AS sc ON st.studentNo = sc.studentNo
```

##### 带有where的内连接

```sql
-- 查询王昭君的信息，要求值显示名字，课程号，成绩
SELECT name,courseNo,score FROM students as s1 
INNER JOIN scores as s2 ON s1.studentNo = s2.studentNo 
WHERE s1.name = '王昭君';
```

##### 带有and的where条件

```sql
-- 查询王昭君的信息，要求值显示名字，课程号，成绩
SELECT name,courseNo,score FROM students as s1 
INNER JOIN scores as s2 ON s1.studentNo = s2.studentNo 
WHERE s1.name = '王昭君' AND s2.score < 90;
```

##### 多表内连接

```sql
-- 查询学生信息和成绩以及成绩对应的课程名称
SELECT * FROM students INNER JOIN scores ON students.studentNo = scores.studentNo
INNER JOIN courses ON scores.courseNo = courses.courseNo;
```

# 6.自关联

```sql
-- 查询一共有多少个省
SELECT count(*) from areas where pid is null;
-- 查询有多少市
SELECT count(*) from areas where pid is not null;
```

- 自关联,是同一张表做连接查询,
- 自关联下,一定找到同一张表可关联的不同字段

```sql
-- 例 2：查询广东省的所有城市
SELECT * from areas a1 INNER JOIN areas a2
on a1.id = a2.pid
WHERE a1.name = '广东省';
```

# 7.子查询

- 子查询是嵌套到主查询里面的
- 子查询做为主查询的数据源或者条件
- 子查询是独立可以单独运行的查询语句
- 主查询不能独立独立运行,依赖子查询的结果

```sql
-- 例 1：查询大于平均年龄的学生记录
-- SELECT avg(age) from students;
-- 
-- select * from students where age > 30.1667;

-- 用子查询实现
select * from students where age > (SELECT avg(age) from students);
```

- 标量子查询------子查询返回结果只有一行,一列

```sql
-- 例 2：查询 30 岁的学生的成绩
-- 1,查询30岁学生的studentNO
-- select studentNo from students where age = 30;
-- 
-- SELECT * from scores where studentNo in ('001', '003', '011');

-- 用子查询实现
SELECT * from scores where studentNo in 
(select studentNo from students where age = 30);

```

- 列子查询------子查询返回一列多行

```sql
-- 例 3：用子查询，查询所有女生的信息和成绩
-- 用内连接实现
SELECT * from students INNER JOIN scores ON
students.studentNo = scores.studentNo
where sex = '女';
-- 用子查询实现
select * from (SELECT * from students where sex = '女') stu
INNER JOIN scores sc on stu.studentNo = sc.studentNo;
```

- 表级子查询------子查询返回结果为多行,多列



- 课件提问问题及答案

```sql
-- 查询各个年龄段学生的数量,按照数量从大到小排序
select age, count(*) from students GROUP BY age ORDER BY count(*) desc;

-- 查找年龄大于等于25,小于等于30的男同学
select * from students where (age BETWEEN 25 and 30) and sex = '男';

-- 显示2班和3班的女同学
SELECT * from students where sex = '女' and class in ('2班', '3班');

-- 显示所有有效的card学生记录,null和''都是无效的
SELECT * FROM students where card is not null and card != '';


-- 查找老家不在河北和北京的同学的age总和
SELECT sum(age) from students where hometown <> '北京' and hometown <> '河北'; 
SELECT sum(age) from students where not hometown in ('北京', '河北');

-- 查找不姓'白'的同学
SELECT * from students where not name like '白%';

-- 查询每个班有分别多少同学
SELECT class, count(*) from students GROUP BY class;

-- 这个sql能不能显示年龄最大的同学的姓名
select name,max(age) from students;

-- 显示年龄最大的同学的姓名
SELECT name from students order by age desc limit 1;
SELECT name from students where age = (select max(age) from students);

-- 查询年龄最大的女同学和年龄最小的女同学差多少岁
SELECT max(age) -  min(age) from students where sex = '女';

-- 分别求男女同学的平均年龄
select sex,avg(age) from students GROUP BY sex;

-- 只显示班级人数为3个同学的班级名称
SELECT class from students GROUP BY class HAVING count(*) = 3; 

--  查询姓名只有2个字的女同学的数量
SELECT count(*) from students where sex = '女' and name like '__';

-- 查询年龄大于25,老家不在河北的男同学
SELECT * from students where age > 25 and hometown != '河北' and sex = '男' ;

-- 查询1班加3班所有同学的年龄总和
SELECT sum(age) from students where class = '1班' or class = '3班';

```



## insert插入数据基础语法

- 语法：insert into 表名 values (值,值,值,值...);

```mysql
INSERT INTO c VALUES (0,'小涛',30);
```



## update修改数据的基础语法

- 语法

```sql
update 表名 set 字段1=值1 ，字段2=值2,字段3=值3...
```

- 语法：如果没有where条件表修中所有的记录

```sql
--例1：修改表c，所有人的年龄（age字段）改为30
update c set age = 30;
```

- 带有条件的update语句

```sql
--例2：修改表c，
--id为3的记录
--姓名（name字段）改为‘小涛儿子’,年龄（age字段）改为20
update c set name = '小涛儿子',age = 20 where = 3;
```

```sql
--修改name为小涛奶奶的记录为小涛的祖奶奶
update c set name = '小涛祖奶奶' where name = '小涛奶奶'
```

```sql
--id大于2的记录，增加一岁
update c set age = age + 1 where id > 2
```



## delete删除基础语法

- 语法：delete from 表名 where 条件

```sql
--例子：删除表c中id为6的记录
DELETE FROM c WHERE id = 3;
--删除所有数据
DELETE FROM c;
```



#### 还有一种删除语法 truncate

- 语法：（删除表的所有数据，保留表结构）

```sql
--删除表c所有数据
trancate table 表名;
```

**delecte 和 truncate的区别**

- 在速度上，truncate > delete
- 如果想删除部分数据用delete，注意带上where子句；
- 如果想保留表而将所有数据删除，自增长字段恢复从1开始，用truncate；

## 删除表

- 语法1：drop table 表名

```sql
-- 删除表a
DROP TABLE a;
```

- 语法2：drop table if exists 表名

```sql
-- 如果表a存在，就删除表a不存在什么都不做
DROP TABLE if EXISTS a;
```

## mysql内置函数

### 字符串函数

- 拼接字符串

```sql
-- 把12，34，‘ab’拼接为一个字符串‘1234ab’
SELECT CONCAT(12,34,'ab')
```

###包含字符个数length(str)

- 如果字符串中包含utf8格式的汉字，一个汉字length返回3

```sql
-- 计算字符串‘abc’的长度
SELECT length('abc')
-- 计算字符串‘我和你’ 的长度
SELECT LENGTH('我和你')
```

### 截取字符串

- left（str,len)返回字符串str的左端len个字段，中文与英文字母个数len一致

```sql
-- 截取字符串‘我和你abc’的左端3个字符
SELECT LEFT('我和你abc',3)
```

- right(str,len)返回字符串str的右端len个字符，中文与英文个数len一致

```sql
-- 截取字符串‘我和你abc’的右端3个字符
SELECT RIGHT('我和你abc',3)
```

- substring(str,pos,len)返回字符串str的位置pos起len个字符，pos从1开始计数

```sql
-- 截取字符串‘我和你abc’从第二个字符开始的3个字符
SELECT SUBSTRING('我和你abc',2,3)
```

### 去除空格

- ltrim(str)返回删除左侧空格的字符串str；

```sql
-- 去除字符串‘   abcd   ’左侧空格
SELECT LTRIM('   abcd   ')
```

- rtrim(str)返回删除右侧空的字符串str；

```sql
-- 去除字符串‘   abcd   ’右侧空格
SELECT RTRIM('   abcd   ')
```

- trim(str)返回删除左右两侧空格的字符串str；

```sql
-- 去除字符串‘   abcd   ’左右空格
SELECT TRIM('   abcd   ')
```

## 数据函数

### 求四舍五入round(n,d)

- n表示原数，d表示小数位置，默认整数位

```sql
-- 1.6343四舍五入，保留整数位
SELECT ROUND(1.6343)
-- 1.653四舍五入，保留小数点后2位
SELECT ROUND(1.653,2)
```

### 随机数rand()

- 值为0-1.0的浮点数

```sql
select rand();

-- 从学生表中随机抽出一个学生
SELECT * FROM students ORDER BY RAND() LIMIT 1
```

## 日期时间函数

### 当前日期current_date()

```sql
-- 返回当前日期
SELECT CURRENT_DATE();
```

### 当前系统时间 current_date()

```sql
-- 返回系统时间
SELECT CURRENT_TIME()
```

## 索引

- index
- 给表建立索引，目的是加快select查询的速度
- 如果一个表记录很少，几十条或者几百条不用索引
- 表的记录特别多，如果没有索引，select语句效率会非常低

### 创建索引

- 语法
- 如果指定字段是字符串，需要指定长度，建议长度与定义字段时的长度一致；
- 字段类型如果不是字符串，可以不填写长度部分

```sql
create index 索引名称 on 表名（字段名称（长度））;
```

```sql
-- 为表studetns的name字段创建索引，名为name_index
CREATE INDEX name_index ON students(name(10))
```

### 调用索引

- 不需要显示的写调用索引的语句，只要where条件后面用的字段建立了索引，那么系统会自动调用

```sql
-- 这里会自动调用age_index
SELECT * FROM students WHERE age = 30
```

### 查看索引

- show inde from 表名
- 对于主键，系统会自动建立索引

```sql
-- 查看students表的索引
SHOW INDEX FROM students
```

### 删除索引

- 语法

```sql
drop index 索引名称 on 表名；
```

```sql
-- 删除索引age_index
DROP INDEX age_index ON students
```

- 优点：
  - 索引大大提升了select语句查询速度
- 缺点：
  - 虽然索引跳了查询速度，同时会减低更新表的速度，例如对表进行insert，update和delete操作。因为更新表时，不仅要保存诗句，还要保存索引文件；
- 项目中80%以上时select所以index必须的
- 在实际工作中如果涉及到大量的数据修改操作，修改之前可以把索引删除，修改完后再把索引建立起来

## mysql命令行

- mysql -h mysql服务器的地址 -u 用户名 -p
  - -h 如果是使用本机的mysql -h可以省略

### mysql登录之后的常用命令

- show databases
  - 显示系统所有的数据库
- use 数据库名
  - 使用指定的一个数据库

```cmd
use mydb
```

- show tables
  - 查看只当数据库右多少表
- 如果命令行默认字符集与数据库默认字符集不同
  - 在windows默认字符集是gbk
  - set names gbk
    - 告诉mysql，客户端的字符集是gbk

- 在命令行中每条sql语句用；结尾
- 可以通过desc表名查看一个表的字段结构
  - desc studetns
  - 查看students每个字段的定义

### 在命令行下创建数据库和删除数据库

- create datatase 数据库名 default charset 字符集

```sql
-- 创建一个数据库mytest，默认字符集utf8
create database my test default charset utf8;
-- 删除数据库mytest 
drop database mytest
drop database if exists mytest
```

### 修改用户密码
