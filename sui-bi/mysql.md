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



