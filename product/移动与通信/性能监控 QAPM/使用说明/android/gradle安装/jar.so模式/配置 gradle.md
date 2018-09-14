1. 使用 gradle 安装的，首先打开工程根目录下的 build.gradle
 ![](http://imgcache.tcecqpoc.fsphere.cn/image/main.qcloudimg.com/raw/18f37f7a8bd2271cac31f2e9a4fb1850.png)

2. 在 android 模块中添加
```
sourceSets {
    main {
        jniLibs.srcDir(['libs'])
    }
}
```
![](http://imgcache.tcecqpoc.fsphere.cn/image/main.qcloudimg.com/raw/7fa7055484fbc715d717fd7bfebce966.png)

3. 在 dependencies 模块中添加代码
```
compile files('libs/MagnifierSDK.jar')
```
![](http://imgcache.tcecqpoc.fsphere.cn/image/main.qcloudimg.com/raw/fb73598035a87a5a5badbd8c12cc6fe0.png)