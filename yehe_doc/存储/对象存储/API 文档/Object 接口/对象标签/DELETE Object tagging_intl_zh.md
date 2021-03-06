## 功能描述

DELETE Object tagging 接口用于删除指定对象下已有的对象标签。

如您使用子账号调用此项接口，请确保您已经在主账号处获取了`DELETE Object tagging `这个接口的权限。

## 请求

#### 请求示例

```shell
DELETE /<ObjecKey>tagging&VersionId=VersionId HTTP 1.1
Host:<BucketName-APPID>.cos.<Region>.myqcloud.com
Date:date
Authorization: Auth String
```

>
> - Authorization: Auth String（详情请参见 [请求签名](https://intl.cloud.tencent.com/document/product/436/7778) 文档）。
> - 如果您的存储桶开启了版本控制，并且需要删除指定版本的对象的标签，可以在发起请求时携带 VersionId 参数。

#### 请求头

此接口仅使用公共请求头部，详情请参见 [公共请求头部](https://intl.cloud.tencent.com/document/product/436/7728) 文档。

#### 请求体

该请求的请求体为空。

## 响应

#### 响应头

此接口仅返回公共响应头部，详情请参见 [公共响应头部](https://intl.cloud.tencent.com/document/product/436/7729) 文档。

#### 响应体

该请求无特殊响应体信息。

#### 错误码

以下描述此请求可能会发生的一些特殊的且常见的错误情况：

| 错误码                | 描述                                   | HTTP 状态码   |
| --------------------- | -------------------------------------- | ------------- |
| SignatureDoesNotMatch | 提供的签名不符合规则，返回该错误码     | 403 Forbidden |
| NoSuchObject          | 如果尝试操作的对象不存在，返回该错误码 | 404 Not Found |
| NoSuchTagSetError     | 请求的对象中未设置存储桶标签           | 404 Not Found |

## 实际案例

#### 请求

如下请求申请删除存储桶`examplebucket-1250000000`中的对象`exampleobject.txt`下已有的标签信息。COS 解析该请求后删除该对象中的所有标签。

```shell
DELETE /exampleobject.txt?tagging HTTP/1.1
User-Agent: curl/7.29.0
Accept: */*
Host: examplebucket-1250000000.cos.ap-beijing.myqcloud.com
Authorization: Auth String
Content-Length: 0
Content-Type: application/xml
```

#### 响应

```shell
HTTP/1.1 204 No Content
Content-Type: application/xml
Connection: close
Date: Fri, 19 Jan 2020 11:40:22 GMT
```
