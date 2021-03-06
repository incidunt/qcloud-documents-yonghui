## 1 云数据库适用于哪些业务场景？

MySQL适用的地方都可以使用云数据库。相比于自行搭建MySQL，使用云数据库更加方便和可靠。

云数据库完全兼容MySQL协议，同时提供master-slave热备和定时冷备服务，此外支持实例无缝升级，可最大程度减少开发者在部署、监控、扩容和故障恢复等方面的投入，使开发者可以集中精力进行产品开发和运营。



## 2 使用云数据库前要做什么准备？

开发者需要考虑：

(1) 你的应用是否适合使用DB？比如数据量小、访问量高、key-value存储的场景就应该考虑使用内存级持久化存储服务“云缓存Memcached”。

(2) 考虑一下你的数据库设计是否合理？比如有明显访问热点或者数据量过大的表，则应该考虑拆分成多个表。 

## 3 云数据库对数据量有什么限制？

详见：[云数据库数量限制](/doc/product/236/使用限制#1-数据量限制)

## 4 使用云数据库的注意事项？
详见：[云数据库操作限制](/doc/product/236/使用限制#7-操作限制 )

## 5 如何登录云数据库？

开发人员通过IP/Port的方式就可以完全控制和管理MySQL实例，无需登录到服务器进行操作。

可通过命令行或者云数据库管理台登录云数据库，详见：登录云数据库。

## 6 如何授权其他用户操作云数据库？

root用户可以使用mysql的grant命令对其他用户进行授权，注意不能使用grant all进行授权。

目前shutdown和file权限没有开放给root用户，因此root不能新建拥有所有权限的用户。

授权时，请参考以下命令：
```
grant SELECT,INSERT, UPDATE, DELETE, CREATE, DROP, ALTER on *.* to 'myuser'@'%' identified by 'mypasswd';
```

## 7 是否可以自助修改MySQL实例的配置？

MySQL实例的配置由云数据库统一管理，并支持部分参数的自助修改，详细请参考下面的问题#21. 如何修改云数据库配置参数？

## 8 云数据库如何对MySQL进行管理？

开发者不需要对MySQL进行日常管理，日常的维护和调整由云数据库运维系统完成。

当MySQL出现异常时，运维系统会及时发现并通知运维人员处理，开发者不需要做任何变更操作。

## 9  云数据库中运行的MySQL版本是多少？

云数据库中使用的MySQL版本为5.1.54、5.5.24

## 10 云数据库执行任务是否有缓冲？

问题描述：

在很短的时间，送入了N条SQL语句给云数据库执行，此时云数据库会逐条执行，还是卡死？如果会卡死，那么同时的连接并发数限制是多少？

问题解答：

云数据库提供的MySQL实例与平时我们自己安装的MySQL实例是一样的。并发执行的语句是否会卡死跟系统资源和SQL语句本身有关。

如果连接数max_connections到达极限值，那么该实例基本上已经无法正常提供服务，一般是由以下原因造成的：

（1）业务程序bug导致的空连接过多；

（2）前端过来的访问远远超出实例的处理能力；

（3）某个连接执行了太久地占用了MySQL的独占资源，导致大量的访问请求被阻塞。

## 11  云数据库连接故障诊断及解决方案

当使用云数据库出现连接故障时，首先确认你的云数据库实例的IP、端口、用户、密码，然后在你的应用机器上通过命令行登录云数据库：
```
mysql -h IP -P 端口号 -u root -p 云数据库密码
```

下面是出现的问题类型及解决方案：
```
(1) ERROR 1045(28000)：Access denied for user...
```
当出现“Access denied for user ‘xxx’@‘x.x.x.x’(using password:YES)”的提示语时，表明密码不正确。

请确认你输入的云数据库密码是否正确，如果重复输入正确信息后仍然报该错，则请提交工单联系技术支持。 

```
(2) ERROR 1040(00000):Too many connections
```
当出现“ERROR 1040(00000):Too many connections”的提示语时，表明云数据库实例当前最大连接数超过了限制（云数据库实例的最大连接数限制详见这里）。

请检查程序，适当减少数据库的连接数。如果减少连接数后仍然报该错，则请通过提交工单联系技术支持。 

```
(3) ERROR 2003 (HY000): Can't connect to MySQL server...
```

当出现“ERROR 2003 (HY000): Can't connect to MySQL server on 'x.x.x.x' (111)”的提示语时，表明云数据库地址不能连通，请确认你输入的云数据库的IP、端口信息是否正确。如果重复输入正确信息后仍然报该错，则请通过提交工单联系技术支持。

## 12 云数据库后面是否是实体机？

云数据库后面是实体机。

## 13 云数据库会帮我做分库分表吗？

因为分库分表的标准和业务逻辑相关，所以云数据库不会帮业务做分库分表。

## 14 云数据库的默认字符集编码能修改么？

可以修改。

默认字符集说明以及修改方法详见：云数据库使用限制#6. 字符集说明。 

## 15 如何查看云数据库慢查询日志？

可通过云数据库数据导出工具获取慢查询日志，详见：云数据库冷备数据提取。

## 16 开发者自己如何备份数据？

云数据库实例每天会进行全量备份，开发者也可以采用云数据库提供的多线程快速导入导出工具进行备份，详见手动备份与恢复云数据库,或者通过mysqldump工具自己备份数据。

## 17 云数据库如何统计访问次数？

云数据库的访问次数根据MySQL状态变量Queries计算得来。

## 18 云数据库占用空间与使用空间的区别？

开发者看到的云数据库占用空间会大于使用空间，这是由于统计占用空间的时候包含了binlog等日志数据。云数据库是按实际使用空间计费的。

## 19 如何申请云数据库实例slave只读权限开放/关闭？

如果需要开放/关闭slave只读，请按照模版提交工单申请。

## 20 连接云数据库的MySQL客户端的版本有什么限制吗？

详见：云数据库使用限制#3. 连接云数据库的MySQL客户端的版本限制。

## 21 如何修改云数据库配置参数？

开发者可通过命令行和phpMyAdmin，修改云数据库配置参数：

### 1. 命令行方式

以下变量可以通过执行“set global var_name=var_value”语法运行时动态修改，10分钟左右将自动同步到本机文件，迁移或重启将保持设置后的值。其中常见的var_name包括如下变量：
<table class="t">
<tbody><tr>
<th>  变量
</th><th>  说明
</th></tr>
<tr>
<td> character_set_server
</td><td> 服务器默认字符集
</td></tr>
<tr>
<td> connect_timeout
</td><td> 连接超时
</td></tr>
<tr>
<td> long_query_time
</td><td> 超过该时间的查询为慢查询
</td></tr>
<tr>
<td> max_allowed_packet
</td><td> 最大包长度
</td></tr>
<tr>
<td> max_connections
</td><td> 最大连接数
</td></tr>
<tr>
<td> sql_mode
</td><td> 当前的服务器SQL模式
</td></tr>
<tr>
<td> table_open_cache
</td><td> 所有线程打开表的个数，增大该值可以增加mysqld被请求打开的文件描述符个数
</td></tr>
<tr>
<td> wait_timeout
</td><td> 非交互连接超时时间
</td></tr></tbody></table>

### 2. phpMyAdmin

通过phpMyAdmin登录云数据库后，点击上面菜单中的“变量”，在下面的变量列表中，点击需要修改的变量对应的值，对其进行修改。

![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/faq_cdb_1.png)

更多请参考[云数据库可以修改的配置.](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/doc/cdb_user_modify_var.xls) 

## 22 云数据库的连接数有限制吗？
详见：[云数据库链接数限制](/doc/product/236/使用限制#2-连接数限制)

## 23 云数据库的binlog保存时间是多久？

详见：[云数据库的binlog保存时间说明](/doc/product/236/使用限制#5-云数据库的binlog保存时间说明 )

## 24 云数据库的慢查询时间是多久？

云数据库的慢查询时间(long_query_time)的默认值是10秒，用户可以自行修改，命令如下：
```
set global long_query_time = 1;
```
详细请参考[MySQL官方手册](http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_long_query_time)


## 25 为什么查看云数据库中的中文数据时出现乱码？
开发者将数据存储到云数据库中时，请先到管理中心云数据库的“管理视图”页面查看该实例的默认字符集，在编写程序时，将character_set_client、character_set_results、character_set_connection设置为和云数据库实例相同的字符集。否则，如果存储的数据中有中文，会出现中文数据乱码的现象。

例如：云数据库实例的默认字符集为utf8，在编写程序连接数据库时，需要先执行以下语句，再将中文数据存储到云数据库。
```
SET NAMES 'utf8';
```

## 26 能否通过公网地址访问云数据库？

国内地域的云数据库外网访问已正式发布，使用方式请参考：[外网访问](/doc/product/236/外网访问)

香港与北美地域暂不支持外网访问。

如果您需要通过公网访问，可以通过在有公网IP的云服务器上搭建MySQL Proxy的方式，利用MySQL Proxy进行访问。

详细请参考[MySQL Proxy官方手册](//dev.mysql.com/downloads/mysql-proxy/)

搭建方法参考如下：

1).下载mysql-proxy安装包到云服务器
 ```
wget http://cdn.mysql.com/Downloads/MySQL-Proxy/mysql-proxy-0.8.4-linux-glibc2.3-x86-64bit.tar.gz
```

2).解压上述安装包
```
tar -xzf mysql-proxy-0.8.4-linux-glibc2.3-x86-64bit.tar.gz 
```

3).查看解压出来的目录
	 
ls mysql-proxy-0.8.4-linux-glibc2.3-x86-64bit 目录下包含有bin、lib、libexec等目录： bin、libexec目录包含mysql proxy等程序，lib目录带有程序依赖的库，如glibc、pcre等。 请保持bin、lib、libexec目录的相对路径关系，避免找不到依赖的库。

4).进入mysql proxy所在目录并运行
```
cd mysql-proxy-0.8.4-linux-glibc2.3-x86-64bit/bin 
./mysql-proxy --proxy-backend-addresses=10.**.**.17:3306 --proxy-address=:4040 
```

参数介绍：
--proxy-backend-addresses=10.**.**.17:3306， 云数据库的ip和端口,您需要把其中的10.**.**.17:3306换成您的云数据库的ip和端口。

--proxy-address=:4040，代理的监听地址和端口。默认是":4040"，表示本机所有4040端口的所有ip。 

还可以在命令后面添加一些参数：

--daemon，让代理处于后台运行

--keepalive，代理崩溃后尝试重启代理


运行命令后，会显示如下信息，提示代理搭建成功：
```
2014-09-01 11:56:38: (critical) plugin proxy 0.8.4 started 
```
如果没有成功启动，欢迎咨询我们。

该代理的监听端口是4040,我们接下来测试代理能否成功转发。

5). 从外网访问云服务器上的mysql proxy。

