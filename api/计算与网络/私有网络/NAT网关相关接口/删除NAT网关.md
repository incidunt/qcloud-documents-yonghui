## 1. 接口描述

本接口(DeleteNatGateway)用于删除NAT网关
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>

删除 NAT 网关后，系统会自动删除路由表中包含此 NAT 网关的路由项。

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/document/product/215/4772" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为DeleteNatGateway。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 私有网络ID或者统一ID，建议使用统一ID，例如：vpc-xfd55df |
| natId | 是 | String | 系统分配的高可用网关统一ID，例如：nat-7t9nf3pu |


## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 错误码。0: 成功, 其他值: 失败|
| message | String | 错误信息|
| taskId | Int | 任务ID，操作结果可以用taskId查询，详见<a href="/document/product/215/5094">查询任务执行结果接口</a>。 |

## 4. 错误码表
以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。

| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的VPC，VPC资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询VPC |
| InvalidNatGatewayId.NotFound | 无效的NAT网关，NAT网关资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/4088" title="DescribeNatGateway">DescribeNatGateway</a>接口查询NAT网关 |


## 5. 示例
输入
<pre>
http://vpc.api.qcloud.com/v2/index.php?Action=DeleteNatGateway
&<<a href="/document/product/215/4772">公共请求参数</a>>
&vpcId=190
&natId=nat-7t9nf3pu
</pre>
输出
```
{
    "code":"0",
    "message":"",
    "taskId":"16284"
}
```

