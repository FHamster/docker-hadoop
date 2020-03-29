FROM alpine:3.10

MAINTAINER GaoXin <gaoxin459716010@163.com>

RUN apk add --no-cache curl bash openjdk8-jre python3 py-pip nss libc6-compat perl \
      && ln -s /lib64/ld-linux-x86-64.so.2 /lib/ld-linux-x86-64.so.2
#    \ && chmod +x *.sh \
#RUN wget https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz \
#      && tar -xvzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz \
#      && mv spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark \
#      && rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz \
#      && cd /css \
#      && jar uf /spark/jars/spark-core_2.11-${SPARK_VERSION}.jar org/apache/spark/ui/static/timeline-view.css \
#      && cd /

#RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
#      openjdk-8-jdk \
#      net-tools \
#      curl \
#      netcat \
#      gnupg \
#    && rm -rf /var/lib/apt/lists/*
#
ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk/

#ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/
#
#RUN curl -O https://dist.apache.org/repos/dist/release/hadoop/common/KEYS
#
#RUN gpg --import KEYS
#
ENV HADOOP_VERSION 3.2.1
#ENV HADOOP_URL http://mirror.bit.edu.cn/apache/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz
ENV HADOOP_URL https://www.apache.org/dist/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz
#
RUN set -x \
    && curl -fSL "$HADOOP_URL" -o /tmp/hadoop.tar.gz \
#    && curl -fSL "$HADOOP_URL.asc" -o /tmp/hadoop.tar.gz.asc \
#    && gpg --verify /tmp/hadoop.tar.gz.asc \
    && tar -xvf /tmp/hadoop.tar.gz -C /opt/ \
    && rm /tmp/hadoop.tar.gz*

RUN ln -s /opt/hadoop-$HADOOP_VERSION/etc/hadoop /etc/hadoop

RUN mkdir /opt/hadoop-$HADOOP_VERSION/logs

RUN mkdir /hadoop-data

ENV HADOOP_HOME=/opt/hadoop-$HADOOP_VERSION
ENV HADOOP_CONF_DIR=/etc/hadoop
ENV MULTIHOMED_NETWORK=1
ENV USER=root
ENV PATH $HADOOP_HOME/bin/:$PATH

ADD entrypoint.sh /entrypoint.sh

RUN chmod a+x /entrypoint.sh

#ENTRYPOINT ["/bin/bash"]
ENTRYPOINT ["/entrypoint.sh","/bin/bash"]
