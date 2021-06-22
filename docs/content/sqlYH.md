**sql语句优化相关**

1. 不用*来代替所有列名，尽量采用与访问表相关的实际列名

2. 尽量减少表的查询次数。

3. 对查询进行优化，应尽量避免全表扫描，首先应考虑在 where 及 order by 涉及的列上建立索引

    ***索引的建立和删除：***

        建立索引：
        create index indexName on tableName(字段名词[asc/desc])

        删除索引：
        drop index indexName on tableName

4. 应尽量避免在 where 子句中对字段进行 null 值判断，否则将导致引擎放弃使用索引而进行全表扫描，如：

    select id from t where num is null

    可以在num上设置默认值0，确保表中num列没有null值，然后这样查询：

    select id from t where num=0

    设置默认值语句：

        update tableName set 列名='默认值'
        or
        alter table tableName add default(默认值) for 字段名
    
    删除默认值

        alter table tableName drop constraint 默认值约束的名称

    -查看某字段的默认值-

        select [name] 
        from sysobjects t 
        where id = (select cdefault from syscolumns where id = object_id(N'表名') and name='字段名') 

5. 应尽量避免在 where 子句中使用 or 来连接条件，否则将导致引擎放弃使用索引而进行全表扫描，如：

    select id from t where num=10 or num=20

    可以这样查询：

    select id from t where num=10

    union all

    select id from t where num=20

6. in 和 not in 也要慎用，否则会导致全表扫描，如：

    select id from t where num in(1,2,3)

    对于连续的数值，能用 between 就不要用 in 了：

    select id from t where num between 1 and 3
7. 如果在 where 子句中使用参数，也会导致全表扫描。因为SQL只有在运行时才会解析局部变量，但优化程序不能将访问计划的选择推迟到运行时；它必须在编译时进行选择。然而，如果在编译时建立访问计划，变量的值还是未知的，因而无法作为索引选择的输入项。如下面语句将进行全表扫描：

    select id from t where num=@num

    可以改为强制查询使用索引：

    select id from t with(index(索引名)) where num=@num

8. 应尽量避免在 where 子句中对字段进行表达式操作，这将导致引擎放弃使用索引而进行全表扫描。如：

    select id from t where num/2=100

    应改为:

    select id from t where num=100*2

9. 应尽量避免在where子句中对字段进行函数操作，这将导致引擎放弃使用索引而进行全表扫描。如：

    select id from t where substring(name,1,3)='abc'--name以abc开头的id

    select id from t where datediff(day,createdate,'2005-11-30')=0--'2005-11-30'生成的id

    应改为:

    select id from t where name like 'abc%'

    select id from t where createdate>='2005-11-30' and createdate<'2005-12-1'

10. 不要写一些没有意义的查询，如需要生成一个空表结构：

    select col1,col2 into #t from t where 1=0

    这类代码不会返回任何结果集，但是会消耗系统资源的，应改成这样：

    create table #t(...)
11. 很多时候用 exists 代替 in 是一个好的选择：

    select num from a where num in(select num from b)

    用下面的语句替换：

    select num from a where exists(select 1 from b where num=a.num)

12. 尽量使用表变量来代替临时表。如果表变量包含大量数据，请注意索引非常有限（只有主键索引）

13. 在新建临时表时，如果一次性插入数据量很大，那么可以使用 select into 代替 create table，避免造成大量 log ，以提高速度；如果数据量不大，为了缓和系统表的资源，应先create table，然后insert。

14. 如果使用到了临时表，在存储过程的最后务必将所有的临时表显式删除，先 truncate table ，然后 drop table ，这样可以避免系统表的较长时间锁定。

https://www.cnblogs.com/xc-chejj/p/11244748.html
****

1. 表连接优化

    1.驱动表的选择： 驱动表是指被最先访问的表；

    2.where子句连接顺序： 表连接最好都在where条件以前

2. 索引合理使用

https://www.jianshu.com/p/ddc7bb66a311

****



