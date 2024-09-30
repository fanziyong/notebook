# mysql的常用命令

## 1. 登录mysql

```
mysql -u root -p
```

## 2. 显示所有数据库

```
SHOW DATABASES;
```

## 3. 选择数据库

```
USE database_name;
```

## 4. 显示所有表

```
SHOW TABLES;
```

## 5. 显示表结构

```
DESCRIBE table_name;
```

## 6. 创建数据库

```
CREATE DATABASE database_name;
```

## 7. 删除数据库

```
DROP DATABASE database_name;
```

## 8. 创建表

```
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
    ...
);
```

## 9. 删除表

```
DROP TABLE table_name;
```

## 10. 插入数据

```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

## 11. 更新数据

```
UPDATE table_name
SET column1 = value1, column2 = value2, column3 = value3, ...
WHERE condition;
```

## 12. 删除数据

```
DELETE FROM table_name
WHERE condition;
```

## 13. 查询数据

```
SELECT column1, column2, column3, ...
FROM table_name
WHERE condition;
``` 

## 14. 排序数据

```
SELECT column1, column2, column3, ...
FROM table_name
ORDER BY column1, column2, column3, ... [ASC|DESC];
``` 

## 15. 分组数据

```
SELECT column1, column2, column3, ...
FROM table_name
GROUP BY column1, column2, column3, ...;
```                                                                 
## 16. 联结数据

```                                                                 
SELECT column1, column2, column3, ...
FROM table1
JOIN table2
ON table1.column1 = table2.column1;
```                                                                 

## 17. 子查询

```                                                                 
SELECT column1, column2, column3, ...
FROM table1
WHERE column1 IN (SELECT column1 FROM table2 WHERE condition);
```                                                           
## 18. 索引

```                                                           
CREATE INDEX index_name
ON table_name (column1, column2, column3, ...);
```                                                           
## 19. 事务

1. 开启事务

```
START TRANSACTION;
```

2. 提交事务

```
COMMIT;
```

3. 回滚事务

```
ROLLBACK;
``` 

## 20. 锁定表

```
LOCK TABLES table_name WRITE;
``` 

## 21. 解锁表

```
UNLOCK TABLES;
``` 

## 22. 导出数据

```
SELECT * FROM table_name INTO OUTFILE 'file_name';
```

## 23. 导出数据库结构

```
mysqldump \
  -h ip -P port \
  -u username -password \
  --single-transaction \
  --set-gtid-purged=OFF \
  --no-data \
  Platform_DataNode > Platform_DataNode-schema.sql

mysqldump \
  -h ip -P port \
  -u username -password \
  --single-transaction \
  --set-gtid-purged=OFF \
  --ignore-table=Platform_DataNode.ArchiveAsset \
  --ignore-table=Platform_DataNode.Asset \
  --ignore-table=Platform_DataNode.AudioAsset \
  --ignore-table=Platform_DataNode.ImageAsset \
  --ignore-table=Platform_DataNode.VideoAsset \
  Platform_DataNode > Platform_DataNode-data.sql

mysqldump \
  -h ip -P port \
  -u username -password \
  --single-transaction \
  --set-gtid-purged=OFF \
  --ignore-table=Platform_DataCore.Permission \
  --ignore-table=Platform_DataCore.PermissionBackup \
  --ignore-table=Platform_DataCore.PermissionBackup2 \
  Platform_DataCore > Platform_DataCore.sql
```