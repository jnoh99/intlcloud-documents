## Obtaining the migration Tool  
 [Click here](https://go2tencentcloud-1251783334.cos.ap-guangzhou.myqcloud.com/latest/go2tencentcloud.zip) to obtain the compressed migration tool package.

## Choosing a migration mode based on the network environment
Choose the appropriate migration mode according to the network environments of your source servers and destination CVMs.
Currently, the migration tool supports the default mode and the private network mode. The private network mode applies to three scenarios. Each migration mode or scenario has different network requirements for source servers and destination CVMs. If both source servers and destination CVMs can access the public network, you can use the default mode for migration. If source servers or destination CVMs cannot directly access the public network, you need to establish connections through [VPC Peering Connection](https://intl.cloud.tencent.com/document/product/215/5000), [VPN Connection](https://intl.cloud.tencent.com/document/product/1037), [Cloud Connect Network](https://intl.cloud.tencent.com/document/product/1003) ,or [Direct Connect](https://intl.cloud.tencent.com/document/product/216) before using the private network mode for migration.

## Data Backup
You can back up your data by creating snapshots.

## Checking before migrating
Before migrating, check the following items for source servers and destination CVMs respectively:
<table>
	<tr><th style="width: 15%;">Destination CVM</th><td><ol  style="margin: 0;"><li>Storage: The cloud disks of the destination CVM, including system disks and data disks. Verify that they have sufficient storage to store the data from the source server.</li><li>Security group: Ports 443 and 80 must be open in a security group.</li><li>Bandwidth setting: We recommend that you increase bandwidth for faster migration. The traffic consumed during migration will be approximately equal to the data volume. Change your networking billing method in advance if needed.</li><li>Operating system: We recommend that the destination CVM and the source server use the same operating system. Different operating systems will result in inconsistency between the image that will be created later and the actual operating system. For example, when migrating a source server with the CentOS 7 system installed, choose a CVM with the CentOS 7 system installed as the migration destination.</li></ol></td></tr>
	<tr><th>Linux source server</th><td><ol  style="margin: 0;"><li>Check for and install Virtio. For more information, see <a href="https://intl.cloud.tencent.com/document/product/213/9929">Checking Virtio Drivers in Linux</a>.</li><li>Check whether rsync and grub2-install (or grub-install) are installed.</li><li>Check whether SELinux is enabled. Disable it if enabled.</li><li>When a migration request is sent to Tencent Cloud API, the API uses the current UNIX time to check against the generated token. In this case, ensure that the current system time is correct.</li></ol></td></tr>
</table>

> 
> - You can use tool commands to automate the checking of source servers, for example, `sudo ./go2tencentcloud_x64 --check`.
> - By default, the go2tencentcloud migration tool automatically performs checking when it starts to run. If you want to skip the check and enforce migration, configure the value of the `Client.Extra.IgnoreCheck` field in the client.json file to `true`.
> 

## Starting Migration
 
1. (Optional) Establish a connection between the source server and the destination CVM.  
 - If you are using the private network mode, establish a connection between the source sever and the destination CVM through [VPC Peering Connection](https://intl.cloud.tencent.com/document/product/215/5000), [VPN Connection](https://intl.cloud.tencent.com/document/product/1037), [Cloud Connect Network](https://intl.cloud.tencent.com/document/product/1003), or [Direct Connect](https://intl.cloud.tencent.com/document/product/216).
 - Skip this step if you are using the default mode.
2. Configure the user.json file.
The user.json file is for configuring the source server and the destination CVM. It contains the following configuration items:
 - The access key pair of your account API, that is, SecretId and SecretKey. For more information, see [Access Keys](https://intl.cloud.tencent.com/document/product/598/32675).
 - The region where the destination CVM resides.
 - The instance ID of the destination CVM.
 - (Optional) The data disk configuration of the source server.  
3. Configure the client.json file.
The client.json file is for configuring the migration mode and other migration configuration items. You need to configure the `Client.Net.Mode` parameter in the client.json file despite migration modes or scenarios.
4. (Optional) Remove files and directories on the server that do not need to be migrated.  
 Edit the rsync\_excludes\_linux.txt file on the Linux source server to remove files and directories that do not need to be migrated.
5. Run the tool.
For example, on a 64-bit Linux source server, run the following command with root permissions to run the tool.
```
sudo ./go2tencentcloud_x64
```
Wait for the migration process to complete.
If the migration is successful, the following console output appears:
 ![](https://main.qcloudimg.com/raw/8e0f3c07c186021d4989b3c3c7b3d1cd.png)
