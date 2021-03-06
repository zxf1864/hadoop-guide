## Hadoop2.x的安装与配置

### （一）Hadoop安装部署的预备条件

![image](https://github.com/MrQuJL/hadoop-guide/blob/master/03-Hadoop/imgs/hadoop-logo.jpg)

* 安装Linux

* 安装JDK

### （二）Hadoop的目录结构

![image](https://github.com/MrQuJL/hadoop-guide/blob/master/03-Hadoop/imgs/hadoop.png)

### （三）Hadoop安装部署的三种模式

* 本地模式

参数文件 | 配置参数 | 参考值
---|---|---
hadoop-env.sh | JAVA_HOME | /root/training/jdk1.8.0_144

* 伪分布模式

参数文件 | 配置参数 | 参考值
---|---|---
hadoop-env.sh | JAVA_HOME | /root/training/jdk1.8.0_144
hdfs-site.xml | dfs.replication | 1
... | dfs.permissions | false
core-site.xml | fs.defaultFS | hdfs://<hostname>:9000
... | hadoop.tmp.dir | /root/training/hadoop-2.7.3/tmp
mapred-site.xml | mapreduce.framework.name | yarn
yarn-site.xml | yarn.resourcemanager.hostname | <hostname>
... | yarn.nodemanager.aux-services | mapreduce_shuffle

* 全分布模式

参数文件 | 配置参数 | 参考值
---|---|---
hadoop-env.sh | JAVA_HOME | /root/training/jdk1.8.0_144
hdfs-site.xml | dfs.replication | 2
... | dfs.permissions | false
core-site.xml | fs.defaultFS | hdfs://<hostname>:9000
... | hadoop.tmp.dir | /root/training/hadoop-2.7.3/tmp
mapred-site.xml | mapreduce.framework.name | yarn
yarn-site.xml | yarn.resourcemanager.hostname | <hostname>
... | yarn.nodemanager.aux-services | mapreduce_shuffle
slaves | DataNode的ip地址或主机名 | qujianlei001

如果出现以下警告信息：

![image](https://github.com/MrQuJL/hadoop-guide/blob/master/03-Hadoop/imgs/warn.png)

只需要在以下两个文件中增加下面的环境变量，即可：

* hadoop-env.sh 脚本中：

	export JAVA_HOME=/root/training/jdk1.8.0_144
	export HADOOP_HOME=/root/training/hadoop-2.7.3
	export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
	export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"

* yarn-env.sh 脚本中：

	export JAVA_HOME=/root/training/jdk1.8.0_144
	export HADOOP_HOME=/root/training/hadoop-2.7.3
	export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
	export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"

### （四）验证Hadoop环境

* HDFS Console：http://192.168.157.11:50070

	![image](https://github.com/MrQuJL/hadoop-guide/blob/master/03-Hadoop/imgs/HDFSConsole.png)

* Yarn Console：http://192.168.157.11:8088

	![image](https://github.com/MrQuJL/hadoop-guide/blob/master/03-Hadoop/imgs/YARNConsole.png)

### （五）配置SSH免密登录

![image](https://github.com/MrQuJL/hadoop-guide/blob/master/03-Hadoop/imgs/ssh.png)

详细操作见：https://blog.csdn.net/a909301740/article/details/84147035















