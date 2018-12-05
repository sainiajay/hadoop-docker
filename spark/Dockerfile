FROM sainiajay/scala-docker

MAINTAINER Ajay Saini <saini.ajay172@gmail.com>

USER root

ENV SPARK_VERSION=2.4.0 \
    SPARK_HOME=/usr/share/spark

RUN cd "/tmp" && \
    wget "https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-without-hadoop.tgz" && \
    tar xzf "spark-${SPARK_VERSION}-bin-without-hadoop.tgz" && \
    rm "/tmp/spark-${SPARK_VERSION}-bin-without-hadoop/bin/"*.cmd && \
    mv "/tmp/spark-${SPARK_VERSION}-bin-without-hadoop" "${SPARK_HOME}" && \
    ln -s "${SPARK_HOME}/bin/"* "/usr/bin/" && \
    rm -rf "/tmp/"*