
### 旁路直播请求

- 子命令(uint32_sub_cmd)：0x6 填写在GVCommOprHead中
- 包体结构(reqbody): req_0x6

		req_0x6
		{
			"uint32_oper":xxx,
			"uint32_live_code":xxx,
			"uint32_sdk_type":xxx,
			"str_channel_name":"xxx",
			"str_channel_describe":"xxx",
			"str_player_pwd":"xxx",
			"uint32_push_data_type":xxx,
			"uint32_tape_flag":xxx,
			"uint32_watermark_flag":xxx,
			"uint32_watermark_id":xxx,
			"rpt_rate_type":[xxx]
		}
***注：旁路直播操作的对象为rpt_to_Account，必须填写，只支持一个***

| 参数名称 | 类型 | 说明 | 备注 |
| --- | --- | --- | --- |
| uint32_oper | unsigned int | 操作类型：1 启动旁路直播；2 关闭旁路直播； | 启动旁路直播：必填 停止旁路直播：必填  |
| uint32_live_code | unsigned int | 直播流输出编码： 1  hls旁路直播；5  rtmp旁路直播；6  hls+rtmp旁路直播；  | 启动旁路直播：必填 停止旁路直播：不填  |
| uint32_sdk_type | unsigned int | SDK类型：1 普通SDK ；2 物联摄像头； | 启动旁路直播：必填 停止旁路直播：必填 |
| str_channel_name | string | 通道名称 | 启动旁路直播：可选 停止旁路直播：不填 |
| str_channel_describe | string | 通道描述 | 启动旁路直播：可选 停止旁路直播：不填 |
| str_player_pwd | string | 指定通过密码才允许观看，需使用云平台提供的播放器才支持，否则设置无效 | 启动旁路直播：可选 停止旁路直播：不填 |
| uint32_push_data_type | unsigned int | 旁路直播的数据类型0 旁路直播摄像头；1 旁路直播屏幕分享数据； | 启动旁路直播：必填 停止旁路直播：必填  |
| uint32_tape_flag | unsigned int | 是否需要在旁路直播过程中录制：0 不需要录制；1 需要录制；  | 启动旁路直播：必填 停止旁路直播：不填  |
| uint32_watermark_flag	| unsigned int | 是否添加水印：0 不添加水印; 1 添加水印;	|启动旁路直播：可选 停止旁路直播：不填 (如果需要携带水印，请在直播控制台上传相关水印图片,如果不携带此参数，默认为不添加水印)|
| uint32_watermark_id | unsigned int |水印ID：0为默认水印或者对应的水印ID号|启动旁路直播：可选 停止旁路直播：不填 (如果设置启用水印而当前参数不携带，使用用户上传的默认水印)|
| rpt_rate_type | unsigned int | 支持多码率：0  原始码率 10 标清码率（550K）20 高清码率（900K）|启动旁路直播：可选 停止旁路直播：不填（不携带此参数默认返回原始码率url。数组结构，可以同时返回多组url）





	"reqbody":
	{
			"req_0x6":
			{
				"uint32_oper":xxx,
				"uint32_live_code":xxx,
				"uint32_sdk_type":xxx,
				"uint32_push_data_type":xxx
			}
	}

- 响应包体结构(rspbody): rsp_0x6

		rsp_0x6定义：
		{
		 "uint32_result":xxx,       // 操作结果, 0成功, 非0失败
		 "str_errorinfo":"xxx",
		 "msg_live_url":"[xxx]"
		}

| 参数名称 | 类型 | 说明 | 备注 |
| --- | --- | --- | --- |
| uint32_result | unsigned int | 操作结果0：成功，非0：失败 | 详细错误码见附录 |
| str_errorinfo | string | 错误信息 | 错误字符串信息 |
| uint64_channel_id | unsigned  long long | 启动旁路直播的时候返回 |   |
| msg_live_url | [LiveUrl] | 直播URL | 参考LiveUrl的定义 |
| uint32_tape_task_id | unsigned int | 录制对应的tape_task_id | 只有启动旁路直播的时候设置uint32_tape_flag为1才返回 |

#### LiveUrl

	{
	"uint32_type":"xxx",
	"string_play_url":"xxx"
	"RateType ":xxx
	}

| 参数名称 | 类型 | 说明 | 备注 |
| --- | --- | --- | --- |
| uint32_type | unsigned int | 直播流输出编码1  hls旁路直播；5  rtmp旁路直播；6  hls+rtmp旁路直播； |   |
| string_play_url | String | 直播流输出编码对应URL |   | 
| RateType | unsigned int | 此url对应的码率类型： 0  原始码率 10 标清码率（550K） 20 高清码率（900K）| 不包含此参数表示是原始码率  | 

***注意：启动旁路直播需要用户进入音视频房间之后操作才能成功***

#### json包体请求实例说明：

以启动旁路直播的json包举例说明，需要把里面的参数值替换成自己的

