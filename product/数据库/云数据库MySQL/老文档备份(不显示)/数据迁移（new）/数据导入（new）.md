在线热迁移提供CVM自建MySQL数据库到CDB的在线热迁移功能，用户可在不停服的情况下对数据进行迁移,具有公网IP/Port的本地IDC或其他云上MySQL数据库迁移至与数据库CDB服务。
目前，迁移工具仅支持广州和上海地域.

## 1. 准备
### 1.1注意事项
自建迁移工具分为冷备数据导出和增量数据同步两步操作，其中，冷备数据导出过程会对源库负载产生一定的影响，建议在业务低峰期做数据库迁移。
外网迁移特性目前仅支持基础网络的CDB实例。

### 1.2 预先检查以下几项
  1.  检查目标CDB实例必须为空实例，不能有已创建的库表；
  2.  检查版本目前仅支持（5.1/5.5/5.6）相同版本，以及5.1->5.5，5.5->5.6；
  3.  检查目标CDB实例容量必须大于源实例；
  4.  在源MySQL数据库上创建迁移账号（若有已授权可用于数据迁移的账号，也可不创建）；

		GRANT ALL PRIVILEGES ON *.* TO "迁移账号"@"%" IDENTIFIED BY "迁移密码";
		FLUSH PRIVILEGES;
  5.  确认mysql变量
      通过 SHOW GLOBAL VARIABLES LIKE 'XXX'; 
      查看mysql全局变量，确认当前状态是否可以进行迁移：
			server_id > 1
			log_bin	= ON;
			binlog_format =	ROW/MIXED
			binlog_row_image = FULL
			innodb_stats_on_metadata = 0
  6.  修改变量到指定值：
      a.  修改mysql配置文件my.cnf，需重启：
				log-bin=binlog

      b.  动态修改配置：
				set global server_id = 99;
				set global binlog_format=ROW;
				set global binlog_row_image=FULL;
				set global innodb_stats_on_metadata = 0;
				
## 2. 操作步骤
1.	登录控制台，进入迁移页面
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a76ba50e7cb.png)
2.	创建迁移任务
 点击创建迁移任务，输入任务名称、源库和目标CDB for MySQL的信息。
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a7653c6f568.png)

 然后选择要迁移的数据库(可选择全部迁移或部分库表迁移)，创建并检查迁移任务信息。
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a76670eceb8.png)
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a765eb2bb88.png)
**注：**
**数据迁移**：将选中数据库中的数据导出，然后在TDSQL中导入。
**增量同步**：在进行数据导出导入后，设置TDSQL为源库的备库，进行主备增量同步。

3. 校验迁移任务信息
 在创建完迁移任务后，您需要对迁移任务信息进行校验，只有所有校验项通过后才能启动迁移任务。任务校验存在3种状态：

 通过：表示校验完全通过
 警告：表示校验不通过，迁移过程中或迁移后可能影响数据库正常运行但不影响迁移任务的执行。
 失败：表示校验不通过，无法进行迁移。如果校验失败，请根据出错的校验项，检查并修改迁移任务信息，然后重试校验。失败原因请参考：“校验失败说明”
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a767198f5b7.png)
4.	启动迁移
在校验通过后，您可以启动迁移任务，如果您设定了迁移任务的定时时间，则迁移任务会在设定的时间开始排队并执行，如果没有设置定时任务，则迁移任务会立即执行。
迁移启动后，您可以在迁移任务下看到对应的迁移进度信息。
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a767afe0b8c.png)
注：由于系统设计限制，一次性提交或排队多个迁移任务将按排队时间串行执行。

5.	增量同步
在创建迁移任务时默认必选增量同步选项，在数据迁移完成后，会将目标CDB for MySQL库设置成源数据库的备库，通过主备同步来把迁移过程中源库的新增的数据同步到目标CDB for MySQL库中。此时，源库上的修改都会同步到目标CDB for MySQL中，你可以把业务切换到目标CDB for MySQL上，然后点击完成迁移。
点击完成迁移后，主备同步关系会断开。

6.	终止迁移
在迁移过程中，如果您需要停止迁移，可以点击中止按钮进行中止。
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a76843ea5a9.png)
注意：再次启动可能导致校验失败或任务失败，您可能需要手动清空目标库内的数据，才能再次启动迁移任务。

5、迁移单独的表时，需保证所有表外键依赖的表必须被迁移；
