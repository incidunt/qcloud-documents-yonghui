
本文档主要介绍如何快速使用 Windows 系统的云服务器实例的相关功能，引导新手快速了解云服务器的创建和配置。


## 步骤一：准备与选型

### 确定云服务器所在地域及可用区
地域选择原则：
 - 靠近用户原则。
请根据您的用户所在地理位置选择云服务器地域。云服务器越靠近访问客户，越能获得较小的访问时延和较高的访问速度。比如：您的用户大部分位于长江三角洲附近时，上海地域是较好的选择。
 - 内网通信同地域原则。
同地域内，内网互通；不同地域，内网不通。需要多个云服务器内网通信的用户须选择相同云服务器地域。
相同地域下的云服务器可以通过内网相互通信（内网通信）。
不同地域之间的云服务器不能通过内网互相通信（通信需经过公网）。

## 步骤二：创建 Windows 云服务器

本步骤介绍 Windows 云服务器的创建，云平台提供快速配置 和自定义配置两种方式。本部分以快速配置为例说明，若快速配置不能满足您的需求，您可参考 [自定义配置 Windows 云服务器](/doc/product/213/10516) 文档进行配置。

 1. 登录云平台官网，选择【云产品】-【计算与网络】-【云服务器】，单击【立即选购】按钮，进入 [云服务器购买页面](http://buy.tcecqpoc.fsphere.cn/?tab=custom&devPayMode=hourly&regionId=50000019&zoneId=50190001&instanceType=S2.SMALL1&step=1&bandwidthType=TRAFFIC_POSTPAID_BY_HOUR) 。

 2. 选择镜像。选择符合需求的 Windows 操作系统。
 
 3. 选择机型。
 
 4. 选择地域。靠近您客户的地域可降低访问延迟，提高下载速度。
 
 5. 选择公网带宽。若不需要连接到公网，带宽值选 0 。
 
 6.  选择服务器数量与购买时长。
 
快速配置使用自动生成的密码，创建后密码会通过站内信发送给您。
查看更多默认配置，在快速购买页面顶部，将鼠标留置【更多默认配置】即可。

查看站内信请见下一步骤。
 

## 步骤三：登录 Windows 云服务器

本部分操作介绍登录 Windows 云服务器的常用方法，不同情况下可以使用不同的登录方式，此处介绍控制台登录，更多登录方式请见   [登录 Windows 实例](/doc/product/213/5435) 。

### 前提条件

登录到云服务器时，需要使用管理员帐号和对应的密码。

 * 管理员账号：对于 Windows 类型的实例，管理员帐号统一为 Administrator
 * 密码：快速配置中，初始密码由系统随机分配。在下一环节（查看站内信及云服务器信息）中，具体查看操作。
   更多内容请参考 [登录密码](/doc/product/213/6093) 。
   
### 查看站内信及云服务器信息

完成云服务器的购买和创建后，云服务器的实例名称、公网 IP 地址、内网 IP 地址、登录名、初始登录密码等信息都将以 [站内信](http://console.tcecqpoc.fsphere.cn/message) 的方式发送到账户上。

 1. 登录 [云服务器控制台](http://console.tcecqpoc.fsphere.cn/cvm) 。登录后即可看到公网 IP 地址、内网 IP 地址等信息。

 2. 单击右上角【站内信】。

 3. 站内信页面即可查看新创建的云服务器，及登录名与密码等信息。

## 步骤四：格式化与分区数据盘

这里以 Windows 2012 R2 为例进行格式化说明。

### 前提条件

 - 已购买数据盘的用户，需要格式化数据盘才可使用。未购买数据盘的用户可以跳过此步骤。
 - 请确保您已完成步骤三操作，登录到云服务器。

### 格式化数据盘

 1. 通过步骤三介绍的方法登录 Windows 云服务器。

 2. 单击【开始】-【服务器管理器】-【工具】-【计算机管理】-【存储】-【磁盘管理】。

 3. 在磁盘1上右键单击，选择【联机】：
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/1217193557509925a622dcdb81aa2e35/image.png)

 4. 右键单击，选择【初始化磁盘】：  
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/94ab92867d77ea69bc803a0b20f2b941/image.png)

 5. 根据分区方式的不同，选择【GPT】或【MBR】，单击【确定】按钮：
 > **注意：**
 > 磁盘大于 2TB 时仅支持 GPT 分区形式。若您不确定磁盘后续扩容是否会超过该值，则建议您选择 GPT 分区；若您确定磁盘大小不会超过该值，则建议您选择 MBR 分区以获得更好的兼容性。
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/1f7b0f72767193cfa662e188c86cf31b/image.png)

### 磁盘分区（可选）

 1. 在未分配的空间处右击，选择【新建简单卷】：
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/a6ca720af2082d7a470ece17a8e13f5d/image.png)

 2. 在弹出的“新建简单卷向导”窗口中，单击【下一步】：
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/10fdcd70b510a57919c6a40cf43452a7/image.png)

 3. 输入分区所需磁盘大小，单击【下一步】：
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/05c8d1425a0208597b1d2c75a9c811b6/image.png)

 4. 输入驱动器号，单击【下一步】：  
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/737ed569049ad617715efb06fe44e7b2/image.png)

 5. 选择文件系统，格式化分区，单击【下一步】：
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/896cb3f2705fb9fcd04c236b8fb9ec59/image.png)

 6. 完成新建简单卷，单击【完成】：  
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/1e257b9c76d80f30b34f612496b8007b/image.png)

 7. 在【开始】中打开【这台电脑】，查看新分区：
	![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/1cbb4ad1c3c01852a00a1415526a3e12/image.png)

**至此，您已完成 Windows 系统的云服务器的创建和基础配置。**
