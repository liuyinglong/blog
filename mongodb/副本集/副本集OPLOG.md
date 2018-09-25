# 副本集OPLOG

oplog（操作日志）是一种特殊的 capped 集合，它滚动保存了数据库的数据操作。

> 注意：
>
> 从mongodb4.0之后，不同于其他的capped集合，可以超过其配置的大小限制，以避免删除多数提交点。 

mongodb在primary执行数据操作之后在主节点记录操作日志，副节点异步进程中 复制并执行这些操作。所有副本集成员都拥有oplog的copy。in the [`local.oplog.rs`](https://docs.mongodb.com/manual/reference/local-database/#local.oplog.rs) collection, which allows them to maintain the current state of the database. 

为了保持同步，所有的副本集成员会向其他的所有成员发送心跳，任何一个副节点可以从其他任意节点导入oplog。

每一个操作在oplog是[idempotent](https://docs.mongodb.com/manual/reference/glossary/#term-idempotent). 那就是说，无论对目标数据执行一次或者多次，oplog都会产生相同的结果。



## Oplog的大小

当你开启副本集成员的第一时间，如果您没有特殊指定oplog的大小，mongodb创建一个默认大小的oplog。

### Unix 和 Windowns 系统

| Storage Engine（存储类型）                                   | Default Oplog Size（默认大小） | Lower Bound（最低） | Upper Bound（最高） |
| ------------------------------------------------------------ | ------------------------------ | ------------------- | ------------------- |
| [In-Memory Storage Engine](https://docs.mongodb.com/manual/core/inmemory/) | 5% of physical memory          | 50 MB               | 50 GB               |
| [WiredTiger Storage Engine](https://docs.mongodb.com/manual/core/wiredtiger/) | 5% of free disk space          | 990 MB              | 50 GB               |
| [MMAPv1 Storage Engine](https://docs.mongodb.com/manual/core/mmapv1/) | 5% of free disk space          | 990 MB              | 50 GB               |



### 64位macOS系统

| Storage Engine                                               | Default Oplog Size        |
| ------------------------------------------------------------ | ------------------------- |
| [In-Memory Storage Engine](https://docs.mongodb.com/manual/core/inmemory/) | 192 MB of physical memory |
| [WiredTiger Storage Engine](https://docs.mongodb.com/manual/core/wiredtiger/) | 192 MB of free disk space |
| [MMAPv1 Storage Engine](https://docs.mongodb.com/manual/core/mmapv1/) | 192 MB of free disk space |

在大多数情况下，默认的oplog大小已经足够。举例来说。一个oplog的大小是可用磁盘大小的5%,并且在24小时内填满， then secondaries can stop copying entries from the oplog for up to 24 hours without becoming too stale to continue replicating. However, most replica sets have much lower operation volumes, and their oplogs can hold much higher numbers of operations. 

在mongod创建oplog之前，您可以指定他的大小通过[`oplogSizeMB`](https://docs.mongodb.com/manual/reference/configuration-options/#replication.oplogSizeMB) ，一旦您启动一个副本集成员，可以使用[`replSetResizeOplog`](https://docs.mongodb.com/manual/reference/command/replSetResizeOplog/#dbcmd.replSetResizeOplog)  命令改变oplog的size。[`replSetResizeOplog`](https://docs.mongodb.com/manual/reference/command/replSetResizeOplog/#dbcmd.replSetResizeOplog)  可以动态调整oplog的大小而无需重启mongod程序。

## Workloads that Might Require a Larger Oplog Size

如果您能预测您的副本集的工作量属于以下几种模式，这样您可能需要比默认的oplog size更大的size。反之，如果您的应用是大量的读操作和小量的写操作，那么可以设置一个小的oplog size.

下面几种工作模式需要更大的oplog size.

###一次更新多个dcoument

The oplog must translate multi-updates into individual operations in order to maintain [idempotency](https://docs.mongodb.com/manual/reference/glossary/#term-idempotent). This can use a great deal of oplog space without a corresponding increase in data size or disk use. 

### 删除的数据量等同于插入的数据量

如果你删除的数据等同于你插入的数据，数据库的磁盘没有显著的增长，但是操作日志的大小就相当大了



### Significant Number of In-Place Updates

如果工作的很大一部分是不会增加文档大小的更新，则数据库会记录大量的操作，但是不会改变数据在磁盘中占用的大小。

## oplog 状态

查看oplog的状态，包含size和期间的操作，执行 [`rs.printReplicationInfo()`](https://docs.mongodb.com/manual/reference/method/rs.printReplicationInfo/#rs.printReplicationInfo)  方法。关于更多的oplog操作,戳这里[Check the Size of the Oplog](https://docs.mongodb.com/manual/tutorial/troubleshoot-replica-sets/#replica-set-troubleshooting-check-oplog-size). 



Under various exceptional situations 