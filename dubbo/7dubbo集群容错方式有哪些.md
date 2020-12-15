# 集群容错方式有哪些
1. failover cluster 失败自动切换:dubbo的默认容错方案,具体重试的次数和间隔时间可用引用服务的时候配置,默认重试次数为1,也就是只调一次.
2. failback cluster 失败自动恢复:在调用失败,记录日志和调用信息,然后返回空结果给consumer,并且通过定时任务每隔5秒对失败的调用进行重试,
3. failfast cluster 快速失败:只会调用一次,失败后立即抛出异常
4. failsafe cluster 失败安全:调用出异常,记录日志不抛出,返回空结果
5. forking cluster 并行调用多个服务提供者:通过线程池创建多个线程,并发调用多个provider,结果保存到阻塞队列中,只要有一个provider返回结果,就会立即返回结果
6. broadcase cluster 逐个调用每个provider,如果其中一台报错,在循环调用中结束,抛出异常