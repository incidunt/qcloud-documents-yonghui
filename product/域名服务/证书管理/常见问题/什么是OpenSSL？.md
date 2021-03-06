OpenSSL是用于安全通信的著名开源密码学工具包，包括主要的密码算法、常见密码和证书封装功能。

#### 1. OpenSSL官网

官方下载地址： http://www.openssl.org/source/

#### 2. Windows安装方法

OpenSSL官网没有提供windows版本的安装包，可以选择其他开源平台提供的工具。例如 http://slproweb.com/products/Win32OpenSSL.html 
以该工具为例，安装步骤和使用方法如下：

2.1 选择32位或者64位合适的版本下载，例如Win64OpenSSL_Light-1_0_2h.exe：
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/static/img/cc4da6cc001f66481967485fb6a035d6/openssl-1.png)

2.2 设置环境变量，例如工具安装在C:\OpenSSL-Win64，则将`C:\OpenSSL-Win64\bin；`复制到Path中
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/static/img/48f68528c408e6b7f83956fed009f3b7/openssl-2.png)

2.3 打开命令行程序cmd（以管理员身份运行），进入2_www.domain.com.key、1_www.domain.com_cert.crt所在目录，运行以下命令
```
openssl pkcs12 -export -out www.domain.com.pfx -inkey 2_www.domain.com.key -in 1_www.domain.com_cert.crt
```
例如key和crt文件保存在 D:\ ，运行情况如下：
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/static/img/2388c2fe32dc0bbe32347566fdfb6464/openssl-3.png)
Ps：Export Password不需要可以直接回车不进行输入。

2.4 则在 D:\ 已生成www.domain.com.pfx 文件，可以继续完成在IIS管理器中的证书安装。