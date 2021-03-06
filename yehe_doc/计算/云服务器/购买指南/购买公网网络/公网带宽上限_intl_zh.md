## 出网带宽上限（下行带宽）

我们设置的公网网络带宽上限默认为出网带宽上限，即从云服务器流出的带宽。公网网络的带宽上限根据不同的网络计费模式有所不同。具体信息如下：
- 2020年2月24日00:00以后创建的机器按以下规则执行：
<table>
<tr><th rowspan="2">网络计费模式</th><th colspan="2">实例</th><th rowspan="2">带宽上限的可设置范围（Mbps）</th></tr>
<tr><th>实例计费模式</th><th>实例配置</th></tr>
<tr><td>按流量计费</td><td>按量计费实例</td><td>ALL</td><td>0 - 100</td></tr>
<tr><td>按带宽计费</td><td>按量计费实例</td><td>ALL</td><td>0 - 100</td></tr>
<tr><td>共享带宽</td><td colspan="2">ALL</td><td>0 - 2000</td></tr>
</table>

- 2020年2月24日00:00以前创建的机器按以下规则执行：
<table>
<tr><th rowspan="2">网络计费模式</th><th colspan="2">实例</th><th rowspan="2">带宽上限的可设置范围（Mbps）</th></tr>
<tr><th style="width: 18.5607%;">实例计费模式</th><th style="width: 24.5814%;">实例配置</th></tr>
<tr><td>按流量计费</td><td>按量计费实例</td><td>ALL</td><td>0 - 100</td></tr>
<tr><td>按带宽计费</td><td>按量计费实例</td><td>ALL</td><td>0 - 100</td></tr>
<tr><td>共享带宽</td><td colspan="2">ALL</td><td>0 - 2000</td></tr>
</table>


## 入网带宽上限（上行带宽）

公网的入网带宽是指流入云服务器实例的带宽。
- 用户购买的固定带宽大于10Mbps时，腾讯云会分配与购买的带宽相等的外网入方向带宽。
- 用户购买的固定带宽小于10Mbps时，腾讯云会分配10Mbps外网入方向带宽。

## 上调带宽上限

根据实际需求，选择不同的调整方式：
- [调整网络计费模式（按带宽计费）](#AdjustNetworkModeByBandwidth)
- [调整网络计费模式（按带宽包计费）](#AdjustNetworkModeByBandwidthPackage)

若您无法调整实例、网络的计费模式，可以 [提交工单](https://console.cloud.tencent.com/workorder/category?level1_id=6&level2_id=7&source=0&data_title=%E4%BA%91%E6%9C%8D%E5%8A%A1%E5%99%A8%20CVM&step=1) 申请上调带宽上限，我们将评估后快速给您反馈。

<span id="AdjustNetworkModeByBandwidth"></span>
### 调整网络计费模式（按带宽计费）

1. 将按流量计费的实例调整为按带宽计费，操作详情请参见 [调整网络配置](https://intl.cloud.tencent.com/document/product/213/15517)。
2. 登录 [云服务器控制台](https://console.cloud.tencent.com/cvm/index)。
3. 找到需要调整带宽的实例，单击右侧【更多】>【资源调整】>【调整网络】。
4. 在弹出的“调整网络”窗口中，调整目标带宽上限，单击【确定】即可。

<span id="AdjustNetworkModeByBandwidthPackage"></span>
### 调整网络计费模式（按带宽包计费）

1. 将按流量计费的实例调整为按带宽包计费。
> 带宽包内实例支持将带宽调整为无上限。
>
2. 登录 [云服务器控制台](https://console.cloud.tencent.com/cvm/index)。
3. 找到需要调整带宽的实例，单击右侧【更多】>【资源调整】>【调整网络】。
4. 在弹框中调整网络，调整目标带宽，单击【确定】即可。如下图所示：
![](https://main.qcloudimg.com/raw/4e6a0a6556532e91d7b3101c97c62b77.png) 

