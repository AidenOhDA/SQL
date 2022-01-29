
2022/1/23
1. from yyyyMMdd to TIMESTAMP
### Hive
```sql
select cast(concat_ws('-', substr({date_col},1,4),substr({date_col},5,2),substr({your_col},7,2))) as timestamp)
--> 2020-03-20 3:20:00
```

### Presto
```sql
select date_format(from_unixtime(to_unixtime(cast('yyyy-MM-dd' as timestamp)),9,'%Y-%M-%d %H:%i:%s')
--> 2020-03-20 3:20:00
```

2. from yyyyMMdd to DATE
### Hive
```sql
select date_format(from_unixtime(from_unixtime(unix_timestamp({your_col}, 'yyyyMMdd'), 'yyyy-MM-dd')
--> 2020-03-20
```

### Presto
```sql
select date_format(from_unixtime(to_unixtime(cast('yyyy-MM-dd' as timestamp)),9,'%Y%m%d')
--> 2020929
```

3. from TIMESTAMP to yyyy-MM-dd 
### Hive
```sql
select to_date(from_unixtime(unix_timestamp({your_col}))) 
--> 2020-03-20
```

### Presto
```sql
select date_format(date({your_col}),'%y-%m-%d')
--> 2020-03-20
```

4. from TIMESTAMP to yyyyMMdd 
### Hive
```sql
select regexp_replace(to_date(from_unixtime(unix_timestamp({your_col}))),'-','')
--> 20200320
```

### Presto
```sql
select date_format(date({your_col}),'%y%m%d')
--> 20200320
```

This is so interesting MD
<textarea border-style:dotted="border-style:dotted" class="markdown" disabled="disabled">
# test1
</textarea>


