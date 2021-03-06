## Pay-as-you-go CVM Instances

![](https://main.qcloudimg.com/raw/f9d8b46bf13c0321fcf5290a8f8a0f71.jpg)

### Notes
- When you no longer use pay-as-you-go resources, **terminate them as soon as possible** to avoid further charges.
- After a CVM instance is terminated or repossessed, the data it stores is destroyed and cannot be recovered.
- Since your actual resource consumption may change from time to time, balance alerts may not be accurate 100% of the time.

### Alerts

<table>
	<tr><th>Type</th><th>Description</th></tr>
	<tr><td><b>Arrears reminder</b></td><td>Fees for pay-as-you-go resources are deducted on the hour. If your account balance is in arrears, Tencent Cloud will notify the account owner, global resource collaborators, and financial collaborators through email and SMS.</td></tr>
	<tr><td><b>Arrears alert</b></td><td>This feature is disabled by default.</td></tr>
</table>

### Accounts in arrears
When your account balance falls below zero, you can continue to use CVM instances for the **next 2 hours**. We will continue to bill you for those two hours. After that, if your account is still overdue, your CVM instances are shutdown automatically and billing stops.
After shutdown, your CVM instances go through the following stages:
<table>
	<tr><th>Time since shutdown</th><th>Description</th></tr>
	<tr><td rowspan=2><b>≤ 24 hours</b></td><td>If your account balance is topped up to above 0, you can continue to use your instances and billing resumes.</td></tr>
	<tr><td>If your account balance remains below 0, you will not be able to start your CVM instances.</td></tr>
	<tr><td><b>＞ 24 hours</b></td><td>If your account balance remains negative and is not topped up for more than 24 hours after shutdown, your pay-as-you-go CVM instances are repossessed, and all data will be deleted and cannot be recovered. In this case, we will notify the account owner and all the collaborators through email and SMS.</td></tr>
</table>

## Bill-by-traffic Network
<table>
	<tr><th>Type</th><th>Description</th></tr>
	<tr><td><b>Balance alert</b></td><td>Network traffic consumption tends to fluctuate significantly and is difficult to predict. Therefore, we do not offer balance alerts.</td></tr>
	<tr><td><b>Arrears alert</b></td><td>When your balance falls below 0, you can continue to use the bill-by-traffic network for <b>the next 2 hours<b>. We will also continue to bill you for this usage. After 2 hours, if your account balance remains below 0, the bill-by-traffic network service is automatically stopped. </br>When your account balance is topped up to above 0, the service will resume. Check the affected CVM instances and CLB instances and resume their association if necessary.</td></tr>
</table>

> For information on traffic fees, refer to [Public Network Billing](https://intl.cloud.tencent.com/document/product/213/10578).
>
