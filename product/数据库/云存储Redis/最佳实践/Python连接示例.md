**运行前必备**：

下载并安装
redis-py  
http://github.com/andymccurdy/redis-py?spm=5176.730001.3.11.WvETSA

**示例代码**：

```
\#!/usr/bin/env python   
\#-*- coding: utf-8 -*- 
import redis 

\#这里替换为连接的实例host和port 
host = '192.168.0.195' 
port = 6379 

\#这里替换为实例id和实例password 
user='username' 
pwd='password' 

\#连接时通过password参数指定AUTH信息，由user,pwd通过":"拼接而成 
r = redis.StrictRedis(host=host, port=port, password=user+':'+pwd) 

\#连接建立后就可以进行数据库操作，详情文档参考http://github.com/andymccurdy/redis-py 
r.set('name', 'python_test'); 
print r.get('name')
```

**运行结果**：<br>
![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/Pythpon-1.png)