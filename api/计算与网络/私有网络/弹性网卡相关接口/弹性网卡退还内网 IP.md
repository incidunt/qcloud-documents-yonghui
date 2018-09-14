## 1. 接口描述

本接口(UnassignPrivateIpAddresses)用于弹性网卡退还内网Ip。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>

退还弹性网卡上的辅助内网IP，接口自动解关联弹性公网 IP。不能退还弹性网卡的主辅助内网IP。

## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为UnassignPrivateIpAddresses。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | String | 弹性网卡对应的私用网络ID，例如：vpc-7t9nf3pu |
| networkInterfaceId | 是 | String | 弹性网卡ID，例如：eni-m6dyj72l |
| privateIpAddress.n | 是 | Array | 要退换的辅助内网IP地址数组，例如：privateIpAddress.0=10.0.0.2 |

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
| InvalidNetworkInterface.NotFound | 无效的弹性网卡，弹性网卡资源不存在。请再次核实您输入的资源信息是否正确，可通过<a href="/document/api/215/4814" title="DescribeNetworkInterfaces">DescribeNetworkInterfaces</a>接口查询弹性网卡 |
| InvalidPrivateip.IsPrimary | 主IP不能解绑 |

## 5. 示例
输入
<pre>
http://vpc.api.qcloud.com/v2/index.php?Action=UnassignPrivateIpAddresses
&<<a href="/doc/api/229/6976">公共请求参数</a>>
&vpcId=vpc-7t9nf3pu
&networkInterfaceId=eni-m6dyj72l
&privateIpAddress.0=10.0.0.2
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

