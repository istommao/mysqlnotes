# 一些命令

## 查看mysql的运行时长
```shell
mysql> show global status like 'uptime';
```

## 查看mysql的timeout配置
```shell
mysql> show global variables like '%timeout';

+----------------------------+----------+
| Variable_name              | Value    |
+----------------------------+----------+
| connect_timeout            | 10       |
| delayed_insert_timeout     | 300      |
| innodb_lock_wait_timeout   | 50       |
| innodb_rollback_on_timeout | OFF      |
| interactive_timeout        | 28800    |
| lock_wait_timeout          | 31536000 |
| net_read_timeout           | 30       |
| net_write_timeout          | 60       |
| slave_net_timeout          | 3600     |
| wait_timeout               | 28800    |
+----------------------------+----------+
```

## mysql请求链接进程被主动kill
```shell
mysql> show global status like 'com_kill';

+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| Com_kill      | 21    |
+---------------+-------+
```

## 最大允许的包大小

```shell
mysql> show global variables like 'max_allowed_packet';
```

---

- https://blog.csdn.net/lovemysea/article/details/79121154
- https://stackoverflow.com/questions/6516943/lost-connection-to-mysql-server-during-query
