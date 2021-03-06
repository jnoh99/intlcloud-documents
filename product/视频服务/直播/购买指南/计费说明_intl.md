
## Traffic and Bandwidth
The LVB traffic and bandwidth statistics detail the downstream traffic and bandwidth generated by connecting the user to the cache origin server. LVB offers two pay-as-you-go billing plans: Bill-by-traffic or Bill-by-bandwidth. The default plan for new users is bill-by-traffic. 

### Bill-by-traffic
LVB bill-by-traffic utilizes a tiered pricing rate with a daily billing cycle. See the table below for rates. 

| Traffic tier | Price (USD/GB/day) |
|---------|---------|
|0 - 500GB|	0.0459|
|500GB (inclusive) - 2TB|0.0441|
|2TB (inclusive) - 50TB|	0.0406|
|50TB (inclusive) -100TB	|0.0335|
|≥100TB	|0.0282|

**Billing:**
1. Billable item: The downstream traffic generated in mainland China.
2. Billing method: Pay-as-you-go.
3. Billing cycle: Daily billing cycle. The previous day's fees will be deducted at 10am the next day. See the billing statement for details. 
4. Billing rules: The fee is calculated by multiplying the accumulated traffic on a natural day by the unit price at the corresponding tier.
5. Billing example:
       1. For a 1 hour LVB session at 500Kbps bitrate and 100  viewers, the traffic consumed is approximately:
          500/8 x 3600 x 100 = 22500000KB = 22.5GB
       2. If the LVB session is on January 1, 2019 and generated 22.5GB of downstream traffic, the LVB traffic bill you need to pay on January 2 is as follows:
          Daily LVB fee = 0.0459 (USD/GB) x 22.5 (GB) = 1.03275 USD

### Bill-by-bandwidth
LVB bill-by-bandwidth utilizes a tiered pricing rate billed by the daily peak bandwidth with a daily billing cycle. See the table below for rates. 

| Bandwidth tier | Price (USD/Mbps/day) |
|---------|---------|
|0 - 500Mbps|	0.1129|
|500Mbps (inclusive) - 5Gbps|0.1094|
|5Gbps (inclusive) - 20Gbps|	0.1041|
|≥20Gbps	|0.1024|

**Billing:**
1. Billable item: The downstream bandwidth generated in mainland China.
2. Billing method: Pay-as-you-go.
3. Billing cycle: Daily billing cycle. The previous day's fees will be deducted at 10am the next day. See the billing statement for details. 
4. Billing rules: The fee is calculated by multiplying the peak bandwidth on a natural day by the unit price at the corresponding tier.
5. Billing example:
       1.  For a 1 hour LVB session at 500Kbps bitrate and 100  viewers, the bandwidth consumed is approximately:
          500Kbps x 100 = 50000Kbps = 50Mbps
       2. If the LVB session is on January 1, 2019 and generated 50Mbps of downstream bandwidth, the LVB bandwidth bill you need to pay on January 2 is as follows:
          Daily LVB bandwidth fee = 0.1129 (USD/Mbps/day) x 50 (Mbps) = 5.645 USD

