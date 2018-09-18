# Introduction

## 连接管理与安全性

## 并发控制

### 读写锁

### 锁力度

- 表锁
- 行级锁

## 事务

- 原子性
- 一致性
- 隔离性
- 持久性

## 隔离级别

- READ UNCOMMITTED 未提交读
- READ COMMITTED 提交读
- REPEATABLE READ 可重复读
- SERIALIZABLE 可串行化

## 死锁

`解决方案`
- 死锁检测
- 死锁超时

## 事务日志

### MySQL中的事务

`自动提交`

```bash
SHOW VARIABLES LIKE 'AUTOCOMMIT';

# 如果要开启
SET AUTOCOMMIT = 1;
```

`隐式和显式锁定`
InnoDB采用的是`两阶段锁定协议`

## 多版本并发控制 MVCC

InnoDB的MVCC是通过在每行记录后面添加两个隐藏的列实现的，
一个是行的创建时间，一个是过期时间(或删除时间)，存储的不是实际的时间值而是系统版本号。
每开启一个事务，系统版本号自增。


## MySQL的存储引擎

```bash
mysql> SHOW TABLE STATUS LIKE 'user'\G
*************************** 1. row ***************************
           Name: user
         Engine: InnoDB
        Version: 10
     Row_format: Dynamic
           Rows: 265
 Avg_row_length: 741
    Data_length: 196608
Max_data_length: 0
   Index_length: 114688
      Data_free: 0
 Auto_increment: 337
    Create_time: 2018-09-03 11:26:13
    Update_time: 2018-09-03 11:27:15
     Check_time: NULL
      Collation: utf8_general_ci
       Checksum: NULL
 Create_options:
        Comment:
```
