腾讯移动推送 Rest API 的通用错误主要如下：

| 错误码 | 错误英文描述 | 错误中文描述 | 反馈接口 |
| --- | --- | --- | --- |
|       1008001 | paramter parse error | 参数解析错误 | 通用接口 |
| 1008002 | missing parameter | 必填参数缺失 | 通用接口 |
| 1008003 | auth failure | 认证鉴权失败 | 通用接口 |
| 1008004 | invoke service error | 调用内部服务失败 | 通用接口 |
| 1008006 | invalid token | Token 无效，请检查 | 标签操作，账号操作相关接口 |
| 1008007 | invalid parameter | 参数校验失败 | 通用接口 |
| 1008011 | upload file error | 文件上传失败 | 证书上传接口，号码包上传接口 |
| 1008012 | upload empty file | 上传文件为空 | 证书上传接口，号码包上传接口 |
| 1008013 | parse certificate error | 证书解析失败 | 证书上传接口 |
| 1008015 | push id not exist | 推送任务 ID 不存在 | 统计查询接口 |
| 1008016 | date param formate error | 日期时间参数格式不对 | 统计查询接口 |
| 1008019 | content may be evil | 被内容安全服务判定不和谐 | 推送接口 |
| 10010005 | internal error | 推送目标不存在 | 推送接口 |
| 1008026 | batch op，partly error | 批量操作，部分失败 | 账号绑定，查询接口 |
| 1008027 | batch op，total error | 批量操作，全部失败 | 账号绑定，查询接口 |
| 10110008 | no token，no account  | 查询的 Token ， 账号不存在 | 账号绑定，查询接口 |
| 10010018 | Push repeat | 重复推送 | 推送接口，全量、tag推送 |
