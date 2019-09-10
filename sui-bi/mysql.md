## 主从同步

## 主数据库基本配置-master

##### my.ini

```
# Server Id.
server-id=1
##开启主从复制，主库配置
log-bin=mysql3306-bin
##指定同步的数据库，如果不指定则同步所有数据库
binlog-do-db=weather_data
```

#### 在master中添加一个mysql主从复制需要的账号 {#hmastermysql}

```
GRANT REPLICATION SLAVE,RELOAD,SUPER ON *.*
TO mysql_backup@'localhost' //从机ip号 
IDENTIFIED BY '123123';
flush privileges;
```

#### 查看master的status {#hmasterstatus}

```
mysql> show master status;
+------------------+----------+--------------+------------------+-------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set |
+------------------+----------+--------------+------------------+-------------------+
| mysql-bin.000005 |      761 | demodb       |                  |                   |
+------------------+----------+--------------+------------------+-------------------+
```

## 从数据库基本配置-slave

##### my.ini

```
#"server-id必须有且不能和其他master或slave重复"
server-id         = 1001
replicate-do-db      = demodb
#log-bin              = mysql-bin
#binlog-ignore-db  = mysql       #不备份的数据库
#binlog-ignore-db  = information_schema
#binlog-ignore-db  = performation_schema
#binlog-ignore-db  = sys
#log-slave-updates = 1
#read_only           = 1

--------------

server-id=2
relay-log-index=slave-relay-bin.index
relay-log=slave-relay-bin
```

#### slave连接master库 {#hslavemaster}

```
stop slave;

change master to master_host='localhost',
master_port=3310,
master_user='mysql_backup',
master_password='123123',
master_log_file='mysql-bin.000005',
master_log_pos=761;

start slave;


-----------------
change master to 
master_host='192.168.3.21',
master_user='root',
master_password='237502',
master_log_file='mysql-bin.000005',
master_log_pos=761;

show slave status \G
```



