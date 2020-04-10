# mysql-final-test

2019-2020 mysql final test

姓名：金鑫

学号：17061512

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```sql
select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 08:01:02 |
+---------------------+
1 row in set (0.00 sec)
```

2 组合打印自己的姓名和学号
```sql
select concat('金鑫','+',17061512) 组合打印姓名加学号;
+-----------------------------+
| 组合打印姓名加学号          |
+-----------------------------+
| 金鑫+17061512               |
+-----------------------------+
1 row in set (0.00 sec)
(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果
```

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno, deptno,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```

```sql
 create table t_product(
    -> deptno int primary key,
    -> dname varchar(20),
    -> loc varchar(40)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> insert into t_product
    -> values (10, "ACCOUNTING", "NEW YORK"),
    -> (20, "RESEARCH", "DALLAS"),
    -> (30, "SALES", "CHICAGO"),
    -> (40, "OPERATIONS", "BOSTON");
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> select * from t_product;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)
```

表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
```

```sql
create table t_employee(
    -> empno int primary key,
    -> ename varchar(20),
    -> job varchar(20),
    -> mgr int,
    -> hiredate date,
    -> sal float,
    -> comm float,
    -> deptno int
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO t_employee(empno, ename, job, MGR, Hiredate, sal, comm, deptno) VALUES
    -> (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
    -> (7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
    -> (7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
    -> (7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
    -> (7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
    -> (7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
    -> (7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
    -> (7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
    -> (7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
    -> (7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
    -> (7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10);
Query OK, 13 rows affected (0.01 sec)
Records: 13  Duplicates: 0  Warnings: 0

mysql> select * from t_employee;
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.00 sec)
```

3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`
```sql
INSERT INTO t_employee(empno, ename, job, MGR, Hiredate, sal, comm, deptno) VALUES
    -> (17061512,"jinxin","student",7782,"1999-05-05",null,null,10);
Query OK, 1 row affected (0.01 sec)

mysql>  select * from t_employee;
+----------+--------+-----------+------+------------+------+------+--------+
| empno    | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+----------+--------+-----------+------+------------+------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
| 17061512 | jinxin | student   | 7782 | 1999-05-05 | NULL | NULL |     10 |
+----------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.00 sec)
```

3.2 表中入职时间（Hiredate字段）最短的人。
```sql
select ename from t_employee where hiredate=(select max(hiredate) from t_employee);
+--------+
| ename  |
+--------+
| jinxin |
+--------+
1 row in set (0.01 sec)
```
3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
```sql
 select count(distinct(job)) from t_employee;
+----------------------+
| count(distinct(job)) |
+----------------------+
|                    6 |
+----------------------+
1 row in set (0.00 sec)
```
简单数据查询运算

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```sql
 update t_employee
    -> set comm=100
    ->  where ename='miller';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from t_employee;
+----------+--------+-----------+------+------------+------+------+--------+
| empno    | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+----------+--------+-----------+------+------------+------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 |  100 |     10 |
| 17061512 | jinxin | student   | 7782 | 1999-05-05 | NULL | NULL |     10 |
+----------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.00 sec)

mysql> select ename
    -> from t_employee
    -> where comm<100;
+--------+
| ename  |
+--------+
| TURNER |
+--------+
1 row in set (0.01 sec)
```

3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理；
```sql
select ename,sal+comm
    -> from t_employee;
+--------+----------+
| ename  | sal+comm |
+--------+----------+
| SMITH  |     NULL |
| ALLEN  |     1900 |
| WARD   |     1750 |
| JONES  |     NULL |
| MARTIN |     2650 |
| BLAKE  |     NULL |
| SCOTT  |     NULL |
| KING   |     NULL |
| TURNER |     1500 |
| ADAMS  |     NULL |
| JAMES  |     NULL |
| FORD   |     NULL |
| MILLER |     1400 |
| jinxin |     NULL |
+--------+----------+
14 rows in set (0.01 sec)
```

```sql
select count(ename) '人数',AVG(salary+comm) '平均收入' from t_employee;
+--------+--------------+
| 人数   | 平均收入     |
+--------+--------------+
|     14 |         1840 |
+--------+--------------+
```

3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
```sql
select t1.ename '我', t2.ename '下属'from t_employee t1 left join t_employee t2 on t1.empno=t2.mgr;
+--------+--------+
| 我     | 下属   |
+--------+--------+
| FORD   | SMITH  |
| BLAKE  | ALLEN  |
| BLAKE  | WARD   |
| KING   | JONES  |
| BLAKE  | MARTIN |
| KING   | BLAKE  |
| JONES  | SCOTT  |
| SCOTT  | ADAMS  |
| BLAKE  | JAMES  |
| JONES  | FORD   |
| ADAMS  | NULL   |
| ALLEN  | NULL   |
| JAMES  | NULL   |
| jinxin | NULL   |
| MARTIN | NULL   |
| MILLER | NULL   |
| SMITH  | NULL   |
| TURNER | NULL   |
| WARD   | NULL   |
+--------+--------+
19 rows in set (0.00 sec)
```

3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
```sql
 create view view_t
    -> as
    -> select empno,ename,job
    -> from t_employee;
