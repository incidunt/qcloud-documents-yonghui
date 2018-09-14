## 功能简介
CC 防护功能支持对公网用户访问特定 URL 的行为进行频率控制，人机识别，封禁恶意的高频访问行为。

## 配置示例 
本配置示例可实现，当单个源 IP 在 10 秒内访问` /test.html `超过 10 次，恶意访问惩罚功能将封禁此源 IP 30 分钟。
 
1. 进入网站管家 WAF主界面，单击【防护设置】，单击需要防护的站点域名，单击【CC防护设置】选项卡进入恶意访问惩罚配置界面。
![CC防护设置](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/waf/CC_01.png)
2. 单击【添加规则】，在规则名称输入框里面输入具体的规则名称、选择匹配条件（等于），具体的URI（`/test.html`），以及访问频次（10次10秒），选择执行动作封禁访问（也可以选择人机识别，人机识别采用一定的算法进行验证，如果验证失败后，将自动封禁访问），惩罚时长输入 10 分钟。
![CC防护设置](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/waf/CC_02.png)
3. 单击【添加】保存规则，此时规则将会生效，惩罚恶意访问行为。
![CC防护设置](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/waf/CC_03.png)

