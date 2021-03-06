In Tencent Cloud CMQ, queuing service and requests/message retention in topic mode are free of charge. Traffic is billed in the following way:
- If you are accessing CMQ over the public network, the public network inbound traffic will be free of charge, while the public network outbound traffic will incur traffic fees. For more information, please see [Public Network Billing Mode (Bill-by-Traffic)](https://intl.cloud.tencent.com/document/product/213/10578).
- If you are accessing CMQ over the private network, both outbound traffic and inbound traffic are free of charge; therefore, private network access is recommended.
 
## Queue Pricing
**Total fees** = request fees + message retention fees + outbound traffic fees.
**Billing mode**: all types of fees are charged by region separately and settled hourly.

> Currently, requests and message retention in CMQ are free of charge. You will be notified by email or SMS before billing for them officially begins. Please feel free to use them as you desire.


### Number of requests
In a single region, after you activate the CMQ service, Tencent Cloud will count the API/SDK requests in CMQ **hourly***. The number of requests is in millions and accurate to two decimal places. The request fees are charged at **2.00 USD/million requests** and settled hourly.

#### Example 1
If the total number of user requests between 16:00 and 17:00 on May 20, 2016 is 1,323,454, the billable number of requests will be 1.32 (million requests), and the fees for the requests during this period will be 1.32 * 2.00 = 2.64 USD.
#### Example 2
If the total number of user requests between 18:00 and 19:00 on May 20, 2016 is 181,000, the billable number of requests will be 0.18 (million requests), and the fees for the requests during this period will be 0.18 * 2.00 = 0.36 USD.

### Message retention (including message rewind)
CMQ charges message retention fees hourly by region in the following way:
```
Message retention fees = total number of messages * unit price of heaped messages
```
The unit price of heaped messages is **0.010 USD/million messages/hour**. The total number of messages is counted in millions, and the total number of messages in an hour is the average number of heaped messages per minute (i.e., 60 sample points are collected per hour and then averaged). The fees are rounded to two decimal places. Message rewind fees will be merged in message retention fees and calculated together.

#### Example
If the number of heaped messages in queue A between 16:00 and 17:00 on May 20, 2016 is 1,323,450, the message retention fees for queue A during this period will be 0.01 * 1.32 = 0.01 USD.

### Outbound traffic
Tencent Cloud network traffic billing rule: inbound traffic is free of charge, while outbound traffic is billed (public network traffic fees are charged normally during the beta test; therefore, you are recommended to use the private network API address for testing).

| Traffic Type | Definition | Usage | Unit Price |
|---------|---------|---------|---------|
| Inbound traffic | Data traffic to CMQ | All | Free of charge |
| Private network outbound traffic (intra-region) | Traffic generated when a business system (in the same region as CMQ) actively gets data from CMQ or CMQ actively pushes data to it through the private domain name of CMQ (over Tencent Cloud private network) | All | Free of charge |
| Public network outbound traffic | Traffic generated when a business system (in the same region as CMQ) actively gets data from CMQ or CMQ actively pushes data to it through the internet domain name of CMQ (over the internet) | All | Mainland China: 0.80 USD/GB; Hong Kong (China): 1.00 USD/GB; other regions: 0.50 USD/GB |

## Topic Pricing
**Total fees** = API request fees + message retention fees + outbound traffic fees
**Billing mode**: pay-as-you-go (by hour) and by region (all types of fees are charged by region separately)
> Currently, API requests and message retention in CMQ are free of charge. You will be notified by email or SMS before billing for them officially begins. Please feel free to use them as you desire.


### API requests
- Currently, the maximum message size allowed for publishing is 64 KB, and every 64 KB of published data is billed as one request (if the data is below 64 KB, it will be calculated as 64 KB). One API call by one subscriber to a topic will be billed as one request. For example, with 30 subscribers, one API call with a load of 64 KB will be billed as 30 requests. 
- **Unit price of published messages**: 2 USD/million messages.
The fees are rounded to two decimal places. For example, if the number of published messages is 1,431,321 (1.43 million), the fees will be 2.86 USD.
- **Billing scenario**
When a queue is set as a subscriber to a topic, two parts of fees will be charged after the topic delivers messages: API request fees for receiving messages by the queue and message delivery fees for the topic.

### Message retention
If messages are heaped on the topic (not published or failed after multiple retries), the heaped messages will be billed as follows: 
```
Message retention fees = total number of messages * unit price of heaped messages
```
**Unit price of heaped messages**: 0.010 USD/million messages/hour
Fees are calculated based on the average number of heaped messages in the current hour (i.e., 60 sample points are collected per hour and then averaged).
The fees are rounded to two decimal places. For example, if the number of heaped messages is 1,431,321 (1.43 million), the fees will be 0.01 USD.


#### Billing example
If the number of heaped messages in topic A between 16:00 and 17:00 on May 20, 2016 is 1,323,450, the message retention fees for topic A during this hour will be 0.01 USD.

### Outbound traffic
Tencent Cloud traffic billing rule: topic inbound traffic is free of charge, while topic outbound traffic for message publishing is billed (public network traffic fees are charged normally during the beta test; therefore, you are recommended to use the private network API address for testing).
**Pricing**: Mainland China: 0.80 USD/GB; Hong Kong (China): 1.00 USD/GB; other regions: 0.50 USD/GB.
**Billing dimension**: fees are charged separately by topic; when there are multiple topics, the outbound traffic will be aggregated.

| Traffic Type 	| Definition 	| Usage |	 Unite Price |
|---------|---------|---------|---------|
| Inbound traffic 	| Data traffic to CMQ 	| All	 | Free of charge |
| Private network outbound traffic (in the same region) |	 Traffic generated when a CMQ topic delivers data within the same region (over Tencent Cloud private network) |	 All 	| Free of charge |
| Public network outbound traffic | Traffic generated when a CMQ subscription delivers messages (over the public network) | All | Mainland China: 0.80 USD/GB; Hong Kong (China): 1.00 USD/GB; other regions: 0.50 USD/GB |