{

        "reqhead":{
                "uint32_sub_cmd":6,
                "uint32_seq":xxx,
                "uint32_auth_key":xxx,
                "uint32_sdk_appid":xxx,
                "rpt_to_Account":["xxx"],
                "bytes_cookie_buff":"xxx"
        },

        "reqbody":{
                "req_0x6":{
                        "uint32_oper":xxx,
                        "uint32_live_code":xxx,
                        "uint32_sdk_type":xxx,
                        "str_channel_name":"xxx",
                        "str_channel_describe":"xxx",
                        "uint32_push_data_type":xxx,
                        "uint32_tape_flag":xxx
                }
        }
}




# 错误码说明

## 0x6旁路直播错误码说明

| 错误码 | 错误说明 | 处理建议 |
| --- | --- | --- |
| 40000000 | SDK请求解析失败 | 【旁路直播请求字段填写是否完整】 |
| 40000001 | SDK请求解析失败-没有旁路直播请求包体 | 【旁路直播请求字段填写是否完整】 |
| 40000002 | SDK请求解析失败-没有旁路直播请求操作字段 | 【旁路直播请求字段填写是否完整】 |
| 40000003 | SDK请求解析失败-缺少旁路直播请求的输出编码（HLS/RTMP等） | 【旁路直播请求字段填写是否完整】 |
| 40000004 | SDK请求解析失败-视频源类型错误（摄像头/桌面等） | 【旁路直播请求字段填写是否完整】 |
| 40000005 | SDK请求解析失败-请求操作错误（请求旁路直播、停止旁路直播） | 【旁路直播请求字段填写是否完整】 |
| 40000201 | 请求服务器内部数据打包错误 | 【反馈腾讯客服】 |
| 40000202 | 请求服务器内部数据打包错误 | 【反馈腾讯客服】 |
| 40000203 | 请求服务器内部数据打包错误 | 【反馈腾讯客服】 |
| 40000207 | 请求旁路直播服务器通讯错误-拉取旁路直播服务器地址失败 | 【可能是网络问题，重试处理，重试失败反馈腾讯客服】 |
| 40000208 | 请求旁路直播服务器通讯错误-请求旁路直播服务器超时 | 【可能是网络问题，重试处理，重试失败反馈腾讯客服】 |
| 40000301 | 解析旁路直播服务器回包错误-数据包解析失败 | 【反馈腾讯客服】 |
| 40000302 | 解析旁路直播服务器回包错误-数据包解析失败 | 【反馈腾讯客服】 |
| 40000303 | 解析旁路直播服务器回包错误-没有返回IP | 【反馈腾讯客服】 |
| 40000304 | 解析旁路直播服务器回包错误-没有返回端口 | 【反馈腾讯客服】 |
| 40000305 | 解析旁路直播服务器回包错误-没有返回结果 | 【反馈腾讯客服】 |
| 40000306 | 解析旁路直播服务器回包错误-返回url长度溢出 | 【反馈腾讯客服】 |
| 40000401 | 查询房间获取grocery服务IP错误 | 【可能是网络问题，重试处理，重试失败反馈腾讯客服】 |
| 40000402 | 查询房间拉取grocery数据错误 | 【可能是网络问题，重试处理，重试失败反馈腾讯客服】 |
| 40000403 | 查询房间拉取grocery不存在（请求旁路直播的房间不存在） | 【检查是否成功开房，旁路直播的用户ID，groupid是否填写正确】 |
| 40000404 | 查询房间流控服务器超时 | 【可能是网络问题，重试处理，重试失败反馈腾讯客服】 |
| 40000405 | 查询房间回包错误-数据包解析失败 | 【反馈腾讯客服】 |
| 40000406 | 查询房间回包错误-数据包解析失败 | 【反馈腾讯客服】 |
| 40000407 | 查询房间回包错误-数据包解析失败 | 【反馈腾讯客服】 |
| 40000408 | 查询房间回包错误-没有返回结果 | 【反馈腾讯客服】 |
| 40000409 | 查询房间回包错误-数据包解析失败 | 【反馈腾讯客服】 |
| 40000410 | 请求旁路直播的房间不存在 | 【检查是否成功开房，旁路直播的用户ID，groupid是否填写正确】 |
| 40000411 | 发起旁路直播用户不在房间内 | 【检查是否成功开房，旁路直播的用户ID，groupid是否填写正确】 |
| 40000412 | 停止旁路直播重复发送，用户已经停止旁路直播 | 【如果是旁路直播停止操作说明已经停止，重复停止操作，无需处理】 |
| 40000413 | 停止旁路直播重复发送，用户已经停止旁路直播 | 【如果是旁路直播停止操作说明已经停止，无需处理】 |
| 40000414 | 查询房间-服务器内部操作类型错误 | 【可能是网络问题，重试处理，重试失败反馈腾讯客服】 |
| 40000415 | 启动旁路直播重复发送，用户正在旁路直播 | 【如果是旁路直播启动操作说明已经是在旁路直播状态，无需处理】 |
| 1001 | 权限错误 | 【一般是sdkappid填写错误导致】 |
| 20101 | 通道数超过上限 | 【旁路直播通道数存在上限，在旁路直播控制台检查并删除无用的通道】 |
| 20406 | 用户欠费 | 【检查是否已欠费】 |

