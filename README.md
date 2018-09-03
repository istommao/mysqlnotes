# mysqlnotes
mysql notes

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
