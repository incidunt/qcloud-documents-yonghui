## 云平台私有网络是什么？
云平台私有网络（Virtual Private Cloud，VPC）是一块您在云平台上自定义的逻辑隔离网络空间，与您在数据中心运行的传统网络相似，托管在云平台私有网络内的是您在云平台上的服务资源，包括[云服务器](http://www.qcloud.com/doc/product/213/495)、[负载均衡](http://www.qcloud.com/doc/product/214/524)、[云数据库](http://www.qcloud.com/doc/product/236)等云服务资源。您可以完全掌握您的私有网络环境，包括自定义网段划分、IP地址和路由策略等，并通过[网络ACL](http://www.qcloud.com/doc/product/215/5132)和[安全组](http://www.qcloud.com/doc/product/213/500)等实现多层安全防护。同时，您也可以通过[IPsec VPN](http://www.qcloud.com/doc/product/215/4956)/[专线](http://www.qcloud.com/doc/product/215/4976)连通私有网络与您的数据中心，灵活部署混合云。

## 为什么选择云平台私有网络？
- **无需网络设备采购、简化运维**----在云平台私有网络内，您可以通过控制台或API自定义网段划分、创建子网、配置路由表和网关等，以软件定义网络，节省设备及运维成本。
- **全球部署、跨账户互通**----通过[对等连接](http://www.qcloud.com/doc/product/215/5000)服务，您可以在一分钟内互联海内外多地云资源，轻松实现全球同服和两地三中心容灾部署。同时，通过跨账号对等连接，您还可与云平台上的其它合作伙伴实现数据互通，快速构建开放式云端生态。
- **高性能、灵活Internet访问**----支持1000W并发连接、5Gbps带宽的双机热备[NAT网关](http://www.qcloud.com/doc/product/215/4975)帮助您轻松打破Internet访问性能瓶颈。您还可以通过[弹性IP](http://www.qcloud.com/doc/product/213/1941)灵活绑定云资源的服务，轻松配置哪些实例可以访问Internet。
- **轻松部署混合云**---- 稳定可靠的[IPsec VPN](http://www.qcloud.com/doc/product/215/4956)/[专线](http://www.qcloud.com/doc/product/215/4976)连接云平台私有网络至您的数据中心，您可根据业务量弹性扩展应用程序的云服务器等资源，既降低了企业IT运维成本，又不用担心企业核心数据的扩散，轻松构建混合云。
- **安全无死角**----云平台私有网络是一个内外网隔离的网络环境，通过[网络ACL](http://www.qcloud.com/doc/product/215/5132)和[安全组](http://www.qcloud.com/doc/product/213/500)分别从子网和主机维度控制网络流量，可以精确到协议和端口级粒度，多维度、全方位满足您网络安全需求。

## 选择私有网络 or 基础网络？
云平台上的网络分为私有网络和基础网络，其中：
- 基础网络是云平台上所有用户的公共网络资源池（如左图所示）。所有[云服务器](http://www.qcloud.com/doc/product/213/495)的内网 IP 地址由云平台统一分配，配置简单，使用方便，适合对操作易用性要求比较高、需要快速使用云服务器的场景。
- 私有网络是指用户在云平台上建立的一块逻辑隔离的网络空间（如右图所示）。在私有网络内，用户可以自由定义网段划分、IP地址和路由策略。与基础网络相比，私有网络更适合有网络自定义配置需求的场景。
![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/static/img/f1c113751199560fb87bc002b4bf0207/image.png)
    　　　　　    　　　　　  图1： 基础网络和私有网络对比图
						
私有网络和基础网络的功能区别如下表所示：

| 功能 | 私有网络| 基础网络 |
|---------|---------|---------|
| 租户关联 | 基于GRE封装的逻辑隔离网络| 租户关联 |
| 网络自定义 | 支持| 不支持|
| 路由自定义 | 支持| 不支持 |
| 自定义IP | 支持| 不支持 |
| 互通规则 |支持跨地域跨账号互通| 同租户同地域互通 |
| 安全控制　| [安全组](http://www.qcloud.com/doc/product/213/500)和[网络ACL](http://www.qcloud.com/doc/product/215/5132)| 安全组 |

## 快速使用
- 了解云平台VPC时，通常会涉及到一些基本概念，点击查看[名词解释](http://www.qcloud.com/doc/product/215/4925)。
- 如果这是您第一次开始使用云平台私有网络，要获得有关云平台VPC的实践介绍，请完成练习[VPC快速入门](http://www.qcloud.com/document/product/215/8119)。该练习将指导您完成创建带有子网的VPC并在您的子网中启动云主机实例访问公网。
- 下表列出了您在使用云平台VPC服务时，可为您提供帮助的相关资源。

| 资源 | 说明 | 
|---------|---------|
| [VPC主要功能](http://www.qcloud.com/doc/product/215/3075)  | VPC的功能简介| 
| [VPC使用限制](http://www.qcloud.com/doc/product/215/537)  | VPC内服务使用的约束| 
| [云平台VPC文档](http://www.qcloud.com/doc/api/245) | API文档和开发者指南| 
|  [云平台VPC购买指导](http://www.qcloud.com/doc/product/215/3079)| 计费及到期通知等信息|
|   [云平台VPC论坛](http://bbs.qcloud.com/forum-83-1.html)| 社区论坛，用于讨论云平台VPC的技术性问题。|
| [常见问题](http://www.qcloud.com/doc/product/215/6512)   | VPC的常见问题| 
| [帮助中心]( http://www.qcloud.com/help/page/vpc/1)| VPC的帮助中心 |
|[联系我们](http://www.qcloud.com/doc/product/282/1558)| 我们专业的工程师团队将为您提供7 * 24小时不间断的技术服务。|
