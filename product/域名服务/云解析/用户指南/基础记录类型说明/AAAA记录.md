### 什么情况下会用到AAAA记录？

当您希望访问者通过IPv6地址访问您的域名时，可以使用AAAA记录。

### AAAA记录的添加方式

![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/static/img/8e432533340ec0b090eaeaecdee73e2e/4A-1.png)

![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/static/img/fdba290c73675f5b526eecab58cbd352/4A-2.png)

1. 主机记录处填子域名（比如需要www.123.com ，只需要在主机记录处填写www即可；如果只是想添加123.com的解析，主机记录直接留空，系统会自动填一个“@”到输入框内）。

2. 记录类型为AAAA。

3. 线路类型（默认为必填项，否则会导致部分用户无法解析；在上图中，默认的作用为：除了联通用户之外的所有用户，都会指向ff06:0:0:0:0:0:0:c3）。

4. 记录值为ip地址，只可以填写IPv6地址。

5. TTL为缓存时间，数值越小，修改记录各地生效时间越快，默认为600秒。