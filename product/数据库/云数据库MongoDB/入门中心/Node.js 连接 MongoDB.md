以下详细介绍了在 Windows 系统中 Node.js 连接 MongoDB 的示例。
## 先决条件
1. 在云平台[选购一台 CVM](http://buy.tce.fsphere.cn/cvm)，本文档以 Windows Server 2012 R2 版本为示例。
2. 在云平台[选购 MongoDB](http://buy.tce.fsphere.cn/mongodb)。
3. 在 CVM 中[下载 Node.js](http://nodejs.org/en/download/)。

## 安装驱动
进入[云平台控制台](http://console.tcecqpoc.fsphere.cn/cvm/index)，登录刚刚购买的 CVM ，在左下角【开始】处单击右键，再单击【命令提示符】， 打开 cmd 命令行，进入 nodejs 根目录。
```
cd C:\Program Files\nodejs
```
使用 npm 命令安装驱动。
>**注意：**
>如遇安装不成功可尝试更换源，`npm config set registry http://registry.cnpmjs.org`。

```
npm install mongodb --save
```

出现如下图信息，安装驱动成功。
![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/c00a020f550ffb3afe9f2f5ee38859d4/npm.png)

## 连接示例
在 nodejs 根目录创建 test.js 文件，保存以下代码：
```
'use strict';

var mongoClient = require('mongodb').MongoClient,
    assert = require('assert');

// 拼接URI
var url = 'mongodb://Mongouser:【密码】@【内网地址】:27017/admin';

mongoClient.connect(url, function(err, db) {
    assert.equal(null, err);
    var db = db.db('local'); // 选择一个db
    var col = db.collection('demoCol'); // 选择一个集合(表)
   // 插入数据
    col.insertOne(
        {
            a: 1,
            something: "yy"
        }, 
        //可选参数
        //{
        //    w: 'majority' // 开启 “大多数”模式，保证数据写入Secondary节点
        //}, 
        function(err, r) {
            console.info("err:", err);
            assert.equal(null, err);
            // 断言写入成功
            assert.equal(1, r.insertedCount);
            // 查询数据
            col.find().toArray(function(err, docs) {
                assert.equal(null, err);
                console.info("docs:", docs);
                db.close();
            });
        }
    );
});
```
在命令提示符中输入`node test.js`，输出如下结果，Node.js 连接 MongoDB 示例成功。
![](http://imgcache.tcecqpoc.fsphere.cn/image/mc.qcloudimg.com/static/img/18779d11d3619f1fcbc7bcd8cf253fb5/image.png)

以上为连接示例，后续您可自由编写代码部署应用程序。

## 相关说明
云平台 MongoDB 默认提供了 “rwuser” 和 “mongouser” 两个用户名分别支持 “MONGODB-CR” 和 “SCRAM-SHA-1” 两种认证方式，对于这两种认证方式，连接 URL 需要做不同的处理，详情请参考[连接示例](/document/product/240/3563)。