## 操作场景
本文为您介绍在云数据库 Redis 控制台创建实例的过程。

## 操作步骤
### 创建实例
1. 登录 [云数据库 Redis 控制台](https://console.cloud.tencent.com/redis)，在左侧导航选择【实例列表】页。
2. 单击【新建实例】，根据需求输入参数。
<table>
<thead>
<tr>
<th>参数</th>
<th>备注</th>
</tr>
</thead>
<tbody><tr>
<td>计费模式</td>
<td>支持按量计费。</td>
</tr>
<tr>
<td>网络类型</td>
<td>基础网络与私有网络 VPC 不能互通，购买后不能更换网络类型，请参见 <a href="https://intl.cloud.tencent.com/document/product/213/5227" target="_blank">网络环境</a>。</td>
</tr>
<tr>
<td>引擎</td>
<td>支持社区版 Redis。</td>
</tr>
<tr>
<td>兼容版本</td>
<td>兼容 Redis 2.8 和4.0。</td>
</tr>
<tr>
<td>副本数量</td>
<td><ul><li>Redis 2.8 标准版支持0 - 1个副本。</li><li>Redis 4.0、5.0 标准版支持1 - 5个副本。</li><li>Redis 4.0、5.0 集群版支持1 - 5个副本。</li></td>
</tr>
<tr>
<td>端口</td>
<td>自定义端口号需在1024到65535之间。</td>
</tr>
<tr>
<td>指定项目/安全组</td>
<td>指定数据库的项目和安全组。</td>
</tr>
<tr>
<td>实例名/设置密码</td>
<td>实例名和密码支持直接设置和创建完后在实例列表进行设置。</td>
</tr>
</tbody></table>
3. 确认无误后单击【立即购买】，各版本详细价格请参见 [产品定价](https://intl.cloud.tencent.com/document/product/239/9894)。
4. 返回实例列表，待实例状态显示为【运行中】即可正常使用。

### 修改实例名
在实例列表的【实例 ID / 名称】列，单击以下小图标可修改实例名。
![](https://main.qcloudimg.com/raw/8a6917c05adb4e06731dbdd836c620da.png)
