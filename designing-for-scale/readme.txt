前言
总的来讲，这一章主要就是来给讲述es横向扩展方面的问题也就是scale out，对于需要了解es集群方面非常有帮助
关注点：
    es在横向扩展方面基本是可以平滑过度的painless
    但当你从一个大点的集群到一个非常大的集群的时候，需要计划和设计，但相对而言是平滑过度的
    es也有很多限制和要求，好刀用在刀刃上就好，否则也有很多问题
    默认设置是可以让你用很长时间的，所以小规模的可以暂时忽略这章节了
    具体设置呢，还得看具体的情况，没有银弹，这个章节会从两种业务情况来看这个问题：
        time-based data  例如微博啊，日志啥的
        user-based data 还可以从用户角度分割的

Elasticsearch is used by some companies to index and search petabytes of data every day, but most of us start out with something a little more humble in size. Even if we aspire to be the next Facebook, it is unlikely that our bank balance matches our aspirations. We need to build for what we have today, but in a way that will allow us to scale out flexibly and rapidly.

Elasticsearch is built to scale. It will run very happily on your laptop or in a cluster containing hundreds of nodes, and the experience is almost identical. Growing from a small cluster to a large cluster is almost entirely automatic and painless. Growing from a large cluster to a very large cluster requires a bit more planning and design, but it is still relatively painless.

Of course, it is not magic. Elasticsearch has its limitations too. If you are aware of those limitations and work with them, the growing process will be pleasant. If you treat Elasticsearch badly, you could be in for a world of pain.

The default settings in Elasticsearch will take you a long way, but to get the most bang for your buck, you need to think about how data flows through your system. We will talk about two common data flows: time-based data (such as log events or social network streams, where relevance is driven by recency), and user-based data (where a large document collection can be subdivided by user or customer).

This chapter will help you make the right decisions up front, to avoid nasty surprises later.