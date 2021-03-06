## 操作场景
腾讯云容器服务 TKE 支持通过创建 PV/PVC，并为工作负载挂载数据卷的方式使用腾讯云文件存储 CFS。本文介绍如何通过以下两种方式在集群中为工作负载挂载文件存储：
- [方式1：动态创建文件存储](#dynamicCFS)
- [方式2：使用已有的文件存储](#alreadyCFS)


## 准备工作
### 安装文件存储扩展组件
>
>- 使用扩展组件功能前需 [提交工单](https://console.cloud.tencent.com/workorder/category) 进行申请。
>- 若您的集群已安装 CFS-CSI 的扩展组件，则请跳过此步骤。
>
1. 登录[ 容器服务控制台 ](https://console.cloud.tencent.com/tke2)，选择左侧导航栏中的【扩展组件】。
2. 在“扩展组件”管理页面上方选择需使用文件存储扩展组件的集群及其所在地域，并单击【新建】。
3. 在“新建扩展组件”页面，选择【CFS 腾讯云文件存储】并单击【完成】即可。



## 操作步骤
<span id="dynamicCFS"></span>
### 动态创建文件存储
<span id="StepOne"></span>
#### 创建文件存储类型 StorageClass 
通过创建文件存储类型的 StorageClass，可自定义文件存储 CFS 使用所需的模板。详情请参见 [StorageClass 管理文件存储模版](https://intl.cloud.tencent.com/document/product/457/36154)。

<span id="StepTwo"></span>
#### 通过 StorageClass 创建 PVC

通过 StorageClass 创建 PVC，可进一步定义所需的文件存储 CFS 参数。具体创建步骤如下：
1. 在目标集群详情页，选择左侧菜单栏中的【存储】>【PersistentVolumeClaim】，进入 “PersistentVolumeClaim” 页面。
2. 单击【新建】，进入“新建PersistentVolumeClaim” 界面，参考以下信息进行创建。如下图所示：
![](https://main.qcloudimg.com/raw/ce54c95ed5d4bfbe05f6c764d18c4a24.png)
	- **名称**：支持自定义设置，本文以 `cfs-pvc` 为例。
	- **命名空间**：根据实际需求进行选择，本文以 `default` 为例。
	- **Provisioner**：选择【文件存储CFS】。
	- **读写权限**：文件存储仅支持多机读写。
	- **StorageClass**：选择已在[ 创建文件存储类型 StorageClass ](#StepOne)中创建的 StorageClass，本文以 “cfs-storageclass” 为例。
3. 单击【创建PersistentVolumeClaim】即可。

#### 创建工作负载挂载 PVC
> 该步骤以创建工作负载 Deployment 为例。
> 
1. 在目标集群详情页，选择左侧导航栏中的【工作负载】>【Deployment】，进入 “Deployment” 页面。
2. 单击【新建】，进入“新建Workload” 页面，参考[ 创建 Deployment ](https://intl.cloud.tencent.com/document/product/457/30662)进行创建。并在“数据卷（选填）”中选择“使用已有PVC”，即在[ 通过 StorageClass 创建 PVC ](#StepTwo) 步骤中已创建的 PVC，本文以 “cfs-pvc” 为例。如下图所示：
![](https://main.qcloudimg.com/raw/6d3ca89ca04568527e3c8981887f284f.png)
3. 单击【创建Workload】即可完成创建。


<span id="alreadyCFS"></span>
### 使用已有的文件存储

当您需要使用已有文件存储时，可以按照以下步骤进行操作：
1. 通过已有的文件存储创建 PV。
2. 创建 PVC 时设置与上述创建的 PV 相同的 StorageClass 和容量。
3. 创建工作负载时，选择上述 PVC。
详细操作步骤请参见 [ PV 和 PVC 管理文件存储](https://intl.cloud.tencent.com/document/product/457/36155)。

## 相关信息

更多关于如何使用文件存储的信息请参见 [README_CFS.md](https://github.com/TencentCloud/kubernetes-csi-tencentcloud/blob/master/docs/README_CFS.md)。
