## 接口说明
**请求方式**：POST。
**调用频率限制**：200次/小时。

接口请求地址与服务接入点一一对应，请选择与您的应用服务接入点对应的请求地址。

广州服务接入点：
```shell
https://api.tpns.tencent.com/v3/statistics/get_push_group_stat_channel
```
中国香港服务接入点:
```shell
https://api.tpns.hk.tencent.com/v3/statistics/get_push_group_stat_channel
```
新加坡服务接入点:
```shell
https://api.tpns.sgp.tencent.com/v3/statistics/get_push_group_stat_channel
```

**接口功能**：可根据 GroupID 来查询**最近7天内相同 GroupID** 的所有已推送任务的分推送渠道的聚合统计数据。


## 参数说明
#### 请求参数

| 参数名称  | 必选 | 类型         | 描述                                                         |
| --------- | ---- | ------------ | ------------------------------------------------------------ |
| groupId   | 是   | string       | 多条任务聚合统计的字段，对应推送参数中的“group_Id”           |
| startDate | 是   | string       | 查询开始日期<li>格式：YYYY-MM-DD</li><li>限制：只能聚合统计最近7天的推送任务</li> |
| endDate   | 是   | string | 查询截止日期，格式：YYYY-MM-DD                               |

#### 应答参数

| 参数名称     | 类型   | 描述                                   |
| ------------ | ------ | -------------------------------------- |
| retCode      | int    | 返回状态码                             |
| errMsg       | string | 错误信息                               |
| pushStatDataAll | JsonArray | 返回结果：单个元素 由 channel 和 pushState 组成，channel 是通道名。pushState 结构变量见下表 |

#### pushState（Android）

| 参数名称            | 类型 | 说明                                                         |
| ------------------- | ---- | ------------------------------------------------------------ |
| pushActiveUv        | int  | 计划发送                                                     |
| pushOnlineUv        | int  | 实际发送                                                     |
| verifySvcUv         | int  | 抵达设备（仅 TPNS 通道、ROG 通道、FCM 通道有效。其他厂商通道由 TPNS 实际发送 pushOnlineUv 指标补齐） |
| callbackVerifySvcUv | int  | 厂商通道抵达回执（限华为、OPPO、 vivo、小米通道有效。厂商通道回执配置请参考 [厂商通道抵达回执获取指南](https://intl.cloud.tencent.com/document/product/1024/35246） |
| verifyUv            | int  | 展示                                                         |
| clickUv             | int  | 点击                                                         |
| cleanupUv           | int  | 清除                                                         |

>数组中“all” 通道对应汇总统计数据。
-  汇总数据中verifySvcUv（抵达设备），verifyUv（展示），clickUv（点击），cleanupUv（清除）指标只汇总计算了TPNS通道数据、ROG通道数据、FCM 通道数据。
-  汇总数据中pushActiveUv（计划发送）, pushOnlineUv（实际发送）汇总计算了 TPNS 通道 + 厂商通道的数据。
-  汇总数据中callbackVerifySvcUv（厂商通道抵达回执）汇总计算了   厂商通道callbackVerifySvcUv（厂商通道抵达回执）+ TPNS 通道 verifySvcUv（抵达设备）+ ROG 通道 verifySvcUv（抵达设备）+ FCM通道 verifySvcUv（抵达设备）。



#### pushState（iOS）

| 参数名称     | 类型   | 说明     |
| ------------ | ------ | -------- |
| pushActiveUv | int    | 计划发送 |
| pushOnlineUv | int    | APNs 成功接收 |
| verifySvcUv  | int    | 抵达 |
| clickUv      | int    | 点击     |



## 示例说明

#### 请求示例

```json
{
    "groupid": "pt:testGroup",
    "startDate": "20190912",
    "endDate": "20190912"
}
```

#### 应答示例

```json
{
    "retCode": 0,
    "errMsg": "NO_ERROR",
    "pushStatDataAll": [
        {
            "channel": "fcm",
            "pushState": {
                "pushActiveUv": 0,
                "pushOnlineUv": 0,
                "verifySvcUv": 0,
                "callbackVerifySvcUv": 0,
                "verifyUv": 0,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "rog",
            "pushState": {
                "pushActiveUv": 0,
                "pushOnlineUv": 0,
                "verifySvcUv": 0,
                "callbackVerifySvcUv": 0,
                "verifyUv": 0,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "hw",
            "pushState": {
                "pushActiveUv": 0,
                "pushOnlineUv": 0,
                "verifySvcUv": 0,
                "callbackVerifySvcUv": 0,
                "verifyUv": 0,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "xm",
            "pushState": {
                "pushActiveUv": 0,
                "pushOnlineUv": 0,
                "verifySvcUv": 0,
                "callbackVerifySvcUv": 0,
                "verifyUv": 0,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "oppo",
            "pushState": {
                "pushActiveUv": 0,
                "pushOnlineUv": 0,
                "verifySvcUv": 0,
                "callbackVerifySvcUv": 0,
                "verifyUv": 0,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "vivo",
            "pushState": {
                "pushActiveUv": 0,
                "pushOnlineUv": 0,
                "verifySvcUv": 0,
                "callbackVerifySvcUv": 0,
                "verifyUv": 0,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "mz",
            "pushState": {
                "pushActiveUv": 0,
                "pushOnlineUv": 0,
                "verifySvcUv": 0,
                "callbackVerifySvcUv": 0,
                "verifyUv": 0,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "xg",
            "pushState": {
                "pushActiveUv": 4641,
                "pushOnlineUv": 4641,
                "verifySvcUv": 4641,
                "callbackVerifySvcUv": 0,
                "verifyUv": 4639,
                "clickUv": 3818,
                "cleanupUv": 4200
            }
        },
        {
            "channel": "all",
            "pushState": {
                "pushActiveUv": 4641,
                "pushOnlineUv": 4641,
                "verifySvcUv": 4641,
                "callbackVerifySvcUv": 4641,
                "verifyUv": 4639,
                "clickUv": 3818,
                "cleanupUv": 4200
            }
        }
    ]
}
```