在一台外网机子运行【假设外网ip为182.*.*.2】 mysql -h 182.*.*.2 -P 4040 -u root -p 按提示输入您的云数据库密码后，看是否成功登录云数据库。 如果登录失败，请检查：

     a.第4)步中云数据库的ip和端口是否正确。
     b.外网机子是否能ping通云服务器的外网ip
     c.云服务器是否成功启动mysql proxy。
		 
## 27 phpMyAdmin上传文件的限制

云数据库目前可以通过phpMyAdmin导入/导出sql数据文件。在导入上传文件时，文件必须是sql文件或者压缩（tar、bz2、zip）的sql文件，而且文件的大小不能超过2M。

## 28 如何导出数据库数据？

1，如果需要导出冷备数据，请使用冷备提取工具导出，详见云数据库冷备数据提取

2，如果需要导出实时数据，可以申请从库访问权限，通过从库mysqldump获取

## 29 为什么云数据库默认会有tencentroot这个用户？

tencentroot是云数据库的内部系统管理帐户。为确保云数据库的正常工作，切勿删除该帐户。

## 30 如何获知云数据库磁盘空间不足了？

监控中心对云数据库的磁盘空间进行了监控，当云数据库的使用空间超过90%的时候就会触发短信和邮件告警，这里只需要在云监控中配置好对应的告警接收人，当空间不足的时候就能收到告警。

具体配置可以查看请点击这里。

## 31 密码重置

1 登录云平台，进入管理中心，点击“云产品”模块的“云数据库”，进入云数据库“管理视图”页面。

![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/cdb_login1.png)

2 找到待重置密码的云数据库实例，在实例后点击“配置”按钮。

![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/cdb_passwdrs.png)


3 在云数据库管理页面，点击密码后的“忘记密码”。

![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/cdb_fpasswdrs.png)

4 在忘记密码页面，输入验证码后，点击“我要修改密码”按钮，重置密码邮件将会发送到页面中显示的电子邮箱，如下图所示：

![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/cdb_fpasswdrs2.png)

5 登录页面中显示的电子邮箱，打开邮件中的链接，进入重置密码页面

![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/cdb_email.png)

6 在重置密码页面，输入新密码及验证码后，点击“确定修改”，完成云数据库的密码重置。

![](http://imgcache.tcecqpoc.fsphere.cn/image/qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/cdb_passwdrs2.png)