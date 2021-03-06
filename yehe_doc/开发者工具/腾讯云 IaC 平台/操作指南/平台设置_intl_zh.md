首次使用 TIC 时，需要您显示授权资源编排 TIC 服务编排腾讯云账号下云资源，否则 TIC 将无法执行腾讯云资源的编排操作。

资源编排 TIC 提供了两种授权方式：

1. TIC 授权「推荐」：基于访问管理 CAM 内置的服务相关角色授权机制，用户无需向 TIC 平台托管 API 密钥，即可实现通过 TIC 对腾讯云资源的编排，操作更高效，更安全，且满足审计合规要求。
2. API 密钥托管「废弃」：需要将用户将 [API 密钥](https://console.cloud.tencent.com/cam/capi)（SecretID 和 SecretKey）托管在 TIC 平台中，TIC 平台对 API 密钥加密存储后，将通过托管的 API 密钥对请求进行签名，实现对用户资源的编排操作。API 密钥托管功能仅对存量用户（TIC 平台中存在托管的 API 密钥 ）可见。


>TIC 授权方式提供了更高效、更安全的权限管理机制，建议您尽快升级到 TIC 授权方式，清理托管的 API 密钥。

## 操作步骤

### TIC 授权

#### 开启 TIC 授权

1. 登录 [TIC 控制台](https://console.cloud.tencent.com/tic)；
2. 在左侧菜单栏中，选择【平台设置】>【API 密钥】，进入 API 密钥管理页面；
3. 点击开启【TIC 授权】开关，提示跳转到访问管理 CAM 页面进行授权；![开启TIC授权](https://main.qcloudimg.com/raw/12bfc355259a53d04b0359cd78ffcf23.png)
4. 跳转到访问管理 CAM 页面，完成授权；![CAM授权](https://main.qcloudimg.com/raw/3e379ef890932bdc3241c29eca4ddc8a.png)
5. 授权成功，跳回到 TIC 页面，TIC 授权开启成功；![TIC授权成功](https://main.qcloudimg.com/raw/76a7856f2743005462b2633e0de29ec7.png)



开启 TIC 授权后，您可以继续[新建资源栈](https://console.cloud.tencent.com/tic/stacks/create-stack)，或访问[资源安全助手](https://console.cloud.tencent.com/tic)了解资源安全状态。

#### 禁用 TIC 授权

1. 登录 [TIC 控制台](https://console.cloud.tencent.com/tic)；
2. 在左侧菜单栏中，选择【平台设置】>【API 密钥】，进入 API 密钥页面；
3. 点击禁用【TIC 授权】开关，禁用 TIC 授权；![禁用TIC授权](https://main.qcloudimg.com/raw/ee521f3484cf485af21ed6715c6b0de2.png)
4. 若仍存在绑定了 TIC 授权的资源栈，将无法执行禁用 TIC 授权操作，需要您手动将资源栈删除后，才能禁用 TIC 授权：![禁用TIC授权提示](https://main.qcloudimg.com/raw/aa92c19e049cb4e8f360d50414c1ce52.png)



>禁用 TIC 授权，并不会删除访问管理 CAM 侧的服务相关角色配置，如果彻底删除 CAM 侧的服务相关角色授权配置，请跳转到 [CAM 角色](https://console.cloud.tencent.com/cam/role)页面，搜索 TIC_QCSLinkedRole 角色名称，点击【删除】按钮即可彻底删除 TIC 服务相关角色授权配置。![删除CAM授权配置](https://main.qcloudimg.com/raw/a9caed0b9a56a129e6cf61eee0328e95.png)

#### 授权失败异常

若您在访问管理 CAM 角色中删除了 TIC_QCSLinkedRole 角色，且未关闭 TIC 授权，TIC API 密钥管理页面会提示【授权失败】信息。鼠标悬浮在![TIC授权失败图标](https://main.qcloudimg.com/raw/ad9e06421b49df1717643d2e3f161f86.png)图标上，系统提示重新授权：![TIC授权失败提示](https://main.qcloudimg.com/raw/4ada396201747261694fd3de2bab2966.png)

点击【重新授权】，跳转到访问管理  CAM 页面进行重新授权：![CAM授权](https://main.qcloudimg.com/raw/ee521f3484cf485af21ed6715c6b0de2.png)

授权成功后，授权状态恢复正常：![授权成功](https://main.qcloudimg.com/raw/76a7856f2743005462b2633e0de29ec7.png)

#### 授权产品列表

授权 TIC 进行编排的云产品列表如下：



>该列表会持续更新，若您希望将某个云产品纳入到 TIC 中进行编排，请您[提交工单](https://console.cloud.tencent.com/workorder/category)告知 TIC 团队，马上安排。

### API 密钥托管（废弃）

仅对存量用户（TIC 平台中存在托管的 API 密钥 ）可见。

#### 清理

当您启用 TIC 授权后，【清理】按钮可见，点击【清理】按钮后，将删除所有您在 TIC 平台托管的 API 密钥配置。

API 密钥删除后，存量通过 API 密钥关联的资源栈，默认通过 TIC 授权方式完成后续的资源编排操作。

>TIC 授权方式目前仍不支持跨腾讯云账号的资源编排，若您仍有对其他腾讯云主账号资源编排的需求，为保证业务延续性，建议继续保留 API 密钥托管的方式。

#### 删除

选中 API 密钥，点击删除，即可完成密钥删除按钮。

>若开启了 TIC 授权，存量通过 API 密钥关联的资源栈，默认通过 TIC 授权方式完成后续的资源编排操作
>
>若未开启 TIC 授权，删除 API 密钥时，当处于 Active 状态时不可删除。同时，当有资源栈正在使用该凭证时，即使该凭证的状态为 Ready，也不可删除，需要先进行 Destroy 相关联的资源栈，方可删除。

#### 新建

单击【新建】，在弹出的新建窗口中，配置相关信息：

 - **名称**：输入名称。
 - **Provider**：默认为 Tencent Cloud，当前仅有 Tencent Cloud 一个选项。
 - **SecretID 和 SecretKey**：输入对应的 SecretID 和 SecretKey，请前往 [API 密钥管理](https://console.cloud.tencent.com/cam/capi) 页面获取。
 
 <!-- ![](https://main.qcloudimg.com/raw/7e2f57c00d4f4bd7bac10e1b8dfa2fc4.png)-->
 
>同一 Provider 有且仅有一个 Key 为 Active 状态。新建资源栈时，TIC 会自动选取 Active 状态的 Key 用于 API 调用。
>
>若开启了 TIC 授权，将不再支持新建 API 密钥操作。
单击【确认】，即可完成新增 API 密钥操作。
