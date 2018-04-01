# Session一致性问题
## ngnix + 多appserver登陆的时候
### 方法一 ngnix ip_hash
	 ngnix使用ip_hash,对于同一个iphash落在同一个appserver上
	 appserver应用不需要修改
	 缺点：类似于单点故障session丢失，负载高
### 方法二 tomcat session复制
    服务器session复制
    tomcat服务器创建session后，会通过组播方式广播到其他tomcat集群中
    缺点：网络占用，占用资源
### 方法三 session集中统一管理
    session不是由应用服务器管理，而是统一放到一个地方集中管理，读取和写入session都依赖于其他第3方软件，如redis、mongodb、mysql等
