# SQL 语法

## 1 SQL 概要
SQL结构化查询语言是访问数据库的标准查询工具。许多数据库都支持它。 

有关SQL的知识，可以参考： https://www.w3school.com.cn/sql/sql_syntax.asp

可以把 SQL 分为两个部分：数据操作语言 (DML) 和 数据定义语言 (DDL)。SQL (结构化查询语言)是用于执行查询的语法。但是 SQL 语言也包含用于更新、插入和删除记录的语法。

## 2 快速参考

https://www.w3school.com.cn/sql/sql_quickref.asp

## 3 数据操作语言 (DML)

查询和更新指令构成了 SQL 的 DML 部分：

### 3.1 SELECT - 从数据库表中获取数据

```
# 最简查询
SELECT 列名称 FROM 表名称 

# 去除重复行
SELECT DISTINCT 列名称 FROM 表名称

# 按条件查询，其中运算符有：= <> > < >=	<=	BETWEEN	LIKE；
# SQL 使用单引号来环绕文本值（大部分数据库系统也接受双引号）。如果是数值，请不要使用引号。
# AND 和 OR 可在 WHERE 子语句中把两个或多个条件结合起来。还可以使用圆括号来组成复杂的表达式。
SELECT 列名称 FROM 表名称 WHERE 列 运算符 值

# ORDER BY 语句用于对结果集进行排序。默认按照升序对记录进行排序。如果您希望按照降序对记录进行排序，可以使用 DESC 关键字。
SELECT Company, OrderNumber FROM Orders ORDER BY Company DESC, OrderNumber ASC
```

### 3.2 UPDATE - 更新数据库表中的数据
```
# 标准语法
UPDATE 表名称 SET 列名称1 = 新值1 [，列名称2 = 新值2 ] WHERE 列名称 = 某值

```
DELETE - 从数据库表中删除数据
```
# 标准型
DELETE FROM 表名称 WHERE 列名称 = 值
# 删除所有行
DELETE FROM 表名称
```
### 3.3 INSERT INTO - 向数据库表中插入数据
```
# 标准形态
INSERT INTO 表名称 VALUES (值1, 值2,....)
# 或
INSERT INTO table_name (列1, 列2,...) VALUES (值1, 值2,....)

```

## 4 数据定义语言 (DDL)
SQL 的数据定义语言 (DDL) 部分使我们有能力创建或删除表格。我们也可以定义索引（键），规定表之间的链接，以及施加表间的约束。

SQL 中最重要的 DDL 语句:

### 4.1 CREATE DATABASE - 创建新数据库
```
```
### 4.2 ALTER DATABASE - 修改数据库
### 4.3 CREATE TABLE - 创建新表
```
CREATE TABLE employees(
    userid varchar(6) not null primary key,
    first_name varchar(20),
    last_name varchar(20),
    department varchar(20),
    salary varchar(10),
    auth_tan varchar(6)
);
```
### 4.4 ALTER TABLE - 变更（改变）数据库表
### 4.5 DROP TABLE - 删除表
### 4.6 CREATE INDEX - 创建索引（搜索键）
### 4.7 DROP INDEX - 删除索引

几乎每个应用程序都使用数据库来存储数据。随着应用程序安全意识的提高，SQL注入变得日益困难。很多程序使用API来防止注入，所以SQL注入目前已成为一项艰难的任务，需要测试人员坚持不懈的探查细节。

## 5 SQL特殊字符

### 5.1 SQL语句后面的分号

某些数据库系统要求在每条 SQL 命令的末端使用分号。在我们的教程中不使用分号。

分号是在数据库系统中分隔每条 SQL 语句的标准方法，这样就可以在对服务器的相同请求中执行一条以上的语句。

如果您使用的是 MS Access 和 SQL Server 2000，则不必在每条 SQL 语句之后使用分号，不过某些数据库软件要求必须使用分号。



#### 5.1.1 行内注释
```
/* */
# 或：
-- ， #
# 例如：
SELECT * FROM users WHERE name='admin' --and pass='pass'
```

#### 5.1.2 允许查询链(语句分割符)
```
;
# 例如：
SELECT * FROM users; drop table users;
```

#### 5.1.3 字符串连接符
```
' 或 + 或 ||
# 使用char函数，将ASCII码转换为字符
char()

# 例如：
SELECT * FROM users WHERE name='+char(27) or 1=1

```

### 5.2 SQL 特殊语句

#### 5.2.1 UNION

使用 union 操作符可以将两个或多个 SELECT 语句的结果合并起来。

需要特别注意的是：
- union 合并中的每个 SELECT 语句的输出结果，必须在列的数量上是相同的。
- 第一个 SELECT 语句的第一列、第二列...的数据类型，必须匹配第二个、第三个... SELECT 语句的第一列、第二列...的数据类型。即每个对应列的数据类型都要相同。

```
SELECT First_Name from user_system_data UNION SELECT login_count FROM user_data;
```

#### 5.2.2 Joins

join 运算符用于合并两个或多个表的行，合并条件是对应列。

```
SELECT * FROM user_system_data UNION SELECT  login_count FROM user_data;

```