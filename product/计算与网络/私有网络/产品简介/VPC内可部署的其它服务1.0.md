<style rel="stylesheet">
table th:nth-of-type(1){
width:200px;
}</style>
<style rel="stylesheet">
table th:nth-of-type(2){
width:200px;
}</style>
<style rel="stylesheet">
table th:nth-of-type(3){
width:200px;
}</style>
<style rel="stylesheet">
table th:nth-of-type(4){
width:200px;
}</style>
<style rel="stylesheet">
table tr:hover {
background: #efefef; 
</style>
云平台 VPC 可以许多其他 云平台 服务集成，它们之间的关系如下表所示：

## 1.计算与网络服务

| 产品 | 与 VPC 的关系 | 
|---------|---------|
|<a href="/product/cvm.html" target="_blank">云主机 CVM</a>| 您可将云主机部署在 VPC 中 |
|<a href="/product/clb.html?idx=2" target="_blank">负载均衡 CLB</a>|您可以在私有网络内部署内网 LB 或者公网 LB|
|<a href="/product/nat.html" target="_blank">NAT 网关</a>|可用于私有网络内流量访问 Internet|
|<a href="/product/crc.html" target="_blank">跨地域互联 CRC</a>|可用于连接多个地域的私有网络|
|<a href="/product/vpn.html" target="_blank">VPN 连接</a>|通过 IPsec VPN 连接私有网络和用户 IDC|
|<a href="/product/dc.html" target="_blank">专线接入 DC</a>|通过专线连接私有网络和用户 IDC|
|<a href="/product/bcm.html" target="_blank">基础监控  BCM</a>|为 VPC内某些服务的关键指标提供自定义告警|

## 2. 数据库服务
|产品 |与 VPC 的关系 | 
|---------|---------|
|<a href="/product/cdb.html" target="_blank">云数据库MySQL</a>|您可在私有网络部署该数据库服务，该服务将占用私有网络 IP 资源|
|<a href="/product/sqlserver.html" target="_blank">云数据库 SQLServer</a>|同上|
|<a href="/product/cdb.html" target="_blank">云数据库 TDSQL</a>|同上|
|<a href="/product/postgresql.html" target="_blank">云数据库 PostgreSQL</a>|同上|
|<a href="/product/cmem.html" target="_blank">云缓存 Memcached</a>|同上|
|<a href="/product/mongodb.html" target="_blank">云数据库  MongoDB</a>|同上|
|<a href="/product/HBase.html" target="_blank">云数据库  HBase</a>|同上|