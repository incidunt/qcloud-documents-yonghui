## 1. 集群相关接口
| 接口功能 | Action ID | 功能描述
|---------|---------|---------|
| 查询集群列表 | [DescribeCluster](/doc/api/457/9448) | 用于查询集群列表
| 创建集群 | [CreateCluster](/doc/api/457/9444) |用于创建集群
| 删除集群 | [DeleteCluster](/doc/api/457/9445) | 用于删除集群
| 查询集群节点列表 | [DescribeClusterInstances](/doc/api/457/9449) |  用于查询集群节点，该接口返回集群内节点信息
| 扩展集群节点 | [AddClusterInstances](/doc/api/457/9447) |  用于集群扩展节点
| 删除集群节点 | [DeleteClusterInstances](/doc/api/457/9446) |  用于删除集群节点
| 添加已存在云主机到集群 | [AddClusterInstancesFromExistedCvm](/doc/api/457/9450) | 用于添加已存在的云主机到集群
 
## 2. 服务相关接口
| 接口功能 | Action ID | 功能描述
|---------|---------|---------|
| 查询服务列表 | [DescribeClusterService](/doc/api/457/9440) | 用于查询服务列表，该接口返回的列表只包含服务的扼要信息
| 查询服务详情 | [DescribeClusterServiceInfo](/doc/api/457/9441) | 用于查询单个服务详情
| 创建服务 | [CreateClusterService](/doc/api/457/9436) | 用于创建服务
| 修改服务 | [ModifyClusterService](/doc/api/457/9434) | 用于更新服务
| 删除服务 | [DeleteClusterService](/doc/api/457/9437) | 用于删除服务
| 修改服务描述 | [ModifyServiceDescription](/doc/api/457/9435) | 用于修改服务描述
| 获取服务事件列表 | [DescribeServiceEvent](/doc/api/457/9443) | 用于查询服务最近一小时的事件列表
| 继续服务更新 | [ResumeClusterService](/doc/api/457/9442) | 用于继续被暂停中的服务更新
| 暂停服务更新 | [PauseClusterService](/doc/api/457/9439) | 用于暂停升级中的服务
| 回滚服务 | [RollBackClusterService](/doc/api/457/9438) | 用于回滚服务至升级前的配置，只能回滚至上一个配置

## 3. 服务实例相关接口
| 接口功能 | Action ID | 功能描述
|---------|---------|---------|
| 查询服务实例列表 | [DescribeServiceInstance](/doc/api/457/9433)|  用于查询服务的实例列表
| 修改服务实例副本数 | [ModifyServiceReplicas](/doc/api/457/9431) | 用于修改服务的容器数量
| 删除服务实例 | [DeleteInstances](/doc/api/457/9432) | 用于删除实例

## 4. 命名空间相关接口
| 接口功能 | Action ID | 功能描述
|---------|---------|---------|
| 查询集群命名空间 | [DescribeClusterNameSpaces](/doc/api/457/9430) | 用于查询集群的命名空间
| 创建集群命名空间 | [CreateClusterNamespace](/doc/api/457/9428) |  用于创建命名空间
| 删除集群命名空间 | [DeleteClusterNamespace](/doc/api/457/9429) | 用于删除命名空间

