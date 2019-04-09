### Insert
插入单条数据,句式:
```
insert into table_name(field1,field2,field3...) values(value1,value2,value3...)
```
插入多条语句,句式:
```
insert into table_name(field1,field2,field3...) values(value1,value2,value3...)
```
批量插入语句,句式:
```
insert into 要插入数据的目标表或者视图名 select 检索语句
```
将存储过程或SQL处理的结果集插入到目标表中,句式:
```
insert into target_table(field1,field2,field3...)
EXEC stored_procedure
```
创建新表并将查询结果集数据插入到表中(目标表的结构和数据是基于源表的,但不会从源表复制:约束、索引、触发器和权限.),句式:
```
select field1,field2,field3... into target_table from raw_table
```
将文件中的数据插入到一个现有表中,句式:
```
bulk insert target_table from 'date_file_path' with
(
datafiletype='',
fieldterminator='',
rowterminator=''
)
```

### Update
基本的更新，句式：
```
update target_table set field1=value1,field2=value2,field3=value3...
where ...
```
基于子查询更新，句式：
```
update target_table set(field1,field2,field3...)=(Select field1,field2,field3... from table where 查询条件) 
```

借助事务更新（防止误操作），句式：
```
begin tran update ... rollback
```
基于联接的更新(先from，后where，再update)，句式：
```
update OD set dicount+=0.5 from dbo.OrderDetails as OD join dbo.Orders as O on OD.orderid=O.orderid where O.custid=1
```
### Delete
基本的删除,句式：
```
delete from target _table where ...
```
基于连接的删除(先from，后where，再delete)，句式：
```
delete from tableA from tableA as A inner join tableB as B on A.field1=B.field1 where B.field2>25
```
```
delete A from tableA as A inner join tableB as B on A.field1=B.field2 where B.field2>25
```
删除符合条件的部分数据，句式：
```
delete TOP(20) from tableA where field1>25
```

### Truncate
truncate会删除表中所有的数据并重置表结构（删掉表然后重建）。当目标表被外键约束引用时，即使引用表（父表）为空或外键被禁用，也不运用使用truncate删除表（可以通过建一个虚拟表，带有指向引用表的外键（可以禁止外键以防影响性能），以此来避免truncate的误操作）。
```
truncate table target_table;
```