## Packetfor query is too large \(\*\*\*&gt; 4194304\). You can change this value on theserver by setting the max\_allowed\_packet' variable.

* 错误描述

从错误中, 我们看到是 一次插入的数据过大, 大于了设置的4M. 也提示了解决方案"Youcan change this value on the server by setting the max\_allowed\_packet'variable."

* 解决方法

```
查看配置：show VARIABLES like'%max_allowed_packet%';

1.  临时更改
 set global max_allowed_packet =2*1024*1024*10;

2.  永久更改
 修改配置文件
 max_allowed_packet=20M
 重启服务
```



