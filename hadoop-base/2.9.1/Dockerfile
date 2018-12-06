FROM sainiajay/oraclejdk

MAINTAINER Ajay Saini <saini.ajay172@gmail.com>

USER root

# Passwordless SSH
# RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key
# RUN ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key
# RUN ssh-keygen -q -N "" -t rsa -f /root/.ssh/id_rsa
# RUN cp /root/.ssh/id_rsa.pub /root/.ssh/authorized_keys

# ADD ssh_config /root/.ssh/config
# RUN chmod 600 /root/.ssh/config
# RUN chown root:root /root/.ssh/config

# RUN echo "Port 2122" >> /etc/ssh/sshd_config

# Install Hadoop
ENV HADOOP_VER 2.9.1
ENV HADOOP_HOME /usr/local/hadoop
ENV PATH $PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin

ENV HDFS_NAMENODE_USER root
ENV HDFS_DATANODE_USER root
ENV HDFS_SECONDARYNAMENODE_USER root
ENV YARN_RESOURCEMANAGER_USER root
ENV YARN_NODEMANAGER_USER root

ENV HADOOP_COMMON_HOME $HADOOP_HOME
ENV HADOOP_HDFS_HOME $HADOOP_HOME
ENV HADOOP_MAPRED_HOME $HADOOP_HOME
ENV HADOOP_YARN_HOME $HADOOP_HOME
ENV HADOOP_CONF_DIR $HADOOP_HOME/etc/hadoop

RUN wget -O hadoop.tar.gz https://archive.apache.org/dist/hadoop/common/hadoop-$HADOOP_VER/hadoop-$HADOOP_VER.tar.gz && \
    tar -xzf hadoop.tar.gz -C /usr/local/ && \
    rm hadoop.tar.gz && \
    ln -s /usr/local/hadoop-$HADOOP_VER $HADOOP_HOME && \
    mkdir $HADOOP_HOME/logs && \
    ssh-keygen -AP "" && \
    cp /root/.ssh/id_rsa.pub /root/.ssh/authorized_keys && \
    /usr/sbin/sshd

WORKDIR $HADOOP_HOME