Query OK, 0 rows affected (0.01 sec)

mysql> select * from view_t;
+----------+--------+-----------+
| empno    | ename  | job       |
+----------+--------+-----------+
|     7369 | SMITH  | CLERK     |
|     7499 | ALLEN  | SALESMAN  |
|     7521 | WARD   | SALESMAN  |
|     7566 | JONES  | MANAGER   |
|     7654 | MARTIN | SALESMAN  |
|     7698 | BLAKE  | MANAGER   |
|     7788 | SCOTT  | ANALYST   |
|     7839 | KING   | PRESIDENT |
|     7844 | TURNER | SALESMAN  |
|     7878 | ADAMS  | CLERK     |
|     7900 | JAMES  | CLERK     |
|     7902 | FORD   | ANALYST   |
|     7934 | MILLER | CLERK     |
| 17061512 | jinxin | student   |
+----------+--------+-----------+
14 rows in set (0.01 sec)
为了保护隐私不被别人侵犯
```

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？
```sql
alter table t_employee
    -> change column deptno
    -> int not null;
```
 实体完整性
 
3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引
```sql
create index index_ename
    -> on t_employee(ename);
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> show create table t_employee \G
*************************** 1. row ***************************
       Table: t_employee
Create Table: CREATE TABLE `t_employee` (
  `empno` int(11) NOT NULL,
  `ename` varchar(20) DEFAULT NULL,
  `job` varchar(20) DEFAULT NULL,
  `mgr` int(11) DEFAULT NULL,
  `hiredate` date DEFAULT NULL,
  `salary` float DEFAULT NULL,
  `comm` float DEFAULT NULL,
  `deptno` int(11) DEFAULT NULL,
  PRIMARY KEY (`empno`),
  KEY `index_ename` (`ename`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8
1 row in set (0.00 sec)
```
 为了提高从表中检索数据的速度

3.10 将表2的 sal 字段改名为 salary
```sql
alter table t_employee
    -> change sal salary float;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from t_employee;
+----------+--------+-----------+------+------------+--------+------+--------+
| empno    | ename  | job       | mgr  | hiredate   | salary | comm | deptno |
+----------+--------+-----------+------+------------+--------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |    800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 |   1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 |   1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 |   2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 |   1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 |   2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 |   5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 |   1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 |   1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |    950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 |   1300 |  100 |     10 |
| 17061512 | jinxin | student   | 7782 | 1999-05-05 |   NULL | NULL |     10 |
+----------+--------+-----------+------+------------+--------+------+--------+
14 rows in set (0.00 sec)
```

3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。
```sql
DELIMITER $$
mysql> CREATE FUNCTION func_get_deptno_from_empno (empno INT)
    -> RETURNS int
    -> BEGIN
    -> RETURN (SELECT deptno FROM t_employee WHERE t_employee.empno = empno);
    -> end$$
Query OK, 0 rows affected (0.00 sec)

mysql> delimiter ;
mysql> select func_get_deptno_from_empno(7369);
+----------------------------------+
| func_get_deptno_from_empno(7369) |
+----------------------------------+
|                               20 |
+----------------------------------+
1 row in set (0.01 sec)
```

4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；

```sql
create user 'jinxin'
    -> identified by '17061512';
Query OK, 0 rows affected (0.01 sec)
```

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。

4.2 显示该账号权限

```sql
select * from user \G
*************************** 1. row ***************************
                  Host: localhost
                  User: root
           Select_priv: Y
           Insert_priv: Y
           Update_priv: Y
           Delete_priv: Y
           Create_priv: Y
             Drop_priv: Y
           Reload_priv: Y
         Shutdown_priv: Y
          Process_priv: Y
             File_priv: Y
            Grant_priv: Y
       References_priv: Y
            Index_priv: Y
            Alter_priv: Y
          Show_db_priv: Y
            Super_priv: Y
 Create_tmp_table_priv: Y
      Lock_tables_priv: Y
          Execute_priv: Y
       Repl_slave_priv: Y
      Repl_client_priv: Y
      Create_view_priv: Y
        Show_view_priv: Y
   Create_routine_priv: Y
    Alter_routine_priv: Y
      Create_user_priv: Y
            Event_priv: Y
          Trigger_priv: Y
Create_tablespace_priv: Y
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin: mysql_native_password
 authentication_string: *2CB241218353BFEB472D9F73C779DB70968D127A
      password_expired: N
 password_last_changed: 2020-02-20 12:52:03
     password_lifetime: NULL
        account_locked: N
*************************** 2. row ***************************
                  Host: localhost
                  User: mysql.sys
           Select_priv: N
           Insert_priv: N
           Update_priv: N
           Delete_priv: N
           Create_priv: N
             Drop_priv: N
           Reload_priv: N
         Shutdown_priv: N
          Process_priv: N
             File_priv: N
            Grant_priv: N
       References_priv: N
            Index_priv: N
            Alter_priv: N
          Show_db_priv: N
            Super_priv: N
 Create_tmp_table_priv: N
      Lock_tables_priv: N
          Execute_priv: N
       Repl_slave_priv: N
      Repl_client_priv: N
      Create_view_priv: N
        Show_view_priv: N
   Create_routine_priv: N
    Alter_routine_priv: N
      Create_user_priv: N
            Event_priv: N
          Trigger_priv: N
Create_tablespace_priv: N
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin: mysql_native_password
 authentication_string: *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE
      password_expired: N
 password_last_changed: 2020-02-20 12:51:59
     password_lifetime: NULL
        account_locked: Y
*************************** 3. row ***************************
                  Host: %
                  User: jinxin
           Select_priv: N
           Insert_priv: N
           Update_priv: N
           Delete_priv: N
           Create_priv: N
             Drop_priv: N
           Reload_priv: N
         Shutdown_priv: N
          Process_priv: N
             File_priv: N
            Grant_priv: N
       References_priv: N
            Index_priv: N
            Alter_priv: N
          Show_db_priv: N
            Super_priv: N
 Create_tmp_table_priv: N
      Lock_tables_priv: N
          Execute_priv: N
       Repl_slave_priv: N
      Repl_client_priv: N
      Create_view_priv: N
        Show_view_priv: N
   Create_routine_priv: N
    Alter_routine_priv: N
      Create_user_priv: N
            Event_priv: N
          Trigger_priv: N
Create_tablespace_priv: N
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin: mysql_native_password
 authentication_string: *CC394FDAC55B6734D993509899E3567D9FC015BC
      password_expired: N
 password_last_changed: 2020-04-10 11:01:22
     password_lifetime: NULL
        account_locked: N
3 rows in set (0.00 sec)
```

4.3 `with grant option` 是什么意思。

```sql
传递权限
```

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？

符合第一范式，也符合第二范式，因为有主码empno，第一范式（1NF）是指数据库表的每一列都是不可分割的基本数据项，同一列中不能有多个值，即实体中的某个属性不能有多个值或者不能有重复的属性。如果出现重复的属性，就可能需要定义一个新的实体，新的实体由重复的属性构成，新实体与原实体之间为一对多关系。第二范式就是非主属性非部分依赖于主关键字

6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？

外模式是用户与数据库系统的接口，是用户用到的那部分数据的描述。它由若干个外部记录类型组成。
外模式也称子模式(Subschema)或用户模式，它是数据库用户（包括应用程序员和最终用户）能看见和使用的局部数据的逻辑结构和特征描述，是数据库用户的数据视图，是与某一应用有关的数据逻辑表示。对应于用户级。它是某个或某几个用户所看到的数据库的数据视图，是与某一应用有关的数据的逻辑表示。
内模式又称存储模式，对应于物理级，它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存储介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义所有内部记录类型、索引和文件的组织方式，以及数据控制方面的细节，它是数据库的存储观。”


8 什么是ACID？

“ACID，指数据库事务正确执行的四个基本要素的缩写。包含：原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）。一个支持事务（Transaction）的数据库，必须要具有这四种特性，否则在事务过程（Transaction processing）当中无法保证数据的正确性，交易过程极可能达不到交易方的要求。

8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？

选择数据库,查看当前事务隔离界别
```sql
 show variables like 'tx_isolation';
+---------------+-----------------+
| Variable_name | Value           |
+---------------+-----------------+
| tx_isolation  | REPEATABLE-READ |
+---------------+-----------------+
1 row in set, 1 warning (0.02 sec)
```

8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？

1） 图片、文件、二进制数据对数据库的读/写的速度永远都赶不上文件系统处理的速度，数据库备份变的巨大，越来越耗时间，对文件的访问需要穿越你的应用层和数据库层
2）短生命期数据使用情况统计数据，测量数据，GPS定位数据，session数据，任何只是短时间内对你有用，或经常变化的数据。
3）日志文件也许你的日志记录做的很保守，每次web请求只产生一条日志。 对于整个网站的每个事件来说，这仍然会产生大量的数据库插入操作，争夺你用户需要的数据库资源。
