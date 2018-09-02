# 配置


## 开启binlog

`/etc/my.cnf 中添加以下配置`

```bash
[mysqld]
log_bin=/data/logs/mysql/binarylog
server-id=1
binlog-do-db=dbname
binlog_format=mixed
expire_logs_days=9
max_binlog_size = 500M
binlog_cache_size = 128K
```
