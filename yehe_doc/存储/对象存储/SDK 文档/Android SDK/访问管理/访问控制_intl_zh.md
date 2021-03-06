## 简介

本文档提供关于存储桶、对象的访问控制列表（ACL）的相关 API 概览以及 SDK 示例代码。

**存储桶 ACL**

| API                                                          | 操作名         | 操作描述                                |
| ------------------------------------------------------------ | -------------- | --------------------------------------- |
| [PUT Bucket acl](https://intl.cloud.tencent.com/document/product/436/7737) | 设置存储桶 ACL | 设置指定存储桶的访问权限控制列表（ACL） |
| [GET Bucket acl](https://intl.cloud.tencent.com/document/product/436/7733) | 查询存储桶 ACL | 查询指定存储桶的访问权限控制列表（ACL） |

**对象 ACL**

| API                                                          | 操作名       | 操作描述                                      |
| ------------------------------------------------------------ | ------------ | --------------------------------------------- |
| [PUT Object acl](https://intl.cloud.tencent.com/document/product/436/7748) | 设置对象 ACL | 设置存储桶中某个对象的访问控制列表 |
| [GET Object acl](https://intl.cloud.tencent.com/document/product/436/7744) | 查询对象 ACL | 查询对象的访问控制列表                |


## 存储桶 ACL

### 设置存储桶 ACL

#### 功能说明

设置指定存储桶的访问权限控制列表（ACL）。

#### 方法原型

```java
PutBucketACLResult putBucketACL(PutBucketACLRequest request) throws CosXmlClientException, CosXmlServiceException;

void putBucketACLAsync(PutBucketACLRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-put-bucket-acl)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
PutBucketACLRequest putBucketACLRequest = new PutBucketACLRequest(bucket);

// 设置 bucket 访问权限
putBucketACLRequest.setXCOSACL("public-read");

// 赋予被授权者读的权限
ACLAccount readACLS = new ACLAccount();
readACLS.addAccount("100000000001", "100000000001");
putBucketACLRequest.setXCOSGrantRead(readACLS);

// 赋予被授权者写的权限
ACLAccount writeACLS = new ACLAccount();
writeACLS.addAccount("100000000001", "100000000001");
putBucketACLRequest.setXCOSGrantWrite(writeACLS);

// 赋予被授权者读写的权限
ACLAccount writeandReadACLS = new ACLAccount();
writeandReadACLS.addAccount("100000000001", "100000000001");
putBucketACLRequest.setXCOSReadWrite(writeandReadACLS);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
putBucketACLRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    PutBucketACLResult putBucketACLResult = cosXmlService.putBucketACL(putBucketACLRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.putBucketACLAsync(putBucketACLRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        PutBucketACLResult putBucketACLResult = (PutBucketACLResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo Put Bucket ACL failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

>请求时，如需直接设置已计算好的签名串，则可通过调用`putBucketACLRequest.setSign("已计算好的签名串")`方法设置，默认由 SDK 计算签名串。

#### 参数说明

| 参数名称            | 设置方法                                                  | 描述                               | 类型           |
| ------------------- | --------------------------------------------------------- | ---------------------------------- | -------------- |
| bucket              | 构造方法                                                  | 设置 ACL 的存储桶名称，格式：BucketName-APPID | string         |
| cosAcl              | SetCosAcl                                                 | 设置存储桶的 ACL 权限              | string         |
| grandtAccout        | SetXCosGrantRead 或 SetXCosGrantWrite 或 SetXCosReadWrite | 授予用户读写权限                   | GrantAccount   |
| headerKeys          | setSignParamsAndHeaders  | 签名是否校验 header                | `Set<String>` |
| queryParameterKeys  | setSignParamsAndHeaders  | 签名是否校验请求 url 中查询参数    | `Set<String>` |
| cosXmlResultListener      | putBucketACLAsync                                                 | 结果回调        | CosXmlResultListener   |

#### 返回结果说明

通过 PutBucketACLResult 返回请求结果。

| 成员变量 | 类型 | 描述                                                     |
| -------- | ---- | -------------------------------------------------------- |
| httpCode | int  | HTTP Code， [200，300)之间表示操作成功，否则表示操作失败 |

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。

### 查询存储桶 ACL

#### 功能说明

查询指定存储桶的访问权限控制列表（ACL）。

#### 方法原型

```java
GetBucketACLResult getBucketACL(GetBucketACLRequest request) throws CosXmlClientException, CosXmlServiceException;

void getBucketACLAsync(GetBucketACLRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-get-bucket-acl)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
GetBucketACLRequest getBucketACLRequest = new GetBucketACLRequest(bucket);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
getBucketACLRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    GetBucketACLResult getBucketACLResult = cosXmlService.getBucketACL(getBucketACLRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.getBucketACLAsync(getBucketACLRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        GetBucketACLResult getBucketACLResult = (GetBucketACLResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo Get Bucket ACL failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

>请求时，如需直接设置已计算好的签名串，则可通过调用 `getBucketACLRequest.setSign("已计算好的签名串")` 方法设置，默认由 sdk 计算签名串。

#### 参数说明

| 参数名称            | 设置方法 | 描述                               | 类型           |
| ------------------- | -------- | ---------------------------------- | -------------- |
| bucket              | 构造方法 | 被查询 ACL 的存储桶名称，格式：BucketName-APPID | string         |
| headerKeys          | setSignParamsAndHeaders  | 签名是否校验 header                | `Set<String>` |
| queryParameterKeys  | setSignParamsAndHeaders  | 签名是否校验请求 URL 中查询参数    | `Set<String>` |
| cosXmlResultListener      | getBucketACLAsync                                                 | 结果回调        | CosXmlResultListener   |

#### 返回结果说明

通过 GetBucketACLResult 返回请求结果。

| 成员变量            | 类型                                                         | 描述                                                     |
| ------------------- | ------------------------------------------------------------ | -------------------------------------------------------- |
| httpCode            | int                                                          | HTTP Code， [200，300)之间表示操作成功，否则表示操作失败 |
| accessControlPolicy | [AccessControlPolicy](https://github.com/tencentyun/qcloud-sdk-android/blob/master/QCloudCosXml/cosxml/src/normal/java/com/tencent/cos/xml/model/tag/AccessControlPolicy.java) | 返回 Bucket 访问权限列表信息                             |

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。


## 对象 ACL

### 设置对象 ACL

#### 功能说明

设置存储桶中某个对象的访问控制列表（ACL）。

#### 方法原型

```java
PutObjectACLResult putObjectACL(PutObjectACLRequest request) throws CosXmlClientException, CosXmlServiceException;

void putObjectACLAsync(PutObjectACLRequest request, final CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-put-object-acl)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
String cosPath = "exampleobject"; //对象在存储桶中的位置标识符，即对象键。 例如 cosPath = "text.txt";
PutObjectACLRequest putObjectACLRequest = new PutObjectACLRequest(bucket, cosPath);

// 设置 bucket 访问权限
putObjectACLRequest.setXCOSACL("public-read");

// 赋予被授权者读的权限
ACLAccount readACLS = new ACLAccount();
readACLS.addAccount("100000000001", "100000000001");
putObjectACLRequest.setXCOSGrantRead(readACLS);

// 赋予被授权者读写的权限
ACLAccount writeandReadACLS = new ACLAccount();
writeandReadACLS.addAccount("100000000001", "100000000001");
putObjectACLRequest.setXCOSReadWrite(writeandReadACLS);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
putObjectACLRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    PutObjectACLResult putObjectACLResult = cosXmlService.putObjectACL(putObjectACLRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.putObjectACLAsync(putObjectACLRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        PutObjectACLResult putObjectACLResult = (PutObjectACLResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo Put Bucket ACL failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```

>请求时，如需直接设置已计算好的签名串，则可通过调用`putObjectACLRequest.setSign("已计算好的签名串")`方法设置，默认由 SDK 计算签名串。


#### 参数说明

| 参数名称            | 设置方法                                                  | 描述                                                         | 类型           |
| ------------------- | --------------------------------------------------------- | ------------------------------------------------------------ | -------------- |
| bucket              | 构造方法                                                  | 对象所在的存储桶名称，格式：BucketName-APPID                           | String         |
| cosPath                 | 构造方法 或 SetCosPath                                    | 对象位于存储桶中的位置标识符，即 [对象键](https://intl.cloud.tencent.com/document/product/436/13324) | String         |
| cosAcl              | SetCosAcl                                                 | 设置存储桶的 ACL 权限                                          | String         |
| grandtAccout        | SetXCosGrantRead 或 SetXCosReadWrite | 授予用户读写权限                                             | GrantAccount   |
| headerKeys          | setSignParamsAndHeaders  | 签名是否校验 header                | `Set<String>` |
| queryParameterKeys          | setSignParamsAndHeaders  | 签名是否校验请求 url 中查询参数    | `Set<String>` |
| cosXmlResultListener      | putObjectACLAsync                                                 | 结果回调        | CosXmlResultListener   |

#### 返回结果说明

通过 PutObjectACLResult 返回请求结果。

| 成员变量 | 类型 | 描述                                                       |
| -------- | ---- | ---------------------------------------------------------- |
| httpCode | int  | HTTP Code，  [200， 300)之间表示操作成功，否则表示操作失败 |

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。

### 查询对象 ACL

#### 功能说明

查询对象的访问控制列表。

#### 方法原型

```java
GetObjectACLResult getObjectACL(GetObjectACLRequest request) throws CosXmlClientException, CosXmlServiceException;

void getObjectACLAsync(GetObjectACLRequest request, CosXmlResultListener cosXmlResultListener);
```

#### 请求示例

[//]: # (.cssg-snippet-get-object-acl)
```java
String bucket = "examplebucket-1250000000"; //格式：BucketName-APPID
String cosPath = "exampleobject"; //对象在存储桶中的位置标识符，即对象键。例如 cosPath = "text.txt";
GetObjectACLRequest getBucketACLRequest = new GetObjectACLRequest(bucket, cosPath);
// 设置签名校验 Host，默认校验所有 Header
Set<String> headerKeys = new HashSet<>();
headerKeys.add("Host");
getBucketACLRequest.setSignParamsAndHeaders(null, headerKeys);
// 使用同步方法
try {
    GetObjectACLResult getObjectACLResult = cosXmlService.getObjectACL(getBucketACLRequest);
} catch (CosXmlClientException e) {
    e.printStackTrace();
} catch (CosXmlServiceException e) {
    e.printStackTrace();
}

// 使用异步回调请求
cosXmlService.getObjectACLAsync(getBucketACLRequest, new CosXmlResultListener() {
    @Override
    public void onSuccess(CosXmlRequest request, CosXmlResult result) {
        GetObjectACLResult getObjectACLResult = (GetObjectACLResult) result;
    }

    @Override
    public void onFail(CosXmlRequest cosXmlRequest, CosXmlClientException clientException, CosXmlServiceException serviceException) {
        // todo Get Bucket ACL failed because of CosXmlClientException or CosXmlServiceException...
    }
});
```
>请求时，如需直接设置已计算好的签名串，则可通过调用 `getBucketACLRequest.setSign("已计算好的签名串")` 方法设置，默认由 SDK 计算签名串。


#### 参数说明

| 参数名称            | 设置方法               | 描述                                                         | 类型           |
| ------------------- | ---------------------- | ------------------------------------------------------------ | -------------- |
| bucket              | 构造方法               | 对象所在的存储桶名称，格式：BucketName-APPID                           | String         |
| cosPath                 | 构造方法 或 SetCosPath | 对象位于存储桶中的位置标识符，即 [对象键](https://intl.cloud.tencent.com/document/product/436/13324) | String         |
| headerKeys          | setSignParamsAndHeaders  | 签名是否校验 header                | `Set<String>` |
| queryParameterKeys          | setSignParamsAndHeaders  | 签名是否校验请求 url 中查询参数    | `Set<String>` |
| cosXmlResultListener      | getObjectACLAsync                                                 | 结果回调        | CosXmlResultListener   |

#### 返回结果说明

通过 GetObjectACLResult 返回请求结果。

| 成员变量            | 类型                                                         | 描述                                                       |
| ------------------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| httpCode            | int                                                          | HTTP Code，  [200， 300)之间表示操作成功，否则表示操作失败 |
| accessControlPolicy | [AccessControlPolicy](https://github.com/tencentyun/qcloud-sdk-android/blob/master/QCloudCosXml/cosxml/src/normal/java/com/tencent/cos/xml/model/tag/AccessControlPolicy.java) | 返回对象的访问权限列表信息                               |

>操作失败时，SDK 将抛出 [CosXmlClientException](https://intl.cloud.tencent.com/document/product/436/31517) 或 [CosXmlServiceException](https://intl.cloud.tencent.com/document/product/436/31517) 异常。

