###Insert
���뵥������,��ʽ:
```
insert into table_name(field1,field2,field3...) values(value1,value2,value3...)
```
����������,��ʽ:
```
insert into table_name(field1,field2,field3...) values(value1,value2,value3...)
```
�����������,��ʽ:
```
insert into Ҫ�������ݵ�Ŀ��������ͼ�� select �������
```
���洢���̻�SQL����Ľ�������뵽Ŀ�����,��ʽ:
```
insert into target_table(field1,field2,field3...)
EXEC stored_procedure
```
�����±�����ѯ��������ݲ��뵽����(Ŀ���Ľṹ�������ǻ���Դ���,�������Դ����:Լ������������������Ȩ��.),��ʽ:
```
select field1,field2,field3... into target_table from raw_table
```
���ļ��е����ݲ��뵽һ�����б���,��ʽ:
```
bulk insert target_table from 'date_file_path' with
(
datafiletype='',
fieldterminator='',
rowterminator=''
)
```