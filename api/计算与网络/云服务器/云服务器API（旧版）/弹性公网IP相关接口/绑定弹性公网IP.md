## 1. 接口描述
 
域名: eip.api.qcloud.com
接口名: EipBindInstance

弹性公网IP和服务器或弹性网卡绑定

>注意：
如待操作服务器带有普通公网IP，绑定过程会把其普通公网IP自动解绑并释放，服务器将绑定所指定的弹性公网IP。

 

## 2. 输入参数
 

<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>必选</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> eipId <td> 是 <td> String <td> EIP的实例ID，可通过<a href="/doc/api/229/%E6%9F%A5%E8%AF%A2%E5%BC%B9%E6%80%A7%E5%85%AC%E7%BD%91IP%E5%88%97%E8%A1%A8" title="DescribeEip">DescribeEip</a>接口返回字段中的eipId获取
<tr>
<td> unInstanceId <td> 否 <td> String <td> 待操作服务器的实例ID，可通过<a href="/doc/api/229/%E6%9F%A5%E7%9C%8B%E5%AE%9E%E4%BE%8B%E5%88%97%E8%A1%A8" title="DescribeInstances">DescribeInstances</a>接口返回字段中的unInstanceId获取，传入参数unInstanceId表示绑定服务器的主网卡主IP
<tr>
<td> networkInterfaceId <td> 否 <td> String <td> 弹性网卡唯一ID，可通过<a href="/doc/api/245/4814" title="DescribeNetworkInterfaces">DescribeNetworkInterfaces</a>接口返回字段中的networkInterfaceId获取
<tr>
<td> privateIpAddress <td> 否 <td> String <td> 服务器内网IP，绑定时或者传入参数unInstanceId，或者传入参数networkInterfaceId和privateIpAddress。当networkInterfaceId和privateIpAddress没有绑定在服务器上时，绑定操作会保持其与EIP的关系。
</tbody></table>

 

## 3. 输出参数
 

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码。0表示成功，其他值表示失败。详见错误码页面的[公共错误码](/document/api/377/4173)。|
| message | String | 模块错误信息描述，与接口相关。详见错误码页面的[模块错误码](/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#2.E3.80.81.E6.A8.A1.E5.9D.97.E9.94.99.E8.AF.AF.E7.A0.81)。|


 

## 4. 示例
 
输入
<pre>

  http://eip.api.qcloud.com/v2/index.php?
  &<<a href="/doc/api/229/6976">公共请求参数</a>>
  &eipId=eip-mksy14ay
  &unInstanceId=ins-hyvbipjg

</pre>

输出
```

{
    "code": 0,
    "message": ""
}

```

