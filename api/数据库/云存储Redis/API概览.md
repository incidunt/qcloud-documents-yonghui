## 1. 地域相关接口
| 接口名 | Action Name | 功能描述 |
|---------|---------|---------|
| [查询售卖可用区](/doc/api/260/4951) | DescribeRedisZones | 查询可以购买redis的可用区列表。 |
| [查询可售卖规格](/doc/api/260/4974) | DescribeRedisProduct | 查询可购买实例的规格，比如最大容量、可购买数量等。 |


## 2. 实例相关接口

| 接口名 | Action Name | 功能描述 |
|---------|---------|---------|
| [创建实例](/doc/api/260/5325) | CreateRedis | 按照指定的规格、网络等配置，创建redis实例。|
| [升级实例](/doc/api/260/5328)| UpgradeRedis | 升级实例到指定的规格。|
| [查询订单详情](/doc/api/260/5329) | DescribeRedisDealDetail | 查询订单详细信息。|
| [查询 CRS 实例及实例列表](/doc/api/260/1384) | DescribeRedis |  按条件查询实例详情列表。 | 
| [修改CRS实例密码](/document/product/239/8405) | ModfiyRedisPassword | 修改实例密码。|
| [重置CRS实例密码](/document/product/239/1390) | ResetRedisPassword | 重置实例密码。|
| [修改Redis实例项目](/doc/api/260/1385) | ModifyRedisProject |  修改实例所属项目。 |
| [修改CRS实例名称](/document/api/239/8431) | ModifyRedisName |  修改CRS实例名称。 | 
| [清空CRS实例](/doc/api/260/1386) | ClearRedis |  清空实例数据。 | 
| [CRS查询任务结果](/doc/api/260/1387) | DescribeTaskInfo | 查询任务执行结果。 |
| [手动备份 CRS 实例](/document/product/239/8402) | ManualBackupInstance | 手动备份 CRS 实例。 |
| [查询 CRS 实例备份列表](/document/product/239/8403) | GetRedisBackupList | 查询 CRS 实例备份列表。 |  
| [恢复 CRS 实例](/document/product/239/8401) | RestoreInstance | 恢复 CRS 实例。 |
| [导出CRS实例备份](/document/product/239/8430) | ExportRedisBackup | 导出CRS实例备份。 |  
| [查询 CRS 实例的任务列表](/document/product/239/8404) | GetRedisTaskList | 查询 CRS 实例的任务列表。 |
