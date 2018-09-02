# 源码安装

```bash
# 下载安装包

wget https://jaist.dl.sourceforge.net/project/boost/boost/1.59.0/boost_1_59_0.tar.gz

wget https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.23.tar.gz


# 新建MySQL用户和用户组
groupadd -r mysql
useradd -r -g mysql -s /sbin/nologin -M mysql
```

`预编译`
```bash
# 解压
tar -zxvf mysql-5.7.23.tar.gz
tar -zxvf boost_1_59_0.tar.gz

mkdir -p /data/mysql

cd mysql-5.7.23

cmake . -DCMAKE_INSTALL_PREFIX=/usr/local/mysql \
-DMYSQL_DATADIR=/data/mysql \
-DWITH_BOOST=/root/boost_1_59_0 \
-DSYSCONFDIR=/etc \
-DWITH_INNOBASE_STORAGE_ENGINE=1 \
-DWITH_PARTITION_STORAGE_ENGINE=1 \
-DWITH_FEDERATED_STORAGE_ENGINE=1 \
-DWITH_BLACKHOLE_STORAGE_ENGINE=1 \
-DWITH_MYISAM_STORAGE_ENGINE=1 \
-DENABLED_LOCAL_INFILE=1 \
-DENABLE_DTRACE=0 \
-DDEFAULT_CHARSET=utf8mb4 \
-DDEFAULT_COLLATION=utf8mb4_general_ci \
-DWITH_EMBEDDED_SERVER=1

# 安装
make install
```

```bash
# 启动mysqld
cp support-files/mysql.server /lib/systemd/system

systemctl start mysqld

# 查看 mysqld 状态
systemctl status mysqld

# 客户端
cp client/mysql /usr/local/bin/
```

`参数`
- DCMAKE_INSTALL_PREFIX= 数据库程序安装路径;
- DMYSQL_DATADIR= 数据库文件存放路径（不配置的话会默认创建$PREFIX_DIR/data）
- DMYSQL_UNIX_ADDR= 默认位置是/tmp/mysql.sock
- DDEFAULT_CHARSET= 默认数据库编码
- DDEFAULT_COLLATION= 默认数据库整理编码
- DWITH_EXTRA_CHARSETS= 扩展支持编码(all | utf8,gbk,gb2312 | none)
- DWITH_MYISAM_STORAGE_ENGINE= MYISAM引擎支持(1|0)
- DWITH_INNOBASE_STORAGE_ENGINE= innoDB引擎支持(1|0)
- DWITH_MEMORY_STORAGE_ENGINE= MEMORY引擎支持(1|0)
