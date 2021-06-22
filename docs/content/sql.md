**连表查询**

    1 外连接：
        1 左连接 left join / left outer jion   [左外连接包含left join左表所有行，如果左表中某行在右表没有匹配，则结果中对应行右表的部分全部为空(NULL).]
            select * from ta1 left join ta2 on ta1.id = ta2.id
        2 右连接 right join / right outer join
            select * from ta1 right joi ta2 on ta1.id = ta2.id
        3 完全外连接 full join / full outher join   [完全外连接包含full join左右两表中所有的行，如果右表中某行在左表中没有匹配，则结果中对应行右表的部分全部为空(NULL)，如果左表中某行在右表中没有匹配，则结果中对应行左表的部分全部为空(NULL)。]
            select * from ta1 full join ta2 on ta1.id =ta2.id
    2 内连接 join / inner join
        select * from ta1 inner join ta2 on ta1.id=ta2.id
            相当于：
        select * from ta1,ta2 where ta1.ID=ta2.ID
    
    3 交叉连接 ：cross join
        select * from ta1 cross join ta2  [没有 WHERE 子句的交叉联接将产生连接所涉及的表的笛卡尔积。第一个表的行数乘以第二个表的行数等于笛卡尔积结果集的大小。]
    
    4 合并查询结果
        select id from stu UNION select stu_id from score

**表的操作**
    
    1 更新表记录
        update 表名 set 列名=值 where 条件
    
    2  删除记录
        delete from 表名 where 条件
    
    3 插入记录
        insert into 表名 values();
    
    4 删除整个表
        drop table 表名
    
    5 创建表
        create table 表名(列名1 类型 约束，。。。)；
    
    6 更改表结构
        alter table 表名 add/drop 列名｜约束名

**查看当前使用的哪个数据库**

    1 select database();
    2 show  tables;
    3 status;

**统计函数**

    1 查询表中有多少数据
        select count(code) frome tabName; 
    
    2 查询最大值
        select max(code) from tabName;
    
    3 查询最小值
        select min(code) from tabName;
    
    4 查询总和
        select sum(code) from tabName;
    
    5 查询平均值
        select avg(code) from tabName;

**分组查询**

    1 查询所有系中数量大于2的
        select * from tabName group by code having count(*) > 2;

**分页查询**

    跳过几条数据取几条数据
        select * from tabName limit 0,5 

**去重查询**

    select distinct code from tabName;

**函数和存储过程的区别**

    1 函数有返回值，存储过程没有
    2 函数可以在select语句中使用，存储过程不能



**随机查询&排除中文：**

> 1. 随机查询一条数据：
>    1. *SELECT* * FROM tableName *ORDER* *BY*  RAND() limit 1 
>    2. select * 
> 2. SELECT * FROM tableName ORDER BY RAND() LIMIT 100
> 3. 排除中文：SELECT * FROM tableName WHERE memberAccount REGEXP '^[1-9A-Za-z]' ORDER BY RAND() LIMIT 100
> 4. 只选择中文：SELECT memberAccount FROM uic_member_login_account WHERE NOT memberAccount REGEXP '^[1-9A-Za-z]' ORDER BY RAND() LIMIT 100
>
> https://blog.csdn.net/weixin_30316097/article/details/97576927
>
> https://blog.csdn.net/weixin_32484447/article/details/113317286?utm_term=mysql查询过滤中文&utm_medium=distribute.pc_aggpage_search_result.none-task-blog-2~all~sobaiduweb~default-1-113317286&spm=3001.4430
>
> 

https://zhuanlan.zhihu.com/p/91749976

http://blog.itpub.net/31407649/viewspace-2639500/
