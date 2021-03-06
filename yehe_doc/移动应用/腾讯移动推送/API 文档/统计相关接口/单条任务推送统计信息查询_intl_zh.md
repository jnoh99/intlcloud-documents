## 接口说明
**请求方式**：POST。
**调用频率限制**：200次/小时。

接口请求地址与服务接入点一一对应，请选择与您的应用服务接入点对应的请求地址。

广州服务接入点：
```shell
https://api.tpns.tencent.com/v3/statistics/get_push_task_stat_channel
```
中国香港服务接入点:
```shell
https://api.tpns.hk.tencent.com/v3/statistics/get_push_task_stat_channel
```
新加坡服务接入点:
```shell
https://api.tpns.sgp.tencent.com/v3/statistics/get_push_task_stat_channel
```

**接口功能**：查询每个推送任务的详细统计, 包含所有通道信息及汇总结果。pushStatDataAll 里的通道类型会变化，根据 iOS/Android 和推送通道的不同而不同。



## 参数说明
#### 请求参数

| 参数名称 | 必选 | 类型   | 描述   |
| -------- | ---- | ------ | ------ |
| pushId   | 是   | string | 推送任务 ID，限制查询当前日期起1个月内的推送任务|

#### 应答参数

| 参数名称        | 类型   | 描述                                                         |
| --------------- | ------ | ------------------------------------------------------------ |
| retCode         | int    | 返回状态码                                                   |
| errMsg          | string | 错误信息                                                     |
| pushStatDataAll | Json   | 返回结果：单个元素由 channel 和 pushState 组成，channel 是推送通道名称。pushState 结构变量见下表 |

#### PushState（Android）

| 参数名称            | 类型 | 说明                                                         |
| ------------------- | ---- | ------------------------------------------------------------ |
| pushActiveUv        | int  | 计划发送                                                     |
| pushOnlineUv        | int  | 实际发送                                                     |
| verifySvcUv         | int  | 抵达设备（仅 TPNS 通道、ROG 通道、FCM 通道有效。其他厂商通道由 TPNS 实际发送 pushOnlineUv 指标补齐） |
| callbackVerifySvcUv | int  | 厂商通道抵达回执（限华为、OPPO、 vivo、小米通道有效。厂商通道回执配置请参考 [厂商通道抵达回执获取指南](https://intl.cloud.tencent.com/document/product/1024/35246)） |
| verifyUv            | int  | 展示                                                         |
| clickUv             | int  | 点击                                                         |
| cleanupUv           | int  | 清除                                                         |

>说明：
>数组中“all” 通道对应汇总统计数据。
>
>-  汇总数据中verifySvcUv（抵达设备），verifyUv（展示），clickUv（点击），cleanupUv（清除）指标只汇总计算了TPNS通道数据、ROG通道数据、FCM 通道数据。
>-  汇总数据中pushActiveUv（计划发送）, pushOnlineUv（实际发送）汇总计算了 TPNS 通道 + 厂商通道的数据。
>-  汇总数据中callbackVerifySvcUv（厂商通道抵达回执）汇总计算了   厂商通道callbackVerifySvcUv（厂商通道抵达回执）+ TPNS 通道 verifySvcUv（抵达设备）+ ROG 通道 verifySvcUv（抵达设备）+ FCM通道 verifySvcUv（抵达设备）。
#### pushState（iOS&macOS）

| 参数名称     | 类型   | 说明         |
| ------------ | ------ | ------------ |
| pushActiveUv | int    | 计划发送     |
| pushOnlineUv | int    | APNs 成功接收 |
| verifySvcUv  | int    | 抵达 |
| clickUv      | int    | 点击         |

## 示例说明
#### 请求示例

```json
{
   "pushId": "130248"
}
```

#### 应答示例

```json
{
    "retCode": 0,
    "errMsg": "NO_ERROR",
    "pushStatDataAll": [
        {
            "channel": "xm",
            "pushState": {
                "pushActiveUv": 1000,
                "pushOnlineUv": 1000,
                "verifySvcUv": 1000,
                "callbackVerifySvcUv": 800,
                "verifyUv": 1000,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "mz",
            "pushState": {
                "pushActiveUv": 1000,
                "pushOnlineUv": 1000,
                "verifySvcUv": 1000,
                "callbackVerifySvcUv": 800,
                "verifyUv": 1000,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "vivo",
            "pushState": {
                "pushActiveUv": 1000,
                "pushOnlineUv": 1000,
                "verifySvcUv": 1000,
                "callbackVerifySvcUv": 800,
                "verifyUv": 1000,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "hw",
            "pushState": {
                "pushActiveUv": 1000,
                "pushOnlineUv": 1000,
                "verifySvcUv": 1000,
                "callbackVerifySvcUv": 800,
                "verifyUv": 1000,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
        {
            "channel": "xg",
            "pushState": {
                "pushActiveUv": 1000,
                "pushOnlineUv": 800,
                "verifySvcUv": 800,
                "callbackVerifySvcUv": 0,
                "verifyUv": 800,
                "clickUv": 300,
                "cleanupUv": 500
            }
        },
        {
            "channel": "oppo",
            "pushState": {
                "pushActiveUv": 1000,
                "pushOnlineUv": 1000,
                "verifySvcUv": 1000,
                "callbackVerifySvcUv": 800,
                "verifyUv": 1000,
                "clickUv": 0,
                "cleanupUv": 0
            }
        },
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
            "channel": "all",
            "pushState": {
                "pushActiveUv": 6000,
                "pushOnlineUv": 5800,
                "verifySvcUv": 5800,
                "callbackVerifySvcUv": 4000,
                "verifyUv": 5800,
                "clickUv": 300,
                "cleanupUv": 500
            }
        }
    ]
}
```