> If you have a large live broadcast operation and the consumption of Tencent Cloud resources has exceeded or is expected to exceed 10,000 USD, a daily billing plan may not meet your needs. Please contact Tencent Cloud sales team to discuss an appropriate billing plan. For more information, please contact your account manager or [submit a ticket](https://console.cloud.tencent.com/workorder/category).

### Global Acceleration
The LVB global traffic and bandwidth statistics detail the downstream traffic and bandwidth generated by connecting the user and the global cache origin server. LVB Global offers two pay-as-you-go billing plans: Bill-by-global-traffic or Bill-by-global-bandwidth. The default plan for new users is bill-by-global-traffic.

#### Bill-by-global-traffic
LVB bill-by-global-traffic utilizes a tiered pricing rate with a daily billing cycle. See the table below for rates. 

| Traffic tier | Price (USD/GB/day) |
|---------|---------|
|0 - 500GB|	0.0794|
|500GB (inclusive) - 2TB|0.0759|
|2TB (inclusive) - 50TB|	0.0724|
|50TB (inclusive) -100TB |0.0671|
|≥100TB	|00.6|

**Billing:**

1. Billable item: The downstream traffic generated outside Mainland China.
2. Billing method: Pay-as-you-go.
3. Billing cycle: Daily billing cycle. The previous day's fees will be deducted at 10am the next day. See the billing statement for details.
4. Billing rules: The fee is calculated by multiplying the accumulated traffic on a natural day by the unit price at the corresponding tier.
5. Billing example:
		If you use the LVB service on January 1, 2019 and generated 1TB of global downstream traffic, the LVB traffic bill you need to pay on January 2 is as follows:
		Daily LVB traffic fee = 0.0759 (USD/GB) x 1000 (GB) = 75.9 USD

#### Bill-by-global-bandwidth
LVB bill-by-global-bandwidth utilizes a tiered pricing rate billed by the daily peak bandwidth with a daily billing cycle. See the table below for rates. 

| Bandwidth tier | Price (USD/Mbps/day) |
|---------|---------|
|0 - 500Mbps|0.2294|
|500Mbps (inclusive) - 5Gbps|0.2118|
|≥5Gbps	|0.1941|

**Billing:**
1. Billable item: The downstream bandwidth generated outside Mainland China.
2. Billing method: Pay-as-you-go.
3. Billing cycle: Daily billing cycle. The previous day's fees will be deducted at 10am the next day. See the billing statement for details. 
4. Billing rules: The fee is calculated by multiplying the peak bandwidth on a natural day by the unit price at the corresponding tier.
5. Billing example:
		If you use the LVB service on January 1, 2019 and generated 600Mbps of downstream bandwidth, the LVB traffic bill you need to pay on January 2 is as follows:
		Daily LVB traffic fee = 0.2118 (USD/Mbps) x 600 (Mbps) = 127.08 USD

## LVB Transcoding
LVB provides standard transcoding and ultra-fast HD transcoding services which are billed according to the encoding method used, transcoding resolution and transcoding duration. The transcoding feature is disabled by default. If you need to use it, you can enable it in the LVB console or through cloud API. **If you use the watermark or stream mixing feature, transcoding fees will also be incurred, and the resolution will be the same as the resolution of the live stream to which the watermark is added.** The prices of standard transcoding and ultra-fast HD transcoding are as shown in the table below:
> Transcoding pricing will take effect on January 1, 2019.

<table>
<tr>
<td><b>Encoding method</td>
<td><b>Resolution</td>
<td><b>Price (USD/minute)</td>
</tr>
<tr>
<td rowspan="5"><b>H.264</td>
<td>480p</td>
<td>0.0028</td>
</tr>
<tr>
<td>720p</td>
<td>0.0057</td>
</tr>
<tr>
<td>1080p</td>
<td>0.0111</td>
</tr>
<tr>
<td>2K</td>
<td>0.024</td>
</tr>
<tr>
<td>4K</td>
<td>0.0491</td>
</tr>
<tr>
<td rowspan="5"><b>H.265</td>
<td>480p</td>
<td>0.0141</td>
</tr>
<tr>
<td>720p</td>
<td>0.0275</td>
</tr>
<tr>
<td>1080p</td>
<td>0.0549</td>
</tr>
<tr>
<td>2K</td>
<td>0.1183</td>
</tr>
<tr>
<td>4K</td>
<td>0.2366</td>
</tr>
</table>

> Transcoding fee = Encoding method - resolution - price x transcoding duration. If no transcoding service is used, no fees will be incurred.

**Billing:**
1. Billable item: The duration of live stream transcoding (or the duration of the mixed stream or the live stream to which the watermark is added if the stream mixing or watermarking feature is enabled).
2. Billing method: Pay-as-you-go.
3. Billing cycle: For daily billing cycles, the previous day's fees will be deducted at 10am the next day. For users on a monthly billing cycle, this month's transcoding bill will be generated between the 1st and 5th day of the next month. 
4. Billing rules: The fee is calculated by multiplying the transcoding duration for different transcoding methods and resolutions on a natural day by the corresponding unit price.
5. Billing example:
		If you use LVB transcoding and watermarking service on January 1, 2019, where live stream A is transcoded to H.264_720P for one hour and live stream B is watermarked at 480p for 30 minutes, the LVB transcoding bill you need to pay on January 2 is as follows:
		Daily live transcoding fee = 0.0057 (USD/minute) x 60 (minutes) +  0.0028 (USD/minute) x 30 (minutes) = 0.426 USD

### 		Ultra-fast HD
<table>
<tr>
<td><b>Encoding method</td>
<td><b>Resolution</td>
<td><b>Price (USD/minute)</td>
</tr>
<tr>
<td rowspan="5"><b>Ultra-fast HD</td>
<td>480p</td>
<td>0.0116</td>
</tr>
<tr>
<td>720p</td>
<td>0.0222</td>
</tr>
<tr>
<td>1080p</td>
<td>0.0443</td>
</tr>
</table>

> Transcoding fee = Encoding method - resolution - price x transcoding duration.

**Billing:**
1. Billable item: The duration of live stream transcoded to ultra-fast HD.
2. Billing method: Pay-as-you-go.
3. Billing cycle: For daily billing cycles, the previous day's fees will be deducted at 10am the next day. For users on a monthly billing cycle, this month's transcoding bill will be generated between the 1st and 5th day of the next month. 
4. Billing rules: The fee is calculated by multiplying the ultra-fast HD transcoding duration on a natural day by the corresponding unit price.
5. Billing example:
		If you use ultra-fast HD transcoding service on January 1, 2019, where live stream A is transcoded to ultra-fast HD at 720p for one hour and live stream B is transcoded to ultra-fast HD at 480p for 30 minutes, the ultra-fast HD LVB transcoding bill you need to pay on January 2 is as follows:
		Daily ultra-fast HD LVB transcoding fee = 0.0222 (USD/minute) x 60 (minutes) + 0.0116 (USD/minute) x 30 (minutes) = 1.68 USD
		
## Live Recording
LVB can record and store live streams in VOD. The recording feature is disabled by default and can be enabled in the console or through cloud API. Use of the recording feature will incur a fee, and the bill will be calculated according to the peak number of concurrent LVB recording channels of the current month. See the following table for rates. 

| Billing type | Price (USD/channel/month) |
|---------|---------|
| Peak number of recording channels |5.2941 |

**Billing:**
1. Billable item: The number of LVB recording channels.
2. Billing method: Pay-as-you-go.
3. Billing cycle:  Monthly billing cycle. The current month's bill will be generated between the 1st and 5th day of the next month. See the billing statement for details. 
4. Billing rules: The fee is calculated by multiplying the peak number of concurrent LVB recording channels in a natural month by the unit price. One recording file is counted as one channel of recording stream. For example, if MP4 and HLS files are recorded for the same stream ID, they will be counted as two channels of recording streams.
5. Billing example:
		If you use the LVB recording service from January 1 to February 1, 2019, and the peak number of recording channels in the month is 10, then the live recording bill you need to pay on February 2 is as follows:
		LVB recording fee for January  = 5.2941 (USD/channel/month) x 10 (channels) = 52.941 USD

## LVB Screen Capture
LVB can take screenshots of the live stream. The screen capture feature is disabled by default and can be enabled in the console or through cloud API. Use of the screen capture feature will incur a fee. The first 1,000 screenshots are offered for free every month. Any additional screenshots taken will incur fees. The bill will be calculated according to the total number of screenshots taken for the month. See the following table for rates. 

| Screenshots | Price (USD/thousand screenshots) | Note |
|---------|---------|-----|
|< 1,000 | 0 USD | First 1,000 screenshots each month is free |
|≥ 1,000 | 0.0176 USD/thousand screenshots | Screenshots less than 1,000 will be counted as 1,000 each month |

**Billing:**
1. Billable item: The number of LVB screenshots.
2. Billing method: Pay-as-you-go.
3. Billing cycle: Monthly billing cycle. The current month's bill will be generated between the 1st and 5th day of the next month. See the billing statement for details. 
4. Billing rules: The fee is calculated by multiplying the total number of screenshots taken in a natural month by the unit price.
5. Billing example:
		If you use the LVB screen capture service from January 1 to February 1, 2019, and a total of 168,000 screenshots was taken in the month, then the LVB screen capture bill you need to pay on February 2 is as follows:
		LVB screen capture fee for January = 0.0176 (USD/thousand screenshots) x (168 - 1) thousand screenshots = 2.9392 USD

## Intelligent Porn Detection
LVB can intelligently detect pornography in the live stream. The porn detection feature is disabled by default and can be enabled in the console or through cloud API. As the porn detection service requires taking screenshots of the live stream, enabling this feature will include fees for both porn detection and screen capture. The first 1,000 porn detection screenshots are offered for free every month. Any additional screenshots taken will incur fees. The bill will be calculated according to the total number of porn detection screenshots taken for the month. See the following table for rates. 

| Screenshots | Price (USD/thousand screenshots) | Note |
|---------|---------|-----|
|< 1,000 | 0 USD| First 1,000 porn detection screenshots each month is free |
|≥ 1,000 | 0.2294 USD/thousand screenshots | Screenshots less than 1,000 will be counted as 1,000 each month |
