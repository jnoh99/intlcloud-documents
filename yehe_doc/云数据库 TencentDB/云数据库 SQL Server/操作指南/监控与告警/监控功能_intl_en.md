To make it easier for you to view and stay up to date with how instances work, TencentDB for SQL Server provides a wide variety of performance monitoring metrics and convenient monitoring features (custom view, time comparison, merged monitoring metrics, etc).
>If the number of tables in a single instance exceeds one million, database monitoring may be affected. Please control this value appropriately and make sure that it is below one million.
 
 
## Types of Instances for Monitoring
TencentDB for SQL Server master and read-only instances can be monitored, and each instance is provided with a separate monitoring view for easy query.


## Viewing Monitoring Information
1. Log in to the [TencentDB for SQL Server Console](https://console.cloud.tencent.com/sqlserver). In the instance list, click an instance name or **Manage** in the "Operation" column to enter the instance management page.
2. Select the **System Monitoring** tab to view the monitoring information of each metric of the instance.
>
>- TencentDB for SQL Server monitoring supports a granularity of down to 10 seconds.
>- Currently, you can view monitoring data of TencentDB for SQL Server in the last 30 days.


## Monitoring Metrics
The system monitoring of TencentDB for SQL Server supports 25 common parameters of SQL Server. You can collect statistics of other parameters by configuring the counters of SSMS.

<span id = "changjian_canshu"></span>
### Common metrics
| Metric | Description (Unit) | Value | Optimization Suggestion |
|:----:|----|:-----:|--------|
| CPU Utilization <br>(Total Processor Time) | Actual CPU utilization (%) | max | < 30% Good <br>< 60% Normal <br>> 60% Attention required |
| Transaction Count <br>(Transaction/sec) | Average number of transactions per second (transactions/sec) | max | Dependent on business needs |
| Connection Count <br>(User Connection) | Average number of user connections to the database per second (-) | max | Dependent on business needs |
| Request Count <br>(Batch Requests/sec) | - (requests/sec) | max | Dependent on business needs |
| Logins <br>(Logins/sec) | Number of logins per second (logins/sec) | max | Dependent on business needs |
| Logouts <br>(Logouts/sec) | Number of logouts per second (logouts/sec) | max | Dependent on business needs |
| Used Storage Capacity <br>(Storage Space) | Sum of capacity used by instance database files and log files (GB) | max | <30% Good <br><60% Normal <br>>60% Attention required |
| Inbound Traffic <br>(Network Receive Throughput) | Sum of all inbound packets of all connections (MB/s) | max | Dependent on business needs |
| Outbound Traffic <br>(Network Transmit Throughput) | Sum of all outbound packets of all connections (MB/s) | max | Dependent on business needs |
| Disk IOPS <br>(IPOS) | Disk reads/writes (times/second) | max | Follow the suggestions for IOPS in the instance specification center <br>< 30% Good <br>< 60% Normal <br>> 60% Attention required |
| Disk Reads <br>(Read IOPS) | Number of disk reads per second (reads/second) | max | Dependent on business needs |
| Disk Writes <br>(Write IOPS) | Number of disk writes per second (writes/second) | max | Dependent on business needs |
| Memory Usage | Used memory capacity (MB) |max| Dependent on business needs |
| Remaining Storage Space | Sum of capacity used by instance database files and log files (GB) | max | <30% Good <br><60% Normal <br>>60% Attention required |

  
### Performance optimization metrics

| Metric | Description (Unit) | Value | Optimization Suggestion |
|:----:|----|:-----:|--------|
| Slow Queries <br>(SlowQuery) | Number of queries running for more than one second (-) | avg | < 1 Good <br>< 10 Normal <br>> 10 Attention required |
| Blocls <br>(Processes blocked) | Current number of blocked processes (-) | avg | Dependent on business needs |
| Lock Request Count <br>(Lock Requests/sec) | Average number of lock requests per second (requests/sec) | avg | Dependent on business needs|
| User Error Count <br>(User Error/sec) | Average number of errors per second (errors/sec) | avg | 0 Good <br>> 0 Attention required |
| Lock Wait Count <br>(Lock waits) | Number of lock requests requiring caller to wait per second (waits/sec) | avg | Dependent on business needs |
| SQL Compilations <br>(SQL Compilation/sec) | Average number of SQL compilations per second (compilations/sec) | avg | Dependent on business needs |
| SQL Recompilation Count <br>(SQL Re-Compilation/sec) | Average number of SQL recompilations per second (recompilations/sec) | avg | Dependent on business needs |
| Inbound Traffic <br>(Network Receive Throughput) | Sum of all inbound packets of all connections (MB/s) | avg | Dependent on business needs |
| Outbound Traffic <br>(Network Transmit Throughput) | Sum of all outbound packets of all connections (MB/s) | avg | Dependent on business needs |
| Full Table Scans <br>(Full Scans/sec) | Number of disk reads/writes (times/second) | avg | Follow the suggestions for IOPS in the instance specs center <br>< 30% Good <br>< 60% Normal <br>> 60% Attention required |
| Buffer Cache Hit Rate <br>(Buffer cache hit ratio) | Data cache (memory) hit rate (%) |avg|≥ 95% Good <br>≥ 90% Normal <br>< 90% Attention required |
| Latch Waits <br>(Latch Waits/sec) | Number of latch waits per second (waits/sec) | avg | Dependent on business needs |
| Average Lock Wait Delay <br>(Average Wait Time) | Average wait time for each lock request that causes a wait (ms) | max | Dependent on business needs |
| Average Network IO Delay <br>(Network IO waits) | Average network IO delay time (ms) | max | Dependent on business needs |
| Execution Cache Hit Rate <br>(Plan Cache: Cache Hit Ratio) | Hit rate of the execution plan of each SQL (%) | max | ≥ 95% Good <br>≥ 90% Normal <br>< 90% Attention required |



