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
