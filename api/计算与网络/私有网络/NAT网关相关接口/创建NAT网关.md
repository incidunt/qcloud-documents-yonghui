## 1. 接口描述
本接口(CreateNatGateway)用于创建NAT网关 </br>
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>

使用该接口前请前往<a href="/doc/product/215/1682" title="网关说明" >NAT网关说明</a>了解NAT网关特性

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为CreateNatGateway。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| natName | 是 | string | NAT网关名称，支持1-25个中文、英文大小写的字母、数字和下划线分隔符。 |
| vpcId | 是 | string | 私有网络ID或者统一ID，建议使用统一ID,可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询。 |
| maxConcurrent | 是 | int | 网关并发连接上限，例如：1000000、3000000、10000000，具体支持数据请参见<a href="/doc/product/215/1682" title="网关说明" >私有网络网关说明</a>。 |
| bandwidth | 否 | int | 网关最大外网出带宽(单位:Mbps), 默认: 100Mbps, 具体支持数据请参见<a href="/doc/product/215/1682" title="网关说明" >私有网络网关说明</a>。 |
| assignedEipSet.n | 否 | string | 绑定网关的弹性IP数组, assignedEipSet和autoAllocEipNum至少传一个，例如：assignedEipSet.0=10.0.0.1 ，更多关于弹性IP的信息请参考<a href="" title="">弹性IP</a>。|
| autoAllocEipNum | 否 | int | 需要新申请的弹性IP个数，系统会按您的要求生产N个弹性IP, assignedEipSet和autoAllocEipNum至少传一个，更多关于弹性IP的信息请参考<a href="" title="">弹性IP</a>。 |



## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | int | 错误码。0：成功, 其他值：失败|
| message | string | 错误信息|
| billId | string | 订单ID，创建结果可调用<a href="/document/product/215/4088" title="查询NAT网关的生产状态">查询NAT网关的生产状态</a>查询 |

## 4. 错误码表
以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。
 
| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的 VPC，VPC 资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询 VPC |
| InvalidNatGatewayName | NAT 网关名称不合法。NAT 网关名称取值范围：1-60个中文、英文大小写的字母、数字和下划线分隔符 |
| NatGatewayLimitExceeded | 创建的 NAT 网关数量超过上限。更多VPC资源限制信息详见<a href="/doc/product/215/537" title="VPC使用限制">VPC使用限制</a> |

## 5. 示例
输入
<pre>
http://vpc.api.qcloud.com/v2/index.php?Action=CreateNatGateway
&<<a href="/doc/api/229/6976">公共请求参数</a>>
&natName=zhezhe
&vpcId=314
&maxConcurrent=1000000
&bandwidth=10
&autoAllocEipNum=1
</pre>
输出
```
{
    "code":"0",
    "message":"",
    "billId":"20160415160000002485253313199244"
}
```

