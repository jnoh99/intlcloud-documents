## 功能描述

本接口用于获取机器组信息列表。

## 请求

#### 请求示例

```
GET /machinegroups HTTP/1.1
Host: <Region>.cls.tencentyun.com
Authorization: <AuthorizationString>

```

#### 请求行

```
GET /machinegroups
```

#### 请求头

除公共头部外，无特殊请求头部。

#### 请求参数

无。

## 响应

#### 响应示例

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 123

{
  "machine_groups": [
    {
    "group_id": "xxxx-xx-xx-xx-xxxxxxxx",
    "group_name": "testname",
    "create_time": "2017-08-08 12:12:12"
    }
  ]
]
```

#### 响应头

除公共响应头部外，无特殊响应头部。

#### 响应参数

|  字段名      |  类型     | 必有 |        含义                    |
|-------------|-----------|---------|-------------------------------|
| machine_groups|JsonArray| 是      | 机器组信息数组                  |

MachineGroupInfo 格式如下：

|  字段名     |  类型  | 必有 |        含义                    |
|------------|--------|---------|-------------------------------|
| group_id   | string | 是      | 机器组的 ID                  |
| group_name | string | 是      | 机器组的名字                    |
| create_time| string | 否      | 创建时间                       |

## 错误码

参见 [错误码](https://intl.cloud.tencent.com/document/product/614/12402)。
