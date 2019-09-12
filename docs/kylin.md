## 说明

Apache Kylin™是一个开源的分布式分析引擎，提供Hadoop/Spark之上的SQL查询接口及多维分析（OLAP）能力以支持超大规模数据，最初由eBay Inc. 开发并贡献至开源社区。它能在亚秒内查询巨大的Hive表。



###  download

Apache-kylin：[link](http://mirrors.tuna.tsinghua.edu.cn/apache/kylin/apache-kylin-2.3.1/apache-kylin-2.3.1-cdh57-bin.tar.gz)



### 安装

```bash
tar –xzvf apache-kylin-2.3.1-cdh57-bin.tar.gz –C /usr/
cd /usr/
mv apache-kylin-2.3.1-cdh57 kylin


#三台机都需要此操作
vim /etc/profile 
#在最下面追加以下内容，并保存


```

```
export KYLIN_HOME=/usr/kylin
export PATH=$PATH:$KYLYN_HOME/bin

export BASE_PATH=/opt/cloudera/parcels/CDH/lib
export HBASE_HOME=$BASE_PATH/hbase
export PATH=$HBASE_HOME/bin:$PATH
export HCAT_HOME=$BASE_PATH/hive-hcatalog
```

```bash
#三台机都需要此操作
#修改kylin下的配置文件kylin.properties
vim /usr/kylin/conf/kylin.properties
```

```
#在文件最下面追加以下内容，并保存
kylin.metadata.url=kylin_metadata@hbase
kylin.server.mode=all       #hadoop1机器写all，其余为query
kylin.server.cluster-servers=hadoop1:7070    #每台机写自己的主机名
kylin.rest.servers=hadoop1:7070,hadoop2:7070,hadoop3:7070
kylin.job.jar=/usr/kylin/lib/kylin-job-2.3.1.jar
kylin.coprocessor.local.jar=/usr/kylin/lib/kylin-coprocessor-2.3.1.jar
```

```bash
#三台机都需要此操作
chown -R hdfs /usr/kylin

#任意一台机器操作
cd /usr/kylin/bin/
./kylin.sh start
```

