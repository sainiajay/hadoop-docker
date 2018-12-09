FROM sainiajay/oraclejdk

MAINTAINER Ajay Saini <saini.ajay172@gmail.com>

USER root

# Install Hadoop
ENV HADOOP_VER=2.9.1 \
    HADOOP_HOME=/usr/local/hadoop \
    HDFS_NAMENODE_USER=root \
    HDFS_DATANODE_USER=root \
    HDFS_SECONDARYNAMENODE_USER=root \
    YARN_RESOURCEMANAGER_USER=root \
    YARN_NODEMANAGER_USER=root \
    HADOOP_COMMON_HOME=$HADOOP_HOME \
    HADOOP_HDFS_HOME=$HADOOP_HOME \
    HADOOP_MAPRED_HOME=$HADOOP_HOME \
    HADOOP_YARN_HOME=$HADOOP_HOME \
    HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop \
    PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin

RUN apk add --no-cache openssl openssh && \
    wget -O hadoop.tar.gz https://archive.apache.org/dist/hadoop/common/hadoop-$HADOOP_VER/hadoop-$HADOOP_VER.tar.gz && \
    tar -xzf hadoop.tar.gz -C /usr/local/ && \
    rm hadoop.tar.gz && \
    ln -s /usr/local/hadoop-$HADOOP_VER $HADOOP_HOME && \
    mkdir $HADOOP_HOME/logs

#Passwordless SSH
RUN ssh-keygen -qAN "" && \
    ssh-keygen -qN "" -t rsa -f /root/.ssh/id_rsa && \
    cp /root/.ssh/id_rsa.pub /root/.ssh/authorized_keys && \
    /usr/sbin/sshd -D

WORKDIR $HADOOP_HOME
