---


---

<h1 id="zookeeper-学习">zookeeper 学习</h1>
<h2 id="分布式应用">分布式应用</h2>
<p>分布式应用可以在给定时间（同时）在网络中的多个系统上运行，通过协调它们以快速有效的方式完成特定任务。通常来说，对于复杂而耗时的任务，非分布式应用（运行在单个系统中）需要几个小时才能完成，而分布式应用通过使用所有系统涉及的计算能力可以在几分钟内完成。</p>
<p>通过将分布式应用配置为在更多系统上运行，可以进一步减少完成任务的时间。分布式应用正在运行的一组系统称为<strong>集群</strong>，而在集群中运行的每台机器被称为<strong>节点</strong>。</p>
<p>分布式应用有两部分， <strong>Server（服务器）</strong> 和 <strong>Client（客户端）</strong> 应用程序。服务器应用程序实际上是分布式的，并具有通用接口，以便客户端可以连接到集群中的任何服务器并获得相同的结果。  客户端应用程序是与分布式应用进行交互的工具。</p>
<h2 id="一致-有头-数据树">一致 有头 数据树</h2>
<h3 id="解决分布式数据一致性问题">解决分布式数据一致性问题</h3>
<h3 id="提供数据集群">提供数据集群</h3>
<h3 id="gfsbigtablemapreduce">GFS/BigTable/MapReduce</h3>
<blockquote>
<p>HDFS / HBase / HadoopMR【计算框架】</p>
</blockquote>
<h3 id="报这种异常一般有三种情况：">报这种异常一般有三种情况：</h3>
<p>（1）：zoo.cfg配置文件中，server.x:2888:3888配置出现错误；<br>
（2）：myid文件内容和server.x不对应，或者myid不在data目录下；<br>
（3）：系统防火墙是否在启动。<br>
centos7下查看防火墙状态的命令：<br>
firewall-cmd  --state<br>
关闭防火墙的命令：<br>
systemctl  stop firewalld.service<br>
systemctl disable firewalld.service   （禁止开机启动，永久关闭防火墙）</p>
<h2 id="应用场景">应用场景</h2>
<h3 id="配置一致">配置一致</h3>
<blockquote>
<p>在zk中存储配置，观察者模式通知监听者</p>
</blockquote>
<h3 id="ha-高可用">HA 高可用</h3>
<blockquote>
<p>master节点将服务节点放入到zk中<br>
slave节点监听zk中数据是否消失，消失的时候写入自己的服务节点<br>
客户端从zk中获取服务节点</p>
</blockquote>
<h3 id="pubsub">pub/sub</h3>
<blockquote>
<p>监听者模式</p>
</blockquote>
<h3 id="name-service">name service</h3>
<h3 id="load-balance">load balance</h3>
<h3 id="分布式锁">分布式锁</h3>
<h1 id="zookeeper投票算法">zookeeper投票算法</h1>
<h2 id="fastleader选举算法">FastLeader选举算法</h2>
<h1 id="分布式系统cap理论-三者得其二">分布式系统CAP理论-三者得其二</h1>
<h2 id="consistency一致性">Consistency一致性</h2>
<h2 id="avaliability-可用性">Avaliability 可用性</h2>
<h2 id="partition-tolerance-可扩展性">Partition Tolerance 可扩展性</h2>

