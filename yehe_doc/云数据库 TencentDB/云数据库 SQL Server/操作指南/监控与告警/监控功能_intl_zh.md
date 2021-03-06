为方便用户查看和掌握实例的运行信息，云数据库 SQL Server 提供了丰富的性能监控项与便捷的监控功能（自定义视图、时间对比、合并监控项等）。
>单个实例的表数量超过100万后，可能会影响数据库监控，请合理规范表的数量，控制单个实例表数量不超过100万。
 
 
## 支持监控的实例类型
云数据库 SQL Server 支持主实例、只读实例的监控，并为每个实例提供独立的监控视图供查询。


## 查看监控
1. 登录 [SQL Server 控制台](https://console.cloud.tencent.com/sqlserver)，在实例列表，单击实例名或“操作”列的【管理】，进入实例管理页。
2. 选择【系统监控】页，可查看实例各指标的监控信息。
>
>- 云数据库 SQL Server 监控粒度支持最小10s级别。
>- 云数据库 SQL Server 目前最长支持查看30天内的监控数据。


## 监控指标
云数据库 SQL Serve 系统监控支持 SQL Server 常见的25种参数，您可以通过配置 SSMS 的计数器，额外统计其他参数。

<span id = "changjian_canshu"></span>
### 常见指标
|指标|描述（单位）|指标取值|指标优化建议|
|:----:|----|:-----:|--------|
|CPU 利用率<br>（Total Processor Time）|实际 CPU 消耗的百分比（%）|max| < 30% 好<br>< 60% 正常<br>> 60% 需关注|
|事务数<br>（Transaction/sec）|平均每秒的事务数（次/秒）|max|参考业务需要|
|连接数<br>（User Connection）|平均每秒用户连接数据库的个数（个）|max|参考业务需要|
|请求数<br>（Batch Requests/sec）|-（次/秒）|max|参考业务需要|
|每秒登录次数<br>（Logins/sec）|每秒登录次数（次/秒）|max|参考业务需要|
|每秒登出次数<br>（Logouts/sec）|每秒登出次数（次/秒）|max|参考业务需要|
|已用存储空间<br>（Storage Space）|实例数据库文件和日志文件占用的空间总和（GB）|max| < 30% 好<br>< 60% 正常<br>> 60% 需关注|
|输入流量<br>（Network Receive Throughput）|所有连接输入包大小总和（MB/s）|max|参考业务需要|
|输出流量<br>（Network Transmit Throughput）|所有连接输出包大小总和（MB/s）|max|参考业务需要|
|磁盘 IOPS<br>（IPOS）|磁盘读写次数（次/秒）|max|根据实例规格中心 IOPS 建议<br>< 30% 好<br>< 60% 正常<br>> 60% 需关注|
|读取磁盘次数<br>（Read IOPS）|每秒读取磁盘次数（次/秒）|max|参考业务需要|
|写入磁盘次数<br>（Write IOPS）|每秒写入磁盘次数（次/秒）|max|参考业务需要|
|内存使用 | 实际内存消耗量（MB） |max|参考业务需要|
|剩余存储空间 | 实例数据库文件和日志文件占用的空间总和（GB）|max| < 30% 好<br>< 60% 正常<br>> 60% 需关注|

  
### 性能优化指标

|指标|描述（/单位）|指标取值|指标优化建议|
|:----:|----|:-----:|--------|
|慢查询<br>（SlowQuery）|运行时间超过一秒的查询数量（个）|avg| < 1 好<br>< 10 正常<br>> 10 需关注|
|阻塞数<br>（Processes blocked）|当前阻塞数量（个）|avg|参考业务需要|
|锁请求次数<br>（Lock Requests/sec）|平均每秒锁请求的次数（次/秒）|avg|参考业务需要|
|用户错误数<br>（User Error/sec）|平均每秒错误数（次/秒）|avg|0 好<br>> 0 需关注|
|锁等待次数<br>（Lock waits）|每秒要求调用者等待的锁请求数（次/秒）|avg|参考业务需要|
|SQL 编译数<br>（SQL Compilation/sec）|平均每秒 SQL 编译次数（次/秒）|avg|参考业务需要|
|SQL 重编译数<br>（SQL Re-Compilation/sec）|平均每秒 SQL 重编译次数（次/秒）|avg|参考业务需要|
|输入流量<br>（Network Receive Throughput）|所有连接输入包大小总和（MB/s）|avg|参考业务需要|
|输出流量<br>（Network Transmit Throughput）|所有连接输出包大小总和（MB/s）|avg|参考业务需要|
|每秒钟 SQL 做全表扫描数目<br>（Full Scans/sec）|磁盘读写次数（次/秒）|avg|根据实例规格中心 IOPS 建议<br>< 30% 好<br>< 60% 正常<br>> 60% 需关注|
|缓存区缓存命中率<br>（Buffer cache hit ratio）|数据缓存（内存）命中率（%）|avg|≥ 95% 好<br>≥ 90% 正常<br>< 90% 需关注|
|每秒闩锁等待数量<br>（Latch Waits/sec）|每秒闩锁等待数量（次/秒）|avg|参考业务需要|
|平均锁等待延迟<br>（Average Wait Time）|每个导致等待的锁请求的平均等待时间（ms）|max|参考业务需要|
|平均网络 IO 延迟<br>（Network IO waits）|平均网络 IO延迟时间（ms）|max|参考业务需要|
|执行缓存缓存命中率<br>（Plan Cache：Cache Hit Ratio）|每个 SQL 有一个执行计划，执行计划的命中率（%）|max|≥ 95% 好<br>≥ 90% 正常<br>< 90% 需关注|



