[TOC]

# insert overwrite table ... select ...

## 语法与说明

### 语法

```sql
INSERT OVERWRITE TABLE tablename1 [PARTITION  (partcol1=val1, partcol2=val2 ...) [IF NOT EXISTS]] \
select_statement1 FROM from_statement;
```

示例：
```sql
insert overwrite table ods_data_lxcs.test_sun2
select sflsh,sfsj,yhbh,sfn,sfy,fy,sfxz,fq_sjzq from ods_data.ods_zlsgs_sflsls
```

### 说明

如果查询出来的数据类型和插入表格对应的列数据类型不一致，将会进行转换，但是不能保证转换一定成功，比如如果查询出来的数据类型为int，插入表格对应的列类型为string，可以通过转换将int类型转换为string类型；但是如果查询出来的数据类型为string，插入表格对应的列类型为int，转换过程可能出现错误，因为字母就不可以转换为int，转换失败的数据将会为NULL。
　
insert overwrite是删除原有数据然后在新增数据，如果有分区那么只会删除指定分区数据，其他分区数据不受影响。

## insert overwrite table ... select ... 与 insert into table ... select ... 的区别

**overwrite会覆盖现有的数据，而into是直接将数据写入表**

