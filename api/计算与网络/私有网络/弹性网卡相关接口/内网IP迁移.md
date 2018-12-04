## 1. 接口描述

本接口(MigratePrivateIpAddress)用于内网 IP迁移。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>

1) 该接口用户将一个内网IP从一个弹性网卡上迁移到另外一个弹性网卡，主IP地址不支持迁移。<br>
2) 迁移前后的弹性网卡必须在同一个子网内。


## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/document/product/215/4772" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为MigratePrivateIpAddress。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 弹性网卡对应的私用网络ID，例如：vpc-7t9nf3pu。 |
| privateIpAddress | 是 | String | 被迁移的内网IP地址，例如：10.0.0.6。 |
| oldNetworkInterfaceId | 是 | String | 迁移前的弹性网卡ID，例如：eni-m6dyj72l。 |
| newNetworkInterfaceId | 是 | String | 迁移后的弹性网卡ID，例如：eni-dfddf454d。 |


## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 错误码。0：成功, 其他值：失败。|
| message | String | 错误信息。|
| taskId | Int | 任务ID，操作结果可以用taskId查询，详见<a href="/document/product/215/5094">查询任务执行结果接口</a>。 |

## 4. 错误码表
以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见<a href="/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。

| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的VPC，VPC资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/1372" title="DescribeVpcEx">DescribeVpcEx</a>接口查询VPC。 |
| InvalidNetworkInterface.NotFound | 无效的弹性网卡，弹性网卡资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/4814" title="DescribeNetworkInterfaces">DescribeNetworkInterfaces</a>接口查询弹性网卡。 |

## 5. 示例
输入
<pre>
http://vpc.api.qcloud.com/v2/index.php?Action=MigratePrivateIpAddress
&<<a href="/document/product/215/4772">公共请求参数</a>>
&vpcId=vpc-7t9nf3pu
&privateIpAddress=10.0.0.6
&oldNetworkInterfaceId=eni-m6dyj72l
&newNetworkInterfaceId=eni-dfddf454d
</pre>
输出
```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data":
        {
            "taskId": 16284
        }
}
```

