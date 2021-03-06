# 云数据库Redis版监控 {#concept_vhm_kv4_ydb .concept}

云监控通过监控 Redis 的已用容量百分比、已用连接数百分比等监控项，帮助用户获取 Redis 的运行状态和使用情况。

用户创建 Redis 实例后，云监控自动开始对其监控，您登录云监控的Redis 页面即可查看监控详情。您还可以对监控项设置报警规则，以便数据异常时收到报警息

## 监控服务 {#section_j5m_hw4_ydb .section}

-   监控项说明

    |监控项|含义|维度|单位|最小监控粒度|
    |:--|:-|:-|:-|:-----|
    |已用容量|当前已使用Redis容量|实例|字节|1分钟|
    |已用连接数|当前客户端连接总数量|实例|个数|1分钟|
    |写入网速|当前每秒写入网络流量|实例|bps|1分钟|
    |读取网速|当前每秒读取网络流量|实例|bps|1分钟|
    |操作失败数|当前操作KVSTORE失败次数|实例|个数|1分钟|
    |已用容量百分比|当前已使用容量占总容量的比例|实例|百分比|1分钟|
    |已使用连接百分比|当前已建立的连接数占总连接的比例|实例|百分比|1分钟|
    |写入带宽使用率|当前写入带宽占总带宽的百分比|实例|百分比|1分钟|
    |读取带宽使用率|当前读取带宽占总带宽的百分比|实例|百分比|1分钟|
    |实例故障|事件类型指标，可设置报警规则|-|-|-|
    |实例主备切换|事件类型指标，可设置报警规则|-|-|-|


-   查看监控数据
    1.  登录[云监控控制台](http://cms.console.aliyun.com/#/groups/)。
    2.  进入**云服务监控**下的**云服务器 Redis 版**实例列表。
    3.  单击实例名称或**操作**中的**监控图表**，进入监控详情页面。
    4.  单击大小图切换按钮，切换大图显示\(可选\)。

## 报警服务 {#section_yy5_qw4_ydb .section}

-   参数说明
    -   监控项：云服务器 Redis 版提供的监控指标。
    -   统计周期：报警系统会按照这个周期检查您对应的监控数据是否超过了报警阈值。例如设置内存使用率报警规则的统计周期为1分钟，则每间隔 1 分钟会检查一次内存使用率是否超过了阈值。
    -   统计方法：统计方法指对超出阈值范围的设置。统计方法中可以设置平均值、最大值、最小值、求和值。
        -   平均值：统计周期内监控数据的平均值。统计结果是 15 分钟内采集的所有监控数据的平均值，当这个平均值大于80%时，才算超过阈值。
        -   最大值：统计周期内监控数据的最大值。统计周期内采集的监控数据中，最大值超过80%，即为超过阈值。
        -   最小值：统计周期内监控数据的最小值。统计周期内采集的监控数据中，最小值超过80%，即为超过阈值。
        -   求和值：统计周期内监控数据的总和。对统计周期内采集的监控数据进行求和，求和后的结果超过80%即为超过阈值。流量类指标需要用到此类统计方法。
    -   连续几次超过阈值后报警：指连续几个统计周期监控项的值持续超过阈值后触发报警。

        例如：设置 CPU 使用率超过 80% 报警，统计周期为5分钟，连续3次超过阈值后报警，则第一次探测 CPU 使用率超过80%时，不会发出报警通知。5分钟后第二次探测 CPU 使用率超过80%，也不会发出报警。第三次探测仍然超过 80% 时，才会发出报警通知。即从实际数据第一次超过阈值到最终发出报警规则，最少需要消耗的时间为统计周期×\(连续探测次数-1\)=5×\(3-1\)=10分钟。

-   设置报警规则
    1.  登录[云监控控制台](http://cms.console.aliyun.com/#/groups/)。
    2.  进入**云服务监控**下的**云服务器 Redis 版**实例列表。
    3.  单击实例列表**操作**中的**报警规则**，进入实例的报警规则页面。
    4.  单击报警规则页面右上角的**新建报警规则**，根据参数创建一条报警规则。

