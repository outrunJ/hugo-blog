
# 基础
    remote dictionary server
    特点
        no-sql, c编写
        内存数据库       # 请求不经过parser和optimizer
        key-value
        单线程
        可持久化

    与memcache区别
        memcache全在内存，不能持久化，redis部分硬盘
        memcache类型支持简单
            # memcache类型只有字符串，append字符串, blacklist删除麻烦
        emecache多线程, redis单线程
        底层模型，与客户端通信协议不同，redis自己实现vm机制(冷热数据分离)
        value, memcache只能存1MB, redis可存1GB
        redis可设置expire, 支持排行榜, 浮点数
    类型
        string
            整个或一部分操作
            整数、浮点数自增自减
        list
            两边推入或弹出
            偏移量trim
            读单个多个元素
            值查找移除元素
        set
            增删查单个元素
            单个元素是否存在
            交集、并集、差集
            随机取元素
        hash
            增删查单个键值对
            获取所有键值对
        zset
            # 有序集合, 排序根据score, score为双精度浮点数
            增删查单个元素
            根据range或成员获取元素
    应用
        会话缓存(session cache)
        全面缓存(FPC)
        队列
        排行榜/计数器
        发布/订阅
    命令
        文件命令
            redis-server
                # 端口为6379
                redis-server /etc/redis.conf  来加载配置文件
            redis-cli
            redis-benchmark
                # 性能测试工具

        redis-cli命令
            ping
                # 成功时返回 PONG
            shutdown
                # 关闭redis-server服务
                -p 端口号
            quit
# 功能
    性能高     # 100k次读写/s
    数据类型丰富
    所有操作有原子性
    支持发布/订阅，通知，key过期


    发布订阅
            subscribe
            psubscribe
                    # 订阅给定模式匹配的所有频道
            unsubscribe
            punsubscribe
            publish

            sort
                    # 列表、集合、有序集合排序，返回结果或生成存储

    过期
            persist
                    # 移除键过期时间
            ttl
                    # 键距离过期时间还有多少秒
            pttl
                    # 多少毫秒
            expire
                    # 给定键指定数秒后过期
            pexpire
                    # 指定的毫秒后过期
            expireat
                    # unix时间戳过期
            pexpireat
                    # 毫秒unix时间戳

    事务
                    # 事务期其他客户端命令阻塞
            multi
                    # 创建事务队列，开始记录命令
            exec
                    # 提交事务队列
            watch
                    # 对键加锁
            unwatch
            discard
                    # 取消事务
    持久化
            bgsave
                    # fork线程创建快照, windows不支持
            save
                    # 停止响应创建快照
            sync
                    # 向主服务器要求复制时，主服务器bgsave，非刚bgsave过
            bgrewriteaof
                    # 重写aof文件使它缩小
    复制
            slaveof
    客户端分片
    不完全事务
# 性能
    内存数据库，需要预估内存，使用key过期节约
    完整重同步占资源，可以部分重同步
    重启数据加载慢

    master内存快照时，save命令调rdbSave阻塞主线程
    master AOF持久化，追加文件大时影响master重启恢复速度
        用slave AOF
    master调用BGREWRITEAOF重写AOF文件时，cpu和内存负载高
    主从复制最好同局域网
## 数据
    set mykey somvalue
    get mykey
    del mykey
    incr
    decr
    incrby
    decrby
    incrbyfloat
    append
    getrange
    setrange
    getbit
    setbit
    bitcount
            # 二进制位串位为1的数量
    bitop
            # 二进制位串执行and, or, xor, not

    rpush list-key item
    lpush
    lrange list-key 0 -1
            # -1为结束索引
    lindex list-key 1
    rpop
    lpop list-key
    lrange
    ltrim
            # 修剪
    blpop
            # timeout秒内阻塞并等待弹出元素
    brpop
    rpoplpush
            # 一个列表中右弹元素推入另一个列表左端，最后返回这个元素
    brpoplpush

    sadd set-key item
    smembers set-key
    sismember set-key item
    srem set-key item
            # 删除，返回删除的数量
    scard
            # 元素数
    srandmember
            # 随机返回一个或多个元素。count正数时，返回的元素不重复, 负数时可重复
    spop
            # 随机移除一个元素
    smove
            # 一个集合中移除，并在一个集合中添加。返回移除的数量
    sdiff
            # 差集
    sdiffstore
            # 差集生成集合
    sinter
            # 交集
    sinterstore
    sunion
            # 并集
    sunionstore

    hset hash-key sub-key value
    hget hash-key sub-key
    hdel hash-key sub-key
    hlen
    hexists hash-key sub-key
    hkeys hash-key
    hvals
    hgetall hash-key
    hincrbyfloat
    hincrby hash-key field -1
    hmget
    hmset hash-key field1 "foo" field2 "bar"

    zadd zset-key 728 member
    zrange zset-key 0 -1 withscores
    zrevrange zset-key 0 -1 withscores
    zrangebyscore zset-key 0 800 withscores
            # 根据score范围查找
    zrevrangebyscore
    zrem zset-key member
    zremrangebyrank
    zremrangebyscore
    zincrby
    zinterstore sum 3 sub1 sub2 sub3
            # 生成交集, 重复值score相加, 3 指定可变参数的数量
    zunionstore
            # 并集
    zcard
            # 成员数量
    zcount        
            # 分值之间的成员数量
    zrank
            # 返回排名
    zrevrank
    zscore
            # 返回分值
# client
    jedis
        # java, 支持redis sharding, 即ShardedJedis结合ShardedJedisPool

        Jedis jedis = new Jedis("localhost");                        # 连接redis数据库
        jedis.set("name", "aa");                                                # 添加、覆盖
        jedis.append("name", "bb");                                                # 追加，结果为 name=aabb
        jedis.get("name");                                                                # 取值
        jedis.del("name");                                                                # 删除
        jedis.mset("name1", "aa", "name2", "bb");                # 批量添加、覆盖
        jedis.mget("name1", "name2")                                        # 批量取值
# 分布式
    redisCluster
    twemProxy
        # twitter开发的redis集群代理
    redisMonitor
    redisSentinel
        # 主从复制，高可用
    codis
        # 豌豆荚开发的redis集群代理
# 持久化
    方式
        无持久化
        RDB
            # 一段时间备份一个RDB文件，RDB文件很紧凑。用fork子进程的方式备份，恢复速度快
            # 服务器故障时，会丢当前时段数据。数据集大时，fork耗时出现停止服务(毫秒至1秒)
            point-in-time dump
                dump-to-disk二条命令
        AOF
            # 记录写操作, AOF先于RDB
            # fsync不fork在后台执行, 追加写文件，文件大时自动重写
            # AOF文件结构不紧凑，AOF速度慢于RDB(关闭fsync一样快)
            append-only文件
            fsync策略
                从不同步
                每秒同步一次      # 只丢一秒数据
                一命令同步一次
    策略
    配置
        save 60 1000
                # 60秒内有1000次写入时，自动save
        stop-writes-on-bgsave-error no
        rdbcompression yes
        dbfilename dump.rdb

        appendonly no
                # 打开AOF
        appendfsync everysec
                always
                        # 每个写命令都马上同步
                everysec
                        # 每秒
                no
                        # 操作系统决定
        no-appendfsync-on-rewrite no
        auto-aof-rewrite-percentage 100
        auto-aof-rewrite-min-size 64mb

        dir ./